# Dreamweaver-Ubuntu
## Using dream weaver with Ubuntu 19.0 as a localhost PHP server.

There are many times which users do not want to install PHP development requirements on windows due to different reasons, while at the same time they want to develop their website and also test it on different devices. Dreamweaver(DW) is an Adobe product that helps to work more efficiently while developing the website. It has native support for the use of PHP and MySQL. Using the DW and installing all the requirements on a host OS will put too much load on your system and if you are like me using software that needs too many resources, you don't want to run these programs on your main OS. Also, every time you change your OS, going through the process of reestablishing your local server, again and again, is a hassle. Another important feature is the ability to access the website in your home network using different devices (kind of like testing the web in real life). Here is a guide on how to set up a virtual local server that is accessible by all devices in the same network.

I am not a Linux expert, so most of the things I am writing here are from different resources. I'll put a link after each section, so you can go and check the reference. I try to explain everything as simple as possible and I hope the community helps to improve both writing and technical issues.

*__Note: I am running this tutorial on windows 10 version 1909.
and I am using "Cmder" instead of "Windows cmd" or "Windows PowerShell".__*

### Requirement

here is the list of requirements for establishing the local server:
* Ubuntu 19.10
* VirtualBox
* Dreamweaver cc 2019


### Setting up Ubuntu

There are many videos and tutorials on how to install VirtualBox and run Ubuntu. These are some links to Youtube videos:
* Installing VirtualBox: https://youtu.be/4u2HGOagp7c
* Installing Ubuntu on virtualBox: 
  * https://www.codeooze.com/windows-10/windows-10-ubuntu-vbox/
  * https://www.lifewire.com/install-ubuntu-linux-windows-10-steps-2202108
  
  
*__NOTE: It is important to install "virtualbox guest additions" in order for ubuntu to run efficiently.__*
  * https://linuxconfig.org/virtualbox-install-guest-additions-on-ubuntu-19-10-eoan-ermine
