# Proxy Server Configuration for Multiple Domains

```
server {
    listen 80;

    server_name your-domain.com;

    location / {
        proxy_pass http://localhost:{YOUR_PORT};
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```