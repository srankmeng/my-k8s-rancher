# Install Ubuntu Desktop on a Droplet

reference https://docs.digitalocean.com/developer-center/install-ubuntu-desktop-on-a-droplet/

### Step 1: Install and Set Up xrdp

To install xrdp, log in to your Droplet using SSH and then update and upgrade the packages on the Droplet:
```
sudo apt-get update
```

After upgrading the packages, install xrdp on your machine:
```
sudo apt-get install xrdp
```

Once installed, enable xrdp to start on boot by running:
```
sudo systemctl enable xrdp
```

Lastly, make sure that your Droplet’s UFW firewall rules have been set to accept TCP connections on port 3389:
```
sudo ufw allow 3389/tcp
```

### Step 2: Install Ubuntu Desktop
To install Ubuntu Desktop on your Droplet, run the following command and follow the prompts:
```
sudo apt-get install ubuntu-desktop
```

### Step 3: Create a User
add user
```
adduser your_new_username
```

Once you have created the new user, reboot your Droplet to apply all of the changes:
```
reboot
```

### Step 4: Log in to the Droplet
remote login with [Microsoft Remote Desktop](https://apps.microsoft.com/detail/9wzdncrfj3ps?hl=en-us&gl=us)