### Pelo terminal ( Apenas com cabo conectado na interface )

Há a possibilidade de achar qual interface de rede será usada para a ponta apenas
conectando um cabo de rede e o ligando em um `switch`. Para isso, conecte o cabo 
**apenas** na interface que deseja conectar a rede.

Verifique quais interfaces estão disponíveis usando o comando `ifconfig`:

```
root@root-server:~# ifconfig 
eth0      Link encap:Ethernet  Endereço de HW 00:1e:67:c9:f0:78  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:644785381 erros:0 descartados:28556 excesso:0 quadro:0
          Pacotes TX:1099745240 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:244865273853 (244.8 GB) TX bytes:1369989892199 (1.3 TB)
          Memória:c1200000-c1280000 

eth1      Link encap:Ethernet  Endereço de HW 00:1e:67:c9:f0:79  
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
          Memória:c1100000-c1180000 

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:65536  Métrica:1
          pacotes RX:23440 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:23440 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:4250006 (4.2 MB) TX bytes:4250006 (4.2 MB)
```

Neste caso temos **eth0**, **eth1**, **lo**. A interface **lo** é a `localhost` 
e não será **nunca** para a ponte de rede. Agora precisamos verificar se o cabo
está conectado na **eth0** ou **eth1**. Para isso podemos usar a ferramenta
`ethtool` para ver se o cabo está conectado:

```
root@root-server:~# ethtool eth0
Settings for eth0:
     Supported ports: [ TP ]
     Supported link modes:   10baseT/Half 10baseT/Full 
                             100baseT/Half 100baseT/Full 
                             1000baseT/Full 
     Supported pause frame use: Symmetric
     Supports auto-negotiation: Yes
     Advertised link modes:  10baseT/Half 10baseT/Full 
                             100baseT/Half 100baseT/Full 
                             1000baseT/Full 
     Advertised pause frame use: Symmetric
     Advertised auto-negotiation: Yes
     Speed: 1000Mb/s
     Duplex: Full
     Port: Twisted Pair
     PHYAD: 1
     Transceiver: internal
     Auto-negotiation: on
     MDI-X: on (auto)
     Supports Wake-on: pumbg
     Wake-on: g
     Current message level: 0x00000007 (7)
                      drv probe link
     Link detected: yes

root@root-server:~# ethtool eth1
Settings for eth1:
     Supported ports: [ TP ]
     Supported link modes:   10baseT/Half 10baseT/Full 
                             100baseT/Half 100baseT/Full 
                             1000baseT/Full 
     Supported pause frame use: Symmetric
     Supports auto-negotiation: Yes
     Advertised link modes:  10baseT/Half 10baseT/Full 
                             100baseT/Half 100baseT/Full 
                             1000baseT/Full 
     Advertised pause frame use: Symmetric
     Advertised auto-negotiation: Yes
     Speed: Unknown!
     Duplex: Unknown! (255)
     Port: Twisted Pair
     PHYAD: 1
     Transceiver: internal
     Auto-negotiation: on
     MDI-X: off (auto)
     Supports Wake-on: pumbg
     Wake-on: g
     Current message level: 0x00000007 (7)
                      drv probe link
     Link detected: no
```

Como podemos ver na linha `Link detected` apenas o **eth0** está conectado a rede. 
Esta é nossa interface.