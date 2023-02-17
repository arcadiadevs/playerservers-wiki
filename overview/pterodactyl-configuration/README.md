---
description: >-
  Learn how to setup and configure PlayerServers to work with Pterodactyl
  control panel and give your users ability to manage their server through
  Pterodactyl’s beautiful and easy-to-use interface.
---

# 🌐 Pterodactyl configuration

{% hint style="info" %}
The below page explains how to use this feature on PlayerServers 3. This is only relevant if you're a beta tester.
{% endhint %}

## Introduction

> Pterodactyl® is a free, open-source game server management panel built with PHP, React, and Go. Designed with security in mind, Pterodactyl runs all game servers in isolated Docker containers while exposing a beautiful and intuitive UI to end users.

PlayerServers offers the possibility to sync with your panel and create Pterodactyl servers on the fly - offering your users all that PlayerServers offers + the ability to manage their server through Pterodactyl's amazing UI.

## How to setup

{% hint style="info" %}
In order to begin, you need to have Pterodactyl, Docker and PlayerServers properly installed on your system. To learn how to install Pterodactyl, click [here](https://pterodactyl.io/panel/1.0/getting\_started.html).
{% endhint %}

1. Shutdown your BungeeCord
2. Edit PlayerServers [config.yml](../config.md), enable pterodactyl mode
3. Insert your application token and client token
4. Insert your Minecraft nest-id, Paper egg-id and the location-id of the location your nodes are based in.
5. Just like that, you're done!

{% hint style="warning" %}
We highly recommend downloading our custom Wings and replacing Pterodactyl's Wings. This will prevent unwanted modifications to PSServerCore config and jar. Click the button below to learn more.
{% endhint %}
