---
description: Learn how to setup templates with plugins, mods, worlds and configurations
---

# 🎁 Templates

## Introduction

In PlayerServers, Templates are an essential way of managing the creation of your servers.

{% hint style="info" %}
_At minimum you are required to have a `default` Template folder with Spigot.jar file inside. Without that, it will not be possible to create a subserver._
{% endhint %}

## Instructions

1. Create folder in /templates/\<yourtemplate>
2. Put all the server files there **including Spigot.jar** (you must not include server.properties or spigot.yml)
3. If the folder includes plugins, please do not include PSServerCore.jar or it's configuration files
4. If your server includes plugins, please add all of them to the server-plugins folder
