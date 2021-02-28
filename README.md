# Sonarqube docker containers

## Search and replace

    <MY_REPOSITORY>         # URL of your GIT repository
    <MY_PROJECT_PATH>       # Path of your application

## Installation

    git clone git@github.com:dockerguild/sonarqube.git sonarqube
    cd sonarqube
    rm -fr .git
    git init
    git remote add origin <MY_REPOSITORY>

## Configure proxy

Requirement : Nginx

Edit vhost `config/nginx/proxy.conf` and register it to nginx

    ln -s "${PWD}/config/nginx/proxy.conf" /etc/nginx/sites-enabled/sonarqube.conf
    service nginx restart

## Configure crontab

Edit vhost `config/crontab/crontab` and register it to crontab

    ln -s "${PWD}/config/crontab/crontab" "/etc/cron.d/sonarqube"

## Usage

Start containers

    make start

Restart containers

    make restart

Down containers

    make down

Update containers

    make update

## Backup

**Before your must configure** `.make/filesystem` according to your use.

**You must also set up an external backup system !**

Dump containers files

    make filesystem/dump

Restore containers files

    make filesystem/restore

## Crontab

For crontab usage

    bash /<MY_PROJECT_PATH>/bin/console.sh dump
