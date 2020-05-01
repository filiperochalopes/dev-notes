# Dovecot
Serviço de email
### Atualizando ou transferindo caixa de email
```sh
# Entra na pasta ~/mail/dominio.com.br
cd ~/mail/dominio.com.br
# compacta o zip
tar -cf nome_do_arquivo.tar.gz  pastas1 pasta2 pasta3 caixa_de_entrada_4
# descompacta todas as pastas, fazendo automaticamente um mix dos arquivos, atualizando,mas não excluindo
tar -xf nome_do_arquivo.tar.gz
```