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
