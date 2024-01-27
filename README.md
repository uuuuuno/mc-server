# Minecraft Servers

This repository contains a docker-compose configuration for running a Minecraft server setup, including a proxy, lobby, and server1.

## Setup

Before starting the servers, make sure you have updated the `velocity secret` in the following files:

- `./mc-velocity/forwarding.secret` (just paste the secret into an empty file)
- `./mc-lobby/config/paper-global.yml:100` (secret: 'YOUR-SECRET')
- `./mc-server1/config/paper-global.yml:100` (secret: 'YOUR-SECRET')

### If you want to add more servers, follow these steps:

1. Edit `compose.yaml` to add a new container and assign it a container_name. This will be needed in step 2.

2. Edit `./mc-velocity/velocity.toml` to add a new server in the `[servers]` section. Example: `container_name = "container_name:25565"`.

Don't forget to create a folder for the new server with a `paper-global.yml` file and specify the `velocity secret` in it. Also, remember to edit the paths in `compose.yaml` for the new server.

## Getting Started

To run the servers, you will need to have `docker` installed and the `docker-compose-plugin` plugin.

To start the servers, run the following command:

```shell
docker compose up -d
```

This will start the servers in the background.

Note that the servers may take some time to start initially. You can check the logs with the following command:

```shell
docker compose logs -f
```

Once the servers are up and running, you will be able to connect to them using `IP-address:25565`.