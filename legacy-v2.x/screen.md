---
description: >-
  In the tutorial below, you'll learn how to access the console of the
  sub-servers
---

# Screen (accessing consoles)

In order to make our plugin function, we use Screen. In order to access the console of sub-servers, you just need to simply execute the command below:

```
$ screen -r <the first part of the ServerID, example: screen -r 8451ld>
```

{% hint style="info" %}
If the command above does not work for you, you need to execute this one first:

`screen -d <the first part of the ServerID>`

And after that, repeat the command above.
{% endhint %}

In order to see all the active screens, you can execute the command below:

```
$ screen -ls
```

{% hint style="success" %}
That's it. If you want to learn more about Screen, you can always click on the [Screen (Advanced)](https://linuxize.com/post/how-to-use-linux-screen/) section in the Sidebar menu.
{% endhint %}
