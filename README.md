# Coletar_quantidade_de_clientes_ipv6_mikrotik

Para o template acima funcionar vamos criar o script e dar as devidas permissões.

Entre na pasta /usr/lib/zabbix/externalscripts/ crie o arquivo coletar_ipv6

    #!/bin/bash

    ip=10.200.253.1
    usuario=zabbix
    senha=zabbixsmarttelecom1@
    porta=22

    sshpass -p$senha ssh -o "StrictHostKeyChecking=no" -p$porta $usuario@$ip "ipv6 dhcp-server binding print terse" | wc -l
