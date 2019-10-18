# Overview
This guide will show you how to create a systemd service on your Raspberry Pi so that you can have your scripts start on boot & to restart any service that fails.

This repository contains a few simple examples to quickly get started.

# Getting Started
Download and move inside this repository.
```
git clone https://github.com/matrix-io/raspi-systemd-quickstart ~/services

cd ~/services
```

<!-- 

With our service and script defined, it's time to add it.
```bash
# Make the bash file executable
chmod +x ~/services/service.sh

# Give read permissions to your service
sudo chmod 644 ~/services/bashService.service

# Give systemd a symbolic link to your service
sudo ln -s ~/services/bashService.sh /etc/systemd/system/bashService.service
``` -->

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
