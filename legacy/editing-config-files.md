---
description: >-
  This tutorial might be a little bit confusing for non-experienced users, but
  we tried to explain it step-by-step as good as we possibly could. If you need
  additional help, please contact server staff.
---

# Editing config files

## Editing config files - full tutorial

{% hint style="info" %}
In order to edit the config files, you first need to be connected to your subserver. If you're not sure on how to do that, [Basic Instructions](basic-instructions.md) page will help you.
{% endhint %}

After connecting to your server, execute the following command:

```
/config
```

That command will open up the GUI with all the files on your server. From there, you'll be able to navigate to the folder of the plugin you want to edit. There are some screenshots below:

![The main GUI that will show all the contents of /plugins directory](<../.gitbook/assets/screen-shot-2020-05-13-at-6.15.01-pm (2) (1).png>)

![By clicking on the WorldEdit folder, we've entered the sub-folder content.](<../.gitbook/assets/screen-shot-2020-05-13-at-6.15.08-pm (2) (1).png>)

By clicking on the config.yml file, you'll be generated the link in the chat. That link will navigate you to the HasteBin (or in some cases paste.md-5.net) website. By opening it up, you'll see the contents of your config file. The worldedit example will look like the following:

![By clicking on config.yml, we've gotten the hastebin link. We'll open it up in the next screenshot.](<../.gitbook/assets/Screen Shot 2020-05-13 at 6.19.21 PM.png>)

![And here is our config](<../.gitbook/assets/Screen Shot 2020-05-13 at 6.20.35 PM.png>)

Now, in order to edit your config, please click on duplicate and edit button on the top right side of the screen, as it could be seen on the image below:

![By clicking on duplicate & edit button, our config will become editable](<../.gitbook/assets/Screen Shot 2020-05-13 at 6.22.48 PM.png>)

By clicking that option, you'll be granted the access to modify your config. After modifying it, be sure to click the save button:

![](<../.gitbook/assets/Screen Shot 2020-05-13 at 6.24.05 PM.png>)

By clicking the save button, the config will no longer be editable once again. Now, the only thing you need to do is open up the `/config` menu once again, navigate to your config file, and this time, you need to **right click it.** After that, Anvil GUI will pop up and you need to paste the link of your new edited version of the file, **but without https://.** For example, if you've gotten the link https://hastebin.com/mynewconfig.yml, you need to paste in just hastebin.com/mynewconfig.yml, **without **~~**https://.**~~

{% hint style="success" %}
And that's it. Your file is now modified. In order to apply the changes, please consider **restarting your server.** More detailed guide on how to stop & boot up your server can be found on the [Basic Instructions](basic-instructions.md) page. If you need any additional informations, contact the staff team.
{% endhint %}
