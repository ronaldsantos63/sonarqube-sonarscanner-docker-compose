# Using the Docker images in production

The following requirements and recommendations apply when running Elasticsearch in Docker in production.

## Set `vm.max_map_count` to at least `262144`

The `vm.max_map_count` kernel setting must be set to at least `262144` for production use.

How you set `vm.max_map_count` depends on your platform.

## Linux

To view the current value for the `vm.max_map_count` setting, run:

```
grep vm.max_map_count /etc/sysctl.conf
vm.max_map_count=262144
```
To apply the setting on a live system, run:

```
sysctl -w vm.max_map_count=262144
```
To permanently change the value for the `vm.max_map_count` setting, update the value in `/etc/sysctl.conf`.

## macOS with [Docker for Mac](https://docs.docker.com/docker-for-mac)

The `vm.max_map_count` setting must be set within the xhyve virtual machine:

From the command line, run:
```
screen ~/Library/Containers/com.docker.docker/Data/vms/0/tty
```

Press enter and use sysctl to configure vm.max_map_count:

```
sysctl -w vm.max_map_count=262144
```

To exit the `screen` session, type `Ctrl a d`.

## Windows and macOS with [Docker Desktop](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html#_windows_and_macos_with_docker_desktop)

The `vm.max_map_count` setting must be set via docker-machine:
```
docker-machine ssh
sudo sysctl -w vm.max_map_count=262144
```

## Windows with Docker Desktop WSL 2 backend
The vm.max_map_count setting must be set in the docker-desktop container:

wsl -d docker-desktop
sysctl -w vm.max_map_count=262144


# Login

login on: http://localhost:9000<br>
user: admin<br>
pass: admin<br>
