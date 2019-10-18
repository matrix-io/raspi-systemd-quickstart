# Overview
This guide will show you how to create a systemd service on your Raspberry Pi so that you can have your scripts start on boot & to restart any service that fails.

# Getting Started
Download this repository to 
```
git clone https://
```

## Bash Service Example
Create a bash script called `service.sh` in `~/services` and paste the following.

```bash
while :
do
echo "Looping...";
sleep 1;
done
```

Create the `bashService.service` file in `~/services` and paste the following.
```
[Unit]
Description=Example systemd bash service.

[Service]
User=pi
Type=simple
ExecStart=/bin/bash /home/pi/services/bashS$

[Install]
WantedBy=multi-user.target
```

With our service and script defined, it's time to add it.
```bash
# Make the bash file executable
chmod +x ~/services/service.sh

# Give read permissions to your service
sudo chmod 644 ~/services/bashService.service

# Give systemd a symbolic link to your service
sudo ln -s ~/services/bashService.sh /etc/systemd/system/bashService.service
```

# Commands For Managing Your Services
```bash
# Load Any Changes Made To All .service Files
sudo systemctl daemon-reload

# Start
sudo systemctl start YOUR_SERVICE_NAME.service

# Stop
sudo systemctl stop YOUR_SERVICE_NAME.service

# Restart
sudo systemctl restart YOUR_SERVICE_NAME.service

# Run On System Boot
sudo systemctl enable YOUR_SERVICE_NAME.service

# Stop Running On System Boot
sudo systemctl disable YOUR_SERVICE_NAME.service

# View Service Logs
sudo systemctl status YOUR_SERVICE_NAME.service
```
