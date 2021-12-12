---
description: >-
  Learn how to install and configure PlayerServers daemon and be the first to
  try out our experimental support for hosting your servers on multiple
  machines.
---

# Multi-Node Support

## Requirements

* Purchased PlayerServers. This addon is free of charge
* Have two (or more) machines
* Decent network connection
* At least 200MB of RAM dedicated to Daemon

## Instructions

{% hint style="info" %}
Before reading this, please read [update notes](https://www.spigotmc.org/resources/82268/update?update=359257) for version v1.0-dev2.
{% endhint %}

The installation process for PlayerServers Daemon, even in developer beta is pretty straight forward. The first thing you need to do is simply enable multi-node support under experimental options at the end of your configuration file. After that, just reboot your BungeeCord and let the plugin generate required files.

After that's done, create a folder Daemon (in /root directory, if possible). Download the following jar file and drop it into your Daemon folder:

{% file src="../.gitbook/assets/Daemon-v1.1 (1).zip" %}
Daemon v1.1 - Release
{% endfile %}

After that's done, run it for the first time by using `java -Xmx200M -jar Daemon.jar` in order to let it generate the required files. Now exit it by typing in `exit`. After that's done, configure both multinode.toml inside your BungeeCord/plugins/PlayerServers/multinode.toml and your Daemon config.toml which will be generated in your Daemon root directory - please don't forget to include the same key inside both configs!

As the last step, it is required to copy all your templates to each daemon. For example, if you have PS/templates/default and PS/templates/1.8, you need to have the exact same files across each daemon with exact same templates. **Each template MUST have Spigot.jar file inside it!**

Now, you can just make a start.sh script with the following code

```
screen -dmS Daemon java -Xmx200M -jar Daemon.jar
```

and just run it with sh `start.sh` in order to make your Daemon run 24/7 on a separate screen.

{% hint style="warning" %}
Great! You're done! Now, please note that PlayerServersDaemon is still under early-access development and may have a large amount of bugs. Please report all of those to our Issue tracker [here](https://gitlab.com/OpenSource02/playerservers/-/issues). Additionally, please take a backup of your MySQL Database and your server data before proceeding. It is important to note that we did take every possible step to reduce the amount of possible issues that can happen, but we do highly encounter you to take those steps, just to be on the safe side.
{% endhint %}

