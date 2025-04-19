#Ec2 #Pricings #Instances #Ec2Instances

Existem vários tipos de opções de precificação

## On-demand
Aqui as cargas de trabalho não são interrompidas. Não tem custos antecipados e nem contratos mínimos. As instâncias rodam continuamente até que sejam paradas, e você só paga pelo tempo que rodaram


## Saving Plans
Exigem um compromisso de uso de Dólares por hora. Ele fornece flexibilidade de mudar o tipo de instância, as famílias, as regiões e até mesmo serviços, como EC2, Fargate, Lamba, etc. existem dois tipos:
#### Compute Saving Plans
Oferecem até 66% de desconto e são os mais flexíveis, aplicando-se automaticamente ao uso de instâncias EC2 independentemente da família, tamanho, zona de disponibilidade, região, SO ou locação de instância. Também se aplica ao Fargate e AWS Lambda. 
#### Instance Saving Plans
Oferecem até 72% de economia, semelhante às Instâncias Reservadas (RIs) padrão, mas com flexibilidade para alterar o tamanho, SO ou locação dentra da mesma família de instâncias e região. Por exemplo, você pode mudar entre diferentes tamanhos da família M5 no Norte da Virgína e continuar usufruindo do desconto. 


## Reserved Instances
São descontos aplicados no uso de Instâncias por demanda. Existem dois tipos de instâncias reservadas.
#### Standard Reserved Instances
Essa opção é boa quando você sabe o tipo de instância EC2 necessária e a região onde deve ser rodadas. Ademais, você tem que saber o tenancy e a descrição da plataforma (sistema operacional), ex: Microsoft Windows Server ou Red Hat Enterprise Linux

#### Convertible Reserved Instances
Boas quando você precisa rodar instâncias EC2 em diferentes zonas de disponibilidade ou precisar rodar diferentes tipos de instância. Você perde um grande desconto quando requer flexibilidade para rodar suas instâncias EC2. 

Ao final do termo de reserva, você pode continuar usando a instância EC2 sem interrupção. Daí você ficará sendo cobrada por demanda (on-demand) até que a instância seja derrubada ou uma nova reserva seja feita.


## Spot Instances
Ideal para cargas de trabalho com início e finalização flexíveis, ou que podem tolerar interrupções. Essas instâncias usam a capacidade computacional ociosa de EC2 da AWS e oferecem descontos de até 90% se comparadas ao preços sob-demanda.


## Dedicated Hosts
São servidores físicos com capacidade de Amazon EC2 que são inteiramente dedicadas para o uso do cliente. 
