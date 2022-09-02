---
description: Learn how to make a permission-based CPU system for your players
---

# Permission-based CPU

{% hint style="info" %}
The below page explains how to use this feature on PlayerServers 3. This is only relevant if you're a beta tester. This feature is not available in the public release yet.
{% endhint %}

## Introduction

We know that making a permission-based CPU system is a crucial to our customers and could be greately used for safety of your infrastructure and preventing overload as well as for stores in order to motivate players to upgrade to a higher rank, so we've implemented a permission-based CPU system. In this tutorial, you'll learn how to configure it for your needs.

{% hint style="warning" %}
This feature is only working if you have Pterodactyl or Docker enabled. Screen based servers can not have CPU limitations.
{% endhint %}

## Tutorial

In order to begin, you'll need to change a few config options. Make sure your cpu-limiting part of the config looks as following:

```yaml
cpu-limiting:
  # Only for docker-based servers,
  # should we use permissions for cpu management? If set to true, you MUST give
  # your players permission playerserver.cpu.<amount> (ex: playerserver.cpu.1)
  # or, else, the command will be blocked, and player will not be able to create
  # the server. If set to false, everyone will have cpu-per-server amount of CPU.
  use-permissions: false

  # How much CPU (in %) should we allocate to each PlayerServer?
  cpu-per-server: 50
```

By enabling use-permissions, the plugin will ignore cpu-per-server option and will use permission-based CPU management system.

The next thing you'll wanna do is to give all the groups that have `playerserver.manage` permission a new permission as following: `playerserver.cpu.<cpu as percentage>`. Here's an example in LuckPerms:

```yaml
/lp group default permission set playerserver.ram.100
```

In the following example, we gave the role default ability to create a server with 1 CPU core.
