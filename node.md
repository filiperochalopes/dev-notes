# Node

## Instalando node 13 no CentOS
https://computingforgeeks.com/how-to-install-latest-nodejs-on-centos-fedora/
```sh
curl -sL https://rpm.nodesource.com/setup_13.x | sudo bash -
sudo yum -y install gcc-c++ make nodejs
node -v
# v13.1.0
# Instalar yarn depois
```

## Instalando versão mais recente
```sh
yum install -y gcc-c++ make
curl -sL https://rpm.nodesource.com/setup_14.x | sudo -E bash -
# yum install nodejs
curl -sL https://dl.yarnpkg.com/rpm/yarn.repo | sudo tee /etc/yum.repos.d/yarn.repo
yum install yarn
```