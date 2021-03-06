# Dreamweaver-Ubuntu
## Using Dreamweaver CC 2019 with Ubuntu 19.10 as a localhost PHP server.

There are many times which users do not want to install PHP development requirements on windows due to different reasons, while at the same time, they want to develop their website and also test it on different devices. Dreamweaver(DW) is an Adobe product that helps to work more efficiently while designing the website. It has native support for the use of PHP and MySQL. Using the DW and installing all the requirements on a host OS will put too much load on your system, and if you are like me using software that needs too many resources, you don't want to run these programs on your primary OS. Also, every time you change your OS, going through the process of reestablishing your local server, again and again, is a hassle. Another essential feature is the ability to access the website in your home network using different devices (kind of like testing the web in real life). Here is a guide on how to set up a local virtual server that is accessible by all devices in the same network.

I am not a Linux expert, so most of the things I am writing here are from different resources. I'll put a link after each section, so you can go and check the reference. I try to explain everything as simple as possible, and I hope the community helps to improve both writing and technical issues.

>*__Note: I am running this tutorial on windows 10 version 1909 (host OS). I am using "Cmder" instead of "Windows cmd" or "Windows PowerShell".__*

### Requirement

here is the list of requirements for establishing the local server:
* Ubuntu 19.10
* VirtualBox
* Dreamweaver CC 2019


### Setting up Ubuntu

There are many videos and tutorials on how to install VirtualBox and run Ubuntu. These are some links to Youtube videos:
* Installing VirtualBox: 
  * https://youtu.be/4u2HGOagp7c
* Installing Ubuntu on virtualBox: 
  * https://www.codeooze.com/windows-10/windows-10-ubuntu-vbox/
  * https://www.lifewire.com/install-ubuntu-linux-windows-10-steps-2202108
  
  
>*__Note: It is essential to install "VirtualBox guest additions" for ubuntu to run efficiently.__*
>* https://linuxconfig.org/virtualbox-install-guest-additions-on-ubuntu-19-10-eoan-ermine


### Installing SSH on Ubuntu

To communicate with the guest OS(ubuntu), we will be using SSH. Also, Dreamweaver will use SSH (SFTP) to connect to the localhost.
* https://help.ubuntu.com/community/UFW

>*__Note: "UFW - Uncomplicated Firewall" is ubuntu's default firewall. Since this OS is running on VirtualBox, there is no need to enable it. You do not need to run the "ufw" commands. Make sure that the firewall is inactive using the following command:__*
```
sudo ufw disable
```
>*__Note: This is a reference to "UFW":__*
>* https://help.ubuntu.com/community/UFW

### Setting up the Engine

This part is the most important. You need to install and test the engine on your guest os to make sure that it works. Please install the package in an ordered matter as follow:

1. Install Apache, MySQL, PHP: 
* https://www.ostechnix.com/install-apache-mysql-php-lamp-stack-on-ubuntu-18-04-lts/
* https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-16-04
 
2. Install phpMyAdmin: 
* https://www.ostechnix.com/install-phpmyadmin-with-lamp-stack-on-ubuntu-18-04-lts/

>*__While installing PHPMyAdmin, an error occurred. The package was not in the package list. To resolve that I installed it from a repository:__*
>* https://launchpad.net/~phpmyadmin/+archive/ubuntu/ppa

>*__Note: You do not need to run "ufw" commands on your local environment. Make sure that the firewall is inactive.__*

3. Change the working directory for your website to the desired location. This step is essential to make a note of the directory it will be given to Dreamweaver to copy the files automatically:
* https://www.digitalocean.com/community/tutorials/how-to-move-an-apache-web-root-to-a-new-location-on-ubuntu-16-04

After these steps, you should be able to see the website or Apache welcome page by typing "localhost" or "127.0.0.1" within firefox's address bar within ubuntu. Now it is time to connect the guest OS to the local network.

### Configuring VirtualBox

By changing the network mode for the VM(guest OS: ubuntu) to bridge mode, the VM will become part of the network and will have an IP. Make sure that the "Name" option of the adapter is correct. The name should be the adapter that is connected to the local network (either wireless or LAN). 
* https://www.linuxbabe.com/virtualbox/a-pretty-good-introduction-to-virtualbox-bridged-networking-mode
>*__Note: You can access the ssh using the "NAT" option with port forwarding. However, you will not be able to get access to the webserver.__*
>* https://bobcares.com/blog/virtualbox-ssh-nat/
>* https://www.techrepublic.com/article/how-to-use-port-forwarding-in-virtualbox/

You can find the IP of the VM(ubuntu) by typing the following command inside the terminal:
```
ifconfig
```
By typing that IP inside any browser, whether a pc or mobile or tablet, etc., you should be able to access the guest os and the server in our case the welcome page of apache or a test page. If you reached it here, you have finished the hard part of this tutorial. The only thing left to do is to connect the Dreamweaver using "SFTP".

### Connecting Dreamweaver to Guest OS

This part is exactly like connecting the DW to a real webserver. Enter the followings for the inputs:
* **Server Nama:** You can use whatever you like here.
* **Connect USing:** SFTP
* **SFTP Address:** The IP of your guest OS.
* **Port:** 22 (make sure it is 22).
* **Username and Password/Private Key File:** I used a username and password, which is the username and the password for the guest OS. Alternatively, you can create a key file and use it. I found the first solution easier since it is the local server.
* **Root Directory:** The desired location you created while configuring the server(make sure it is in Unix format).
* https://www.digitalmastersmag.com/magazine/how-to-set-up-adobe-dreamweaver-for-uploads-to-amazon-aws-ec2-without-an-ftp-account/


## The END
### That's it!
Just like that, and it is finished. You can create a clone of that VM for maybe later use or as a backup. But that's it! And you know the rest. I hope this tutorial will be useful for anyone who likes working with Dreamweaver, PHP, Ubuntu. Please tell me if there is any problem with the tutorial. 

Thanks.
