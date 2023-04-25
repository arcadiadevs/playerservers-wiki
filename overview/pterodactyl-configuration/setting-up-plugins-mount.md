---
description: Learn how to setup plugins repository as a mount for your Pterodactyl servers.
---

# ⛲ Setting up plugins mount

## Introduction

In order for your players to be able to install plugins via plugin management GUI, we need to mount the plugins repository folder to each of your virtualised containers (servers).

Unfortunately, Pterodactyl doesn't provide an API for that at the moment (until v2 is out), so we will need to perform a quick modification on your Pterodactyl's code.

{% hint style="info" %}
**You will need to perform these modifications every time you update Pterodactyl.**
{% endhint %}

## Instructions

1. Navigate to your Pterodactyl folder, preferably via some kind of SFTP file manager, like [WinSCP](https://winscp.net/eng/download.php) or [CyberDuck](https://cyberduck.io/). The directory is usually `/var/www/pterodactyl`.
2. Open up `app/Http/Controllers/Api/Application/Servers/ServerManagementController.php` preferably using some sort of text editor, like [VSCode](https://code.visualstudio.com/) or Notepad++.
   1.  Below all imports, paste `use Pterodactyl\Models\MountServer;` Your imports should look like the following:\


       {% code title="ServerManagementController.php" overflow="wrap" lineNumbers="true" %}
       ```php
       <?php

       namespace Pterodactyl\Http\Controllers\Api\Application\Servers;

       use Illuminate\Http\Response;
       use Pterodactyl\Models\Server;
       use Pterodactyl\Services\Servers\SuspensionService;
       use Pterodactyl\Services\Servers\ReinstallServerService;
       use Pterodactyl\Http\Requests\Api\Application\Servers\ServerWriteRequest;
       use Pterodactyl\Http\Controllers\Api\Application\ApplicationApiController;
       use Pterodactyl\Models\MountServer; # This is the line we added
       ```
       {% endcode %}


   2.  Below reinstall function, paste the following code block:\


       {% code title="ServerManagementController.php" overflow="wrap" %}
       ```php
       public function mount(ServerWriteRequest $request, Server $server): Response
       {
           $mountServer = (new MountServer())->forceFill([
               'mount_id' => $request->input('mount_id'),
               'server_id' => $server->id,
           ]);

           $mountServer->saveOrFail();

           return $this->returnNoContent();
       }
       ```
       {% endcode %}


   3.  The end result will be the following file (which you may as well just copy and replace your whole file contents with, but a more manual approach like in steps 1 and 2 is recommended):\


       {% code title="ServerManagementController.php" lineNumbers="true" %}
       ```php
       <?php

       namespace Pterodactyl\Http\Controllers\Api\Application\Servers;

       use Illuminate\Http\Response;
       use Pterodactyl\Models\Server;
       use Pterodactyl\Services\Servers\SuspensionService;
       use Pterodactyl\Services\Servers\ReinstallServerService;
       use Pterodactyl\Http\Requests\Api\Application\Servers\ServerWriteRequest;
       use Pterodactyl\Http\Controllers\Api\Application\ApplicationApiController;
       use Pterodactyl\Models\MountServer; # This is the line we added

       class ServerManagementController extends ApplicationApiController
       {
           /**
            * ServerManagementController constructor.
            */
           public function __construct(
               private ReinstallServerService $reinstallServerService,
               private SuspensionService $suspensionService
           ) {
               parent::__construct();
           }

           /**
            * Suspend a server on the Panel.
            *
            * @throws \Throwable
            */
           public function suspend(ServerWriteRequest $request, Server $server): Response
           {
               $this->suspensionService->toggle($server);

               return $this->returnNoContent();
           }

           /**
            * Unsuspend a server on the Panel.
            *
            * @throws \Throwable
            */
           public function unsuspend(ServerWriteRequest $request, Server $server): Response
           {
               $this->suspensionService->toggle($server, SuspensionService::ACTION_UNSUSPEND);

               return $this->returnNoContent();
           }

           /**
            * Mark a server as needing to be reinstalled.
            *
            * @throws \Pterodactyl\Exceptions\DisplayException
            * @throws \Pterodactyl\Exceptions\Model\DataValidationException
            * @throws \Pterodactyl\Exceptions\Repository\RecordNotFoundException
            */
           public function reinstall(ServerWriteRequest $request, Server $server): Response
           {
               $this->reinstallServerService->handle($server);

               return $this->returnNoContent();
           }

           # Our mount function
           public function mount(ServerWriteRequest $request, Server $server): Response
           {
               $mountServer = (new MountServer())->forceFill([
                   'mount_id' => $request->input('mount_id'),
                   'server_id' => $server->id,
               ]);

               $mountServer->saveOrFail();

               return $this->returnNoContent();
           }
       }
       ```
       {% endcode %}


3. Now navigate to app/routes/api-application.php and open it.
   1.  Below the following line:

       {% code overflow="wrap" %}
       ```php
       Route::post('/{server:id}/reinstall', [Application\Servers\ServerManagementController::class, 'reinstall'])->name('api.application.servers.reinstall');
       ```
       {% endcode %}

       \
       Paste this line\


       {% code overflow="wrap" %}
       ```php
       Route::post('/{server:id}/mount', [Application\Servers\ServerManagementController::class, 'mount'])->name('api.application.servers.mount');
       ```
       {% endcode %}


   2.  The end result should look like the following. You can also just use it to completely copy-paste the content to your api-application.php, but a more manual approach like in step 1 is preferred as Pterodactyl may do additional modifications to this file in the future.\


       {% code title="api-application.php" lineNumbers="true" %}
       ```php
       <?php

       use Illuminate\Support\Facades\Route;
       use Pterodactyl\Http\Controllers\Api\Application;

       /*
       |--------------------------------------------------------------------------
       | User Controller Routes
       |--------------------------------------------------------------------------
       |
       | Endpoint: /api/application/users
       |
       */

       Route::group(['prefix' => '/users'], function () {
           Route::get('/', [Application\Users\UserController::class, 'index'])->name('api.application.users');
           Route::get('/{user:id}', [Application\Users\UserController::class, 'view'])->name('api.application.users.view');
           Route::get('/external/{external_id}', [Application\Users\ExternalUserController::class, 'index'])->name('api.application.users.external');

           Route::post('/', [Application\Users\UserController::class, 'store']);
           Route::patch('/{user:id}', [Application\Users\UserController::class, 'update']);

           Route::delete('/{user:id}', [Application\Users\UserController::class, 'delete']);
       });

       /*
       |--------------------------------------------------------------------------
       | Node Controller Routes
       |--------------------------------------------------------------------------
       |
       | Endpoint: /api/application/nodes
       |
       */
       Route::group(['prefix' => '/nodes'], function () {
           Route::get('/', [Application\Nodes\NodeController::class, 'index'])->name('api.application.nodes');
           Route::get('/deployable', Application\Nodes\NodeDeploymentController::class);
           Route::get('/{node:id}', [Application\Nodes\NodeController::class, 'view'])->name('api.application.nodes.view');
           Route::get('/{node:id}/configuration', Application\Nodes\NodeConfigurationController::class);

           Route::post('/', [Application\Nodes\NodeController::class, 'store']);
           Route::patch('/{node:id}', [Application\Nodes\NodeController::class, 'update']);

           Route::delete('/{node:id}', [Application\Nodes\NodeController::class, 'delete']);

           Route::group(['prefix' => '/{node:id}/allocations'], function () {
               Route::get('/', [Application\Nodes\AllocationController::class, 'index'])->name('api.application.allocations');
               Route::post('/', [Application\Nodes\AllocationController::class, 'store']);
               Route::delete('/{allocation:id}', [Application\Nodes\AllocationController::class, 'delete'])->name('api.application.allocations.view');
           });
       });

       /*
       |--------------------------------------------------------------------------
       | Location Controller Routes
       |--------------------------------------------------------------------------
       |
       | Endpoint: /api/application/locations
       |
       */
       Route::group(['prefix' => '/locations'], function () {
           Route::get('/', [Application\Locations\LocationController::class, 'index'])->name('api.applications.locations');
           Route::get('/{location:id}', [Application\Locations\LocationController::class, 'view'])->name('api.application.locations.view');

           Route::post('/', [Application\Locations\LocationController::class, 'store']);
           Route::patch('/{location:id}', [Application\Locations\LocationController::class, 'update']);

           Route::delete('/{location:id}', [Application\Locations\LocationController::class, 'delete']);
       });

       /*
       |--------------------------------------------------------------------------
       | Server Controller Routes
       |--------------------------------------------------------------------------
       |
       | Endpoint: /api/application/servers
       |
       */
       Route::group(['prefix' => '/servers'], function () {
           Route::get('/', [Application\Servers\ServerController::class, 'index'])->name('api.application.servers');
           Route::get('/{server:id}', [Application\Servers\ServerController::class, 'view'])->name('api.application.servers.view');
           Route::get('/external/{external_id}', [Application\Servers\ExternalServerController::class, 'index'])->name('api.application.servers.external');

           Route::patch('/{server:id}/details', [Application\Servers\ServerDetailsController::class, 'details'])->name('api.application.servers.details');
           Route::patch('/{server:id}/build', [Application\Servers\ServerDetailsController::class, 'build'])->name('api.application.servers.build');
           Route::patch('/{server:id}/startup', [Application\Servers\StartupController::class, 'index'])->name('api.application.servers.startup');

           Route::post('/', [Application\Servers\ServerController::class, 'store']);
           Route::post('/{server:id}/suspend', [Application\Servers\ServerManagementController::class, 'suspend'])->name('api.application.servers.suspend');
           Route::post('/{server:id}/unsuspend', [Application\Servers\ServerManagementController::class, 'unsuspend'])->name('api.application.servers.unsuspend');
           Route::post('/{server:id}/reinstall', [Application\Servers\ServerManagementController::class, 'reinstall'])->name('api.application.servers.reinstall');
           # The line we added (below)
           Route::post('/{server:id}/mount', [Application\Servers\ServerManagementController::class, 'mount'])->name('api.application.servers.mount');

           Route::delete('/{server:id}', [Application\Servers\ServerController::class, 'delete']);
           Route::delete('/{server:id}/{force?}', [Application\Servers\ServerController::class, 'delete']);

           // Database Management Endpoint
           Route::group(['prefix' => '/{server:id}/databases'], function () {
               Route::get('/', [Application\Servers\DatabaseController::class, 'index'])->name('api.application.servers.databases');
               Route::get('/{database:id}', [Application\Servers\DatabaseController::class, 'view'])->name('api.application.servers.databases.view');

               Route::post('/', [Application\Servers\DatabaseController::class, 'store']);
               Route::post('/{database:id}/reset-password', [Application\Servers\DatabaseController::class, 'resetPassword']);

               Route::delete('/{database:id}', [Application\Servers\DatabaseController::class, 'delete']);
           });
       });

       /*
       |--------------------------------------------------------------------------
       | Nest Controller Routes
       |--------------------------------------------------------------------------
       |
       | Endpoint: /api/application/nests
       |
       */
       Route::group(['prefix' => '/nests'], function () {
           Route::get('/', [Application\Nests\NestController::class, 'index'])->name('api.application.nests');
           Route::get('/{nest:id}', [Application\Nests\NestController::class, 'view'])->name('api.application.nests.view');

           // Egg Management Endpoint
           Route::group(['prefix' => '/{nest:id}/eggs'], function () {
               Route::get('/', [Application\Nests\EggController::class, 'index'])->name('api.application.nests.eggs');
               Route::get('/{egg:id}', [Application\Nests\EggController::class, 'view'])->name('api.application.nests.eggs.view');
           });
       });
       ```
       {% endcode %}


4. Now cd into your Pterodactyl folder via the following command: `cd /var/www/pterodactyl`
5.  Execute the following commands:\


    ```shell-session
    root@pterodactyl:/var/www/pterodactyl# php artisan optimize:clear

       INFO  Clearing cached bootstrap files.  

      events .................................................................................................................................. 5ms DONE
      views ................................................................................................................................... 6ms DONE
      cache ................................................................................................................................... 6ms DONE
      route ................................................................................................................................... 1ms DONE
      config .................................................................................................................................. 1ms DONE
      compiled ................................................................................................................................ 2ms DONE

    root@pterodactyl:/var/www/pterodactyl# php artisan optimize

       INFO  Caching the framework bootstrap files.  

      config ................................................................................................................................. 25ms DONE
      routes ................................................................................................................................. 59ms DONE
    ```


6.  After that's done, we can now create our mount. Go to the mounts tab on your Pterodactyl admin panel and click the Create New and fill the fields as in the following example. Make sure to name Target folder as /plugins-repo. Source folder should be set to the path of your plugins folder.\


    <figure><img src="../../.gitbook/assets/Screenshot 2023-04-25 at 21.37.19.png" alt=""><figcaption><p>Mount creation example</p></figcaption></figure>
