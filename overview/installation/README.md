---
description: >-
  Here is a guide with details that you need to follow in order to complete the
  installation.
---

# 🚀 Plugin Installation Tutorial

## Before installation

In order to install PlayerServers, you will need to have a **VPS or Dedicated** server with **root** access. If you do not have it, please do not buy the plugin or try to install it on a **Shared (Game) Hosting.**

## Picking the right OS

We understand that if you have your server already up and running, it might come hard for you to change your OS. That's why we tested our plugin on many of the popular OS-es. Even tho some of them are marked with ⚠️, it doesn't mean the plugin will not work there, it just means that the instructions from this guide will not help you while setting up the plugin on those Operating Systems, but if you configure everything correctly (like installing Java, Screen & Fuser) the plugin should work without any problems. If you have any problems with an OS marked with ✅, please contact me so we can solve it.

Operating Systems marked with ⛔️ are currently not supported at all, but the support for them come in the future versions. Below is the list of all the popular operating systems:

<table data-header-hidden><thead><tr><th>Operating System</th><th width="157">Version</th><th width="178">Supported</th><th>Notes</th></tr></thead><tbody><tr><td><strong>Operating System</strong></td><td>Version</td><td>Supported</td><td>Notes</td></tr><tr><td><strong>Ubuntu</strong></td><td><p>20.04</p><p>22.04</p></td><td>✅</td><td>Documentation written assuming Ubuntu 22.04<br>as the base OS. Heavily tested on 20.04 as well.</td></tr><tr><td><strong>Ubuntu</strong></td><td><p>18.04</p><p>(Bionic)</p></td><td>✅</td><td>The plugin was tested on this OS and confirmed to have no issues.</td></tr><tr><td><strong>Ubuntu</strong></td><td>16.04</td><td>⚠️</td><td>Untested, but the plugin should work</td></tr><tr><td><strong>Debian</strong></td><td><p>9</p><p>10</p><p>11</p></td><td>✅</td><td><p>Tested, the plugin worked but the instructions from this guide might be invalid for that OS.</p><p></p><p>Some additional repos might be required.</p></td></tr><tr><td><strong>Debian</strong></td><td>8</td><td>⚠️</td><td>Untested, additional repos may be required</td></tr><tr><td><strong>CentOS</strong></td><td>7 &#x26; 8</td><td>⚠️</td><td><strong>Not tested</strong>, though we had reports of centOS working without any issues and we do not see any reason for it not to work there.</td></tr><tr><td><strong>Windows</strong></td><td><p>Server 2016</p><p>Server 2019</p><p>Server 2022</p><p>10</p><p>11</p></td><td>✅</td><td><strong>Tested, works perfectly.</strong><br><br>PlayerServers v3+ introduced the full Windows support by using Docker for instance management</td></tr><tr><td><strong>MacOS</strong></td><td><p>Mojave</p><p>Catalina</p><p>Big Sur</p><p>Monterey<br>Ventura</p></td><td>✅</td><td><p>Should work without any problems as it comes with</p><p>screen &#x26; fuser pre-installed. <br><br>Tested on M1 processors as well. On M1 machines, ARM JVM like Azul Zulu is highly recommended.</p></td></tr></tbody></table>

## Requirements

{% hint style="info" %}
Before installing the dependencies below, it is recommended to run `apt-get update` command as the commands below might not work without it.
{% endhint %}

In order to install PlayerServers on your machine, you need to have Java. The minimum version of Java to be used with this plugin is Java 18. If you don't have it already installed, please follow the link below in order to learn how to install it.

{% embed url="https://docs.azul.com/core/zulu-openjdk/install/debian" %}
Azul Zulu Java installation guide (for Debian/Ubuntu)
{% endembed %}

## Installation of the plugin

In order to install the plugin, you just need to put it into your BungeeCord plugins folder. After that, please reboot your server and let the plugin generate it's config files and download some other required dependencies.

{% hint style="danger" %}
After the first boot of the server, you will see some errors generated by the plugin. Don't worry, just **shutdown** your BungeeCord server and follow the instructions below in order to solve it.
{% endhint %}

Now navigate to the `plugins folder -> PlayerServers` and open up the config.yml file. It is recommended to open it using some sort of advanced text editor (like [Notepad++](https://notepad-plus-plus.org) or [VisualStudio Code](https://code.visualstudio.com)). After that, you will have to enter your MySQL informations. If you don't have a MySQL server running already, please follow the link below.

{% content-ref url="../../legacy/creating-mysql-database.md" %}
[creating-mysql-database.md](../../legacy/creating-mysql-database.md)
{% endcontent-ref %}

After the configuration of MySQL database, boot up your BungeeCord server. The plugin should successfully launch this time.

{% hint style="success" %}
### That's it!

If you followed the guide correctly, you will have a working version of PlayerServers installed. If there are any additional errors, or you need help with something, please don't hesitate to send me PM od MC-Market, or on Discord - `OpenSource#3310`
{% endhint %}

## Now setup your first node

After successfully installing the plugin, in order to create your first server, you'll need to configure nodes (if not running in [Pterodactyl mode - learn more](pterodactyl-configuration.md)). To learn how to configure nodes, click the button below.
