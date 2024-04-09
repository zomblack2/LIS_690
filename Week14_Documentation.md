# Install Koha ILS

## Create a new VM

- click on the hamburger icon
- click on compute engine and VM instances
- create instance
- provide a name
- select E2 in machine configuration section
- select e2 medium (2 vCPU, 1 core, 4 GB memory)
- click change under boot disk
- select Ubuntu 20.04 LTS x86/64
- leave set to Balanced persistent disk
- set disk size to 10GB
- click select button
- allow HTTP traffic
- click create button

## Set firewall rule

- click on hamburger icon
- click on VPC network
- click on Firewall
- Create a firewall rule
    - add name: koha
    - add description: open port 8080
- next to targts click on all instances in the network
- add 0.0.0.0/0 to source IPv4 ranges
- slick on specified protocols and ports
    - click on TCP
    - add 8080 in ports box
- click Create

## Install Koha Repo

- upgrade local repositories
- upgrade servers
- commands to save disk space
- install gnupg2 to create digital signatures
- reboot system

      sudo apt update
      sudo apt upgrade
      sudo apt autoremove -y && sudo apt clean
      sudo apt install gnupg2
      sudo reboot now

## Add Koha Repository

    sudo su
    echo 'deb http://debian.koha-community.org/koha stable main' | sudo tee /etc/apt/sources.list.d/koha.list
    wget -q -O- https://debian.koha-community.org/koha/gpg.asc | sudo apt-key add -

## Install Koha

- update/synch new repository with Koha remote repository
- view package info
- install

      apt update
      apt show koha-common
      apt install koha-common

## Configure Koha

- edit configuration files
- install and set up mysql-server
- set root MySQL password
- enable URL rewriting and CGI functionality
- restart apache
- create database for Koha
- tell apache to listen on port 8080
- confirm apache configurations
- restart apache

      nano /etc/koha/koha-sites.conf

Change: INTRAPORT="80" to INTRAPORT="8080"

      apt install mysql-server

      mysqladmin -u root password bibliolib1

      a2enmod rewrite
      a2enmod cgi

      systemctl restart apache2

      koha-create --create-db bibliolib

      nano /etc/apache2/ports.conf
ADD: Listen 8080

      apachectl configtest

      systemctl restart apache2

- disable default apache2 setup, enable traffic compression, enable bibliolib site, reload apache's configurations, restart apache

      a2dissite 000-default
      a2enmod deflate
      a2ensite bibliolib
      systemctl reload apache2
      systemctl restart apache2

## Koha Web Installer

- get Koha username and password from this file:

      nano /etc/koha/sites/bibliolib/koha-conf.xml

  - look for <config> stanza and line beginning with <user
NOTE: DO NOT CHANGE USERNAME AND PASSWORD just look them up this way

- Go to http://34.16.180.91:8080 and use web installer configuration

## Public OPAC

- click on More in the top drop down box
- click on Administration
- click on Global System Preferences
- click on OPAC in the left hand side bar
- Scroll down to the OPACBaseURL line
- enter IP address of your server: http://34.16.180.91
- Click on Save all OPAC Preferences

## Additional Tasks

- create patron accounts
- create bibliographic records
- check out books to patrons
- delete patron circulation history

