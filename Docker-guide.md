This is a Debian 10 docker guide for Alpha-core emulator. You need to run this commands inside of alpha-core directory



## Install



```Bash
# dependencies
apt-update && apt install docker-compose

cd /opt
git clone https://github.com/The-Alpha-Project/alpha-core.git
cp /opt/alpha-core/etc/config.yml.dist /opt/alpha-core/etc/config.yml

cd /opt/alpha-core

# build, this can take some time
docker-compuse up -d

# if you got an error what docker is not started then run
systemctl restart docker

# You also might need to run this if you can login.
docker-compose restart main 

# Now you can log into alpha-core server with your computers ip adress. 
```



## Commands

```bash
# to stop server
docker-compuse stop

# to start server
docker-compuse start

# list machines
docker-compose ps

# list processes
docker-compose top

# remove everything/ uninstall images.
docker-compose down
```








