# Setting Up My Lab On Cloud (DigitalOcean and AWS)

---

> **on DigitalOcean**
> 

Use this ref link to get free $200 credit for Digital Ocean. 

[DigitalOcean | The Cloud for Builders](https://m.do.co/c/22d9fd8163c5)

create an account on digital ocean and create a project

create a droplet and select preferred image and cpu resources, set password or ssh-key then create and apply,

 

![Untitled](Setting%20Up%20My%20Lab%20On%20Cloud%20(DigitalOcean%20and%20AWS)%207e8a0767a7ca435f81be42aa75a1b6f0/Untitled.png)

use a terminal or putty(windows) to ssh into the machine.

on the machine;

run; 

```bash
apt-get update && apt-get upgrade -y
apt-get install xfce4 xfce4-goodies xorg dbus-x11 x11-xserver-utils net-tools -y //this is for the GUI and all needed resources
apt-get install virtualbox virtualbox-ext-pack firefox -y
apt-get install xrdp -y
```

when all is done installing, next is to configure the firewall to allow only needed ports

```bash
ufw status verbose
ufw allow 3389/tcp //this is the rdp port
ufw allow 22/tcp //this is for the ssh port
ufw enable
```

next is to enable the xrdp server so it can allow connection to it

```bash
systemctl enable xrdp --now
```

once that is done reboot the droplet

```bash
reboot
```

---

open any RDP client like the microsoft RDP or RealVNC Viewer

![Untitled](Setting%20Up%20My%20Lab%20On%20Cloud%20(DigitalOcean%20and%20AWS)%207e8a0767a7ca435f81be42aa75a1b6f0/Untitled%201.png)

click connect and you’ll be prompted to enter password

![Untitled](Setting%20Up%20My%20Lab%20On%20Cloud%20(DigitalOcean%20and%20AWS)%207e8a0767a7ca435f81be42aa75a1b6f0/Untitled%202.png)

this is the droplet opened in xfce4 GUI

![Untitled](Setting%20Up%20My%20Lab%20On%20Cloud%20(DigitalOcean%20and%20AWS)%207e8a0767a7ca435f81be42aa75a1b6f0/Untitled%203.png)

open the browser and download kali and any other VM you want to install on the virtualbox.

you can run install juiceshop via docker

[Docker](https://hub.docker.com/r/bkimminich/juice-shop)

[How To Install and Use Docker on Ubuntu 20.04  | DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04)

to install docker;

```docker
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
apt-get install docker-ce -y
sudo systemctl status docker // docker is installed and running
docker pull bkimminich/juice-shop
docker run -d -p 80:3000 bkimminich/juice-shop //this will also pull it if not found on local base
```

![Untitled](Setting%20Up%20My%20Lab%20On%20Cloud%20(DigitalOcean%20and%20AWS)%207e8a0767a7ca435f81be42aa75a1b6f0/Untitled%204.png)

the juice shop is running on docker and to confirm, we’ll open our firefox and assess it via [localhost:3000](http://localhost:3000) or from anywhere on the web on <myIP>:3000

![Untitled](Setting%20Up%20My%20Lab%20On%20Cloud%20(DigitalOcean%20and%20AWS)%207e8a0767a7ca435f81be42aa75a1b6f0/Untitled%205.png)

on the virtualbox i’ve installed windows server 19 and kali linux 

![Untitled](Setting%20Up%20My%20Lab%20On%20Cloud%20(DigitalOcean%20and%20AWS)%207e8a0767a7ca435f81be42aa75a1b6f0/Untitled%206.png)

---

> **On AWS**
> 

First install vbox on [localhost](http://localhost) and install all the flavours of vms needed.

export the vm as .ova

On the aws platform, 

Create an Amazon WorkSpaces account and launch a WorkSpace

Import the exported Ova file into the workspace and boot it up. 

Use an RDC to connect.
