# Boilerplate settings
            #user www-data;
            #user  nobody;

            worker_processes  4;

            #error_log  logs/error.log;
            #error_log  logs/error.log  notice;
            #error_log  logs/error.log  info;

            #pid        logs/nginx.pid;


            events {
                worker_connections  1024;
            }


            http {
                include       mime.types;
                default_type  application/octet-stream;

                proxy_cache_path /var/lib/nginx/cache levels=1:2 keys_zone=backcache:8m max_size=50m;
                proxy_temp_path   /var/lib/nginx/tmp;
                proxy_cache_key "$scheme$request_method$host$request_uri$is_args$args";
                proxy_cache_valid 200 302 10m;
                proxy_cache_valid 404 1m;

                keepalive_timeout  65;

                gzip  on;
                gzip_types application/json text/css text/javascript;
                gzip_proxied any;
                gzip_vary on;


                server {
                listen       80;
                server_name  dkun.ru;

                    location / {
                        proxy_pass http://dkunin.github.io;
                    }
                }

                server {

                    listen 9090;
                    location / {
                        root /home/deploy/app;
                    }
                }

            }