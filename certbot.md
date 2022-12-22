### [Instalando certbot](https://certbot.eff.org/instructions?ws=other&os=pip) na versão genérica python

```sh
sudo apt-get update
sudo apt-get install python3 python3-venv libaugeas0
sudo python3 -m venv /opt/certbot/
sudo /opt/certbot/bin/pip install --upgrade pip
sudo /opt/certbot/bin/pip install certbot certbot
sudo ln -s /opt/certbot/bin/certbot /usr/bin/certbot
sudo certbot certonly --webroot
```

Ao ser solicitado o diretório deve ser colocado o ponto de referência de onde são encaminhados os `acme-challenges` a depender da configuração nginx. Que no caso de sucesso se encontrava dessa maneira em `/etc/nginx/sistes-enabled/default`

```conf
server {
	listen 80 default_server;
	listen [::]:80 default_server;

        # SSL configuration
          location ~ /.well-known {
                allow all;
          root /var/www/html;
        }
	

	root /var/www/html;


	server_name _;

	location / {
		# First attempt to serve request as file, then
		# as directory, then fall back to displaying a 404.
		try_files $uri $uri/ =404;
	}	
}
```

Para garantir que seja sempre automaticamente atualizados os certificados:

```sh
echo "0 0,12 * * * root /opt/certbot/bin/python -c 'import random; import time; time.sleep(random.random() * 3600)' && sudo certbot renew -q" | sudo tee -a /etc/crontab > /dev/null
```

Mensalmente é aconselhado verificar se há novas atualizações do certbot

```sh
sudo /opt/certbot/bin/pip install --upgrade certbot
```
