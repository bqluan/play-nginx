Nginx load balance
==================

### nginx rate limiting ###
See [here](https://www.nginx.com/blog/rate-limiting-nginx/).
```
http {
	limit_req_zone $binary_remote_addr zone=backendlimit:10m rate=100r/s;
	server {
		location / {
			limit_req zone=backendlimit burst=200 nodelay;
		}
	}
}
```

### nginx ip whitelist ###
See [here](https://unix.stackexchange.com/questions/365946/the-best-way-to-create-an-ip-whitelist-with-nginx) and [there](http://nginx.org/en/docs/http/ngx_http_access_module.html).
```
location / {
	allow 192.168.1.21;
	deny all;
}
```

### Benchmark ###
```
ab -k -c 10 -n 10 http://172.16.18.1/becky
```
