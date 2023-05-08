# Coletar_quantidade_de_clientes_ipv6_mikrotik

Para o template acima funcionar vamos criar o script e dar as devidas permissões.

Entre na pasta /usr/lib/zabbix/externalscripts/ 

Crie o arquivo coletar_ipv6

    #!/bin/bash

    ip=seu_ip
    usuario=crie_um_user_no_seu_mikrotik
    senha=crie_uma_senha_para_o_user_no_seu_mikrotik
    porta=22

    sshpass -p$senha ssh -o "StrictHostKeyChecking=no" -p$porta $usuario@$ip "ipv6 dhcp-server binding print terse" | wc -l
De permissão para o seu zabbix

    chown zabbix. /usr/lib/zabbix/externalscripts/coletar_ipv6
    chmod a+x /usr/lib/zabbix/externalscripts/coletar_ipv6
Agora no terminal execute o script e veja se retorna algo.

    ./coletar_ipv6
![image](https://user-images.githubusercontent.com/94009104/236940404-9ed894d7-4fbf-4288-b625-7ea750d77668.png)

Importe o template 
