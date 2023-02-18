# Creating MySQL database

In order to **create** required **MySQL database** on your server, you first need to have **mariadb-server** installed. If you don't have it, please run the command below:

{% hint style="info" %}
Please note that it is generally recommended to execute`apt-get update`before installing new packages on the machine, as else you might encounter some errors.
{% endhint %}

```
$ apt-get install mariadb-server -y
```

After successfully installing MariaDB server, you can now proceed with creating required databases. First of all, you need to login to the mysql terminal. Execute the command below in order to do so.

```
$ mysql -u root -p
```

After that, we need to create user. You can do that by executing the command below:

```sql
CREATE USER 'playerserversuser'@'127.0.0.1' IDENTIFIED BY 'somePassword';
```

After that, you need to create **new database** for PlayerServers:

```sql
CREATE DATABASE PlayerServers;
```

Next up, we need to give playerservers user permission to access the database. We can do that by executing the next two commands:

```sql
GRANT ALL PRIVILEGES ON PlayerServers.* TO 'playerserversuser'@'127.0.0.1';
FLUSH PRIVILEGES;
```

{% hint style="success" %}
### That's it!

If you've done everything correctly, you'll now have a new user called `playerserversuser` which will have password you defined in the second step under`somePassword`field and that user will be able to access the newely created database called `PlayerServers`.
{% endhint %}
