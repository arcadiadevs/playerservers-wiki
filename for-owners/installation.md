---
description: >-
  Here is a guide with details that you need to follow in order to complete the
  installation.
---

# Plugin Installation Tutorial

## Before installation

In order to install PlayerServers, you will need to have a **VPS or Dedicated** server with **root** access. If you do not have it, please do not buy the plugin or try to install it on **Shared (Game) Hosting.**

{% hint style="info" %}
Also, thanks to FullOfCode#6328, we have a (unofficial) video tutorial, so maybe you should consider [watching it,](https://www.youtube.com/watch?v=VApcwAG4y5c) instead of reading the rest of this page.
{% endhint %}

## Picking the right OS

I understand that if you have your server already up and running, it might come hard for you to change your OS. That's why we tested our plugin on many of the popular OS-es. Even tho some of them are marked with ⚠️, it doesn't mean the plugin will not work there, it just means that the instructions from this guide will not help you while setting up the plugin on those Operating Systems, but if you configure everything correctly (like installing Java, Screen & Fuser) the plugin should work without any problems. If you have any problems with an OS-es marked with ✅ or ⚠️, please contact me so we can solve it.

Operating Systems marked with ⛔️ are currently not supported at all, but the support for them come in the future versions. Below is the list of all the popular operating systems:

| **Operating System** | Version                                                   | Supported | Notes                                                                                                                                                                                         |
| -------------------- | --------------------------------------------------------- | --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Ubuntu**           | <p>20.04</p><p>21.04</p>                                  | ✅         | This OS-es are fully supported by PlayerServers                                                                                                                                               |
| **Ubuntu**           | <p>18.04</p><p>(Bionic)</p>                               | ✅         | <p>Documentation written assuming Ubuntu 18.04<br>as the base OS.</p>                                                                                                                         |
| **Ubuntu**           | 16.04                                                     | ⚠️        | Untested, but the plugin should work                                                                                                                                                          |
| **Debian**           | <p>9</p><p>10</p><p>11</p>                                | ✅         | <p>Not <em>heavely</em> tested, the plugin worked but the<br>instructions from this guide might be invalid for that OS.</p><p>Some additional repos might be required.</p>                    |
| **Debian**           | 8                                                         | ⚠️        | Untested, additional repos are most likely required                                                                                                                                           |
| **CentOS**           | 7 & 8                                                     | ⚠️        | **Not tested** and **not recommended** at all                                                                                                                                                 |
| **Windows**          | <p>Server 2016</p><p>Server 2019</p><p>10</p><p>11</p>    | ❌❓        | <p><strong>Not tested at all.</strong> It <strong>may</strong> work though, by installing</p><p>Ubuntu subsystem for Windows 10. You can find more</p><p>tutorials about that on Youtube.</p> |
| **MacOS**            | <p>Mojave</p><p>Catalina</p><p>Big Sur</p><p>Monterey</p> | ✅         | <p>Should work without any problems as it comes with</p><p>screen &#x26; fuser pre-installed. Tested on M1 processors as well.</p>                                                            |

## Requirements

{% hint style="info" %}
Before installing the dependencies below, it is recommended to run `apt-get update` command as the commands below might not work without it.
{% endhint %}

In order to install PlayerServers on your machine, you obviously need to have Java (the plugin was compiled using Java 8, as it's the standard version of Java, and it's been tested on Java 11, but it should work on newer versions as well. If it does not, please report it). The recommended version of Java to be used with this plugin is Java 11. If you don't have it already installed, please execute the command below in your Linux Terminal.

{% hint style="warning" %}
If you're using 2.0+ versions of PlayerServers, you'll need to install Java 16, or preferrably Java 17 - as it'll become standard as of PlayerServers 3.0.

You can find an in-depth guide on that [here](https://linuxways.net/ubuntu/how-to-install-oracle-java-16-on-ubuntu-18-04-20-04/).
{% endhint %}

```bash
$ apt-get install default-jre -y
```

The second required dependency is Screen. We use screens for providing easy access to PlayerServers. In order to install it, you need to execute the command below. For further help with Screen, please go to the [Screen (accessing consoles)](screen.md) page.

```
$ apt-get install screen -y
```

After successfully installing Screen, you will need to install **fuser**. Many Linux distros already come with it **pre-installed**, but if you don't have it, make sure to install it by executing the following command:

```
$ apt-get install fuser -y
```

## Installation of the plugin

In order to install the plugin, you just need to put it into your BungeeCord plugins folder. After that, please reboot your server and let the plugin generate it's config files and download some other required dependencies.

{% hint style="danger" %}
After the first boot of the server, you will see some errors generated by the plugin. Don't worry, just **shutdown** your BungeeCord server and follow the instructions below in order to solve it.
{% endhint %}

Now navigate to the `plugins folder -> PlayerServers` and open up the config.yml file. It is recommended to open it usign some sort of advanced text editor (like [Notepad++](https://notepad-plus-plus.org) or [VisualStudio Code](https://code.visualstudio.com)). After that, you will have to enter your MySQL informations. If you're unsure on how to create database on Linux machine, this [Creating MySQL database](creating-mysql-database.md) page might help you.

After the configuration of MySQL database, boot up your BungeeCord server. The plugin should successfully launch this time.

{% hint style="success" %}
### That's it!

If you followed the guide correctly, you will have a working version of PlayerServers installed. If there are any additional errors, or you need help with something, please don't hesitate to send me PM od MC-Market, or on Discord - `OpenSource#3310`
{% endhint %}

## ~~Possible Issues~~

~~While installing PlayerServers for the first time, it is **required** for the plugin to download some **dependencies** from our servers. If servers are down, you might encounter some errors. If you see those errors, please contact the developer on our~~ [~~Support Discord~~](https://discord.io/arcadiaservices)~~.~~

\~\~Don't worry, **you can still install the plugin even if servers are down**. In the downloaded .zip file, you'll see sub-folder called **Use only if needed**. Copy the contents of that folder to:

`BungeeCord -> plugins -> PlayerServers -> Templates`

and you should be fine to complete the installation. If there are any other unexpected issues, don't hesitate to ask. We'll always respond in less than 24 hours.\~\~

{% hint style="warning" %}
~~**NOTE FOR SPIGOT / MINEMEN USERS:** Since spigot does not allow large file sizes, you'll need to download required files from links blow, as your download does not include **Use only if needed** folder.~~

* ~~\~\~\[~~PlayerServerCore.jar~~]\(~~[http://cdn.thearcadia.xyz/playerservers/PlayerServerCore.jar](http://cdn.thearcadia.xyz/playerservers/PlayerServerCore.jar)~~)~~\~\~
* ~~\~\~\[~~Launcher.jar~~]\(~~[http://cdn.thearcadia.xyz/playerservers/Launcher.jar](http://cdn.thearcadia.xyz/playerservers/Launcher.jar)~~)~~\~\~
* ~~\~\~\[~~Spigot.jar~~]\(~~[http://cdn.thearcadia.xyz/playerservers/Spigot.jar](http://cdn.thearcadia.xyz/playerservers/Spigot.jar)~~)~~\~\~
* ~~\~\~\[~~eula.txt~~]\(~~[http://cdn.thearcadia.xyz/playerservers/eula.txt](http://cdn.thearcadia.xyz/playerservers/eula.txt)~~) \~\~- copy contents of this page inside new file: eula.txt, and put it in your templates directory, as described above.~~
{% endhint %}

If you're using 8.0+, you will not ever encounter those issues, as the plugin is no longer cloud-depandent
