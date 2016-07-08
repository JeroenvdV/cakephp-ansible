# Ansible LEMP setup with CakePHP 3 (PHP 7)

[![Build Status](https://travis-ci.org/voycey/cakephp-ansible.svg?branch=master)](https://travis-ci.org/voycey/cakephp-ansible)

This Ansible playbook is designed to be a one command setup of an entire LEMP server with webroot directories created for CakePHP ( but easily overridable for any PHP system)

## Defaults
* PHP 7 - with Modules:
  * FPM
  * GD
  * Intl
  * Json
  * Mbstring
  * MySql
  * Redis


* Nginx (Ubuntu package)
* MySQL 5.6 (5.7 is currently broken with Docker / Travis - Port 3306)
* Redis (Port 6379)
* Sphinxsearch (Port 9307)
* Git

It has pretty sane defaults (for development only!), a standard my.cnf and a single FPM pool (all customisable).

_Please note: MySQL has an empty root password when using sudo_

## Installation

1. Edit ```defaults/user.yml``` and enter your own details
2. If you wish to populate MySQL then place a dump called ```dump.sql``` or ```dump.sql.gz``` into the ```sql``` directory
2. If you are using Vagrant then you can simply issue a ```sudo vagrant up``` in the root directory and it should download everything and set up your system
3. If you are just using this on a server then you can clone this repo somewhere on your server and then run ```sudo ansible-playbook setup.yml```
4. CakePHP latest version is installed automatically to ```/var/www/vhosts/<domain>/```


## TODO:

1. Install josediazgonzalez/dotenv and enable programatically (point to .env file in config)
2. Use a DSN to connect to the DB with .env variables (DATABASE_URL is used by default)
3. Source ENV file for environment
4. Check Sphinx works
5. Set up Cake to use Redis for caching

Adapted from: https://github.com/chusiang/php7.ansible.role