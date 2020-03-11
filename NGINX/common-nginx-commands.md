# Common NGINX Commands

Test configuration file

```
sudo nginx -t
```

Start server (on *nix)

```
sudo systemctl start nginx
```

Stop server (on *nix)

```
sudo systemctl stop nginx
```

Restart server (on *nix)

```
sudo systemctl restart nginx
```

Create symlink from Sites Enabled to Sites Available (on *nix)

```
sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/default
```