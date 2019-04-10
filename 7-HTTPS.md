## 通过配置HTTPS加密证书

安装certbot之后，它可以帮我们生成加密证书，然后通过nginx配置。

```bash
$ sudo certbot --nginx
$ $ sudo certbot --nginx certonly
```



```
server {
  listen 80;
  server_name mb.bitfish.xyz;
  location / {
    # as a static file
    root /var/www/MessageBoardVue;
    index index.html ;
 }

    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/mb.bitfish.xyz/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/mb.bitfish.xyz/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot

}
```

