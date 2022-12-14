---
description: >-
  Since PlayerServers v3, we now offer Docker support as well for those that
  care about security and network isolation of their subservers.
---

# 🛳 Docker configuration

{% hint style="info" %}
The below page explains how to use this feature on PlayerServers 3. This is only relevant if you're a beta tester. This feature does not exist on the public release yet.
{% endhint %}

## Introduction

Docker adds a secure isolation layer to your PlayerServers, so you can safely allow players to install all sorts of plugins without being afraid of them breaking something.&#x20;

## Tutorial

### Docker installation

For a quick install of Docker CE, you can execute the command below:

```bash
curl -sSL https://get.docker.com/ | CHANNEL=stable bash
```

### Configuration

After successfully installing docker, you can enable docker support inside your config.yml.

{% code title="Config.yml" overflow="wrap" lineNumbers="true" %}
```yaml
docker:
    enabled: true
```
{% endcode %}
