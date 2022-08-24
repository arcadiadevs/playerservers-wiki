---
description: Learn how to make a permission-based RAM system for your players
---

# Permission-based RAM

## Introduction

We know that making a permission-based RAM system is a crucial to our customers and could be greately used for online stores in order for them to earn money for Ranks & Perks, so we've implemented a permission-based RAM system. In this tutorial, you'll learn how to configure it for your needs.

## Tutorial

In order to begin, you'll need to change a few config options. Make sure your ram-limiting part of the config looks as following:

```yaml
ram-limiting:
  # Should we use permissions for ram management? If set to true, you MUST give
  # your players permission playerserver.ram.<amount> (ex: playerserver.ram.512)
  # or, else, the command will be blocked, and player will not be able to create
  # the server. If set to false, everyone will have ram-per-server amount of RAM.
  use-permissions: true

  # How much RAM (in MB) should we allocate to each of the PlayerServers?
  ram-per-server: 512
```

By enabling use-permissions, the plugin will ignore ram-per-server option and will use permission-based RAM management system.

The next thing you'll wanna do is to give all the groups that have `playerserver.manage` permission a new permission as following: `playerserver.ram.<amount in MB>`. Here's an example in LuckPerms:

```yaml
/lp group default permission set playerserver.ram.512
```
