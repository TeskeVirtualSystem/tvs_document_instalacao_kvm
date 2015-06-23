## Configurando a Ponte de Rede

Para configurar a ponte de rede, teremos que editar o arquivo
`/etc/network/interfaces` para adicionar a configuração da ponte
de rede. A partir daqui as referências para **eth0* deverão ser trocadas
para a interface que você detectou com os passos anteriores.

Para iniciar a configuração da ponte editaremos dessa maneira:

    sudo nano /etc/network/interfaces
    
O conteúdo do arquivo deve estar assim:

```
auto lo
iface lo inet loopback
```

Para configurarmos a ponte, devemos setar a nossa interface **eth0** 
para **manual** adicionando as seguintes linhas

```
auto eth0
iface eth0 inet manual
```

Agora iremos configurar nossa ponte de rede como dispotivio virtual **br0**.
Para isso iremos adicionar as seguintes linhas:

```
auto br0
iface br0 inet static
        address IP_DA_MAQUINA
        netmask MASCARA
        gateway GATEWAY
        broadcast BROADCAST (exemplo: 10.10.5.255 para rede 10.10.5.0)
        dns-nameservers DNS (repetir essa linha para todos servidores DNS)
        search DOMINIO (por exemplo teske.local)
        bridge_ports eth0
```

ou caso queira que a ponte fique em **DHCP** você pode fazer:

```
auto br0
iface br0 inet dhcp
```

No final seu arquivo deve ficar algo próximo disso:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 10.10.5.2
        netmask 255.255.255.0
        gateway 10.10.5.5
        broadcast 10.10.5.255
        bridge_ports eth0
```

Agora aperte `Ctrl + X` para salvar e sair. Confirme o salvar apertando **S** 
e depois **ENTER** para manter o nome do arquivo. Feito isso, reinicie o 
computador para que a ponte esteja ativa.