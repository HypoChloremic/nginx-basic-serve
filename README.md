# basic nginx static serve server
## preqs
nixos
`nix-shell -p nginx`

## Running
```bash
$ bash run.sh
```

very simple. Ensure that when `nginx -c <abs path to the conf file>` you provide the entire path to the file nad not just a relative path.
That includes the paths to the static html files as well.

## Proxied server

Very easy to handle proxied server.

We can start upp an nginx proxy server by defining another server "context" i.e. server {}

```nginx
events {}
http {
	server {
		location / {
			# root /data/www;
			proxy_pass http://localhost:8080;
		}

		location /images/ {
			root /data;
		}
	}

	server {
		listen 8080;
		root /data/up1;

		location / {
		}
	}
}
```

so we see that in the second server context we start an nginx server that listens on 8080, and it will be using the dirs at /data/up1, with the location /. 

then in the main server, which is the first one being defined, we define a "proxy_pass" where we define the actual path to the proxied server. Very interesting.
