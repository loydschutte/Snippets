# Virtual Host Configuration with Subdomain

```
server {
	listen 80;
	listen [::]:80;

	server_name subdomain.demoserver.com;

	root /var/www/demoserver.com;
	index index.php index.html;

	location / {
		try_files $uri $uri/ =404;
	}
}
```