# Install the alpha-core server on Big Sur



Install instructions to install the alpha-core server on macOS Big Sur.



## Install dependencies Mac

All mac dependencies (if needed)



```bash
# Install brew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

brew update
brew install git mariadb python3

# if mariadb not starting directly
brew services mariadb start

# Python3 dependencies
pip3 install virtualenv virtualenvwrapper
mkdir ~/project
```



## .bash_profile

Add this lines to the end of **~/.bash_profile**, so virtualenv and virtualenvwrapper will work. Don't forget to reopen the shell.



```bash
# Virtualenv
export WORKON_HOME=$HOME/project/.virtualenvs
export PROJECT_HOME=$HOME/project
export VIRTUALENVWRAPPER_PYTHON=/usr/local/opt/python/libexec/bin/python
source /usr/local/bin/virtualenvwrapper.sh
```



## MariaDB user and database

Log into your MariaDB server and create the databases and user. Please use something safer then 'password'



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
cd project
git clone https://github.com/The-Alpha-Project/alpha-core
cd alpha-core

# create an virtual environment. 
mkvirtualenv alpha-core
pip install -r requirements.txt
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



Change server IP to your computer in config.yml. This is an optional step! **If you got your server and client on the same computer you don't need to edit this**. Otherwise, you enter your computer's local IP-address (for lan usage). Also, you need to open 8100, 9090, 9100 ports. If you are running client and server on the same computer you can skip this.



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

SQL scripts does not MySQL, **you must use MariaDB**



First time you install the server you need to run the scripts below.



```bash
mysql -u alpha-core -p alpha_dbc < etc/databases/dbc/updates/updates.sql
mysql -u alpha-core -p alpha_realm < etc/databases/realm/updates/updates.sql
mysql -u alpha-core -p alpha_world < etc/databases/world/equip_template.sql
mysql -u alpha-core -p alpha_world < etc/databases/world/item_display_fixes.sql
mysql -u alpha-core -p alpha_world < etc/databases/world/updates/updates.sql
```



### Update repository and databases

Sometimes you need to rerun the update scripts. Check if where are any SQL files updated then you updated the repository. To update the repository you just run git pull at server base.



```bash
git pull
# if needed
mysql -u alpha-core -p alpha_dbc < etc/databases/dbc/updates/updates.sql
mysql -u alpha-core -p alpha_realm < etc/databases/realm/updates/updates.sql
mysql -u alpha-core -p alpha_world < etc/databases/world/updates/updates.sql
```



## Run server

Now everything should be working, let's try. Run from server root.



```bash
workon alpha-core # if needed
pyhton3 main.py
```



## Client

- Mangosrumors got an excellent article about running older WoW clients in newer Mac OS's (Big Sur, Catalina) https://www.mangosrumors.org/how-to-run-wow-32-bit-on-mac-os/
- Valid client is: **WoW-0.5.3.3368_install_enUS.iso**




