# HOME ASSISTANT
## I. Use with docker
### - Install docker
* Get root access
```
sudo -i
```
* Install packages
```
apt-get install \
  apt-transport-https \
  ca-certificates \
  curl \
  gnupg-agent \
  software-properties-common
```
* Add the Docker’s official GPG key
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
* Add repository
```
add-apt-repository \
 "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
 $(lsb_release -cs) \
 stable"
```
* Install docker
```
apt-get install docker-ce docker-ce-cli containerd.io
```

* Check docker version
```
docker --version
```
* enable docker
```
systemctl enable docker
```

### - Install Home Assistant Supervised
* Install required packages
```
apt-get install \
  apparmor-utils \
  avahi-daemon \
  dbus \
  jq \
  network-manager \
  socat
```
* Install hass.io
```
curl -sL "https://raw.githubusercontent.com/home-assistant/supervised-installer/master/installer.sh" | bash -s
```
##### home assistant ready now at [localhost:8123](localhost:8123)

### - Install portainer (docker container management)
* Create a new Docker volume for Portainer
```
docker volume create portainer_data
```
* Run Portainer
```
docker run -d -p 9000:9000 \
--name portainer \
--restart always \
-v /var/run/docker.sock:/var/run/docker.sock \
-v portainer_data:/data portainer/portainer
```
##### Portainer ready now at [localhost:9000](localhost:9000)
