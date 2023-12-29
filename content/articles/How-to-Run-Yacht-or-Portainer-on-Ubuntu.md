---
title: "How to Run Yacht or Portainer on Ubuntu"
date: 2023-08-31
url: /How-to-Run-Yacht-or-Portainer-on-Ubuntu/
description:
categories: [Software]
draft: false
---
## Requirment needed to run Yacht or Portainer (Ubuntu)

All we need to run yacht or Portainer to manage our docker container is docker itself. According to docker official documnetation we need to do the following.

First command

```
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
```
This will allow apt install over HTTPS.

Second command

```
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```
This will add docker GPG keyrings for safety purpose.

Third command

```
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
This will add the docker repository to apt.

Fourth command
```
sudo apt-get update
```
This will update the repository and index the docker repository.

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
Fifth command
```
sudo systemctl enable docker
```
This will auto start docker on reboot.

## Install Yacht

To install Yacht run this command

```
sudo docker volume create yacht
sudo docker run -d -p 8000:8000 -v /var/run/docker.sock:/var/run/docker.sock -v yacht:/config --name yacht selfhostedpro/yacht
```

The following command starts a yacht container and configures it to always restart unless it is explicitly stopped or Docker is restarted.


```
sudo docker run -d --restart unless-stopped yacht
```

```
sudo docker update --restart unless-stopped yacht
```
Now that the installation is complete, you can log into your Yacht Server instance by opening a web browser and going to:

```
https://Local_PC_IP_Address:8000
```



## Install Portainer


To install Portainer run these commands after docker is installed.

```
sudo docker volume create portainer_data
```

```
sudo docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
```

This will install Portainer and make it restart always after boot.

Now that the installation is complete, you can log into your Portainer Server instance by opening a web browser and going to:

```
https://localhost:9443
```

For more documnetation see [Portainer](https://docs.portainer.io/start/install-ce/server/docker/linux) & [Yacht](https://yacht.sh/docs/Installation/Install/)