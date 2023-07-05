## 👋 Welcome to analytics 🚀  

 Container installer script for analytics  
  
  
## Install my system scripts  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 sudo systemmgr --config && sudo systemmgr install scripts  
```
  
## Automatic install/update  
  
```shell
dockermgr update analytics
```
  
## Install and run container
  
```shell
mkdir -p "$HOME/.local/share/srv/docker/analytics/rootfs"
git clone "https://github.com/dockermgr/analytics" "$HOME/.local/share/CasjaysDev/dockermgr/analytics"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/analytics/rootfs/." "$HOME/.local/share/srv/docker/analytics/rootfs/"
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-analytics \
--hostname analytics \
-e TZ=${TIMEZONE:-America/New_York} \
-v $HOME/.local/share/srv/docker/casjaysdevdocker-analytics/rootfs/data:/data:z \
-v $HOME/.local/share/srv/docker/casjaysdevdocker-analytics/rootfs/config:/config:z \
-p 0.0.0.0:8000:8000 \
casjaysdevdocker/analytics:latest
```
  
## via docker-compose  
  
```yaml
version: "2"
services:
  ProjectName:
    image: casjaysdevdocker/analytics
    container_name: casjaysdevdocker-analytics
    environment:
      - TZ=America/New_York
      - HOSTNAME=analytics
    volumes:
      - $HOME/.local/share/srv/docker/casjaysdevdocker-analytics/rootfs/data:/data:z
      - $HOME/.local/share/srv/docker/casjaysdevdocker-analytics/rootfs/config:/config:z
    ports:
      - 0.0.0.0:8000:8000
    restart: always
```
  
## Get source files  
  
```shell
dockermgr download src casjaysdevdocker/analytics
```
  
OR
  
```shell
git clone "https://github.com/casjaysdevdocker/analytics" "$HOME/Projects/github/casjaysdevdocker/analytics"
```
  
## Build container  
  
```shell
cd "$HOME/Projects/github/casjaysdevdocker/analytics"
buildx 
```
  
## Authors  
  
🤖 casjay: [Github](https://github.com/casjay) 🤖  
⛵ casjaysdevdocker: [Github](https://github.com/casjaysdevdocker) [Docker](https://hub.docker.com/u/casjaysdevdocker) ⛵  
