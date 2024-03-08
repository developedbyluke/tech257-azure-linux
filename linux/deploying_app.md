# Using a VM to Deploy an App

### Commands to run once you SSH into the VM

1. `sudo apt update -y`
2. `sudo apt upgrade -y`
3. `sudo apt install nginx -y`
4. `sudo systemctl restart nginx`
5. `sudo systemctl enable nginx`
6. `curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash - &&\ sudo apt-get install -y nodejs`

### Transfer files to the VM

#### Method 1: Using SCP

```bash
scp -i /c/Users/username/.ssh/private_key -r /c/Users/username/Downloads/app username@public-ip:/path/to/save
```

#### Method 2: Using GitHub

1. Create a new repository on GitHub.
2. Push the app to the repository.
3. SSH into the VM.
4. Run the following commands:

```bash
sudo apt install git -y
git clone https://github.com/developedbyluke/sparta-test-app.git
mv sparta-test-app/app .
rm -rf sparta-test-app
```

### Run the app

```bash
cd app
npm install
npm start
```

### Access the app

Go to `http://public-ip:3000` in a web browser.

### Automating the Deployment

To automate the installation and configuration of Nginx and the app on a Linux system, you can create a shell script. Here's an example script that installs Nginx, starts the service, and enables it to run at boot:

```bash
#!/bin/bash

# Update the package list
sudo apt update -y
sudo apt upgrade -y

# Install nginx
sudo apt install nginx -y

# Restart nginx
sudo systemctl restart nginx

# Enable nginx to start on boot
sudo systemctl enable nginx

# Install Node.js
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash - && sudo apt-get install -y nodejs

# Clone the app from GitHub
sudo apt install git -y
git clone

# Run the app
cd app
npm install
npm start
```
