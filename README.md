
# Deploy Next js app on VPS
Buy the VPS from [linode](https://github.com/Uday032/svalync-webapp/blob/main/.env.example) or [DigitalOcean](https://github.com/Uday032/svalync-webapp/blob/main/.env.example). 



## Creating a user

```shell
ssh root@ip-address
```
```shell
apt-get update && apt-get upgrade
```
```shell
hostnamectl set-hostname your-app #give your app name
```


Go to
```shell
nano /etc/hosts
```
Add this line 
```shell
127.0.0.1  localhost  
ip-address  your-app   #Add this line
```


```shell
adduser yourname 
```

```shell
adduser yourname sudo
```

```shell
exit
```


## Securing VPS

Login through your user
```bash
  ssh yourname@ip-address
```

```bash
    mkdir -p ~/.ssh
```

### Create a key-pair to login
Open another terminal in your local and run these commands 
```bash
    ssh-keygen -b 4096
```
```bash
    scp ~/.ssh/id_rsa.pub yourname@ip-address:~/.ssh/authorized_keys
```

Go to your VPS server
```bash
    cd ~
```
```bash
    ls .ssh #check if authorized_keys folder is there or not
```
```bash
    ssh chmod 700 ~/.ssh/
```
```bash
    ssh chmod 600 ~/.ssh/*
```
```bash
    sudo nano /etc/ssh/sshd_config
```
```bash
    # Go Down
    LoginGraceTime 2m
    PermitRootLogin yes # make it no and if commented uncomment it 
```
```bash
    # Go Down
    PasswordAuthentication yes # make it no and if commented uncomment it 
    PermitEmptyPasswords no
```
```bash
    ssh systemctl restart sshd
```
```bash
    sudo apt-get install ufw
```
```bash
    sudo ufw default allow outgoing
```
```bash
    sudo ufw default deny incoming
```
```bash
    sudo ufw allow ssh
```
```bash
    sudo ufw allow ssh
```
```bash
    sudo ufw allow 8000
```
```bash
    sudo ufw enable
```
```bash
    sudo ufw status
```
    