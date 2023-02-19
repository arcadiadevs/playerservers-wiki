---
description: Learn how to create a node for servers to be deployed to.
---

# 🛳 Adding a node

## Introduction

In order to create subservers, you need to have nodes configured. Each node can have a configurable amount of servers running at the same time. A node can be the same machine that you host your BungeeCord on, or any other machine connected to the internet.

## Instructions

### Download Daemon

In order to create a node, you'll need to download the latest Daemon.

{% file src="../../.gitbook/assets/PlayerServersDaemon-v3.1-beta5.zip" %}
Download the latest daemon
{% endfile %}

After downloading it, put it in a separate folder and extract it, preferably **out** of your BungeeCord folder. This is not a plugin, but a separate software made for handling server requests.

Now run the Daemon with the following command:

{% code title="Command to start Daemon" %}
```sh
java -Xmx500M -jar PlayerServeshersDaemon.jar
```
{% endcode %}

After running it, type `exit` to stop your Daemon.

Now, edit your config.toml generated inside Daemon folder to your preference and make sure to use the same token as in config.toml when creating a new node.

### Create node in-game

The last step would be to add the node to PlayerServers. To do so, type the following command:

{% code overflow="wrap" %}
```sh
/psadmin node create <nodename> <ip> <port> <minPort> <maxPort> <maxOnline> <token>
```
{% endcode %}

* NodeName is any name you want to give to your node
* IP is the ip of the machine the node is located on
* Port is the port, configurable in config.toml of your Daemon.
* MinPort and MaxPort represent the port range in which your servers are going to be created on. For example, if you put 30000 and 30100 as min and max port respectively, your servers will get a random port between those two numbers when created on this node.
* MaxOnline is the max number of online instances at once on this node.
* Token is the token configured in Daemon's config.toml

{% hint style="success" %}
If everything was done correctly, your node is ready to start accepting new subservers. However, make sure to have at least one template configured for it (default). Learn more below on how to do so.
{% endhint %}
