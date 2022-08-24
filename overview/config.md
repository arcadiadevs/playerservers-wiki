# 📜 Current Config files

Below you can see the contents of the newest BungeeCord PlayerServers configuration file.

{% hint style="info" %}
Please note that in some extremely rare cases I may **forget to update the config** on this page.
{% endhint %}

```yaml
#  __________.__                             _________
#  \______   \  | _____  ___.__. ___________/   _____/ ______________  __ ___________  ______
#  |     ___/  | \__  \<   |  |/ __ \_  __ \_____  \_/ __ \_  __ \  \/ // __ \_  __ \/  ___/
#  |    |   |  |__/ __ \\___  \  ___/|  | \/        \  ___/|  | \/\   /\  ___/|  | \/\___ \
#  |____|   |____(____  / ____|\___  >__| /_______  /\___  >__|    \_/  \___  >__|  /____  >
#                     \/\/         \/             \/     \/                 \/           \/
#
# An advanced plugin which allows your players to create their own sub-servers, created by thearcadia.xyz

# Please enter your MySQL information below.
mysql:
  hostname: 127.0.0.1
  username: web
  password: webmaster
  database: playerservers
  useSSL: true

  additionaloptions: []
  #  - "allowPublicKeyRetrieval=true"

  url-based-connection:
    enabled: false
    driverName: "com.mysql.cj.jdbc.Driver"

    # If you're using this connection method, you'll be entering your hostname,
    # port and database name below in the jdbcUrl string. The ones above will not
    # be considered.
    jdbcUrl: "jdbc:mysql://localhost:3306/playerservers"

  # Between version v1.2-RC6 and v1.2-RC7 there was a change in
  # Database handling. Everyone upgrading that were satisfied
  # on how it worked before should keep it as false, or first
  # try enabling it and seeing if their servers are still
  # attached to their account or not. In some rare cases it
  # can happen that changing the value of this option can
  # detach servers from your account, so enabling it if it
  # worked correctly for you before is not needed.
  use-modern-database: true

# This setting defines port range
ports:
  # Server port range
  start-port: 30000
  end-port: 40000

  # Panel port range only if experimental-panel is enabled
  panel-start-port: 40000
  panel-end-port: 50000

# Where should players be moved after they /stop or /ps kill their server?
balancer:
  - Hub1
  - Hub2

# Use player-name instead of server UUID? Basically, when turned on, server-names
# will be equal to player username instead of (for example) aa386b6h
use-usernames: true

server-name-format:
  # Should we enable custom server name formatting?
  enabled: false

  # Which format should we use?
  # %id% equals to player name or uuid depending on use-usernames option
  format: "PS_%id%"

# What is the max amount of servers that can be running at once?
max-running-instances: 15

# If there are no online players, and the last join was before
# more than minutes-to-shutdown, the server will automatically shutdown
# to allow more space for active ones.
minutes-to-shutdown: 15

# After how many seconds after executing cp -r <templatefile> <yourserverfolder>
# should we launch the server? Increase this if you get could not connect message.
copy-delay: 3

# Default startup command. Supports %uuid% for server UUID and %mem% for memory.
launch-command: "screen -dmS %uuid% java -Xmx%mem%M -jar Spigot.jar"

# In how much seconds, after first boot-up of the server should we
# teleport the player to their sub-server? This depends on the strength
# of your machine CPU. If you have a stronger machine, you might wanna set
# it to something like 12 seconds, if you have some kind of Xeon with less
# than 3.9Ghz, you might wanna set this to 15-20 seconds.
teleport-time: 15

# In how many seconds should we attempt to connect player to their
# sub-server after it being launched by /playerserver start command?
teleport-time-normal: 10

ram-limiting:
  # Should we use permissions for ram management? If set to true, you MUST give
  # your players permission playerserver.ram.<amount> (ex: playerserver.ram.512)
  # or, else, the command will be blocked, and player will not be able to create
  # the server. If set to false, everyone will have ram-per-server amount of RAM.
  use-permissions: false

  # How much RAM (in MB) should we allocate to each PlayerServer?
  ram-per-server: 512

player-limiting:
  # Should we use permissions for max-players management? If set to true, your
  # players should have playerserver.players.<amount>. The max amount of players
  # that you could give to a single server is 100000. You can also give them
  # playerserver.players.unlimited - for unlimited players. If the player
  # has no permission, he'll be able to have unlimited players.
  #
  # NOTE: If you use permissions, and you change player's permissions,
  # their server will need to reboot in order for changes to take place.
  use-permissions: false

  # What is the max players each server should have?
  max-players-per-server: 20

plugin-limiting:
  # Should we use permissions for max-plugins management? If set to true, your
  # players should have playerserver.plugins.<amount>. The max amount of plugins
  # that you could give to a single server is 20000. You can also give them
  # playerserver.plugins.unlimited - for unlimited plugins. If the player
  # has no permission, he'll be able to have unlimited players.
  #
  # NOTE: If you use permissions, and you change player's permissions,
  # their server will need to reboot in order for changes to take place.
  use-permissions: false

  # What is the max players each server should have?
  max-plugins-per-server: 20

# Should we enable smart /ps command? You can find more info about it here:
# https://gitlab.com/OpenSource02/playerservers/-/issues/21
smart-command: false

# Should we enable permissions for server creation, deletion & more?
# If set to false, all the players will have access to those basic commands.
# Obviously, admin commands require permission no matter what.
enable-permissions: true

templates:
  default:
    # This is just an example of what you can do with requires-permission.
    # Default template will never require permission, even if set to true.
    requires-permission: false
    # What launch command should be used? If set as %default%, launch-command
    # from above will be used (~line 70). Supports %mem% and %uuid% placeholders.
    launch-command: "%default%"
    # What plugins does this template contain?
    # More info: https://playerservers.thearcadia.xyz/experimental/templates
    plugins: []

# Which folders or files will not show in /config file manager?
disabled-access:
  - "ExampleFolder"
  - "Plugin.jar"

# BETA FEATURES. USE AT OWN RISK!!
multi-node: false
experimental-rename: false

# PlayerServers 2.0 experimental web-panel feature (concept only, for now).
# Enable it only for testing purposes. It can and will cause security vulnerabilities.
#
# Read instructions here https://www.spigotmc.org/resources/82268/update?update=394183
experimental-panel: false
```

## Current messages.toml

```
run-in-game = "&9Error> &7Oops! You can only run this command in-game."
not-enough-arguments = "&9PlayerServers> &7Oops, not enough arguments: /playerservers admin test <node-name>"
not-enough-arguments-kill = "&9PlayerServers> &7Oops, not enough arguments: /playerserver kill stop <uuid (example: 1F4a2id)>"
not-enough-arguments-delete = "&9PlayerServers> &7Not enough arguments. &a/playerservers admin delete <uuid>. Please keep in mind that you should not enter the full id. You should just enter the first part (example: if full UUID is 1234-5678-1223-5623, you should just enter 1234)."
no-permission = "&9Error> &7Oops, it seems like you don't have permission to do that."
launching-server = "&c&lLaunching your server. This might take some time. You will be teleported as soon as it's ready."
server-online = "&9PlayerServers> &7Oops, it seems like your server is not online."
successfully-renamed = "&9PlayerServers> &7Successfully renamed server."
rename-failed = "&9PlayerServers> &7Oops, the server with that name already exists."
already-have = "&9Error> &7Oops, it seems like you already have a server!"
too-many-online = "&9Error> &7Oops, it seems like too many servers are running at the moment."

[server-creation]

process-first = "&9PlayerServer> &7Starting the creation of your server..."
process-second = "&9Process> &7Successfully copied Spigot.jar & created eula.txt"
process-third = "&9Process> &7Successfully copied the PlayerServerCore to your server."
process-fourth = "&9Process> &7Successfully created server.properties & start.sh"

post-process-one = "&9PostProcess> &7Your server has been added to the BungeeCord. Teleporting in &a%time% &7seconds..."

sending-to-remote-server = "&9Process> &7We're beginning the creation of your server on the first remote node that provides us with ample resources. This will not take a while."

[server-stop]

not-online = "&9PlayerServers> &7Oops, it seems like your server is not online."
successfully-killed = "&9Success> &7Your server has been successfully killed."

[server-start]

prepairing = "&9PlayerServers> &7Preparing to launch your server."

[server-connect]

connected = "&9PlayerServer> &7You've been successfully sent to your server. Your friends can use &a/server %uuid%&7 to connect."

[server-restart]

killing = "&9PlayerServers> &7Trying to kill your server..."
```
