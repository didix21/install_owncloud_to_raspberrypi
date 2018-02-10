# Install ownCloud X in Raspberry Pi 2.0 or 3.0

<p align="center"><img width="600" height="296.5" src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f6/OwnCloud_logo_and_wordmark.svg/1200px-OwnCloud_logo_and_wordmark.svg.png"><img width="255.5" height="321" src="https://www.raspberrypi.org/wp-content/uploads/2015/08/raspberry-pi-logo.png"></p>


## Raspberry Pi 2.0 or 3.0

The first step is installing the **Raspbian Software** to our **Raspberry Pi**. Follow the official [documentation](https://www.raspberrypi.org/documentation/installation/noobs.md) to do that. 

## Connect to Raspberry Pi via SSH (Optionaly)
This is step is not required, you can execute all the commands directly in your raspberry pi but you will need an external keyboard, mous and PC monitor with a HDMI connection. But if you don't have a Keyboard, you can do the folliwing steps in order to connect your computer to your Raspberry Pi. In this case I work with ubuntu so I can connect remotelly using a SSH connection between my Computer and the Raspberry Pi. 

Now, open the Bash command line or type **Ctrl + t**- And if you don't have nmap, then install it:

```bash
$ sudo apt-get update
$ sudo apt-get install nmap
```
We need the default IP of our Router, so type the following commands

```bash
$ ip route show | grep -i 'default via' | awk '{print $3}'
```
You are going to obtain something like this:

**IMAGE**

Now, we know our router IP's address. Taking this addres we have to scan our private net. Using the following command, we are going to obtain a list of IP of our different devices connected to our local net. **nmap** will be used in order to obtain the IP Addres of our Raspberry Pi. The ip will be used to connect using **SSH** protocol. Thus, execute the following command: **_sudo nmap -sP <your ip>.0-255_**:

```bash
$ sudo nmap -sP 192.168.1.0-255     # In my case
```

You will see something like this:

**IMAGE**

Now, we are going to connec to our Raspberry PI using our computer. Type: **_ssh pi@<your ip>_**

```bash
$ ssh pi@192.168.1.52   # In my case
```
So now we are connected to our Raspberry Pi and it is ready for execute commands.

# Steps before installing OwnCloud
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
