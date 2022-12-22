### Deixando imagens e containers em outra pasta
https://medium.com/clusterfk/use-a-different-volume-for-your-docker-images-in-ubuntu-4c0315be6d66  

```sh
sudo systemctl stop docker
sudo mv /var/lib/docker /var/lib/docker-backup
sudo mkdir /var/lib/docker
sudo mount /dev/sda2 /var/lib/docker
sudo cp -a /var/lib/docker-backup/. /var/lib/docker
sudo systemctl start docker
```

### [Instalando Docker](https://docs.docker.com/engine/install/debian/) no Debian 11 com plugin Docker Compose

```sh
sudo apt-get remove docker docker-engine docker.io containerd runc
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

Lembrando que o docker compose plugin funciona sem o hífen. `docker compose`. Um `alias` pode ser adicionado em ~/.bashrc
