# Reverse proxy configuration for Nginx

```
server {
        listen       8080;
        server_name  localhost;
        
        gzip on;
	gzip_types      text/css text/plain text/xml application/xml application/javascript application/x-javascript text/javascript application/json text/x-json;
	gzip_proxied    no-store no-cache private expired auth;
	gzip_disable     "MSIE [1-6]\.";
		
	location /api {
		proxy_pass          http://127.0.0.1:8081;
		proxy_http_version  1.1;
		gzip_static on;
	}

        location / {
                proxy_pass          http://127.0.0.1:8082;
                proxy_http_version  1.1;
                gzip_static on;
        }
}
```
