# lista 1


### 1) Definição de protoclo do livro:

A protocol defines the format and the order of messages exchanged between
two or more communicating entities, as well as the actions taken on the transmission and/or receipt of a message or other event.

Protoclos são importantes porque eles definem a consistência e universalidade para receber e enviar mensagens e assim os sistemas podem ter interoperabilidade. 


### 2) A seis tecnologias de acesso:


Corporativo: 
1. Dial-up modem por linha telefone; 
2. DSL por linha de telefone;
3. Cable to HFC; 
4. 100 Mbps switched Ethernet; 
5. Wifi (802.11): home and enterprise;

Residencial:
1. DSL por linha de telefone;
2. Cable to HFC;
3. 100 Mbps switched Ethernet; 
4. Wifi (802.11): home and enterprise;


Móvel:
2. 3G and 4G: wide-area wireless.


### 3)
LANs de Ethernet possuem taxa de transmissão de 10 Mbps, 100Mbp,s 1 Gbps e 10Gps.
Ethernet hoje em dia funciona geralmente por meio de pares trançado de cobre mas pode também funcionar por cabos de fibra ótica.


### 4)
No tempo t0 o hospedeiro de envio faz a transmissão em tempo L/R1. No tempo t1 = t0 + L/R1, o hospedeiro conclui a transmissão. 
Como o roteador usa comutação de pacotes baseado em armazenamento e encaminhamento, ele precisa do pacote completo para fazer o envio. Logo, o tempo t2 = t1 + L/R2 é o tempo necessário para fazer o envio do pacote completo ao host receptor. Então, o atraso fim-a-fim é de L/R1 + L/R2


### 5)

Os possíveis atrasos são: transmissão,
propagaçã e fila. Todos esses são fixos exceto o de fila. O de fila é variável.


### 6 a)
500kbps, porque o gargalo é no enalce mais lento.

### 6 b)

4 milhões de bytes = (4* 10 **6) * 8 bits = 32.000.000 de bits
500kbps = 500 * 10**3 bits = 500.000 bits
32.000.000 b / 500.000 bps = 64 segundos 

### 6 c)
100kbps; 
4 milhões de bytes = (4* 10 **6) * 8 bits = 32.000.000 de bits
100kbps = 100 * 10**3 bits = 100.000 bits
32.000.000 b / 100.000 bps = 320 segundos 


### 7)
RFC 2418 e RFC 1608 referem-se a working group guidelines.


### 8)
https://datatracker.ietf.org/doc/html/rfc791



### 9)

O host A quebra o pacote em chunks e adiciona um header em cada chunk. Existem então múltiplos pacotes para o arquivo. O header de cada pacote inclui o endereço IP do destino
(o sistema final B). O packet switch usa o IP de destino nos headers para dterminar o link de saída. Perguntar a rua de saída é análogo a perguntar o link de saída.


### 10)





