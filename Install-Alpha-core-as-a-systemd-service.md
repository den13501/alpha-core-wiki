
We want to run Alpha-core as a systemd service in Debian 10. For this tutorial you need to have followed my guide on how to run Alpha-core in a virtual python environment. 



**Add a new user**

Then we are creating the new user, we set home dir to our alpha-core server. 

```bash
adduser --home /opt/alpha-core alpha-core
# follow the instructions
```



**Service**

We already have installed our virtual environment so now we just need to start it from a service. We cannot use workon, but we can call our installed python directly, then python will handle the virtualenv. Create a new file **/etc/system/systemd/alpha-core.service** and copy and paste the information below. Don't forgot to run **chmod +x /etc/system/systemd/alpha-core.service**



```Bash
touch /etc/system/systemd/alpha-core.service
chmod +x /etc/system/systemd/alpha-core.service
```



**Alpha-core.service**

```Bash
[Unit]
Description=Alpha-core Server
After=network.target

[Install]
WantedBy=multi-user.target

[Service]
RemainAfterExit=yes
WorkingDirectory=/opt/alpha-core
User=alpha-core
Group=alpha-core

ExecStart=/usr/bin/tmux new -d -s "alpha-core" "/opt/virtualenvs/alpha-core/bin/python3 main.py"
ExecStop=/usr/bin/tmux send -t alpha-core 'Shuting down Alpha-core' C-m

# SECURITY
PrivateUsers=true
ProtectSystem=full
ProtectHome=true
ProtectKernelTunables=true
ProtectControlGroups=true

Restart=on-failure
RestartSec=60s
```



Now we got a system service, we can now use these commands:

First we need to run **systemctl daemon-reload** so Debian recognise the new service. We need to run this command every time we update the service file.

- systemctl daemon-reload
- service alpha-core start
- service alpha-core stop
- service alpha-core status

**Run alpha-core on boot**

- service alpha-core enable

**Remove it from boot**

- service alpha-core disable

