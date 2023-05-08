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
