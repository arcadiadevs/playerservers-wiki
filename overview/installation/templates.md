---
description: Learn how to setup templates with plugins, mods, worlds and configurations
---

# 🎁 Templates

## Introduction

In PlayerServers, Templates are an essential way of managing the creation of your servers.

{% hint style="info" %}
_At minimum you are required to have a default Template folder with Spigot.jar file inside. Without that, it will not be possible to create a subserver._
{% endhint %}

## Instructions

1. Create folder in /templates/\<yourtemplate>
2. Put all the server files there INCLUDING Spigot.jar (do not include server.properties or spigot.yml)
3. If the folder includes plugins, <mark style="color:yellow;">please do not include PSServerCore.jar or it's configuration files</mark>
4. If your server includes plugins, please add all of them to plugins-to-be-installed-ingame folder
5. Add your template to config.yml as in the following example:

```yaml
templates:
  default:
    # Below you should add all the plugins from your template in the described format
    plugins:
      - EssentialsX-2.18.1.0.jar;Essentials;Provides an essential, core set of commands for Bukkit.
```

**As you can see, the template is the following:** \
<mark style="color:blue;">JarFileNameFromPluginsToBeInstalledIngameFolder</mark>;<mark style="color:yellow;">PluginNameFromPlugin.yml</mark>;<mark style="color:green;">Description</mark>

* <mark style="color:blue;">JarFileNameFromPluginsToBeInstalledIngameFolder</mark> - the name of the jar file from the plugins to be installed ingame folder (example: EssentialsX-2.18.1.0.jar)
* <mark style="color:yellow;">PluginNameFromPlugin.yml</mark> - Find it by openning the plugin with WinRar, for example. Inside, you will see plugin.yml. Copy the plugin name from there
* <mark style="color:green;">Description</mark> - As described in the previous step, there is also a plugin description in plugin.yml. Copy it in the description part. NOTE THAT NOT ALL THE PLUGINS CONTAIN DESCRIPTION. In that case, you can create a custom one.
