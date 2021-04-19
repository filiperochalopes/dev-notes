https://linuxconfig.org/how-to-configure-samba-server-share-on-ubuntu-18-04-bionic-beaver-linux

### Instalando samba
```sh
sudo apt install tasksel
sudo tasksel install samba-server
```

### Resetando configurações em arquivo limpo
```sh
# /etc/samba/smb.conf
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
sudo bash -c 'grep -v -E "^#|^;" /etc/samba/smb.conf_backup | grep . > /etc/samba/smb.conf'
```

### Adicionar usuário ao samba
```sh
sudo smbpasswd -a SEUUSUARIO
```

### Adicionar configurações de pasta pública ao arquivo `smb.conf`
```conf
[Public]
  comment = public LOPES LAN folder
  path = /media/filipelopes/0d95f444-92eb-4627-baed-8b0dfff53c5f
  browsable =yes
  create mask = 0660
  directory mask = 0771
  writable = yes
  guest ok = yes
```
