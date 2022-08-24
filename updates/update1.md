# 3.7-D to 4.0

## Introduction

4.0 is quite a huge update, as the introduction of Permission-based RAM management requires update for other dependencies & config, and therefore requires you to do some additional steps in order to upgrade.

## Upgrade process

This update required me to change some of the functionalities of LauncherWrapper. That being said, it was required to implement a command to automatically download the latest Launcher.jar and replace it in all of your sub-servers. Begin this update process by executing:

```
/ps admin updatelauncher
```

Wait for the process to finish. After that, it is required to change a few things in your config.yml. Begin by removing the following line: `ram-per-server: 512`, and replace it with the following block:

```yaml
ram-limiting:
  # Should we use permissions for ram management? If set to true, you MUST give
  # your players permission playerserver.ram.<amount> (ex: playerserver.ram.512)
  # or, else, the command will be blocked, and player will not be able to create
  # the server. If set to false, everyone will have ram-per-server amount of RAM.
  use-permissions: false

  # How much RAM (in MB) should we allocate to each of the PlayerServers?
  ram-per-server: 512
```

In case you'd like to see the default config after this update, please click the link below:

{% content-ref url="../for-owners/config.md" %}
[config.md](../for-owners/config.md)
{% endcontent-ref %}

In case you'd like to learn more about permission-based RAM system, follow this link:

{% content-ref url="../for-owners/limitations/permission-based-ram.md" %}
[permission-based-ram.md](../for-owners/limitations/permission-based-ram.md)
{% endcontent-ref %}



