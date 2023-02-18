---
description: Learn how to create Pterodactyl client and application API token.
---

# 🔓 How to create tokens

## Introduction

Application and Client tokens are essential in the way PlayerServers communicates with your panel and thus need to be correctly set with appropriate privileges.

## How to create Application Token

In order to create an application token, please navigate to the Pterodactyl admin interface, and select "Application API"

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-11 at 00.01.14.png" alt=""><figcaption><p>Application API interface</p></figcaption></figure>

Afterwards, click on the blue Create New button on the top right and make sure to fill the fields just like on the image below.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-11 at 00.03.44.png" alt=""><figcaption><p>Application API - required permissions</p></figcaption></figure>

As that's done, you'll receive your application token which you need to put in your `config.yml`.

## How to create Client Token

In order to create an application token, please navigate to the Pterodactyl admin interface and click on your profile icon on the top right.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-17 at 12.29.22.png" alt=""><figcaption><p>Click on profile icon</p></figcaption></figure>

After that, navigate to the API Credentials tab.

<figure><img src="../../.gitbook/assets/Screenshot 2023-02-17 at 12.31.20.png" alt=""><figcaption><p>API Credentials</p></figcaption></figure>

From here, create a new API key. Name it whatever you want and click create. Optionally, add the IP address of your BungeeCord instance to prevent unauthorised access to your API key.

From there, proceed by putting the newly generated API key to your `config.yml` file.
