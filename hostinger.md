## Criação de novo servidor ubuntu 24.04 para publicação dos inúmeros projetos em desenvolvimento

### Instalação do casaos

```sh
wget -qO- https://get.casaos.io | sudo bash
```

Facilita o manejo de containers e do servidor com a instalação facilitada de

- Nginx Manager Proxy
- Portainer
- Plex

### Instalação do [conda-forge](https://github.com/conda-forge/miniforge/?tab=readme-ov-file#install) e comandos importantes

```sh
wget "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
bash Miniforge3-$(uname)-$(uname -m).sh
```

Comando úteis

```sh
conda create -n env_name python=3.12
conda activate env_name
```

### Instalando [nvm](https://github.com/nvm-sh/nvm?tab=readme-ov-file#installing-and-updating) e yarn

Útil para fazer funcionar o desenvolvimento remoto no ipad etc com vscode.dev que ainda não funciona o devcontainer

```sh
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash

export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm

nvm install node
nvm use node
npm install --global yarn
```








