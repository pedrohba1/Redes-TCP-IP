# lista 1 sobre camada de redes

### 1)

O pacote na camada de rede é chamado de datagrama da camada de rede. Comutadores da camada de enlace decidem
como eles vão fazer o repasse baseado nos dados presente no frame da camada de enlace (endereço MAC).
Roteadores baseiam seu repasse nos valores dos campos da camada de rede. (Endereço IP).

### 2)

Repasse é uma ação local de transferir pacotes de uma interface de entrada a uma interface de saída.
Repasse dura apenas um intervalo muito pequeno e normalmente é implementado em nível de hardware.
Roteamento refere-se ao processo em rede, que determina todos os caminhos do começo ao fim que um pacote
precisa tomar para chegar da origem ao seu destino. Roteamento demora muito mais tempo e é implementado
em software. Determinar todos esses caminhos no roteamento, requer um algoritmo de roteamento.

O repasse também é uma pequena etapa dentro de um roteamento. Ou seja, um roteamento consiste de muitos repasses.
Isso porque cada roteador tem uma tabela de repasse (forwarding table) que é usada para saber para qual interface
de saída enviar esse pacote. Dependendo do protocolo da camada de rede, o header nesse pacote pode ser o endereço
de destino ou uma indicação da conexão que esse pacote pertence.

### 3)

A tabela de repasse contém os campos para determinar qual "link interface" de saída que o pacote que está chegando
será redirecionado. 


### 4)

Comutação via memória: um pacote que chega, sinaliza para o processador uma interrupção. O pacote então é copiado da
input port para a memória do processador. O processador então extrai o endereço de destino e com base nele
descobre para qual output port enviar. Nesse cenário, se a banda de memória é B pacotes por segundos em escrita e leitura, então o throughput (taxa total de que os pacotes são transferidos da input port para a output port) deve ser menor que B/2. Isso porque tem a leitura antes que é de taxa B e depois a escrita que também é de taxa B. 


Comutação por barramento (switch via bus): Nesse procedimento, a input port manda o pacote diretamente para a
output port por meio de um barramento compartilhado sem a intevenção do processador de roteamento. Nesse mecanismo,
o pacote é recebido por todas as output ports mas somente a correta irá receber o pacote. Se múltiplos pacotes 
chegarem ao mesmo tempo, cada uma em uma output port diferente, apenas um por vez passará pelo barramento. 
Como diferentes pacotes precisam atravessar o mesmo barramento, a velocidade de comutação do roteador é limitada
pela velocidade de comutação do barramento. Então se o barramento permite transmitir B pacotes por segundo, o thorughput deve ser B também? (verificar com o professor hoje)

Comutação por interconexão (switch via interconnection): A comutação por interconexão supera a limitação de banda
de um único barramento. Basicamente, o barramento é uma matriz de 2N barramentos conectando as N input ports aos N output ports. Se o caminho de entrada e saída usar barramentos diferentes, é possível fazer a passagem de pacotes de maneira paralela. Ou seja, se um pacote chega na porta A e precisa ir para a porta X enquanto um pacote chega na porta B e precisa ir para a porta Y, essa passagem pode ser feita ao mesmo tempo. Porém, se dois pacotes de diferentes input ports forem para a mesma output port, então um deles terá que esperar. 

Dados essas descrições dos métodos de comutação, podemos afirmar que a comutação via interconexão é mais vantajosa
porque ela permite comutar pacotes paralelamente, desde que eles não tenha a mesma saída. É bem mais eficiente que a comutação por memória e extende a capacidade da comutação por barramento.

Comutação por interconexão > comutação por barramento > comutação por memória.


### 5) 

Head of the line blocking é um bloquei que acontece nas portas de entrada. No HOL, pacotes chegam na porta de entrada a cada unidade de tempo mais rapidamente do que o switching fabric consegue processar para a saída.  Especificamente no HOL, ele acontece quando pacotes de diferentes portas de entrada querem ir para a mesma porta de saída. Se apenas um pacote por vez pode ser transferido de uma entrada para uma saída, k-1 pacotes precisarão esperar sua vez.

### 6)

FIFO.

### 7)

Quem determina a prioridade é o ISP. Ele pode decidir que pacotes VOIP tem maior prioridade, por exemplo. Para a ISP pode ser benéfico dar satisfação para usuários que utilizem VOIP. Verificando as portas na camada de transporte é possível saber o dado que está sendo carregado pelo datagrama e assinalar a prioridade,
por isso a ISP consegue fazer isso.

Outro jeito de classificar prioridade é uma empresa pagar uma ISP para dar prioridade para seus pacotes. 
Como a Netflix pode fazer por exemplo.

### 8)

No RR (Round Robin) pacotes são ordenados em classses
com prioridade na fila. Porém, no lugar de ter um serviço estrito por prioridade entre as classes, o RR scheduler alterna serviço entre as classes. Ou seja, um pacote da classe 1 é transmitido, depois um da classe 2, depois um da classe 1, depois um da classe 2 e por aí vai (tendo duas classes de pacotes).


No WFQ (Weighted fair queuing) pacotes que chegam são classificados igual no RR, mas cada classe pode receber uma quantidade diferente de serviço em uma quantia de tempo. Ou seja, tem pacotes da classe `i` para serem enviados,
então a classe `i` tem garantidamente uma fração do serviço dada por `Wi/Sum(Wj)` onde a soma no denominador é dada pelos pesos das outras classes. Assim, no pior caso, mesmo se todas as classes tem pacotes na fila, a classe `i` ainda receberá  `R * Wi/Sum(Wj))` de serviço. 

Se os pesos das classes forem todos iguais, então o RR e o WFQ se comportam da mesma maneira.


### 9)

No IPV4 é o chamado TTL que conta quantos roteadores o pacote pode ser encaminhado. No IPV6 é o Hop Limit.


### 10)

O roteador tem a quantidade de IPs igual a quantidade de interfaces físicas. 
Porém, um roteador tem também um WAN address e um LAN address, ambos usados no NAT. Isso conta?


### 11)

 11001010.00000011.00001110 .00011001

 ### 13)
 
 Como são 4 roteadores e 2 hospedeiros, existem 5 interfaces entre os 2 hospedeiros: 3 interfaces que ligam os roteadores, uma interface ligando o primeiro hospedeiro ao primeiro roteador e uma interface ligando o roteador final ao hospedeiro final.
 Dos roteadores, serão indexadas 4 tabelas de encaminhamento


### 14)

Agregação de rotas é um método usado para minimizar o número de tabelas de roteamento. 
Consiste em combinar múltiplas rotas com endereços diferentes em uma única entidade. A vantagem é que
reduz custo de bandwidth e cpu e diminui o tamanho da routing table.
Consiste encontrar os bits comuns de várias rotas, representar bits comuns com 1 e incomuns com 0, calcular o block size
e em seguida representar a rede com o block size.


 ### 15) 

 16

 ### 16)

 Tem isso no mesmo vídeo acima


 ### 19) tem como resolver com esse vídeo

 https://www.youtube.com/watch?v=NfHR94JAO-s