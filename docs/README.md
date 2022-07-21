# Algumas informações sobre o projeto e um controle de versão do arquivo do gns3

Eu deixei o arquivo do GNS3 nessa pasta. 

Vou fazer o seguinte para a topologia:
Roteador | Interface | Endereço IP | Prefixo 
| --- | --- | --- | ---   
| R1  | f0/0 | 192.168.1.1 | /24
|   | g1/0 | 192.168.2.1 | /24
| R2 | f0/0 | 192.168.1.2 | /24
|    | g1/0 | 192.168.4.2 | /24
|    | g2/0 | 192.168.3.1 | /24
| R3 | f0/0 | 192.168.2.3 | /24 
|    | g1/0 | 192.168.3.2 | /24 
| R4 | g1/0 | 192.168.4.3 | /24 
|    | f0/0 | 192.168.5.1  | /24 
|    | g2/0 | 192.168.8.1  | /24 
| R7 | f0/0 | 192.168.5.2 | /24 
|    | g1/0 | 192.168.6.1 | /24
| R6 | f0/0 | 192.168.6.2 | /24
|    | g1/0 | 192.168.7.1 | /24
| R5 | g1/0 | 192.168.7.2 | /24
| R8 | e0/0 | 192.168.8.2 | /24


Agora tem que carregar cada um desses IPs nos roteadores, assim:

```
config
interface FastEthernet 0/0 
ip address <endereço-ip> 255.255.255.0
no shutdown 
exit
```

```
config
interface GigabitEthernet 1/0 
ip address <endereço-ip> 255.255.255.0
no shutdown 
exit

```

comando útil: `show ip interface brief`

Até agora eu só configurei o R1.

Na verdade, eu tentei configurar o R1 com o IP certinho, mas assim que eu fechei o GNS3 a configuração não salvou. Tem que ver direito como que salva.

Colocar no AS1, R2,R3,R1

Colocar no AS2, R4,R7,R6

Depois disso, configurar items i) ii)
