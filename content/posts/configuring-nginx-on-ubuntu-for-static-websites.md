---
title: "Configuring Nginx on Ubuntu for Static Websites"
date: 2023-02-04T23:26:43+10:00
draft: false
categories:
  - Ubuntu
  - Nginx
---

# Introduction
Nginx is a popular open-source web server that can be used to serve static websites. In this guide, we will show you how to install Nginx on Ubuntu and configure it for a static website or multiple websites.

## Installing Nginx on Ubuntu
To install Nginx on Ubuntu, you can use the following commands:

```
sudo apt update
sudo apt install nginx
```


This will install Nginx and all of its dependencies.

## Configuring a Static Website with Nginx
To configure a static website on Nginx, follow these steps:

1. Create a directory to store the website's files. This directory will be the root directory for the website. For example, `/var/www/example.com/`

2. Create a new configuration file in the `/etc/nginx/sites-available` directory for the website. For example, `/etc/nginx/sites-available/example.com`. 

3. Open the configuration file in a text editor, and add the following basic configuration:

```
server {
    listen 80;
    server_name example.com;
    root /var/www/example.com;
    index index.html;
    location / {
        try_files $uri $uri/ =404;
    }
}
```


This configuration tells Nginx to listen on port 80 for incoming requests for example.com. It also specifies the root directory for the website and the default index file. The `location /` block tells Nginx to try to serve the requested file, and if it doesn't exist, to return a 404 error.

4. Create a symbolic link from the `sites-available` directory to the `sites-enabled` directory by running the command: `sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/`

5. Test the configuration by running the command: `sudo nginx -t` 

6. If the configuration is correct, reload Nginx to apply the changes: `sudo systemctl reload nginx`

7. Finally, copy the static files of your website to the root directory you defined in the configuration file  `/var/www/example.com/`

8. Now you can visit your website by visiting the IP address or hostname of your server in a web browser.

## Configuring Multiple Websites with Nginx
To configure multiple websites with Nginx, you can use the virtual host feature. Here are the steps to configure multiple websites on Nginx:

1. Create a directory to store the files for each website. These directories will be the root directories for the websites. For example, `/var/www/example1.com/` and `/var/www/example2.com/`

2. Create a new configuration file in the `/etc/nginx/sites-available` directory for each website. For example, `/etc/nginx/sites-available/example1.com` and `/etc/nginx/sites-available/example2.com`

3. Open the configuration file for each website in a text editor and add the
