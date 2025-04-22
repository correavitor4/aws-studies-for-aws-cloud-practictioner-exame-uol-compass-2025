#Simulado #SimuladoEmGrupo
Obtivemos 92% de acertos, acertando 60 de 65 questões. Contudo, precisamos revisar as 5 questões que erramos


# Análise de questões incorretas
#### Pergunta 2 
#Kinesis
Quais são as principais características do Amazon Kinesis?

(selecione duas alternativas)

Respostas:
1. coletar, processar e analisar streaming de dados em tempo real **Acertamos**
2. cgerar insights rápidos de acordo com os dados obtidos**Não marcamos** -> O Kinesis permite obter insights imediatos, possibilitando a Tomada de decisões rápidas

Descrição do erro: Marcamos uma opção que falava que o Amazon Kinesis permite armazenar os resultados do que foi processado. Contudo, o Kinesis não armazena. Na verdade, ele pode enviar os dados para outros serviços como S3, DynamoDB, etc, mas ele não armazena os dados. 


#### Pergunta 4
#NACL #ACL 
Qual é a principal função para o NACL - Network Access Control List dentro de uma rede virtual privada da cloud?

Resposta:
É um serviço opcional que serve como um firewall para controlar o fluxo de entrada e saída de dados de uma ou mais subnets

Descrição do erro: Marcamos uma opção onde ele seria obrigatório. Mas, na verdade, ele é opcional


#### Pergunta 24
#CloudSearch #ElasticSearchService
Qual é o serviço gerenciado na nuvem AWS com o qual é possível configurar, gerenciar e dimensionar uma solução de pesquisa, de forma simples e econômica, para o seu site ou aplicativo ?

Resposta:
Amazon CloudSearch

Descrição do problema:
Acabei marcando Amazon ElasticSearchService, mas o correto seria CloudSearch. Os colegas do meu grupo falaram a opção correta mas, por erro meu, acabei marcando a opção incorreta.

É bom esclarecer qual a diferença entre eles 

| Amazon CloudSeach                                                                      | Amazon ElasticSearchService        |
| -------------------------------------------------------------------------------------- | ---------------------------------- |
| Configurar, gerenciar e dimensionar uma solução de pesquisa para um site ou aplicativo | Esse é voltado a logs de serviços. |


#### Pergunta 58
#IPv4 #AZ #AvailabilityZone #Region 
Quais são as considerações importantes sobre a utilização de endereços IPv4 públicos na AWS?

Resposta:
São limitados a 5 por conta por região

Descrição do problema: marcamos que era limitado a 10 por Zona de Disponibilidade


#### Pergunta 59
Sobre o gerenciamento de Grupos no AWS IAM, podemos afirmar que:

(Selecione 3 alternativas)

Respostas:
1. Um usuário pode pertencer a vários grupos
2. Os grupos não pode ser aninhados, eles só podem conter usuários
3. Um Grupo pode conter diversos usuários

Descrição do erro: 
Marcamos que o número e o tamanho dos grupos do AWS IAM são virtualmente ilimatados, quando na verdade são sim. 
1. Pode criar até 300 grupos IAM
2. Cada grupo pode conter até 1000 usuário
3. Um usuário pode ser membro de até 10 grupos


# Questões para revisão
#### Questão 39, sobre o SAP
#LauncWizard
Acertamos por chute, e a resposta é LaunchWizard. Ele simplifica o processo de configurações de ambientes #SAP

#### Questão 50, sobre o AWS RAM (Resource Access Manager)
#RAM #ResourceAccessManager
O RAM permite o compartilhamento seguro de recursos da AWS entre múltiplas contas dentre de uma organização

#### Questão 54 - Sobre o Workspace Web 
#WorkspacesWeb 
O workspaces web é um serviço de desktop virtual para que organizações criam ambientes de trabalho em nuvem, oferecendo acesso remoto seguro a desktops e aplicativos através de qualquer dispositivo com um navegador WEB