# docker-compose-drone
Working drone configuration with github.com SCM - made with docker-compose.

# Prerequisites

## Create github oAuth
You need to create an OAuth application in github.com like described in the [docs.drone.io /installation / single-machine](https://docs.drone.io/installation/github/single-machine/)

## Use github oAuth
Put the created github OAuth credentials into your environment.

```yaml
- DRONE_GITHUB_CLIENT_ID={% github oauth client id %} # your client id goes here
- DRONE_GITHUB_CLIENT_SECRET={% github oauth client secret %} # your client secret goes here
```

# RPC secret
Generate a secret e.g. with openssl and use it at both services.

## drone_server
For drone/server here:
```yaml
- DRONE_RPC_SECRET={% remote call secret %} # put your self created secret here
```

## drone_agent
For drone/agent here:
```yaml
- DRONE_SECRET={% remote call secret %} # put your self created secret here
``` 

# Aim here: Simplicity

