# Hospedagem compartilhada

### Atualizando python para 3.5
```sh
python_enable_3.5
```

# VPS

## Email

### Habilitando HTML inline em HORDE

Edite o arquivo `/usr/local/cpanel/base/horde/imp/config/mime_drivers.php`

```php
/* HTML driver settings */
    'html' => array(
        /* NOTE: Inline HTML display is turned OFF by default. */
        // 'inline' => false // default
        'inline' => true,
        'handles' => array(
            'text/html'
        ),
	    'icons' => array(
            'default' => 'html.png'
        ),

	    'limit_inline_size' => 1048576,

        /* Check for phishing exploits? */
        'phishing_check' => true
    )
// ...
```

## Python

### Instalando pyenv

```sh
yum -y install epel-release
yum install git gcc zlib-devel bzip2-devel readline-devel sqlite-devel openssl-devel
git clone https://github.com/pyenv/pyenv.git $HOME/.pyenv
vim $HOME/.bashrc
```

`.bashrc`
```
# ...
## pyenv configs
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"

if command -v pyenv 1>/dev/null 2>&1; then
  eval "$(pyenv init -)"
  eval "$(pyenv virtualenv init -)"
fi
```

```sh
source $HOME/.bashrc
```

## Workarounds

### /tmp
Sempre tem algum problema com o `/tmp`, permissões. Alguns programas que necessitam dele para execução:
```sh
# docker-compose
export TMP=/home/wworan/tmp && docker-compose
```