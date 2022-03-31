# 🔙 Reverse Proxy

Running a reverse proxy in front of pupcloud is almost mandatory if you want to expose it on the internet. More than that, there are a number of reverse proxies that allow you to protect a http connection with https, using a free certificate provided for example by [Let's Encrypt](https://letsencrypt.org) or similar.

Read more here.

We'll show here how to integrate with two popular solutions, [Caddy](https://caddyserver.com) and [NGINX](https://www.nginx.com).

#### Caddy

To access pupcloud from (e.g.) `https://pupcloud.test.com`:

1. Expose ports 80 and 443 of the server to which the DNS points;
2. Run pupcloud. Leave the port as 17178;
3. Launch caddy:\
   `sudo caddy reverse-proxy --from pupcloud.test.com --to localhost:17178`

{% hint style="danger" %}
You'll need to launch caddy with root/admin privileges, as it must access privileged ports.
{% endhint %}

#### NGINX

NGINX is quite complex to configure, and it's beyond the scope of this document. Usually, we make use of [LinuxServer's Swag](https://docs.linuxserver.io/general/swag) Docker image, paired with pupcloud's own docker image. The relevant config is in `nginx/site-confs/default`:

```nginx
server {
        listen 443 ssl http2;
        server_name pupcloud.test.com;
        include /config/nginx/proxy-confs/*.subfolder.conf;
        include /config/nginx/ssl.conf;
        location / {
                proxy_pass http://localhost:17178/;
        }
}
```
