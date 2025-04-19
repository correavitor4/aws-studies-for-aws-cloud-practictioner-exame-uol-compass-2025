
#Infrastructure #Global #GlobalInfrastructure 
Não é bom ter todos os Data Centers em um só lugar. Pode isso, é bom distribuir os recursos globalmente. Isso também protege contra desastres naturais e outros imprevistos.

**Global Footprint**: está ligada à pegada ecológica. 

## Infraestrutura Global e Regiões
Ao escolher uma região da AWS, é importante considerar os quatros fatores de negócios a seguir:
1. Conformidade com dados governamentais e requerimentos legais -> A depender da companhia e da localização, você precisa rodar os dados fora de áreas específicas. Por exemplo, uma companhia pode exigir que todos os dados trafeguem dentro do Reino Unido. Sendo assim, eu poderia escolher a região de Londres. Antes de qualquer outra coisa, é preciso se preocupar com *Compliance*
2. Proximidade aos clientes -> Pode reduzir o tempo de comunicação entre as máquinas dos clientes e os recursos computacionais onde estão rodando os servidores. É preciso considerar o quão próximo estou do cliente. Quanto mais longe, maior será a latência.
3. Disponibilidade de serviços dentro de uma região -> Às vezes alguns recursos podem não ser ofertados pela região mais próxima. Sendo assim, devem ser usadas regiões que oferecem esses serviços 
4. Precificação -> Os preços de algumas regiões são mais altas do que em outras. Por exemplo, a estrutura tributária do Brasil faz com que os preços sejam muito altos, então pode-se escolher outra região. 
**Uma região da AWS consiste em 3 ou mais AZs**


## Availability Zones (Zonas de disponibilidade) 
#AvailabilityZone #AZ 
Uma zona de disponibilidade é um único Data Center ou um grupo de Data Centers dentro de uma região. AZs são separadas umas das outras por 10 milhas de distância. Isso as deixa próximas o suficiente para que a latência entre elas seja a menor possível, mas distantes o suficientes para caso alguma sofra com algum desastre. É bom deixar os serviços disponíveis em pelo menos 2 zonas, para que haja redundância. 


## Edge Locations
#EdgeLocations
Uma Edge Location é um lugar onde o AWS CloudFront usa para armazenas cópias em cache de seu conteúdo para que estejam próximos dos clientes. 
Por exemplo: imagine que tenho uma companhia que que tem dados armazenados no Brasil. Um cliente da China quer acessar esses dados. Contudo, os dados ficam muito distantes do cliente, fazendo com que a latência fique muito alta. O CloudFront pode armazenar uma cópia em cache do dado em uma Edge Location na China. Isso faz com que o usuário receba o dado que está na Edge Location, ao invés de ter que esperar o dado atravessar o mundo inteiro para chegar até lá.


# Interação com os Serviços da AWS
#### Console
É a interação usando o navegador, o "site" da AWS

#### Linha de comando
Permite chamadas de API usando a própria máquina do cliente.

#### SDKs
Você integra isso ao seu código e ele abstrai a interação com os serviços da AWS. 


#### Outros serviços
#CloudFormation #Beanstalk
1. Beanstalk: Ajuda a configurar ambientes na AWS. Ele permite, pode exemplo, salvar configurações inteiras. Assim, eu posso derrubar um ambiente e, posteriormente, colocá-lo novamente para rodar.
2. AWS CloudFormation: Permite tratar a infraestrutura como um código. Isso significa que você pode construir um ambiente escrevendo linhas de código ao invés de usar o Managmente console para o provisionamento individual de recursos. O CloudFormation provém seus recursos em um ambiente seguro, de maneira repetitiva, habilitando o cliente para frequentemente construir sua infraestrutura e aplicações sem precisar performar manualmente. Ele determina as operações corretas a serem performadas quando o gerenciamento de sua stack e faz mudanças de rollback automaticamente se detectar erros. 
**Diferenças entre Beanstalk e CloudFormation**: O Beanstalk é um Platform as a Service (PaaS), enquanto o CloudFormation é um Infraestructure as a Code (IaC). O beanstalk até usa CloudFormation por baixo dos panos, mas ele fornece um nível de abstração bem mais alto do que o CloudFormation. No Cloud formation é possível modelar toda a infraestrutura de Nuvem, considerando os serviços internos da AWS e os externos a ela. 


