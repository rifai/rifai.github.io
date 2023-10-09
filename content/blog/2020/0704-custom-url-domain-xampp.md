---
title: Custom url domain in Xampp
summary:  If you are developing website in Xampp, you can use custom domain instead of localhost or 127.0.0.1.
description: Custom url domain in Xampp
date: 2020-07-04
tags:
    - webdev
    - windows
---
If you are developing website in Xampp, you can use custom domain instead of **localhost** or **127.0.0.1**. You can make url like **http://mydomain.local** as an url for you local development.

## Prepare project
I'm assuming you have website project directory in **C:/xampp/htdocs/mywebsite**. We want to use url **http://mydomain.local**. I like using **.local** TLD to differentiate it with actual internet url. Then, add this line in the bottom.

## Edit hosts file

Open **C:\Windows\System32\drivers\etc\hosts**. You need Administrator Access to edit this file.

```systemd
127.0.0.1 mywebsite.local
127.0.0.1 www.mywebsite.local
```

## Edit httpd-vhosts.conf

This file is located in **C:\xampp\apache\conf\extra\httpd-vhosts.conf**. Add this code to the bottom. 

```apacheconf
<VirtualHost *:80>
  DocumentRoot C:/xampp/htdocs/
  ServerName localhost
</VirtualHost>
```

Then, add this code and adjust with your projects. 

```apacheconf
<VirtualHost *:80>
    DocumentRoot "C:/xampp/htdocs/mywebsite"
    ServerName mywebsite.local
    ServerAlias www.mywebsite.local
    <Directory "C:/xampp/htdocs/mywebsite">
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

## Finishing

You are done. Start or restart your Apache server. Go to **http://mywebsite.local** to test it. If you have any problems, drop the comments below. 