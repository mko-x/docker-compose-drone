# docker-compose-drone
Working drone configuration made with docker-compose

# Info
This **work in progress** may change until next final version is released.

# Prerequisites

You need to create an OAuth application in github.com like described in the [docs.drone.io /installation / single-machine](https://docs.drone.io/installation/github/single-machine/).

# Dockerfile

Dockerfile is extended to have the path '/var/lib/drone' available and provides it as volume.

The first part ensures the path to exist:

```Dockerfile
RUN apk add --no-cache bash && \
      mkdir -p /var/lib/drone

RUN apk del bash
```
and

```Dockerfile
VOLUME [ "/var/lib/drone" ]
```

# docker-compose.yml

## Errors 'unable to open database file' and 'database ping attempts failed'
These errors typically occur if '/var/lib/drone' is not extisting/mounted in the container.

To prevent these errors in docker-compose subst the '/var/lib/drone' dir like this:

```docker-compose
volume:
  /opt/docker/drone/drone:/var/lib/drone
```

Only provide DRONE_HOST -> **NO** DRONE_SERVER_HOST, DRONE_SERVER_PORT or DRONE_SERVER_PROTO necessary.

## DEBUG vs RELEASE

If you want to strip down logs and optimize some other stuff, enable Gin's release mode via environment variable.

```docker-compose
environment:
  - GIN_MODE=release
```  
