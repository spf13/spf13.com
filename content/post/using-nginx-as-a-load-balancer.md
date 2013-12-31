{
	"disqus_url" : "http://spf13.com/post/using-nginx-as-a-load-balancer/",
	"disqus_identifier" : "262 http://localhost/~sfrancia/wordpress/?p=262",
	"disqus_title" : "Using Nginx as a Load Balancer",
	"Title": "Using Nginx as a Load Balancer",
	"Description": "",
	"Keywords": [
		"nginx"
	],
	"Tags": [
		"nginx"
	],
	"Pubdate": "2009-09-24",
	"Topics": [
		"Systems"
	],
	"Url": "post/using-nginx-as-a-load-balancer",
	"Slug": "using-nginx-as-a-load-balancer",
	"Section": "post",
	"Thumbnail": ""
}

Nginx is a relatively new web server that has a light footprint
and relatively easy configuration. The following configuration
demonstrates how to properly use nginx as a load balancer in 
front of two web servers.

    pid /var/run/nginx.pid;

    events {
        worker_connections 1024;
    }

    http {
        include mime.types;

        default_type application/octet-stream;
        sendfile on;
        keepalive_timeout 75;
        proxy_buffering off;
        log_not_found off;
        error_log /dev/null;
        access_log off;
        proxy_connect_timeout 20;
        client_header_timeout 60;
        client_body_timeout 60;
        send_timeout 60;

        server {
            listen 127.0.0.1:80;
            location /nginx_status {
                stub_status on;
                access_log off;
                allow 127.0.0.1;
                deny all;
            }
        }

        server {
            listen in:80;
            server_name dev.portero.com;

            location ~ ^/(skin|media)/ {
            root /mnt/fs/vhosts/dev.portero.com/public_html;
            expires 30d;
            }

            location / {
            proxy_pass http://portero;
            }
        }

        upstream portero {
            server out1;
            server out2;
        }
    }

## Related articles

-   [Handling web servers of high traffic
    sites](http://www.slideshare.net/ashfame/handling-web-servers-of-high-traffic-sites)
    (slideshare.net)

