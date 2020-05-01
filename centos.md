## fuser
Verificação e gestão de portas
```sh
# Verifica o que está na porta
fuser 8080/tcp
# Deleta o que está na porta
fuser -k 8080/tc
```

## yum
```sh
# atualiza repos disponíveis para a atualização
yum update
# atualiza pacotes disponíveis para a atualização
yum upgrade
# limpa o cache dos repos, possibilitando que o próximo update leia os repos e não o cache
yum clean all
```

## find
```sh
find /path/to/search -option1 -option2
find / -name filename.sh
```