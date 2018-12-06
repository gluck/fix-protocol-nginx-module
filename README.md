Name
=================
fix-protocol-nginx-module - [Nginx](https://www.nginx.com/) stream module for load balancing [FIX](https://www.fixtrading.org/) sessions

*This module is not distributed with the Nginx source.* See [the installation instructions](#installation).

Table of Contents
=================

* [Name](#name)
* [Objective](#objective)
* [Installation](#installation)
* [Links](#links)

Objective
========

Goal of this project is to support TLS termination of FIX sessions and load balance them over multiple endpoints based on message (logon) content (on top of existing load balancing options)

Installation
============

This module can be manually compiled into Nginx:

1. Download the latest version of ngx_stream_fixprotocol [HERE](https://github.com/gluck/fix-protocol-nginx-module/tags).
1. Download the latest version of NGINX [HERE](http://nginx.org/)

Build the source of NGINX with this module, like below:

```bash
wget 'http://nginx.org/download/nginx-1.13.6.tar.gz'
tar -xzvf nginx-1.13.6.tar.gz
cd nginx-1.13.6/

# Here we assume Nginx is to be installed under /opt/nginx/.
./configure --prefix=/opt/nginx \
        --with-stream \
        --with-stream_ssl_module \
        --add-module=/path/to/fix-protocol-nginx-module

# Build and install
make -j4
make install
```

You may use `--without-http` if you do not wish to use this module with the HTTP subsystem.
ngx_stream_fixprotocol will work perfectly fine without the presense of the HTTP subsystem.

[Back to TOC](#table-of-contents)

Links
=====

https://docs.nginx.com/nginx/admin-guide/load-balancer/tcp-udp-load-balancer/
https://nginx.org/en/docs/stream/ngx_stream_proxy_module.html
https://github.com/openresty/stream-lua-nginx-module

[Back to TOC](#table-of-contents)
