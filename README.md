# cheet-sheets

## Git
```sh
git config --global user.name "RivoLink"
git config --global user.email "rivo.link@gmail.com"

# Warning: If you use this method, your Git account passwords will be saved in plaintext format
# in the global .git-credentials file, e.g in Linux it will be /home/[username]/.git-credentials
git config --global credential.helper store
```

## Start
`# start.sh`
```sh
#!/bin/bash

if [ -z "$1" ]; then
      gnome-terminal
else
      open "$1"
fi
```
`# .bash_aliases`
```sh
alias start="eval /path/to/start.sh $@"
```

```sh
# make start.sh executable
sudo chmod +x /path/to/start.sh

# refresh aliases
sudo source ~/.bash_aliases
```

## phpMyAdmin
`# rl-phpmyadmin.service`
```sh
[Unit]
Description=RL - PhpMyAdmin Service
After=mysqld.service

[Service]
User=root
Type=simple
TimeoutSec=0
PIDFile=/run/rl-phpmyadmin.pid
ExecStart=/bin/bash /path/to/onstart.sh
Restart=on-failure
RestartSec=42s

[Install]
WantedBy=default.target
```
`# onstart.sh`
```sh
#!/bin/bash

cd /path/to/phpmyadmin
php7.4 -S localhost:9000 > /path/to/log.txt 2>&1
```
```
# set rl-phpmyadmin.service permissions
sudo chmod 664 /etc/systemd/system/rl-phpmyadmin.service

# make onstart.sh executable
sudo chmod +x /path/to/onstart.sh

# refresh systemd
sudo systemctl daemon-reload

# show proprieties
sudo systemctl show rl-phpmyadmin

# start/stop rl-phpmyadmmin
sudo systemctl start rl-phpmyadmin
sudo systemctl stop rl-phpmyadmin

# list status/history
sudo systemctl status rl-phpmyadmin
sudo journalctl -u rl-phpmyadmin | tail

# enable/disable start on boot
sudo systemctl enable rl-phpmyadmin
sudo systemctl disable rl-phpmyadmin

# check enable/disable status on boot
sudo systemctl is-enabled rl-phpmyadmin
sudo systemctl list-unit-files '*rl-phpmyadmin*'
```
