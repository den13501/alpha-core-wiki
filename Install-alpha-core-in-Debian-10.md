
## Dependencies

```bash
apt update
apt install git vim python3 mariadb

# Python3 dependencies
pip3 install virtualenv virtualenvwrapper
mkdir /opt
```



## Virtualenv

add this to the end of **~./bashrc**

```bash
# Virtualenv
export WORKON_HOME=/opt/virtualenvs
export PROJECT_HOME=/opt
export VIRTUALENVWRAPPER_PYTHON=/usr/local/bin/python3
source /usr/local/bin/virtualenvwrapper.sh
```

You need to restart shell before continue



## MariaDB user and database

Log into your MariaDB server and create the databases and user. Please use something safer than ‘password’

```bash
CREATE DATABASE alpha_dbc;
CREATE DATABASE alpha_realm;
CREATE DATABASE alpha_world;

CREATE USER 'alpha-core'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON `alpha_%`.* TO 'alpha-core'@'localhost';
FLUSH PRIVILEGES;
```



## Download alpha-core

We are gonna download alpha-core and install all its dependencies into a virtual environment.

```bash
# download core
cd /opt
git clone https://github.com/The-Alpha-Project/alpha-core
cd alpha-core

# create an virtual environment. 
mkvirtualenv alpha-core
pip3 install -r requirements.txt
```



## Create and edit config.yml

Create config.yml

```bash
cp etc/config/config.yml.dist etc/config/config.yml
```



Change MariaDB user and password in config.yml. Use whatever text editor you like. (nano, vim, vi, atom)

```bash
Connection:
        host: 127.0.0.1
        username: alpha-core
        password: password
```



Change server IP to your computer in config.yml. This is an optional step! **If you got your server and client on the same computer you don’t need to edit this**. Otherwise, you enter your computer’s local IP-address (for lan usage).  Also, you need to open 8100, 9090, 9100 ports. If you are running client and server on the same computer you can skip this. If you want to have access outside your computer and lan, change ip to 0.0.0.0

```bash
Server:
    Connection:
        RealmServer:
            host: 127.0.0.1  # server machine local IP
            port: 9100
            realm_name: alphacore

        RealmProxy:
            host: 127.0.0.1  # set this to external IP if needed
            port: 9090

        WorldServer:
            host: 127.0.0.1  # set this to external IP if needed
            port: 8100
```



## Populate all databases

We need to populate the databases and add all updates.

```bash
mysql -u alpha-core -p alpha_dbc < etc/databases/dbc/dbc.sql
mysql -u alpha-core -p alpha_realm < etc/databases/realm/realm.sql
mysql -u alpha-core -p alpha_world < etc/databases/world/world.sql
```



## Install updates (first time)

SQL scripts do not work with MySQL.**you must use MariaDB**

The first time you install the server you need to run the scripts below.

```bash
mysql -u alpha-core -p alpha_dbc < etc/databases/dbc/updates/updates.sql
mysql -u alpha-core -p alpha_realm < etc/databases/realm/updates/updates.sql
mysql -u alpha-core -p alpha_world < etc/databases/world/updates/equip_template.sql
mysql -u alpha-core -p alpha_world < etc/databases/world/updates/item_display_fixes.sql
mysql -u alpha-core -p alpha_world < etc/databases/world/updates/updates.sql
```



### Update repository and databases

Sometimes you need to rerun the update scripts. Check if there are  any SQL files updated then you updated the repository. To update the  repository you just run git pull at server base.

```bash
git pull
# if needed
mysql -u alpha-core -p alpha_dbc < etc/databases/dbc/updates/updates.sql
mysql -u alpha-core -p alpha_realm < etc/databases/realm/updates/updates.sql
mysql -u alpha-core -p alpha_world < etc/databases/world/updates/updates.sql
```



## Run server

Now everything should be working, let’s try. Run from the server root.

```bash
workon alpha-core # if needed
pyhton3 main.py
```



## Client

- Mangosrumors got an excellent article about running older WoW clients in newer Mac OS’s (Big Sur, Catalina) https://www.mangosrumors.org/how-to-run-wow-32-bit-on-mac-os/
- The valid client is: **[WoW-0.5.3.3368_install_enUS.iso](https://archive.org/download/World_of_Warcraft_Client_and_Installation_Archive/ISO/WoW-0.5.3.3368_install_enUS.iso)**



## Windows

- Download client

- Install it to c:\games\wow-alpha

- inside wow-alpha, create directory **WTF**

- inside WTF create 

  config.wtf

   and add 127.0.0.1 for local machine. otherwise external IP. 

  ```bash
  SET realmName "alphacore"
  SET realmList "127.0.0.1"
  SET realmAddress "127.0.0.1"
  ```

- Create 

  wow.ses

   in the game root, the first line is a username and the second is a password. You can choose whatever username and password you like, the server will create the account.

  ```bash
  admin
  admin
  ```

- Works best if set to compatible with Windows XP S3

- Start WoWClient.exe from cmd OR create a shortcut and add the flags below.

```bash
WoWClient.exe -uptodate -console -windowed
```

You can also use a modified exe file. If your using this file you don't need to use uptodate or windowed flags, it also supports bigger resolutions then the original. Also, you don't need to use the ses file. 

[Moded 0.5.3 client ](http://www.mediafire.com/file/wjbk1ovyyb6ry7l/Mods.zip/file)