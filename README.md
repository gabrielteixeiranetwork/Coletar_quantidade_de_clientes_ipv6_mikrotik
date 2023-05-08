# Coletar_quantidade_de_clientes_ipv6_mikrotik

Para o template acima funcionar vamos criar o script e dar as devidas permissões.

Entre na pasta /usr/lib/zabbix/externalscripts/ 

Crie o arquivo coletar_ipv6

    #!/bin/bash

    ip=ip_do_seu_mikrotik
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

https://github.com/gabrielteixeiranetwork/Coletar_quantidade_de_clientes_ipv6_mikrotik/blob/main/Mikrotik_ipv6.xml

Vamos editar algumas informações

![image](https://user-images.githubusercontent.com/94009104/236944261-f3927489-e035-49d8-963d-f3802292fbf7.png)

Adicione o template no seu host

Note que ele não irá coletar os dados ainda, portanto vamos corrigir isso!!!

Crie o diretório 

    mkdir -p /var/lib/zabbix/.ssh
Vá até o diretório

    cd /var/lib/zabbix/.ssh
Acesse o seu Mikrotik

    ssh usuário@ip
Vai te pedir a senha, logo em seguida feche o mesmo.

Vamos ajustar a permissão

    chown -R zabbix:zabbix /var/lib/zabbix/
Agora saia do diretório e vá até o seu zabbix

![image](https://user-images.githubusercontent.com/94009104/236945763-cd8da07a-af19-4629-be21-949253a77f46.png)

Só ativar ipv6 nos seus clientes e observar :)
