# Overview
This guide will show you how to create a systemd service on your Raspberry Pi so that you can have your scripts start on boot & to restart any service that fails.

This repository contains a few simple examples to quickly get started.

# Getting Started
Download and move inside this repository.
```bash
git clone https://github.com/matrix-io/raspi-systemd-quickstart ~/services

cd ~/services
```

Turn the bash script into an executable.
```bash
# This is only required for the bash example
chmod +x ~/services/bash_example.sh
```

Add read permissions for each service file
```bash
chmod 644 ~/services/*.service
```

Create a symbolic link in systemd for each service. This allows us to neatly store all our services in a home folder.
```bash
sudo ln -s ~/services/*.service /etc/systemd/system/
```

# Commands For Managing Your Services
> [Helpful .service file options](https://www.freedesktop.org/software/systemd/man/systemd.service.html)

Your services are now setup! Use any of the commands below to control your services.

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
