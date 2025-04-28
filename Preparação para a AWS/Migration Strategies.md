#Migration #CloudMigration #MigrationStrategy #CloudMigrationStrategy
Quando se migra para a Cloud, as 6 estratégias mais comuns são:
1. [[#Rehosting]]
2. [[#Replatforming]]
3. [[#Refactoring/re-architecting]]
4. [[#Repurchasing]]
5. [[#Retaining]]
6. [[#Retiring]]
Em geral, a migração para a nuvem não acontece magicamente. Essas estratégias ajudam a fazer esse processo de migração. A seguir, detalharei os citados acima


## Rehosting
#Rehosting 
Envolve mover os aplicativos para a Cloud sem alterá-los. O que se faz aqui é basicamente re-hospedá-los na Cloud. Isso pode ser útil, por exemplo, quando uma empresa tem um série de aplicações legadas e quer movê-las rapidamente para a nuvem, afim de escalar e migrar rapidamente.
Em geral, **não se altera a arquitetura ou o código**, e também não se fazer otimizações e nem nada do tipo. 
Ainda é vantajoso, pois migrando para a Cloud, mesmo que não se façam modificações, ainda assim se torna mais fácil (ou menos difícil) escalar as aplicações. Também elimina os gasto com hardware local.


## Replatforming
#Replatforming
São aplicadas **otimizações pontuais** nas aplicações para aproveitar serviços gerenciados da AWS, mas é mantido o núcleo da arquitetura original. Trata-se de uma meio-termo entre o [[#Rehosting]] e o [[#Refactoring/re-architecting]].
Um exemplo seria migrar um banco de dados local para o RDS.
Reduzem-se os custo operacionais, vista que elimina a gestão de infraestrutura de componentes específico (como patches bancos de dados).
Uma outra vantagem é que, mesmo se mantendo a velocidade próxima ao rehosting, ainda assim há ganhos adicionais de eficiência, já que algumas partes da arquitetura são alteradas.


## Refactoring/re-architecting
#Refactoring #ReArchitecting
Envolve o redesenho completo da arquitetura, afim de aproveitar ao máximo os serviços nativos da AWS, como o #ServerLesss, #Microsservices e soluções gerenciadas. É bom para aplicar, por exemplo, em sistemas monolíticos legados ou aplicações que precisam de uma escalabilidade extrema.
É importante dizer que essa estratégia de migração tende a ser mais **complexa** do que as citadas anteriormente, e mais transformadora também.
Existem algumas características a serem citadas:
1. Modernização profunda -> Substituição de componentes legados por serviços como AWS Lamba, Amazon EKS, etc
2. Padrão Strangler Fig #StranglerFigPattern -> Migração incremental usando o #MigrationHubRefactorSpaces para a coexistência entre sistemas antigos e novos #Microsservices 
3. Automação nativa -> Uso de ferramentas como o #StepFunctions para substituir código customizado por fluxos gerenciados


## Repurchasing
#Repurchasing 
É uma estratégia de migração para a AWS que substitui aplicações legadas por solução #SaaS ou produtos comerciais disponíveis no ecossistema AWS, eliminando a necessidade de gerenciar infraestrutura e reduzindo custos operacionais
Algumas características principais
1. Substituição por #SaaS -> Troca de aplicações locais por versões gerenciadas por terceiros (ex: Salesforce, Zscale)
2. Licenciamento simplificado -> Modelo de assinatura #PayAsYouGo, com cobrança integrada à fatura AWS via AWS Marketplace
3. Integração acelerada -> Soluções pré-configuradas no AWS Marketplace


## Retaining
#Retaining
Consiste em manter algumas aplicações ou workloads no ambiente on-premises, sem migrá-las para a nuvem (ao menos por enquanto). Existem alguns motivos para adotar o Retaining:
1. Requisitos de segurança e compliance
2. Dependências técnicas ou de outros sistemas -> integrações complexas, ou senão que dependem de Hardware especializado
3. Aplicações de missão crítica ou de alto risco -> Muitas exigem uma avaliação detalhada e muito planejamento antes de migrar par aa CLoud

Existem vantagens:
1. Permite compliance
2. Sincroniza migrações de aplicações interdependentes, reduzindo o risco de falhas

Mas também há desvantagens:
1. Perde benefícios da nuvem
2. Aumente a complexidade operacional, já que agora será preciso um ambiente híbrido (on-premises + Cloud)
3. Pode limitar integrações futuras se aplicações permanecerem isoladas ou defasadas


## Retiring
#Retiring
Envolve desativar aplicações que não mais agregam valor ao negócio, eliminando custos operacionais e riscos de segurança associados a sistemas legados
Quando usar:
1. Aplicações "zumbis" -> Sistemas com uso de CPU/memória muito baixos por um longo período de tempo
2. Sem conexões ativas
3. Legados inseguros
4. Redundâncias que podem ser substituídas por soluções SaaS ou cloud-native

Exemplo: Um banco de dados SQL Server local, sem conexões ativas há 6 meses e com custo anual de US$ 15k em licenças, é desativados após migrar seus dados históricos para o Amazon S3 Glacier #S3 

Obviamente, existem boas práticas relacionadas ao Retiring
1. Documentar decisões -> Registrar justificativas para auditorias futuras
2. Fazer Backups
3. Priorizar aplicações de baixo risco
