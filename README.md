# Install ownCloud X in Raspberry Pi 2.0

<p align="center"><img width="600" height="296.5" src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f6/OwnCloud_logo_and_wordmark.svg/1200px-OwnCloud_logo_and_wordmark.svg.png"><img width="255.5" height="321" src="https://www.raspberrypi.org/wp-content/uploads/2015/08/raspberry-pi-logo.png"></p>


## Raspberry Pi 2.0 or 3.0

The first step is to install the software in this case noobs. Follow the official [documentation](https://www.raspberrypi.org/documentation/installation/noobs.md) to do that. 

## Connect to Raspberry Pi via SSH (Optionally)

* In this case I work with ubuntu so I can connect remotelly using a SSH connection between my Computer and the Raspberry Pi. Now, Open the Bash command line or type **Ctrl + t**- And if you don't have nmap, then install it:

```bash
$ sudo apt-get update
$ sudo apt-get install nmap
```
* But first, we need the default IP of our Router, so type the following commands

```bash
$ ip route show | grep -i 'default via' | awk '{print $3}'
```
The IP similar like in the following image is going to show:

**IMAGE**

* **nmap** will be used in order to obtain the IP Addres of our Raspberry Pi. The ip will be used to connect using **SSH** protocol. Thus, execute the following command

```bash
$ sudo nmap -sP 192.168.1.0-255 # Your IP
```


After that follow these steps to install all the necessary packages:

* First, make an **Update** and an **Upgrade**.

```bash

$ sudo apt-get update
$ sudo apt-get upgrade

```

* Now install **apache2** and **php7**.

```bash
$ sudo apt-get install apache2 php7.0 php7.0-json php7.0-xml php7.0-gd php7.0-sqlite curl libcurl3 libcurl3-dev php7.0-curl php7.0-common
```


## ownCloud

After installing all the previous packages, you have to download owncloud. You can get it from [here](https://owncloud.org/install/).
* Download **ownCloud Server**.

* Now, install it.

```bash

$ cd ~/Download						# Go to download path.
$ tar -xjf owncloud-10.0.3.zip 		# Select your file, the version could be different.
$ sudo mv owncloud /var/www/html

```

* Give permission to web server to acces owncloud

```bash

$ sudo chown -R www-data:www-data /var/www/
$ sudo chown -R www-data:www-data /var/www/html/owncloud

```

## Use HDD as data



### Change data save path
[Link of tutorial](https://www.digitalocean.com/community/tutorials/how-to-move-the-data-directory-for-owncloud-on-ubuntu-16-04)
