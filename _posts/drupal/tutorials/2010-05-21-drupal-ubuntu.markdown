---
layout: post
title: Drupal on Ubuntu
teaser: A guide to setting up a Drupal development environment for debugging and profiling with NetBeans and Xdebug.
permalink: drupal/tutorials/drupal-ubuntu.html
language: en
categories: tutorials
tags: ubuntu drupal tutorial
---

This guide walks you through setting up a Drupal development environment using Ubuntu and NetBeans. This setup will allow you to do step through debugging and profiling of your Drupal sites.

See also:

* [Debugging Drupal](/drupal/tutorials/debugging-drupal.html)
* [Localizing Drupal](/drupal/tutorials/localizing-drupal.html)

## Install Ubuntu

Download the latest desktop CD image from [ubuntu.com](http://www.ubuntu.com) and burn it to a CD. Use the CD to boot your development machine and install Ubuntu. This guide assumes that Ubuntu will be the only operating system on your machine. Please see the Ubuntu documentation if you want to run Ubuntu alongside an existing Windows installation.

[![Download Ubuntu](/img/tutorials/drupal-ubuntu/01-download-ubuntu.png)](/img/tutorials/drupal-ubuntu/01-download-ubuntu.png){: .noborder}

When the installer has finished booting, the first thing you’ll have to do is to choose a language for the installer. This choice only affects the very first part of the installation process. If you are using a non-US keyboard, you can press F3 to select another keymap (this is usually not necessary since you’ll get to choose a keymap in the main installer).

[![Choose language](/img/tutorials/drupal-ubuntu/02-ubuntu-language.png)](/img/tutorials/drupal-ubuntu/02-ubuntu-language.png){: .noborder}

[![Choose keymap](/img/tutorials/drupal-ubuntu/03-ubuntu-keymap.png)](/img/tutorials/drupal-ubuntu/03-ubuntu-keymap.png){: .noborder}

For now, just use the arrow keys to select Install Ubuntu and press enter. Now is the time to go get the first of many cups of coffee, while you wait for the main installer to load.

[![Start the installer](/img/tutorials/drupal-ubuntu/04-ubuntu-install.png)](/img/tutorials/drupal-ubuntu/04-ubuntu-install.png){: .noborder}

[![Initializing](/img/tutorials/drupal-ubuntu/05-ubuntu-working.png)](/img/tutorials/drupal-ubuntu/05-ubuntu-working.png){: .noborder}

The first step of the installation process is to choose the language to use during installation. The chosen language will also be the default language for the final system.

[![Installation language](/img/tutorials/drupal-ubuntu/06-ubuntu-wiz-1.png)](/img/tutorials/drupal-ubuntu/06-ubuntu-wiz-1.png){: .noborder}

Next, you should select your current timezone. This information will be used to set the correct time and date.

[![Time zone](/img/tutorials/drupal-ubuntu/07-ubuntu-wiz-2.png)](/img/tutorials/drupal-ubuntu/07-ubuntu-wiz-2.png){: .noborder}

The final localization step involves choosing your keyboard layout. In most cases the installer can figure it out on its own, but you have the opportunity to override the default choice. This step of the installer also has a text field, which you can use to make sure you have chosen the correct layout.

[![Keyboard layout](/img/tutorials/drupal-ubuntu/08-ubuntu-wiz-3.png)](/img/tutorials/drupal-ubuntu/08-ubuntu-wiz-3.png){: .noborder}

Then it’s time to prepare the hard disk for Ubuntu. Since Ubuntu will be the only operating system on this machine, we choose the option Use the entire disk. This will erase all existing data on the hard disk!

[![Prepare disk space](/img/tutorials/drupal-ubuntu/09-ubuntu-wiz-4.png)](/img/tutorials/drupal-ubuntu/09-ubuntu-wiz-4.png){: .noborder}

Next, you must provide the necessary information for the installer to create an account for you. Enter your full name and (optionally) choose the username you want to use to log in, and a password. Finally, choose a name for the computer. In this guide, we’ll just go with drupal, but you’re free to choose any name you like.

[![Who are you?](/img/tutorials/drupal-ubuntu/10-ubuntu-wiz-5.png)](/img/tutorials/drupal-ubuntu/10-ubuntu-wiz-5.png){: .noborder}

The installer then displays a summary of your choices, and if you like what you see, you can start the installation process. Now would be a good time to get a second cup of coffee.

[![Ready to install](/img/tutorials/drupal-ubuntu/11-ubuntu-wiz-6.png)](/img/tutorials/drupal-ubuntu/11-ubuntu-wiz-6.png){: .noborder}

[![Installing](/img/tutorials/drupal-ubuntu/12-ubuntu-installing.png)](/img/tutorials/drupal-ubuntu/12-ubuntu-installing.png){: .noborder}

[![Installation complete](/img/tutorials/drupal-ubuntu/13-ubuntu-installation-complete.png)](/img/tutorials/drupal-ubuntu/13-ubuntu-installation-complete.png){: .noborder}

When the installation process finishes, you will be asked to remove the CD and restart the machine. Once the machine restarts, you are ready to log in to your new Ubuntu system with the username and password you chose during installation.

[![Reboot](/img/tutorials/drupal-ubuntu/14-ubuntu-remove-disc.png)](/img/tutorials/drupal-ubuntu/14-ubuntu-remove-disc.png){: .noborder}

[![Login](/img/tutorials/drupal-ubuntu/15-ubuntu-login.png)](/img/tutorials/drupal-ubuntu/15-ubuntu-login.png){: .noborder}

## Install Apache, MySQL, and PHP

When the Ubuntu install is finished and any available updates have been installed, it’s time to install the server software required to run Drupal.

Open a terminal window (Applications → Accessories → Terminal) and run the following command to install Apache, MySQL and PHP:

    sudo apt-get install lamp-server^

When sudo asks for a password, simply enter the password you used to log in to the system.

Apt-get displays a list of the packages which are about to be installed. Answer yes or press enter to start the installation. Apt-get will then download and install the required packages. (See the screenshot “Continue” below.)

[![Continue](/img/tutorials/drupal-ubuntu/16-stack-continue.png)](/img/tutorials/drupal-ubuntu/16-stack-continue.png){: .noborder}

As part of the installation process, you will be asked for a password for the MySQL root user. You will need this password to configure the database server later. (See the screenshot “MySQL password” below.)

[![MySQL password](/img/tutorials/drupal-ubuntu/17-stack-mysql-1.png)](/img/tutorials/drupal-ubuntu/17-stack-mysql-1.png){: .noborder}

[![MySQL password](/img/tutorials/drupal-ubuntu/17-stack-mysql-2.png)](/img/tutorials/drupal-ubuntu/17-stack-mysql-2.png){: .noborder}
