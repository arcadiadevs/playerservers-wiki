# 📜 Current Config files

{% hint style="info" %}
The below page explains how to use this feature on PlayerServers 3. This is only relevant if you're a beta tester. To view this page for PlayerServers 2, click [here.](../legacy/config.md)
{% endhint %}

Below you can see the contents of the newest BungeeCord PlayerServers configuration file.

{% hint style="info" %}
Please note that in some extremely rare cases I may **forget to update the config** on this page. For the most up to date config.yml and messages.yml, click [here](https://github.com/arcadiadevs/playerservers-everything).
{% endhint %}

```yaml
#  __________.__                             _________
#  \______   \  | _____  ___.__. ___________/   _____/ ______________  __ ___________  ______
#  |     ___/  | \__  \<   |  |/ __ \_  __ \_____  \_/ __ \_  __ \  \/ // __ \_  __ \/  ___/
#  |    |   |  |__/ __ \\___  \  ___/|  | \/        \  ___/|  | \/\   /\  ___/|  | \/\___ \
#  |____|   |____(____  / ____|\___  >__| /_______  /\___  >__|    \_/  \___  >__|  /____  >
#                     \/\/         \/             \/     \/                 \/           \/
#
# An advanced plugin which allows your players to create their own sub-servers, created by thearcadia.xyz

# Please enter your MySQL information below.
mysql:
  # Url of the MySQL server, in format: jdbc:mysql://<host>:<port>/<database>
  # Any additional options can be added at the end of url, such as:
  # ?autoReconnect=true&useSSL=false?useUnicode=true&characterEncoding=UTF-8
  url: "jdbc:mysql://localhost:3306/playerservers?useSSL=false&serverTimezone=UTC"

  username: root
  password: root

  # Developer options, do not change unless you know what you are doing.
  driver: "com.mysql.cj.jdbc.Driver"
  update-policy: "update"
  debug: false
  get-from-file: false

# Should we automatically update the server core to the latest version
# for all sub-servers upon server restart?
auto-update-server-core: true

# Where should players be moved after they /stop or /ps kill their server?
balancer:
  - Hub1
  - Hub2

# Use player-name instead of server UUID? Basically, when turned on, server-names
# will be equal to player username instead of (for example) aa386b6h
use-usernames: true


# Should we use domain name instead of IP address for servers?
use-subdomain:
  # Should we enable custom subdomain formatting?
  enabled: false

  # What is the API key that we should use?
  # To create an API token, from the Cloudflare dashboard,
  # go to My Profile > API Tokens and select Create Token.
  # When creating the token, select the following permissions:
    # - Zone > DNS > Edit
  api-key: ""

  # What is the IP address that we should use?
  # If you want to use auto-detection, set this to "auto"
  # If you want to use a specific IP address, set this to the IP address
  network-ip: "auto"

  # What is the zone ID that we should use?
  zone-id: ""

  # What is the domain name that we should use?
  domain: "example.com"

  # What is the subdomain format?
  # %id% equals to player name or uuid depending on use-usernames option
  # %uuid% is a random UUID (independent of use-usernames option)
  # %uuid_short% is a random UUID without dashes (independent of use-usernames option)
  # %player% is the player name (independent of use-usernames option)
  # %playeruuid% is the player UUID
  # %playeruuid_short% is the player UUID without dashes
  # %timestamp% is a timestamp in milliseconds
  # %timestampshort% is a timestamp in seconds
  # %day% is a day of the month
  # %month% is a month of the year
  # %year% is a year
  #
  # To find out what a UUID looks like, you can use this website:
  # https://www.uuidgenerator.net
  sub-domain: "%player%"

server-name-format:
  # Should we enable custom server name formatting?
  enabled: false

  # Which format should we use?
  # %id% equals to player name or uuid depending on use-usernames option
  # %uuid% is a random UUID (independent of use-usernames option)
  # %uuid_short% is a random UUID without dashes (independent of use-usernames option)
  # %player% is the player name (independent of use-usernames option)
  # %playeruuid% is the player UUID
  # %playeruuid_short% is the player UUID without dashes
  # %timestamp% is a timestamp in milliseconds
  # %timestampshort% is a timestamp in seconds
  # %day% is a day of the month
  # %month% is a month of the year
  # %year% is a year
  #
  # To find out what a UUID looks like, you can use this website:
  # https://www.uuidgenerator.net
  format: "PS_%id%"

# What is the max amount of servers that can be running at once?
max-running-instances: 15

# If there are no online players, and the last join was before
# more than minutes-to-shutdown, the server will automatically shutdown
# to allow more space for active ones.
minutes-to-shutdown: 15

# After how many seconds after executing cp -r <templatefile> <yourserverfolder>
# should we launch the server? Increase this if you get could not connect message.
copy-delay: 3

ram-limiting:
  # Should we use permissions for ram management? If set to true, you MUST give
  # your players permission playerserver.ram.<amount> (ex: playerserver.ram.512)
  # or, else, the command will be blocked, and player will not be able to create
  # the server. If set to false, everyone will have ram-per-server amount of RAM.
  use-permissions: false

  # How much RAM (in MB) should we allocate to each PlayerServer?
  ram-per-server: 512

cpu-limiting:
  # Should we use permissions for cpu management? If set to true, you MUST give
  # your players permission playerserver.cpu.<amount> (ex: playerserver.cpu.1)
  # or, else, the command will be blocked, and player will not be able to create
  # the server. If set to false, everyone will have cpu-per-server amount of CPU.
  use-permissions: false

  # How much CPU (in %) should we allocate to each PlayerServer?
  cpu-per-server: 50

disk-limiting:
    # Should we use permissions for disk management? If set to true, you MUST give
    # your players permission playerserver.disk.<amount> (ex: playerserver.disk.256)
    # or, else, the command will be blocked, and player will not be able to create
    # the server. If set to false, everyone will have disk-per-server amount of disk.
    use-permissions: false

    # How much disk (in MB) should we allocate to each PlayerServer?
    disk-per-server: 1024

player-limiting:
  # Should we use permissions for max-players management? If set to true, your
  # players should have playerserver.players.<amount>. The max amount of players
  # that you could give to a single server is 100000. You can also give them
  # playerserver.players.unlimited - for unlimited players. If the player
  # has no permission, he'll be able to have unlimited players.
  #
  # NOTE: If you use permissions, and you change player's permissions,
  # their server will need to reboot in order for changes to take place.
  use-permissions: false

  # What is the max players each server should have?
  max-players-per-server: 20

plugin-limiting:
  # Should we use permissions for max-plugins management? If set to true, your
  # players should have playerserver.plugins.<amount>. The max amount of plugins
  # that you could give to a single server is 20000. You can also give them
  # playerserver.plugins.unlimited - for unlimited plugins. If the player
  # has no permission, he'll be able to have unlimited players.
  #
  # NOTE: If you use permissions, and you change player's permissions,
  # their server will need to reboot in order for changes to take place.
  use-permissions: false

  # What is the max players each server should have?
  max-plugins-per-server: 20

# Should we enable smart /ps command? You can find more info about it here:
# https://gitlab.com/OpenSource02/playerservers/-/issues/21
smart-command: false

# Should we enable permissions for server creation, deletion & more?
# If set to false, all the players will have access to those basic commands.
# Obviously, admin commands require permission no matter what.
enable-permissions: true

# Should we disable OOM killer? If set to true, the server will not be
# killed if it runs out of memory, but will instead slowly crash.
# Enable this if your server is crashing due to OOM killer.
disable-oom-killer: false

# Templates will not work on Pterodactyl.
templates:
  default:
    # This is just an example of what you can do with requires-permission.
    # Default template will never require permission, even if set to true.
    requires-permission: false

    # The plugin is built around itzg/minecraft-server as a base image.
    # You can use any image you want, but we do not provide support for it.
    # Use variables below to customize the way your server will be created.
    docker-image: "itzg/minecraft-server"

    # The type of the server jar. Can be "SPIGOT", "PAPER", "PUFFERFISH",
    # "PURPUR", "MAGMA", "FORGE", "FABRIC" and much more.
    #
    # For a full list of supported server jars, check out this link:
    # https://github.com/itzg/docker-minecraft-server/blob/master/README.md#server-types
    type: "PAPER"

    # The version of the template. Paper jar will be downloaded automatically
    # Please avoid using non-standard versions such as 1.7.5 or 1.10 or 1.17.1
    # If you use LATEST, server will always automatically update to the latest
    # version of Minecraft available, as soon as server is restarted.
    # If you use SNAPSHOT, server will always automatically update to the latest
    # snapshot version of Minecraft available, as soon as server is restarted.
    # SNAPSHOT may not work on all types of servers.
    version: "1.8.8"

    # These variables are always sent if you use the default docker image
    # (itzg/minecraft-server) and can not be changed.
    #
    # EULA=true
    # TYPE=%typeFromAbove%
    # VERSION=%versionFromAbove%
    # ONLINE_MODE=false
    # SERVER_PORT=%serverPort%
    #
    # Below you can add more variables for this image or in case you use a custom one.
    # Format: VARIABLE_NAME: "VARIABLE_VALUE"
    variables:
      USE_NATIVE_TRANSPORT: "false" # Required for older versions of Minecraft

# Which folders or files will not show in /config file manager?
disabled-access:
  - "ExampleFolder"
  - "Plugin.jar"

pterodactyl:
  # Should we enable Pterodactyl deployment? If set to true, you don't need
  # to configure PlayerServers Daemon. All deployments will be done by Pterodactyl.
  enabled: false

  # Url of your panel. Example: https://panel.example.com
  # Make sure not to have / at the end!!
  url: "http://localhost:8080"

  # Application token can be created under "Admin" -> "Application API."
  # Make sure to give it read/write access:
  # - Servers
  # - Allocations
  # - Users
  # For everything else except "server databases", give it read-only access.
  application-token: "token"

  # Client token can be generated under "Account" -> "API Credentials."
  # Url: https://panel.example.com/account/api
  # This token must be generated by an admin account.
  client-token: "token"

  # Important variables to configure. Make sure to enter valid nest and egg id from
  # which the servers will be deploy.
  # Location id is the ID of location used for load-balanced deployments.
  # Nodes under the selected location will be slowly filled up with servers.
  # MountID is the id of your plugins mount. If you don't have one, set it to -1.
  nest-id: 0
  egg-id: 0
  location-id: 0
  mount-id: -1

  # Should we print the docker container installation output to the user?
  # Could be useful for debugging, and nonetheless, it can be cool for the player :)
  install-output: true

  environment_map:
    SERVER_JARFILE: "server.jar"
    MINECRAFT_VERSION: "1.8.8"
```

## Current messages.toml

```toml
playerservers-default-cmd="&9PlayerServers> &7An advanced Server Management plugin which allows players to create and manage their own subserver."
license-msg="&9Licence> &7%license%"
no-server="&9Error> &7You don't own a server. Don't worry, you can create one by executing &a/ps create"
not-enough-arguments="&9Error> &7Not enough arguments. Please use &a/ps help &7for more information."
not-enough-arguments-kill="&9PlayerServers> &7Oops, not enough arguments: /playerserver kill stop <uuid (example: 1F4a2id)>"
not-enough-arguments-delete="&9PlayerServers> &7Not enough arguments. &a/playerservers admin delete <uuid>. Please keep in mind that you should not enter the full id. You should just enter the first part (example: if full UUID is 1234-5678-1223-5623, you should just enter 1234)."
no-permission="&9Error> &7Oops, it seems like you don't have permission to do that."
launching-server="&9PlayerServers> &7Your server is starting up. Please wait..."
server-online="&9PlayerServers> &7Your server is now online. You will be connected shortly. Your friends can use &a/server %uuid%&7 to connect."
server-offline="&9PlayerServers> &7Your server is offline. You can start it by executing &a/ps start&7."
already-have="&9PlayerServers> &7You already have a server!"
too-many-online="&9PlayerServers> &7You have too many servers online. Please wait until one of your servers is offline."
template-no-permission="&9PlayerServers> &7You don't have permission to use this template."
starting-creation="&9PlayerServers> &7Your server is being created. Please wait..."
teleporting-soon="&9PlayerServers> &7You will be teleported to your server in a few seconds."
sending-to-remote-server="&9PlayerServers> &7Sending you to your server..."
message="&9PlayerServers> &7%message%"
warning="&c&lAre you sure you want to do that? If you do, please repeat this command in the next 5 seconds."
successfully-renamed="&9PlayerServers> &7Your server has been successfully renamed."
too-long="&9Error> &7Your server name is too long. Please choose a shorter name."
invalid-characters="&9Error> &7Your server name contains invalid characters. Please choose a valid name."
rename-failed="&9Error> &7Renaming your server failed. Please try again later."
not-online="&9Error> &7Your server is not online."
successfully-killed="&9PlayerServers> &7Your server has been successfully killed."
connected="&9PlayerServers> &7You are being connected to your server..."
killing="&9PlayerServers> &7Killing your server..."
successfully-removed="&9PlayerServers> &7Your server has been successfully removed."
removing="&9PlayerServers> &7Deleting your server..."
remove-warning="&9PlayerServers> &7Are you sure you want to remove your server? If you do, please repeat this command in the next 5 seconds."
account-created-successfully="&9PlayerServers> &7Your account has been created successfully."
account-creation-failed="&9Error> &7Account creation failed. Please try again later.  Error: %error%"
server-created-successfully="&9PlayerServers> &7Your server has been created successfully on Pterodactyl panel. Please login at &6%link% &7 with username &6%username% &7 and password &6%password% &7 to manage your server."
server-creation-failed="&9Error> &7Server creation failed. Please try again later. Error: %error%"
no-port-available="&9Error> &7Oops, it seems like there are no ports available. Please try again later."
no-node-available="&9Error> &7Oops, it seems like there are no nodes available. Please try again later."
action-error="&9Error> &7Oops, it seems like there was an error while performing this action. Please try again later. Error: %error%"
node-created-successfully="&9PlayerServers> &7Node has been created successfully."
server-not-found="&9Error> &7Oops, we couldn't find that server."
not-enough-arguments-start="&9Error> &7You didn't provide enough arguments. Please use &a/ps admin start <uuid>&7."
sending-info-to-remote-server="&9PlayerServers> &7Sending information to the remote node..."
node-not-found="&9Error> &7Oops, we couldn't find that node."
node-removed-successfully="&9PlayerServers> &7Node has been removed successfully."
```
