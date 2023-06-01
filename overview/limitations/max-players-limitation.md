# Max players limitation

## Introduction

We know that making a permission-based slots system is a crucial to our customers and could be greately used for online stores in order for them to earn money for Ranks & Perks, so we've implemented a permission-based slots system. In this tutorial, you'll learn how to configure it for your needs.

## Tutorial

In order to begin, you'll need to change a few config options. Make sure your player-limiting part of the config looks as following:

```yaml
player-limiting:
  # Should we use permissions for max-players management? If set to true, your
  # players should have playerservers.players.<amount>. The max amount of players
  # that you could give to a single server is 100000. You can also give them
  # playerserver.players.unlimited - for unlimited players. If the player
  # has no permission, he'll be able to have unlimited players.
  #
  # NOTE: If you use permissions, and you change player's permissions,
  # their server will need to reboot in order for changes to take place.
  use-permissions: true

  # What is the max players each server should have?
  max-players-per-server: 20
```

By enabling use-permissions, the plugin will ignore max-players-per-server option and will use permission-based slots management system.

The next thing you'll wanna do is to give all the groups that have `playerservers.manage` permission a new permission as following: `playerservers.players.<amount>`. Here's an example in LuckPerms:

```yaml
/lp group default permission set playerservers.players.10
```

If your groups have parent permission, the plugin will give the player the largest possible amount of slots by their permission.
