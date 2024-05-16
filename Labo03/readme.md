# Labo03 - Run a first container

## Pedagogical intent

In this lab, you'll:

* Get to grips with the first Docker commands,
* Run your first Docker
* Familiarize yourself with port publishing

---

Note: the docker engine must be running

## Task 01 - Get to grips with the first Docker commands

* List all images present on your installation

[INPUT]
```bash
docker images
```

[OUTPUT]
```
REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
```

* Get the official Nginx image using this command

[INPUT]
```bash
docker pull nginx
```

[OUTPUT]
```
Using default tag: latest
latest: Pulling from library/nginx
09f376ebb190: Pull complete 
a11fc495bafd: Pull complete 
933cc8470577: Pull complete 
999643392fb7: Pull complete 
971bb7f4fb12: Pull complete 
45337c09cd57: Pull complete 
de3b062c0af7: Pull complete 
Digest: sha256:a484819eb60211f5299034ac80f6a681b06f89e65866ce91f356ed7c72af059c
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest

What's Next?
  1. Sign in to your Docker account → docker login
  2. View a summary of image vulnerabilities and recommendations → docker scout quickview nginx
```

Note : do you see the different layer uploaded ?

* List -again- all image present on your installation

[INPUT]
```bash
docker images
```

[OUTPUT]
```
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
nginx        latest    e784f4560448   12 days ago   188MB
```

Note : 188 MB is the size of your image... check it.

* List all Docker

[INPUT]
```
docker ps -a
```

[OUTPUT]
```
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

## Task 02 - Run the container

* Run Nginx Docker

[INPUT]
```
docker run nginx
```

[OUTPUT]
```
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2024/05/16 08:00:59 [notice] 1#1: using the "epoll" event method
2024/05/16 08:00:59 [notice] 1#1: nginx/1.25.5
2024/05/16 08:00:59 [notice] 1#1: built by gcc 12.2.0 (Debian 12.2.0-14) 
2024/05/16 08:00:59 [notice] 1#1: OS: Linux 6.5.0-35-generic
2024/05/16 08:00:59 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2024/05/16 08:00:59 [notice] 1#1: start worker processes
2024/05/16 08:00:59 [notice] 1#1: start worker process 28
2024/05/16 08:00:59 [notice] 1#1: start worker process 29
2024/05/16 08:00:59 [notice] 1#1: start worker process 30
2024/05/16 08:00:59 [notice] 1#1: start worker process 31
2024/05/16 08:00:59 [notice] 1#1: start worker process 32
2024/05/16 08:00:59 [notice] 1#1: start worker process 33
2024/05/16 08:00:59 [notice] 1#1: start worker process 34
2024/05/16 08:00:59 [notice] 1#1: start worker process 35
```

* Can you reach the default page of nginx

Note : By default, Nginx is listening on port 80

[INPUT]
```
curl localhost
```

[OUTPUT]
```
curl: (7) Failed to connect to localhost port 80 after 0 ms: Connection refused
```

* Stop this first attempt

[INPUT]
```
docker stop <id>
```

[OUTPUT]
```
571e696e8c2d
```

## Task 03 - Familiarize yourself with port publishing

* Make it possible to reach nginx with this command

[Publish a port](https://docs.docker.com/network/#published-ports)

[INPUT]
```
curl localhost:8080
```

[OUTPUT]
```
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

* Stop and delete the container

[INPUT]
```
sudo docker rm 46d10be08b24
```

[OUTPUT]
```
46d10be08b24
```

* Delete the image

[INPUT]
```
sudo docker image rm e784f4560448
```

[OUTPUT]
```
Untagged: nginx:latest
Untagged: nginx@sha256:a484819eb60211f5299034ac80f6a681b06f89e65866ce91f356ed7c72af059c
Deleted: sha256:e784f4560448b14a66f55c26e1b4dad2c2877cc73d001b7cd0b18e24a700a070
Deleted: sha256:38ecd4de01b55beb32c596678b061db27f8ecb586096f031e4553869e52a1dc2
Deleted: sha256:168e1116c229abdf6cd9c0f07f82d40d53e358b1da4e1242a15101ece28ccb28
Deleted: sha256:0b7dc712f354a2312c1f1bb6380d8e23919baf0cc09f32a5a4595afb6c3a440b
Deleted: sha256:3ecb32a94af1f9a46cc259bf6cc677acd1fef2023f746e973862d1a8c9e31fe3
Deleted: sha256:b4c8fa0ae3e9f4f7d0ee49a9ac13d8aebd6f2d4a53e204e75f74e4bcb143132f
Deleted: sha256:cd5b03306052e1a435b98a34cd2579dc48f8f0ca280a147f19f066ddb6a0b81d
Deleted: sha256:5d4427064ecc46e3c2add169e9b5eafc7ed2be7861081ec925938ab628ac0e25
```
