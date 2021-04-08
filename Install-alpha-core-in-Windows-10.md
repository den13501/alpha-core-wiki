## Required Software

- Python 3 (https://www.python.org/downloads/ anything newer than 3.6) 
- MariaDB (The easiest way is probably to install xampp for that https://www.apachefriends.org/download.html) 
- The alpha client (Just ask for a link on this server)



## Recommended Software

- Git (https://git-scm.com/downloads makes your life a lot easier) 

- HeidiSQL (I personally like this for managing databases, but you could also use phpmyadmin that comes preinstalled with xampp https://www.heidisql.com/download.php)



## Steps to get it running

1. Clone the repository or download it (Run cmd and execute `git clone https://github.com/GrenderG/alpha-core.git` to clone the repository into your current directory) 
2. After you got the files change into the new directory and install the dependencies with `pip3 install -r requirements.txt`
3. Now start mysql and create 3 new databases - alpha_realm - alpha_world - alpha_dbc 
4. Populate the databases with the data from the .sql files in `/etc/databases`
5. After that is done execute the updates from `/etc/databases/realm/updates` and `/etc/databases/world/updates` 
6. Now rename the file `/etc/config/config.yml.dist` into `/etc/config/config.yml`  and change the username and password fields to the ones of your MariaDB setup
7. Now you are basically done, you can now start the server with `py main.py`


