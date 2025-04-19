#InternetGateway #VPC #Subnet
## VPC - Virtual Private Cloud
Um serviço de rede que o cliente pode usar para estabelecer limites ao redor dos serviços da AWS
Ele permite provisionar uma seção isolada na Cloud da AWS.


## Internet Gateway
Para permitir o tráfego público da Internet à sua VPC, você deve associá-la a um Internet Gateway. O VPC é a conexão entre a VPC e a Interner. Fazendo uma analogia com a [[Cafeteria]], é como se fosse a porta que permite que os clientes entrem na cafeteria. Sem um Internet Gateway, ninguém consegue acessar os recursos que estão dentro da VPC.


## Virtual Private Gateway
#VPN
Ele estabelece uma conexão entre uma rede privada (VPN) e a VPC. A VPN pode ser, por exemplo, algo on-premise. 
Em analogia à [[Cafeteria]], é como se a VPN fosse um guarda (segurança) ou escolta que te protegesse no caminho entre a sua casa e a cafeteria (considerando que você seja um cliente). 
A VPN garante a segurança na comunicação, geralmente através de criptografia. Provavelmente existem mais detalhes a respeito do que seja uma VPN, mas aqui não é tão importante agora, já que o foco é a Virtual Private Gateway. O Virtual Private Gateway vai garantir esse comunicação entre recursos privados da VPC e a VPN, garantindo que só possa trafegar aquilo que for especificado.


## AWS Direct Connect
#DirectConnect 
É um serviço que permite que você estabeleça uma conexão dedicada dedicada e privada entre seu Data Center e uma VPC. 
Analogia à [[Cafeteria]]: Imagina um apartamento onde há uma conexão direta com a cafeteria. Somente os residentes desse apartamento podem viajar por esse caminho, e quem o fizer não precisará usar uma estrada pública. Simplesmente irá pegar esse caminho direto. 
Supostamente o AWS Direct Connect pode ajudar a rejudar custos de rede e aumentar a largura de banda que pode viajar por ela.


## Subnets e ACLs (Network Access Control Lists)
#Subnet #ACL
Analogia com a [[Cafeteria]]: os cliente chegam no funcionário do caixa, e fazem o pedido. O funcionário do caixa passa o pedido para o barista. Agora imagine que alguns clientes pulem a parte de fazer o pedido no caixa e façam o pedido diretamente com o barista. Isso prejudica o fluxo de tráfego e resultados já que os cliente estariam acessando uma área da cafeteria que deveria ser restrita a eles. Para resolver isso, a cafeteria faz uma parte onde há o caixa o que os cliente possam acessar, e uma parte onde os clientes não podem entrar (onde fica o barista). Isso impede que os clientes tenham contato com o barista, e garante que somente o caixa possa passar os pedidos para ele, através de uma interação que pode pode ocorrer entre os dois
Isso é semelhante à maneira como os serviços de rede da AWS podem isolar os recursos e determinar quem pode acessar o que e como deve ser o fluxo de tráfego. 


#### Subnets
#Subnet 
É uma seção da VPC onde recursos podem ser agrupados de acordos com os fatores de segurança e requisitos operacionais. Essas subnets podem ser pública ou privadas:
1. **Subnets Públicas** -> contém recursos que precisam ser acessível pelo público
2. **Subnets Privadas** -> contém recursos que só podem trafegar através da VPC, como dados vindos de bancos de dados, por exemplo. 
Subnets podem se comunicar entre si dentro de uma mesma VPC.


#### Network ACLs.
#ACL #Security #Inbound #OutBound #TrafficControl 
Quando um cliente requisita dados de uma aplicação hospedada na AWS, a requisição é enviada como um pacote, que é uma unidade de dados enviada pela internet ou uma rede. Esse pacote entre na VPC através do Internet Gateway, mas antes é necessário checar as permissões desse pacote. São essas permissões que indicam como e quem está tentando se comunicar com os recursos da subnet. O componente que verifica checa essas permissões é o Network Access Control List (ACL)
Uma rede ACL é um Firewall virtual que controla as regras de entrada e saída de dados ao **nível de subnet**. 
Toda conta da AWS tem, por padrão, uma rede ACL default. Quando você configura uma VPC, você pode usá-la ou criar uma ACL customizada. Essa rede Default permite (por padrão) todo o tráfego de entrada (inbound) e saída (outbound). Já uma rede customizada proíbe, por padrão, todo o tráfego de entrada e saída. Para que a ACL customizada aceite entrada e saída, é preciso configurá-la.
ACL tem comportamento #Stateless, ou seja, ela não armazena estado. Se uma requisição de entrada é feita, ela é verificada e a resposta de saída também é verificada (independentemente da entrada)
As ACLs permitem especificar regas de #Allow e #Deny


# Security Groups (Grupos de Segurança)
#Security #SecurityGroup #TrafficControl 
Assim como as ACls, os Security Groups também são mecanismos de controle de tráfego. Porém existem diferenças entre elas. 
Os Security Groups atuam a **nível de instância** de recurso, controlando o que entra e sai de uma instância EC2 ou outro recurso associado. 
Um outro ponto importante é que os Security Groups são #Stateful. Isso porque se uma conexão de entrada é permitida, o tráfego de saída de resposta é automaticamente permitido, sem necessidade de explicitar regras de saída. 
Os Security Groups só permitem especificar regras de #Allow
Eles bloqueiam todo o tráfego de entrada por padrão #Inbound 

# Global Networking
#### Domain Name System (DNS)
#DNS #DomainNameTranslation #IP #Routing
Faz a tradução do nome do domínio para um endereço de IP

#### Route 53
#Route53 #DNS #Routing
É um serviço Web de DNS. Ele fornece uma maneira confiável para o roteamento entre consumidores finais e aplicações de internet hospedadas na AWS. 
Ele conecta requisições de usuários à infraestrutura que está rodando na AWS. Ele também pode rotear para infraestrutura que está fora da AWS.
Também é possível gerenciar registros de DNS para nomes de domínio. Você pode registrar nomes de domínio diretamente usando Route 53 ou pode transferir registros de DNS para uma registros de outros gerenciadores de domínio. 
Exemplo: Um cliente quer acessar um recurso que será fornecido através do CloudFront. Ele faz uma requisição à AWS, e o Route 53 direciona para a Edge location mais próxima, que devolve o recurso solicitado pelo cliente. 