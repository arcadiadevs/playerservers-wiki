---
description: >-
  Learn how to download our custom wings to prevent unwanted modifications on
  your subservers.
---

# 🕊 Download custom wings

In order to make sure your players can't remove ServerCore from their servers and thus removing the only thing that will stop their server from being online 24/7, this modification is highly recommended.

## Instructions

In order to replace Pterodactyl's wings, you'll first need to download our custom ones from our GitHub. You can also download the latest **dev build** which is almost always in sync with the latest Pterodactyl release [here](https://github.com/arcadiadevs/wings/actions).

{% embed url="https://github.com/arcadiadevs/wings/releases" %}
Download custom wings
{% endembed %}

After downloading it, navigate to `/usr/local/bin` and remove `wings` from there. Afterwards, upload our custom wings and make sure to name it `wings`. Afterwards, simply restart your wings, usually by running `service wings restart`.

Now, make sure to disable automatic restart of containers so that Wings doesn't restart the server as it shuts down due to inactivity. To do that, navigate to `/etc/pterodactyl/config.yml` and set crash\_detection.enabled to false.

{% hint style="success" %}
### Great, you're done!

Our custom wings will not negatively impact your existing non-PlayerServers servers. Any server created outside of PlayerServers environment will not be affected by PlayerServers or our modified wings.
{% endhint %}
