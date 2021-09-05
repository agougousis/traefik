This is an example setup of Traefik v2 for 2 applications. 
One served through HTTP and one served through HTTPS (using self-signed certificates).

The first app will be available through HTTP (port 80) at:  http://api.mydomain.gr/

The second app will be available through HTTPS (port 443) at: https://www.mydomain.gr/  If you try to visit it through HTTP, you will get redirected.

### Preparation

##### DNS

The DNS records we need to add to hosts file for our fake domain names (one for each app) are:

```
127.0.0.1	   api.mydomain.gr
127.0.0.1	   www.mydomain.gr
```

#### Applications

Suppose that the path to this directory is  D:\myapps\traefik-sample. Create 2 more directories:
```
D:\myapps\public_app
D:\myapps\api_app
```
and put inside an index.html and a, index.php  file , for testing purposes. These 2 directories represent
the directories where our 2 web applications are stored.

## Running

Start the containers

`$ docker-compose up -d`

If you have made changes to some configuration files (e.g Default ), make sure you rebuild the docker 
images:

`$ docker-compose up -d --build`

How to connect to traefik container:

`docker-compose exec reverse-proxy /bin/sh`

Traefik dashboard will be accessible at:  http://localhost:8080/dashboard/#/

![dashboard](https://user-images.githubusercontent.com/5471589/132132429-a24dedc5-4954-4858-8227-53fc36c70e35.png)

Traefik API endpoints will also be available e.g:  http://localhost:8080/api/version

![api](https://user-images.githubusercontent.com/5471589/132132434-e1a2f231-7eb3-45b3-99bc-3c64e87a60d5.png)

