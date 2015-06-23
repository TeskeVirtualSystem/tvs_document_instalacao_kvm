### Pelo terminal (`DHCP` da rede)


Este é um dos jeitos mais fácil de se identificar qual dispositivo de rede está
conectado quando há um servidor DHCP na rede. Para isso basta executar o comando
`ifconfig` no terminal:

```
root@root-server:~# ifconfig 
eth0      Link encap:Ethernet  Endereço de HW 00:1e:67:c9:f0:78  
          endereço inet6: fe80::21e:67ff:fec9:f078/64 Escopo:Link
          inet end.: 10.10.5.2  Bcast:10.10.5.255  Masc:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:644782895 erros:0 descartados:28553 excesso:0 quadro:0
          Pacotes TX:1099743780 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:244864812937 (244.8 GB) TX bytes:1369989638569 (1.3 TB)
          Memória:c1200000-c1280000 

eth1      Link encap:Ethernet  Endereço de HW 00:1e:67:c9:f0:79  
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
          Memória:c1100000-c1180000 
```

Neste caso a rede está conectada no dispositivo **eth0**.