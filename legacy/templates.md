---
description: Learn how to setup templates with plugins, mods, worlds, pre-configurations
---

# Templates

## Instructions

1. Create folder in /templates/\<yourtemplate>
2. Put all the server files there INCLUDING Spigot.jar (do not include server.properties or spigot.yml)
3. If the folder includes plugins, please do not include PSServerCore.jar or it's configuration files
4. If your server includes plugins, please add all of them to plugins-to-be-installed-ingame folder
5. Add your template to config.yml as in the following example:

```yaml
templates:
  default:
    plugins:
      - EssentialsX-2.18.1.0.jar;Essentials;Provides an essential, core set of commands for Bukkit.
```

As you can see, the template is the following: \
JarFileNameFromPluginsToBeInstalledIngameFolder;PluginNameFromPlugin.yml;Description

* JarFileNameFromPluginsToBeInstalledIngameFolder - the name of the jar file from the plugins to be installed ingame folder (example: EssentialsX-2.18.1.0.jar)
* PluginNameFromPlugin.yml - Find it by openning the plugin with WinRar, for example. Inside, you will see plugin.yml. Copy the plugin name from there
* Description - As described in the previous step, there is also a plugin description in plugin.yml. Copy it in the description part. NOTE THAT NOT ALL THE PLUGINS CONTAIN DESCRIPTION. In that case, you can create a custom one.
