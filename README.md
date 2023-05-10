## 👋 Welcome to analytics 🚀  

analytics README  
  
  
## Requires scripts to be installed  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 systemmgr --config && systemmgr install scripts  
```

## Automatic install/update  

```shell
dockermgr update analytics
```

OR

```shell
mkdir -p "$HOME/.local/share/srv/docker/analytics/rootfs"
git clone "https://github.com/dockermgr/analytics" "$HOME/.local/share/CasjaysDev/dockermgr/analytics"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/analytics/rootfs/." "$HOME/.local/share/srv/docker/analytics/rootfs/"
```

## via command line  

```shell
docker pull casjaysdevdocker/analytics:latest && \
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-analytics \
--hostname casjaysdevdocker-analytics \
-e TZ=${TIMEZONE:-America/New_York} \
-v $HOME/.local/share/srv/docker/casjaysdevdocker-analytics/rootfs/data:/data:z \
-v $HOME/.local/share/srv/docker/casjaysdevdocker-analytics/rootfs/config:/config:z \
-p 80:80 \
casjaysdevdocker/analytics:latest
```

## via docker-compose  

```yaml
version: "2"
services:
  ProjectName:
    image: casjaysdevdocker/analytics
    container_name: ProjectName
    environment:
      - TZ=America/New_York
      - HOSTNAME=casjaysdevdocker-analytics
    volumes:
      - $HOME/.local/share/srv/docker/casjaysdevdocker-analytics/rootfs/data:/data:z
      - $HOME/.local/share/srv/docker/casjaysdevdocker-analytics/rootfs/config:/config:z
    ports:
      - 80:80
    restart: always
```

## Author  

🤖 casjay: [Github](https://github.com/casjay) 🤖  
🤖 casjaysdevdocker: [Github](https://github.com/casjaysdevdocker) [Docker](https://hub.docker.com/r/casjaysdevdocker) 🤖  
