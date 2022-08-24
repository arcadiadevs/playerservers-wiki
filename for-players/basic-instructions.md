---
description: >-
  Below you can find some of the basic instructions on how to create your
  sub-server, how to shut it down, how to boot it back up, and how to access it.
---

# Basic instructions

Please note that if you need help with those commands, you should ask them on your server's website, their forums, support page, on their email / twitter or their Discord. Please do **not join** our Discord for help with the commands. It's intended to give support for server owners, not their players.

{% tabs %}
{% tab title="Creating the server" %}
## Creating the server

In order to create your player-server, you just need to run the command below:

```
/playerserver create
```

After that, you'll get a message that your server is being created. If everything went fine, you'll be sent to your sub-server and you'll get a special code that other users will be able to use in order to teleport to your server. If not, you'll get an **error** message. In that case, please contact the server administrator.

{% hint style="warning" %}
**WARNING**: You can create only one subserver. The command above will NOT work if you already own one.
{% endhint %}
{% endtab %}

{% tab title="Deletion of your server" %}
In order to delete your server, you need to shut it down first. In order to do so, you first need to join your server. If you're unsure on how to do so, please type the command below:

```
/playerserver join
```

After that, you need to type the command below:

```
/stop
```

After stopping your server, you need to run the final command which will delete your server

```
/playerserver delete
```

If everything went successfully, your server should be deleted now. If something failed, you'll get an error code. In that case, please contact the server administrator
{% endtab %}

{% tab title="Stopping & Booting up your server" %}
## Shutting down your server

In order to stop your server, you just need to execute the command below, while you're connected to your server:

```
/stop
```

## Booting up your server

If your server is down, you just need to execute command below in order to boot it up:

```
/playerserver start
```
{% endtab %}

{% tab title="How to join your server" %}
## How to join your server

If you're on the main lobby, you just need to execute the command below in order to be teleported to your server:

```
/playerserver join
```

After being teleported, you'll get a command that your friends will be able to use to teleport to your server.

{% hint style="danger" %}
## I was not teleported! What now?!

If you were not teleported, it is most likely that your server is down. In order to boot it up, please click on the Stopping & Booting up your server section in order to get instructions on how to boot up your server.
{% endhint %}
{% endtab %}
{% endtabs %}
