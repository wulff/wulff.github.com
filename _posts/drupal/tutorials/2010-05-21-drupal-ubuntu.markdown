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

## Install additional software

Open a terminal window and run the following command to install the rest of the packages required to run Drupal and NetBeans:

(On Ubuntu 10.04 you need to enable the Partner repository to install the Java Development Kit: Go to _System → Administration → Software sources_. Click the _Other software_ tab and enable the _lucid partner_ repository. Click _Close_ and then _Reload_ to rebuild the list of available software.)

    sudo apt-get install php5-cli php5-gd php5-xdebug sun-java6-jdk

This command installs the following packages:

* **php5-cli** The PHP command-line interpreter
* **php5-gd** GD support for PHP
* **php5-xdebug** Xdebug support for PHP
* **sun-java6-jdk** The Sun Java™ Development Kit

As part of the installation process, you must accept the Java license agreement.

[![Java OSDL](/img/tutorials/drupal-ubuntu/18-stack-java-eula.png)](/img/tutorials/drupal-ubuntu/18-stack-java-eula.png){: .noborder}

[![Java OSDL](/img/tutorials/drupal-ubuntu/19-stack-java-eula.png)](/img/tutorials/drupal-ubuntu/19-stack-java-eula.png){: .noborder}

Note that this version of php5-gd uses the system GD library which doesn’t include all the functions which are included in the version of GD which is bundled with PHP. This means that functions like imagefilter() and imagerotate() will not be available. If you need access to these function, you can follow this guide to compile your own version of the php5-gd package.

## PHP

Open a terminal window and run the following command to edit the main PHP configuration file (this is not necessary on 10.04):

    sudo vi /etc/php5/apache2/php.ini

Find the setting *memory_limit* and change it from *16M* to *128M*.

## Configure Apache

In order to use clean URLs in Drupal, you must enable the Apache rewrite module. Open a terminal window and run the following command:

    sudo a2enmod rewrite

When the module has been enabled, you must restart Apache:

    sudo /etc/init.d/apache2 restart

Apache will complain that it can’t determine the server’s fully qualified hostname. You can safely ignore this error message.

If you want to get rid of the error message, create a file called servername in the /etc/apache2/conf.d directory. Put the following line in the file:

    ServerName drupal

Replace drupal with the hostname you chose for you machine during the Ubuntu installation process.

[![Enable mod_rewrite](/img/tutorials/drupal-ubuntu/20-apache-mod_rewrite.png)](/img/tutorials/drupal-ubuntu/20-apache-mod_rewrite.png){: .noborder}

## Configure MySQL

Next you must create a user in the MySQL database. This user will be used to access all your local Drupal databases. Open a terminal window and start the MySQL client (you will be asked to enter the password you chose when you installed MySQL):

    mysql -u root -p

The command tells the MySQL client that you want to log in as the root user and that you want to be prompted for a password.

When you have logged in to the client, you can run the following commands to create a local drupal user and exit the MySQL client:

    CREATE USER drupal@localhost IDENTIFIED BY 'drupal';
    FLUSH PRIVILEGES;
    EXIT

You can run the following command to make sure that the new user can log in:

    mysql -udrupal -pdrupal

The user doesn’t have access to any databases yet. We will grant it database privileges when we set up the local Drupal sites.

[![Create user](/img/tutorials/drupal-ubuntu/21-mysql-user.png)](/img/tutorials/drupal-ubuntu/21-mysql-user.png){: .noborder}

## Install NetBeans

Go to the [NetBeans download page](http://www.netbeans.org/downloads/index.html) and download the PHP package. Save the file on the desktop.

[![Download NetBeans](/img/tutorials/drupal-ubuntu/22-netbeans-download.png)](/img/tutorials/drupal-ubuntu/22-netbeans-download.png){: .noborder}

[![Save](/img/tutorials/drupal-ubuntu/23-netbeans-download.png)](/img/tutorials/drupal-ubuntu/23-netbeans-download.png){: .noborder}

Open a terminal window and run the following command:

    sudo sh Desktop/netbeans-6.7.1-ml-php-linux.sh

[![Run the installer](/img/tutorials/drupal-ubuntu/24-netbeans-configure-installer.png)](/img/tutorials/drupal-ubuntu/24-netbeans-configure-installer.png){: .noborder}

After unpacking the installer you will be presented with the first step of the installation wizard.

[![Welcome](/img/tutorials/drupal-ubuntu/25-netbeans-installer-1.png)](/img/tutorials/drupal-ubuntu/25-netbeans-installer-1.png){: .noborder}

Click next to continue to the license agreement. Accept the license agreement and click next.

[![License agreement](/img/tutorials/drupal-ubuntu/26-netbeans-installer-2.png)](/img/tutorials/drupal-ubuntu/26-netbeans-installer-2.png){: .noborder}

Next, you can choose which folder to install NetBeans in. In most cases, the default folder is fine, so you can just click next.

[![Installation folder](/img/tutorials/drupal-ubuntu/27-netbeans-installer-3.png)](/img/tutorials/drupal-ubuntu/27-netbeans-installer-3.png){: .noborder}

Finally, you will be presented with a summary of your choices. If everything looks OK, click Install to start the installation process.

[![Summary](/img/tutorials/drupal-ubuntu/28-netbeans-installer-4.png)](/img/tutorials/drupal-ubuntu/28-netbeans-installer-4.png){: .noborder}

[![Installing…](/img/tutorials/drupal-ubuntu/29-netbeans-installer-5.png)](/img/tutorials/drupal-ubuntu/29-netbeans-installer-5.png){: .noborder}

Finally you have the option to provide usage data and register NetBeans. None of them are required. Click Finish to exit the installer.

[![Setup complete](/img/tutorials/drupal-ubuntu/30-netbeans-installer-6.png)](/img/tutorials/drupal-ubuntu/30-netbeans-installer-6.png){: .noborder}

NetBeans is now available in your Applications menu and you can delete the installation file from your desktop.

[![Applications menu](/img/tutorials/drupal-ubuntu/31-netbeans-applications-menu.png)](/img/tutorials/drupal-ubuntu/31-netbeans-applications-menu.png){: .noborder}

## Update NetBeans
 
The first time you start NetBeans, you should install any available updates. Click the update icon in the status bar to get started.

[![Updates available](/img/tutorials/drupal-ubuntu/32-netbeans-updates-found.png)](/img/tutorials/drupal-ubuntu/32-netbeans-updates-found.png){: .noborder}

[![Overview](/img/tutorials/drupal-ubuntu/34-netbeans-update-1.png)](/img/tutorials/drupal-ubuntu/34-netbeans-update-1.png){: .noborder}

[![License agreement](/img/tutorials/drupal-ubuntu/35-netbeans-update-2.png)](/img/tutorials/drupal-ubuntu/35-netbeans-update-2.png){: .noborder}
When the updates have been installed, you will have to restart NetBeans.

[![Restart](/img/tutorials/drupal-ubuntu/36-netbeans-update-3.png)](/img/tutorials/drupal-ubuntu/36-netbeans-update-3.png){: .noborder}

## Configure NetBeans
 
When you start NetBeans, you will be presented with a start page which shows NetBeans related news and blog posts. Uncheck “Show On Startup” if you do not wish to see this page every time you launch NetBeans. You can always access the start page from the Help menu.

[![Start page](/img/tutorials/drupal-ubuntu/37-netbeans-startup.png)](/img/tutorials/drupal-ubuntu/37-netbeans-startup.png){: .noborder}

### Basic configuration

Go to *Tools → Options* to configure the global settings. Make the following changes on these tabs:

* **Editor** On the *Formatting* sub-tab set *Number of Spaces per Indent* to 2 and *Tab Size* to 2 to match the Drupal code style guidelines.
* **PHP** Uncheck the box *Stop at the First Line*.
* **Miscellaneous** On the *Files* tab you must add a couple of non-standard file extensions used by Drupal. Click *New* and add the following extensions: *install*, *module*, and *profile*. Set the file type of each extension to *PHP (text/x-php5)*. This enables *Find usages* and code completion across all Drupal source files.

[![Options: Editor](/img/tutorials/drupal-ubuntu/39-netbeans-options-editor.png)](/img/tutorials/drupal-ubuntu/39-netbeans-options-editor.png){: .noborder}

[![Options: PHP](/img/tutorials/drupal-ubuntu/42-netbeans-options-php.png)](/img/tutorials/drupal-ubuntu/42-netbeans-options-php.png){: .noborder}

[![Options: Miscellaneous](/img/tutorials/drupal-ubuntu/110-netbeans-optins-extension.png)](/img/tutorials/drupal-ubuntu/110-netbeans-optins-extension.png){: .noborder}

[![Options: Miscellaneous](/img/tutorials/drupal-ubuntu/111-netbeans-options-mime-type.png)](/img/tutorials/drupal-ubuntu/111-netbeans-options-mime-type.png){: .noborder}

### Database connection

Go to the Services tab, expand the *Databases* item and right-click on the *MySQL Server at localhost* entry and choose *Properties…*. If you can’t see the Services tab, press `CTRL-5` or go to *Windows → Services* to enable it.

Enter the MySQL password you chose when setting up the LAMP stack in the Administrator Password field and check the Save Password box. You are now connected to your local database server. If, for some reason, the connection is dropped, you can right-click on the *MySQL Server at localhost* entry and choose *Connect* to reconnect to the server.

[![MySQL properties](/img/tutorials/drupal-ubuntu/43-netbeans-mysql-properties-popup.png)](/img/tutorials/drupal-ubuntu/43-netbeans-mysql-properties-popup.png){: .noborder}

[![MySQL properties](/img/tutorials/drupal-ubuntu/44-netbeans-mysql-properties-dialog.png)](/img/tutorials/drupal-ubuntu/44-netbeans-mysql-properties-dialog.png){: .noborder}

## Install Drupal
 
Before you can begin installing local Drupal sites you must create a local folder for them. Open a terminal window and run the following command to create a sub-directory in your home directory:

    mkdir Drupal

We will use this as the base directory for all local Drupal sites.

[![Sub-directory](/img/tutorials/drupal-ubuntu/45-drupal-local-folder.png)](/img/tutorials/drupal-ubuntu/45-drupal-local-folder.png){: .noborder}

## From an official release

Installing a local copy of an official Drupal release requires the following actions:

1. Download and unpack a stable release of Drupal
2. Create an entry in the hosts file
3. Create an Apache virtual host
4. Create a NetBeans project
5. Create a MySQL database
6. Run the Drupal installer

In the following sections each of these steps will be described in detail.

## Download and unpack Drupal

Go to [Drupal.org](http://www.drupal.org/) and download the latest version of Drupal. At the time of writing this is version 6.14. Save the file in the Drupal sub-directory in your home folder.

[![Drupal: Download](/img/tutorials/drupal-ubuntu/47-drupal-download.png)](/img/tutorials/drupal-ubuntu/47-drupal-download.png){: .noborder}

Next, open a terminal window and type the following commands to change to the Drupal sub-directory and unpack the downloaded file:

    cd Drupal/
    tar xzf drupal-6.14.tar.gz
    rm drupal-6.14.tar.gz

You now have a copy of the latest version of Drupal in your Drupal folder.

[![Drupal: Unpacking](/img/tutorials/drupal-ubuntu/49-drupal-unpack.png)](/img/tutorials/drupal-ubuntu/49-drupal-unpack.png){: .noborder}

## Create an entry in the hosts file

To make it possible to run a number of local Drupal sites simultaneously, each site must have its own hostname. To add a new hostname, open a terminal window and run the following command to open the hosts file in a text editor:

    sudo gedit /etc/hosts

Since we’re setting up Drupal 6.14, we’ll add the hostname drupal614 to the hosts file and have it point at the local web server on the IP address 127.0.0.1.

Save the file and exit the text editor when you have added the hostname.

[![Hosts file](/img/tutorials/drupal-ubuntu/83-hosts-file.png)](/img/tutorials/drupal-ubuntu/83-hosts-file.png){: .noborder}

## Create a Apache virtual host
 
Next we have to create a new Apache virtual host to handle requests to http://drupal614/. Open a terminal window and run the following commands to create a new virtual host definition:

    cd /etc/apache2/sites-available
    sudo gedit drupal614

It is a good idea to use the hostname as the name of the virtual host file. This makes it easier to manage a lot of virtual hosts.

[![Create virtual hosts file](/img/tutorials/drupal-ubuntu/51-apache-vh-1.png)](/img/tutorials/drupal-ubuntu/51-apache-vh-1.png){: .noborder}

Enter the following virtual host definition and save the file:

    <VirtualHost *:80>
      ServerAdmin webmaster@localhost
      ServerName drupal614

      DocumentRoot /home/<username>/Drupal/drupal-6.14

      <Directory />
        Options FollowSymLinks
        AllowOverride All
      </Directory>
    </VirtualHost>

The ServerName must match the hostname you added to the hosts file, and the DocumentRoot must match the name of the folder where Drupal is installed. Replace `<username>` with the username you use to log in to the local machine (on this machine it got replaced by wulff).

[![Virtual host definition](/img/tutorials/drupal-ubuntu/52-apache-vh-2.png)](/img/tutorials/drupal-ubuntu/52-apache-vh-2.png){: .noborder}

When you have saved the file, you can run the following commands in a terminal window to enable the new virtual host and reload the Apache configuration:

    sudo a2ensite drupal614
    sudo /etc/init.d/apache2 reload

You can now access the Drupal site at http://drupal614/.

[![Enable virtual host](/img/tutorials/drupal-ubuntu/53-apache-reload.png)](/img/tutorials/drupal-ubuntu/53-apache-reload.png){: .noborder}

[![Drupal installed](/img/tutorials/drupal-ubuntu/53-apache-reload.png)](/img/tutorials/drupal-ubuntu/53-apache-reload.png){: .noborder}

## Create a NetBeans project
 
The next step is to create a new NetBeans project to handle the source code of the new Drupal site.

Open NetBeans and choose *File → New Project…* and choose to create a new PHP application from existing sources.

[![New project](/img/tutorials/drupal-ubuntu/55-netbeans-file.png)](/img/tutorials/drupal-ubuntu/55-netbeans-file.png){: .noborder}

[![New project](/img/tutorials/drupal-ubuntu/56-netbeans-project-1.png)](/img/tutorials/drupal-ubuntu/56-netbeans-project-1.png){: .noborder}

Select the correct sub-directory in your Drupal folder and name the project. Leave the encoding as UTF-8 and let NetBeans put its metadata in the sources folder.

[![Name and location](/img/tutorials/drupal-ubuntu/57-netbeans-project-2.png)](/img/tutorials/drupal-ubuntu/57-netbeans-project-2.png){: .noborder}

In the final step, set the project URL to http://drupal614/ and leave the index file as `index.php`.

[![Run configuration](/img/tutorials/drupal-ubuntu/58-netbeans-project-3.png)](/img/tutorials/drupal-ubuntu/58-netbeans-project-3.png){: .noborder}

NetBeans will now scan the source files to enable autocomplete and open the index.php file in the editor pane. You can close the Palette window on the right to get more screen space for the editor window.

[![Editor pane](/img/tutorials/drupal-ubuntu/59-netbeans-project-ready.png)](/img/tutorials/drupal-ubuntu/59-netbeans-project-ready.png){: .noborder}

## Create a MySQL database
 
The final step before you can run the Drupal installer is to create a new database for the new Drupal site.

Go to the services tab in NetBeans and connect to the local database server if you are not already connected.

Right-click on the local MySQL server and choose *Create database*. Choose a name for the database (in this case, we’ll name it `drupal_614`) and grant full access to the drupal user you created in a previous step.

[![Create database](/img/tutorials/drupal-ubuntu/60-netbeans-create-database-1.png)](/img/tutorials/drupal-ubuntu/60-netbeans-create-database-1.png){: .noborder}

[![Create database](/img/tutorials/drupal-ubuntu/61-netbeans-create-database-2.png)](/img/tutorials/drupal-ubuntu/61-netbeans-create-database-2.png){: .noborder}

## Run the Drupal installer
 
Now we are ready to install Drupal. First off, we need to create a writable settings file. Open a terminal window and run the following commands:

    cd Drupal/drupal-6.14/sites/default/
    cp default.settings.php settings.php
    chmod a+w settings.php
    mkdir files
    chmod a+wx files

[![Create settings ](/img/tutorials/drupal-ubuntu/63-drupal-settings.png)](/img/tutorials/drupal-ubuntu/63-drupal-settings.png){: .noborder}

Open Firefox and go to the URL `http://drupal614/`. When you get to the *Set up database* step, enter the name of the database you created previously, and the username and password for the drupal user.

[![Start installation](/img/tutorials/drupal-ubuntu/62-drupal-install.png)](/img/tutorials/drupal-ubuntu/62-drupal-install.png){: .noborder}

[![Set up database](/img/tutorials/drupal-ubuntu/62-drupal-install.png)](/img/tutorials/drupal-ubuntu/62-drupal-install.png){: .noborder}

When you get to the *Configure site* step Drupal has made all necessary changes to the `settings.php` file. You can now write-protect the file by opening a terminal window and running the following commands:

    cd Drupal/drupal-6.14/sites/default/
    chmod a-w settings.php

Perform the final steps of the installer, and you are ready to play around on your new Drupal site.

## From CVS

This section will describe how to set up a new Drupal site from a CVS checkout.

## NetBeans overview
 
If you haven’t changed any settings, NetBeans will show the following windows on startup:

* The main editor
* Projects
* Files
* Services
* Navigator
* Tasks

You can find add more windows by going to the Window menu. We will cover a couple of these windows in the Xdebug section.

The **Projects** window shows a list of all your NetBeans projects. You can use it to browse the source of all your projects in one place and to see the include paths for different projects (by default all new projects use the global PHP include path).

[![Projects](/img/tutorials/drupal-ubuntu/67-netbeans-overview-projects.png)](/img/tutorials/drupal-ubuntu/67-netbeans-overview-projects.png){: .noborder}

The **Files** window shows all source files in the active project.

[![Files](/img/tutorials/drupal-ubuntu/68-netbeans-overview-files.png)](/img/tutorials/drupal-ubuntu/68-netbeans-overview-files.png){: .noborder}

The **Services** window gives you easy access to local database servers, web services, and issue trackers.

[![Services](/img/tutorials/drupal-ubuntu/69-netbeans-overview-services.png)](/img/tutorials/drupal-ubuntu/69-netbeans-overview-services.png){: .noborder}

The **Navigator** window shows a list of all the functions in the active file. You can double-click any function name to jump directly to the first line of a function in the editor window.

[![Navigator](/img/tutorials/drupal-ubuntu/70-netbeans-overview-navigator.png)](/img/tutorials/drupal-ubuntu/70-netbeans-overview-navigator.png){: .noborder}

The **Tasks** window gives you an overview of all syntax errors, warnings, and todo items. By default, all occurences of the strings TODO, FIXME, XXX, and PENDING are added to the task list. Go to *Tools → Options → Miscellaneous → Tasks* to add your own string patterns.

[![Task patterns](/img/tutorials/drupal-ubuntu/70-netbeans-overview-navigator.png)](/img/tutorials/drupal-ubuntu/70-netbeans-overview-navigator.png){: .noborder}

## Code completion
 
NetBeans makes developing for Drupal easier because it offers code completion of all built-in PHP functions and all functions defined in your current project. This way you have the full Drupal API and its documentation at your fingertips without having to consult [api.drupal.org](http://api.drupal.org/) every time you want to check the exact behavior of a function.

You can try it out for yourself by creating a new PHP file in the root of your Drupal folder. Right-click on the root folder (in this case, it’s called `drupal-6.14`) and choose *New → PHP file*.

[![New file](/img/tutorials/drupal-ubuntu/72-netbeans-code-new-1.png)](/img/tutorials/drupal-ubuntu/72-netbeans-code-new-1.png){: .noborder}

[![New file](/img/tutorials/drupal-ubuntu/73-netbeans-code-new-2.png)](/img/tutorials/drupal-ubuntu/73-netbeans-code-new-2.png){: .noborder}

If you place the cursor on an empty line and press `CTRL+SPACE`, NetBeans opens a popup listing all global variables and constants. Start typing to narrow down the list or use the arrow keys to choose the variable you want to insert. Press enter to insert the variable name at the current cursor position.

[![Code completion: Variables](/img/tutorials/drupal-ubuntu/75-netbeans-completion-variables.png)](/img/tutorials/drupal-ubuntu/75-netbeans-completion-variables.png){: .noborder}

Start typing the first few characters of the PHP function `str_replace` and press `CTRL+SPACE` after you have typed `str`. NetBeans opens two popups: One showing a list of matching function names and a second showing the documentation for the currently selected function. Type more characters to narrow your search or use the arrow keys to choose the function you want to insert. Press enter to insert the function name at the current cursor position.

[![Code completion: PHP](/img/tutorials/drupal-ubuntu/74-netbeans-completion-php.png)](/img/tutorials/drupal-ubuntu/74-netbeans-completion-php.png){: .noborder}

This works for Druapl API functions and functions from contributed modules as well. Try typing dru and then press `CTRL+SPACE` to show a list of all matching functions.

[![Code completion: Drupal API](/img/tutorials/drupal-ubuntu/76-netbeans-completion-drupal.png)](/img/tutorials/drupal-ubuntu/76-netbeans-completion-drupal.png){: .noborder}

## Variable highlighting

Another useful feature is variable highlighting. Open the file bootstrap.inc in the includes folder and jump to the function `drupal_bootstrap()` by double-clicking it in the Navigator window. If you place the cursor somewhere in the first occurence of the variable `$phase_index`, NetBeans automatically highlights all four occurences of that variable in the function. This is useful when you are trying to determine whether a local variable is still in use, or to figure out which role a variable plays in a function.

[![Variable highlighting](/img/tutorials/drupal-ubuntu/77-netbeans-highlighting.png)](/img/tutorials/drupal-ubuntu/77-netbeans-highlighting.png){: .noborder}

## Navigating code

Sometimes it’s nice to see where a certain function is defined. This is easy to do in NetBeans by using *Go to Declaration*.

Open `index.php` in the root of the Drupal folder and place the cursor somewhere in the function name `menu_execute_active_handler()` on line 18. (Choose *View → Show Line Numbers* to enable line numbers in the editor.) Right-click the function name and select *Navigate → Go to Declaration* or press `CTRL+B`. NetBeans now opens the file `menu.inc` where the function is defined.

[![Go to declaration](/img/tutorials/drupal-ubuntu/78-netbeans-goto-1.png)](/img/tutorials/drupal-ubuntu/78-netbeans-goto-1.png){: .noborder}

[![Go to declaration](/img/tutorials/drupal-ubuntu/78-netbeans-goto-1.png)](/img/tutorials/drupal-ubuntu/78-netbeans-goto-1.png){: .noborder}

This example also shows a variation of the variable highlighting mentioned above. If you place the cursor at the beginning of a function name, NetBeans automatically highlights all return statements in the function.

Another useful way of navigating your code is to figure out which functions are calling a given function. Return to index.php in the editor and place the cursor somewhere in the function name `menu_execute_active_handler()`. Right-click the function name and select *Find Usages* or press `ALT+F7`. When you click *Find* in the dialog, NetBeans opens the *Usages* window and shows a list of all the calls to the selected function.

[![Find usages](/img/tutorials/drupal-ubuntu/80-netbeans-usages-1.png)](/img/tutorials/drupal-ubuntu/80-netbeans-usages-1.png){: .noborder}

[![Find usages](/img/tutorials/drupal-ubuntu/81-netbeans-usages-2.png)](/img/tutorials/drupal-ubuntu/81-netbeans-usages-2.png){: .noborder}

[![Find usages](/img/tutorials/drupal-ubuntu/82-netbeans-usages-3.png)](/img/tutorials/drupal-ubuntu/82-netbeans-usages-3.png){: .noborder}

**TODO:** Add information on code folding.

## Debug your code

Xdebug lets you step through your code line by line, inspecting variables and the call stack as you go. This makes identifying problems faster than having to rely on printed debug statements or log files.

## Configure Xdebug
 
Before we can start debugging with Xdebug, we need to modify the Xdebug configuration. Open a terminal window and run the following command to open the `xdebug.ini` file in a text editor:

    sudo gedit /etc/php5/conf.d/xdebug.ini

Add the following lines to the file:

    xdebug.remote_enable=on
    xdebug.remote_handler=dbgp
    xdebug.remote_mode=req
    xdebug.remote_host=127.0.0.1
    xdebug.remote_port=9000

When you have saved the file you must run the following command to restart Apache:

    sudo /etc/init.d/apache2 restart

[![xdebug.ini](/img/tutorials/drupal-ubuntu/89-xdebug-configuration.png)](/img/tutorials/drupal-ubuntu/89-xdebug-configuration.png){: .noborder}

## Debug with Xdebug
 
Now that the Xdebug PHP module has been configured, we can use NetBeans to step through the code as it is being executed by the Apache PHP module.

First, we need to mark the line of code where we would like execution to stop. This is called a breakpoint.

We’ll try to step through the Drupal bootstrap process, so start by opening the file `includes/bootstrap.inc`. Double-click the function `drupal_bootstrap()` in the Navigator to jump to line 983 in the file. Place the cursor in the first line of the function and click the line number (line 984) or press `CTRL+F8` to set a breakpoint (Choose *View → Show Line Numbers* to enable line numbers in the editor window).

[![Breakpoint](/img/tutorials/drupal-ubuntu/94-xdebug-breakpoint.png)](/img/tutorials/drupal-ubuntu/94-xdebug-breakpoint.png){: .noborder}

Choose *Debug → Debug Project* or press `CTRL+F5` to start a debugging session. The first time you do this, NetBeans displays a dialog where you can configure some general debugging options. Choose *Server side PHP* and tell NetBeans not to show the dialog again.

[![Debug project](/img/tutorials/drupal-ubuntu/95-xdebug-debug-project.png)](/img/tutorials/drupal-ubuntu/95-xdebug-debug-project.png){: .noborder}

[![Dialog](/img/tutorials/drupal-ubuntu/88-xdebug-dialog.png)](/img/tutorials/drupal-ubuntu/88-xdebug-dialog.png){: .noborder}

NetBeans will open the front page of your site in FireFox and stop at the first breakpoint it encounters. If you return to the NetBeans window you will see a small green arrow next to the line which is about to be executed.

[![Waiting](/img/tutorials/drupal-ubuntu/90-xdebug-waiting.png)](/img/tutorials/drupal-ubuntu/90-xdebug-waiting.png){: .noborder}

Also, NetBeans automatically opens four windows below the editor windows: Watches, Variables, Call Stack, and Breakpoints. In the Variables window you can see a list of all the variables which are currently in scope as well as all the PHP superglobals. The Call Stack window displays the current call stack, and the Breakpoints windows displays a list of all breakpoints.

[![Variables](/img/tutorials/drupal-ubuntu/96-xdebug-variables.png)](/img/tutorials/drupal-ubuntu/96-xdebug-variables.png){: .noborder}

[![Call stack](/img/tutorials/drupal-ubuntu/97-xdebug-callstack.png)](/img/tutorials/drupal-ubuntu/97-xdebug-callstack.png){: .noborder}

[![Step over](/img/tutorials/drupal-ubuntu/98-xdebug-step.png)](/img/tutorials/drupal-ubuntu/98-xdebug-step.png){: .noborder}

## Keyboard shortcuts
 
Use the following shortcuts to step through the code when running under the debugger:

Key     | Action        | Description
--------|---------------|------------------------------------------------------
F5      | Continue      | Runs until the next breakpoint or until the code exits, whichever comes first
F8      | Step over     | Steps through the code one line at a time, but doesn’t enter any functions it encounters
F7      | Step into     | Like step over, but steps into any functions it encounters
CTRL+F7 | Step out      | Steps out of a function which has previously been stepped into
F4      | Run to cursor | Runs until the current line of execution is on the same line as a cursor (this is useful to skip past big blocks of uninteresting code)

## Profile your code
 
In addition to doing step through debugging, you can also use Xdebug to profile your code. Profiling your code lets you see which functions use most of the execution time, making it easy to spot candidates for optimization.

## Configure Xdebug

Before you can use Xdebug to profile your code, you have to modify the configuration slightly. Open a terminal window and run the following command to open the `xdebug.ini` file in a text editor:

    sudo gedit /etc/php5/conf.d/xdebug.ini

Add the following line to the end of the file:

    xdebug.profiler_enable_trigger=1

[![xdebug.ini](/img/tutorials/drupal-ubuntu/99-xdebug-ini.png)](/img/tutorials/drupal-ubuntu/99-xdebug-ini.png){: .noborder}

This lets you trigger the xdebug profiler from the browser.

When you have saved the file you must run the following command to restart Apache:

    sudo /etc/init.d/apache2 restart

## Install Webgrind

In order to analyze the output files generated by the profiler, you must install Webgrind.

Start by downloading the [latest version of Webgrind](http://code.google.com/p/webgrind/). Open the file with the Archive Manager and extract the `webgrind` folder to the `Drupal` folder in your home directory.

[![Download](/img/tutorials/drupal-ubuntu/100-webgrind-download.png)](/img/tutorials/drupal-ubuntu/100-webgrind-download.png){: .noborder}

[![Extract](/img/tutorials/drupal-ubuntu/101-webgrind-extract-1.png)](/img/tutorials/drupal-ubuntu/101-webgrind-extract-1.png){: .noborder}

[![Extract](/img/tutorials/drupal-ubuntu/102-webgrind-extract-2.png)](/img/tutorials/drupal-ubuntu/102-webgrind-extract-2.png){: .noborder}

Next, we’ll add a hostname for the local webgrind installation. Open a terminal window and run the following command to open the hosts file in a text editor:

    sudo gedit /etc/hosts

Add an entry for webgrind and point it at the local web server on 127.0.0.1.

[![Hosts file](/img/tutorials/drupal-ubuntu/103-webgrind-hosts.png)](/img/tutorials/drupal-ubuntu/103-webgrind-hosts.png){: .noborder}

Finally, we have to create a new Apache virtual host to handle requests to http://webgrind/. Open a terminal window and run the following commands to create a new virtual host definition:

    cd /etc/apache2/sites-available
    sudo gedit drupal614

It is a good idea to use the hostname as the name of the virtual host file. This makes it easier to manage a lot of virtual hosts.

Enter the following virtual host definition and save the file:

    <VirtualHost *:80>
      ServerAdmin webmaster@localhost
      ServerName drupal614

      DocumentRoot /home/<username>/Drupal/drupal-6.14

      <Directory />
        Options FollowSymLinks
        AllowOverride All
      </Directory>
    </VirtualHost>

The ServerName must match the hostname you added to the hosts file, and the DocumentRoot must match the name of the folder where webgrind is installed. Replace with the username you use to log in to the local machine (on this machine it got replaced by wulff).

[![Virtual host definition](/img/tutorials/drupal-ubuntu/104-webgrind-virtual-host.png)](/img/tutorials/drupal-ubuntu/104-webgrind-virtual-host.png){: .noborder}

When you have saved the file, you can run the following commands in a terminal window to enable the new virtual host and reload the Apache configuration:

    sudo a2ensite webgrind
    sudo /etc/init.d/apache2 reload

You can now access Webgrind at http://webgrind/.

[![Done](/img/tutorials/drupal-ubuntu/105-webgrind-done.png)](/img/tutorials/drupal-ubuntu/105-webgrind-done.png){: .noborder}

## Start profiling
 
To start the profiler, simply add `?XDEBUG_PROFILE` to any URL on your local Drupal site. The page will load normally, but Xdebug will create a `cachegrind.out` file in the `/tmp` folder.

When the cachegrind file has been written you can go to http://webgrind/ to start analyzing it. In the Webgrind window, you can either just press *Update* to analyze the latest cachegrind file or select a specific file from the dropdown.

**TODO:** Description of the Webgrind interface.

[![Start the profiler](/img/tutorials/drupal-ubuntu/106-webgrind-run.png)](/img/tutorials/drupal-ubuntu/106-webgrind-run.png){: .noborder}

[![Choose file to analyze](/img/tutorials/drupal-ubuntu/107-webgrind-choose.png)](/img/tutorials/drupal-ubuntu/107-webgrind-choose.png){: .noborder}

[![Output](/img/tutorials/drupal-ubuntu/108-webgrind-output-1.png)](/img/tutorials/drupal-ubuntu/108-webgrind-output-1.png){: .noborder}

[![Output](/img/tutorials/drupal-ubuntu/109-webgrind-output-2.png)](/img/tutorials/drupal-ubuntu/109-webgrind-output-2.png){: .noborder}
