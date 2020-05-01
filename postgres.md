# Postgres

## CentOS 7

### Instalando
https://computingforgeeks.com/-to-install-postgresql-12-on-centos-7/  
```sh
sudo yum -y install https://download.postgresql.org/pub/repos/yum/reporpms/EL-7-x86_64/pgdg-redhat-repo-latest.noarch.rpm
sudo yum -y install epel-release yum-utils
sudo yum-config-manager --enable pgdg12
sudo yum install postgresql12-server postgresql12
# Inicializando servico de banco de dados
sudo /usr/pgsql-12/bin/postgresql-12-setup initdb
# deve encontrar agora o arquivo de configuração em /var/lib/pgsql/12/data/postgresql.conf
sudo systemctl enable --now postgresql-12
systemctl status postgresql-12
```

### Permitindo acesso remoto
`/var/lib/pgsql/12/data/postgresql.conf`
```conf
; listen_addresses = '192.168.10.10'
listen_addresses = '*'
```

`/var/lib/pgsql/12/data/pg_hba.conf`
```conf
; Adicionar
host all all <my-ip>/32 md5
; ou 0.0.0.0/0 para todos
```
**LEMBRAR DE HABILITAR O FIREWALL**
```sh
sudo systemctl restart postgresql-12
```

### Alterando senha padrão
```sh
# Conectando com o usuário correto
su - postgres
psql
```
```sql
ALTER USER postgres with password 'very_secure_password';
```
```sh
# sudo service postgresql-12 start
sudo service postgresql start
```

### Restaurando um banco de dados a partir de um arquivo plain sql
```sh
# Conectando com usuário postgres
su - postgres
# Só tem acesso a /var/lib/pgsql/
# dentro tem uma pasta 12/backups, onde deve estar o arquivo de backup *.sql
# Usando o sql para restaurar o recém criado banco new_db
psql -d new_db -f restore_file.sql
```