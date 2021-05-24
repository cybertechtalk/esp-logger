# ESP Bug

Remote WiFi data logger using ESP8266 and ESPPL library.  More documentation soon.

## Features
<p align="center">
  <img alt="" src="/img/web.png">
  <br>
  <b>Remote ESP8266 Web Interface</b>
  <br>
  <br>
</p>

## Installation (Linux)
Update machine  
```
sudo apt update
sudo apt upgrade  
```
Install Nginx Server and PHP
```
sudo apt install nginx
sudo apt install php-fpm php-mysql
```
Edit config file
```
sudo nano /etc/nginx/sites-available/default
```
Paste in text file 
```
server {
	listen 80 default_server;
	listen [::]:80 default_server;

	root /home/alex/Crypto4Gas/;
  
	index index.php index.html player.html index.htm index.nginx-debian.html;

	server_name _;

	location / {
		try_files $uri $uri/ =404;
	}

	location ~ \.php$ {
		include snippets/fastcgi-php.conf;
	
		# With php-fpm (or other unix sockets):
		fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
		# With php-cgi (or other tcp sockets):
	#	fastcgi_pass 127.0.0.1:9000;
	}

	location ~ /\.ht {
		deny all;
	}
}
```
