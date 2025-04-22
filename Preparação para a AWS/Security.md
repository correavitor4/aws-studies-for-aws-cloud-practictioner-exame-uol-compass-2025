#Security 
# Shared Responsability Model
Disponível em: [[AWS Shared Responsibility Model]]


# Identity and Access Management (IAM)
#IAM #Identity
#### AWS Account root user
#Root #User #RootUser
De início, a conta da AWS começa com uma usuário root.
Fazendo uma analogia à cafeteria [[Cafeteria]], o usuário root seria o dono dela.
O root é acessada logando com o email e senha usados na criação da conta da AWS, e tem acesso a todos os recursos e serviços da conta.
**Uma boa prática é NÃO usar o usuário root para as tarefas do dia a dia. Ao invés disso, é melhor criar um usuário IAM e anexar a ele as permissões para criar outros usuários**

#### IAM
#IAM
É uma identidade que representa uma **pessoas** ou **aplicação**. Ele consiste de nome e credenciais. Por padrão, ele começa sem nenhuma permissão associada. 
**É recomendável criar um Usuário IAM para cada pessoa que precise acessar a conta da AWS**


#### IAM Policies 
#IAM #Policies
Um IAM Policy é um documento que permite ou nega permissões para recursos e serviços da AWS
**É recomendável dar o mínimo de permissões necessários para usuários e roles**
Fazendo uma analogia à [[Cafeteria]], podemos tomar um exemplo: um novo funcionário do caixa é um IAM User. Ele tem apenas a permissão de ler um recurso do S3. Sendo assim, devemos dar apenas a permissão de acessar a esse recurso em específico do S3 para ele. 

#### IAM Groups
#IAM #Groups #IAMGroups
Um IAM Groups é uma coleção de IAM Users. Tomemos o exemplo do tópico anterior (IAM Policies). Imagine que em vez de ter apenas um funcionário de caixa, existam vários. Ao invés de ter que associar, manualmente, as mesmas permissões a cada um deles, podemos simplesmente criar uma IAM Groups com as devidas permissões, e associar os IAM Users do caixa a esse IAM Group. Assim, ele herdará todas as permissões do IAM Groups. 
Anotação pessoal: Dá pra fazer uma analogia com herança de classes, onde a classe filha herda os atributos e métodos da classe mãe.
Voltando à analogia da [[Cafeteria]], podemos definir vários IAM Groups, como especialistas de inventário, baristas, etc. Cada um  com suas próprias permissões.

#### IAM Roles
#IAM #IAMRoles
Continuando com a analogia à cafeteria descrita no tópico anterior (IAM Groups), vamos imaginar agora que, ao invés dos funcionários terem uma ocupação fixa, eles terão rotatividade de funções ao longo do dia. Em cada uma das ocupações, os funcionários terão as permissões da ocupação anterior revogadas e receberá as permissões da ocupação atual. Assim sendo, podemos usar IAM Roles para dar permissões temporárias para eles enquanto estão ocupando uma determinada função. 
Antes de um usuário, aplicação ou serviço assumir uma IAM Role, ele deve receber a permissão para trocar de role. Quando alguém assume uma role, ele abandona todas as permissões que a ele foram dadas na rola anterior. Ele assume, então, as permissões da role atual. 
**Momento boa prática**: Roles são ideais para situações onde o acesso a recursos ou serviços precisa ser temporário. 


#### Autenticação em dois Fatores (MFA)
#MFA
Não precisa de muita descrição. Basicamente adiciona mais uma etapa ao login, ao invés de pedir somente usuário e senha. Isso não é, nem de longo, exclusivo da AWS. 


# AWS Organizations
#Organizations 
A AWS Organizations permite que múltiplas contas sejam consolidadas e gerenciadas dentro de uma localização central.
Quando uma organização é criada, um #Root é criado, sendo ele o pai de todas as contas da organização
Com o AWS Organizations você pode definir permissões para as contas na organização usando Service Control Policies (SCPs) #SCP. Os SCPs estabelecem restrições à recursos, serviços e ações individuais de API que usuários e roles em cada conta da AWS.

#### Organizational Units (OUs)
#OrganizationalUnits #OUs
As Organizational Units permitem agrupas contas de uma AWS Organization para facilitar o gerenciamento de contas que tenham negócios ou requisitos de segurança parecidos. Quando aplicadas, todas as contas herdam as políticas especificadas. 
**Vamos pensar em um exemplo**: imagine que uma companhia tem contas da AWS separadas para o financeiro, para o TI, para o RH e para o Departamento Legal. A companhia decide consolidar essas contas em uma única organização que possa ser administrada por uma localização central. 
1. Cria-se a organização e, consequentemente, um root. 
2. Considera-se os negócios, segurança e requerimentos regulatórios de cada departamento. 
3. Com as informações acima, as contas são agrupadas em OUs
	1. O departamento de TI e o financeiro não possuem requisitos que se sobrepõem a outros departamentos, então opta-se por não atribuí-las a um OU
	2. O departamento de RH e o Legal precisam acessar os mesmos recursos e serviços da AWS, então eles são colocados juntos em uma OU. 


# Compliance
#Compliance
"Compliance" tem a ver com seguir leis, normal, regulamentos e padrões éticos aplicáveis

#### AWS Artifact
#Artifact
É um serviço que fornece acesso em demanda a relatórios de segurança e #Compliance da AWS. Ele consiste em duas principais seções:
**AWS Artifact Agreements** -> Com ele você pode revisão, aceitar e gerenciar acordos a nível de conta individual e para todas as contas de uma AWS Organization.
**AWS Artifact Reports** -> Ele fornece reportes de #Compliance de auditores terceiros. Esses auditores testam e verificam que a AWS está em conformidade com uma variedade global, regional ou industry-specific de normas e regulamentos de segurança. Os Artifact Reports se mantém atualizados com os últimos reportes disponíveis. 

#### Customer Compliance Center
#CustomerComplianceCenter
Contém recursos que te ajudam a aprender mais sobre a AWS Compliance. É possível fazer coisas como:
1. Ler estórias sobre como companhias de indústrias regulamentas conseguiram resolver desafios de governança, compliance e auditação.
2. Respostas da AWS para questões chave sobre Compliance
3. Uma visão geral de Riscos e Compliance da AWS
4. Um check list de auditoria de segurança.


# AWS Shield e ataques Denial-of-Service (Dos)
#DoSAttack #DDoSAttack #Shield 
Vamos fazer uma analogia à [[Cafeteria]]. Uma imagine que algum engraçadinho está fazendo vários pedidos, múltiplas vezes, mas ele nunca vai pegar as bebidas. A cada vez que alguém faz um pedido, o funcionário do caixa precisa passá-lo ao barista. Entretanto, se alguém ficar pedindo demais, ele pode ficar tempo demais ocupado com esse cliente e deixar de atender os clientes que estão esperando. Essa analogia se aplica aos ataques DDoS, que é uma tentativa deliberada de tentar fazer um uma aplicação ou WebSite ficar indisponível para outros usuários. 
Por exemplo, eu posso fazer requisições excessivas a uma site de maneira que ele fique sobrecarregado, a ponto de ficar indisponível.
Na analogia do feita anteriormente, a cafeteria pode simplesmente bloquear o número de telefone do engraçadinho. Mas ele pode tentar usar múltiplos números de telefone para atacar a cafeteria, de maneira que ela não consiga bloquear todos. Isso seria equivalente a um Distributed Denial-of-Service (DDoS).

#### AWS Shield
#Shield 
Para evitar esses ataques, é possível usar o AWS Shield. Ele fornece 2 níveis de proteção
1. AWS Shield Standard #ShieldStandard -> Protege automaticamente sem nenhum custo. Protege controas os mais comuns e frequentes tipos de ataque DDoS.
2. AWS Shield Advanced #ShieldAdvanced -> É um serviço pago que fornece diagnósticos detalhados de ataques DDoS e habilita a detecção e mitigação de ataques sofisticados. 
O AWS Shield também se integra a outros serviçõs como o Amazon CloudFront, Route 53, Elastic Load Balancing.


# AWS Key Management Service (AWS KMS)
#KMS #KeyManagementService #Cryptography
É um serviço que permite operações de encritações com o uso de **Chaves de Encriptação**. Essas chaves são strings aleatórias usadas para encriptar de desencriptar dados. 
O KMS permite criar, gerenciar e usar chaves de criptografia. 
É possível especificar níveis de controle de acesso necessários para a chaves. Por exemplo, é possível especificar quais IAM User e Roles estão aptos a gerenciar chaves. Também é possível desativar, temporariamente, chaves que não são usadas a muito tempo.
**Se as chaves nunca saírem da AWS KMS, nós sempre estaremos no controle delas**


# AWS WAF 
#WAF
É um Firewall para aplicações Web que permite monitorar requisições de rede que estão chegando nas aplicações. 
Ele usa ACLs #ACL bloquear determinados IPs de acessarem as aplicações web. 


# Amazon Inspector
#Inspector
Ele permite rodar avaliações de segurança automáticas para verificar se a aplicação tem vulnerabilidades e se está em conformidade com as melhores práticas de segurança. Ele estão fornece uma lista que prioriza por nível de severidade, fornecendo recomendações para melhorar. 
Vamos fazer uma analogia à [[Cafeteria]]. Imagine que os funcionários estão desenvolvendo uma aplicação para realizar pedidos. Eles querem verificar se a aplicação está atendendo às normas e boas práticas de segurança. É aí que entraria o Amazon Inspector. 


# Amazon GuardDuty
#GuardDuty
Fornece detecções de ameaças à infraestrutura e recursos da AWS. 


# Quais são as diferenças entre o Amazon Inspector e o Amazon GuardDuty?
Anotação pessoal: à primeira vista, os dois serviços me pareceram bem parecidos, então decidi pesquisar um pouco mais a respeito e verificar quais são as diferenças e quais são os verdadeiros propósitos de cada uma. Acho que já vi questões dos simulados onde esses serviços foram mencionados, então não custa nada tentar buscar mais informações a respeito. 

|        | Amazon GuardDuty                                                                                                                                                            | Amazon Inspector                                                                    |
| ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| Foco   | Detecção de ameaça que monitora continuamente o ambiente AWS para identifcar atividades suspeitas, como acesso não-autorizado, comportamentos anômalos ou padrões de ataque | Serviço de avaliação de vulnerabilidade que examina configurações de instâncias EC2 |
| Escopo | Todo o ambiente AWS                                                                                                                                                         | EC2, imagens de contêineres e funções Lambda                                        |
