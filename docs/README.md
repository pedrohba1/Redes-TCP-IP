# Trabalho Redes II

## Topologia
![topologia](./topologia.png)

Essa é a imagem de como ficará a topologia do trabalho. Cada interface terá seu ip, que estará de acordo com a seguinte tabela:


| Hostname | Interface | CIDR           | Máscara         | iOS      |
| -------- | --------- | -------------- | --------------- | -------- |
| R1       | f0/0      | 192.168.1.1/30 | 255.255.255.252 | Cisco    |
|          | g1/0      | 192.168.2.1/30 | 255.255.255.252 | Cisco    |
| R2       | f0/0      | 192.168.1.2/30 | 255.255.255.252 | Cisco    |
|          | g1/0      | 192.168.4.1/30 | 255.255.255.252 | Cisco    |
|          | g2/0      | 192.168.3.1/30 | 255.255.255.252 | Cisco    |
| R3       | f0/0      | 192.168.2.2/30 | 255.255.255.252 | Cisco    |
|          | g1/0      | 192.168.3.2/30 | 255.255.255.252 | Cisco    |
|          | g2/0      | gerado por dhcp| 255.255.255.252 | Cisco    |
| R4       | f0/0      | 192.168.4.2/30 | 255.255.255.252 | Cisco    |
|          | g1/0      | 192.168.5.1/30 | 255.255.255.252 | Cisco    |
| R5       | g1/0      | 192.168.5.2/30 | 255.255.255.252 | Cisco    |
|          | f0/0      | 192.168.6.1/30 | 255.255.255.252 | Cisco    |
| R6       | f0/0      | 192.168.6.2/30 | 255.255.255.252 | Cisco    |
|          | g1/0      | 192.168.7.1/30 | 255.255.255.252 | Cisco    |
| R7       | g1/0      | 192.168.7.2/30 | 255.255.255.252 | Cisco    |
| R8       | e0/0      | 192.168.8.1/30 | 255.255.255.252 | Mikrotik |


## Configuração
Estes são os comandos para configurar os roteadores com seus respectivos ips.
```
> R1
# configure terminal
# interface fastEthernet 0/0
# ip address 192.168.1.1 255.255.255.252
# no shutdown
# exit
# interface gigabitEthernet 1/0
# ip address 192.168.2.1 255.255.255.252
# no shutdown
# exit
# exit
# wr

> R2
# configure terminal
# interface fastEthernet 0/0
# ip address 192.168.1.2 255.255.255.252
# no shutdown
# exit
# interface gigabitEthernet 1/0
# ip address 192.168.4.1 255.255.255.252
# no shutdown
# exit
# interface gigabitEthernet 2/0
# ip address 192.168.3.1 255.255.255.252
# no shutdown
# exit
# exit
# wr

> R3
# configure terminal
# interface fastEthernet 0/0
# ip address 192.168.2.2 255.255.255.252
# no shutdown
# exit
# interface gigabitEthernet 1/0
# ip address 192.168.3.2 255.255.255.252
# no shutdown
# exit
# exit
# wr

> R4
# configure terminal
# interface fastEthernet 0/0
# ip address 192.168.4.2 255.255.255.252
# no shutdown
# exit
# interface gigabitEthernet 1/0
# ip address 192.168.5.1 255.255.255.252
# no shutdown
# exit
# exit
# wr

> R5
# configure terminal
# interface gigabitEthernet 1/0 
# ip address 192.168.5.1 255.255.255.252
# no shutdown
# exit
# interface fastEthernet 0/0
# ip address 192.168.6.1 255.255.255.252
# no shutdown
# exit
# exit
# wr

> R6
# configure terminal
# interface fastEthernet 0/0 
# ip address 192.168.6.2 255.255.255.252
# no shutdown
# exit
# interface gigabitEthernet 1/0
# ip address 192.168.7.1 255.255.255.252
# no shutdown
# exit
# exit
# wr

> R7
# configure terminal
# interface gigabitEthernet 1/0
# ip address 192.168.7.2 255.255.255.252
# no shutdown
# exit

```

## Próximos passos
1. Implementar protocolos de roteamento
2. Implementar DHCP ou NAT


## Implementação do RIP


```
R1(config)#router rip
R1(config-router)#network 192.168.1.0
R1(config-router)#network 192.168.2.0
```



```
R2(config)#router rip
R2(config-router)#network 192.168.1.0
R2(config-router)#network 192.168.2.0
R2(config-router)#network 192.168.3.0
```



```
R3(config)#router rip
R3(config-router)#network 192.168.2.0
R3(config-router)#network 192.168.3.0
```

```
R4(config)#router rip
R4(config-router)#network 192.168.4.0
```



## Implementação do NAT

Implementamos o NAT no R3:

```
R3# config
R3(config)#int g2/0
R3(config-if)# ip address dhcp   
R3(config-if)#no shut
```

## Implementação do DNS

```
R3# config
R3(config)# ip name-server 8.8.8.8
R3(config)# ip domain-lookup
```
