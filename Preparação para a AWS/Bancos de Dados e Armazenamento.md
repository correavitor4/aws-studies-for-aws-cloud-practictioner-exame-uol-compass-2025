# EBS
#EBS #Block #Storage 
Um volume de armazenamento em bloco que se comporta como um disco rígido. 
Um #InstanceStore fornece um armazenamento temporário para um instância EC2, mas ele é apagado quando a instância é deletada. 
Já o #EBS fornece um tipo de armazenamento que pode ser usado com instâncias EC2. Caso a instância seja terminada, o armazenamento continua persistido. Você pode configurar backups incrementais de volumes EBS criando Snapshots.
#### Snapshots
#EBSSnapshot
EBS Snapshots são backups incrementais. Na primeira vez ele pega tudo que tem no volume. No segundo em diante ele só faz backup do que foi alterado desde o último backup. 


# Amazon S3 - Simple Storage Service
#### Armazenamento a nível de objeto
#S3 #Storage 
Armazenamento a nível de objetos #ObjectStorage, onde cada objeto possui dado, metadado e chave. Os dados podem ser de qualquer tipo, como text, vídeo, imagem, etc. 
#### S3
Você pode enviar qualquer tipo de arquivo para o S3, que ele salvará os dados em buckets #Bucket. O tamanho máximo de arquivo é 5TB 
Você pode enviar um arquivo e definir permissões de controle e visibilidade. Também é possível fazer versionamento #Versioning 

#### Classes de armazenamento
No S3 você para pelo que usa. É possível escolher uma das possíveis classes de armazenamento.
1. **S3 Standard** -> #S3Standard Para dados acessados frequentemente, e os armazena em no mínimo 3 AZs. Tem um custo mais alto do que as outras classes de armazenamento voltadas ao acesso infrequente ou arquivamento
2. **S3 Standard-Infrequent Access (S3 Standard-IA)** -> Ideal para dados que não são frequentemente acessados. É parecido com o S3 Standard, mas tem um preço de armazenamento mais baixo e um preço de retorno mais alto.
3. **S3 One Zone-Infrequente Access (S3 One Zone-IA** -> Armazena os dados em apenas uma AZ, e oferece um preço de armazenamento mais baixo do que a Standard IA. É uma boa opção para quem quer reduzir os custos de armazenamento e os dados podem ser facilmente reproduzidos caso haja falha em alguma AZ.
4. **S3 Intelligent-Tiering** -> A AWS monitora os acessos ao objeto. Se o objeto não for acessado por dias 30 dias consecutivos, o S3 automaticamente mova o objeto para Standard-IA. Caso ele esteja no Standard-IA e seja acessado, ele volta para o S3-Standard.
5. **S3 Glacier Instant Retrieval** -> Ideal para dados arquivados que precisam ser retornados rapidamente. Eles são retornados em questões de milissegundos. Eles podem ser retornados com a mesma performance de um S3 Standard
6. **S3 Glacier Flexible Retrieval** -> Armazenamento de dados arquivados de baixo custo. Ele pode retornar os objetos em alguns minutos ou algumas horas. Na verdade, vai de 1 minutos até 12 horas. 
7. **S3 Glacier Deep Archive** -> O mais barato para armazenar dados arquivados. Ele retorna os dados num período entre 12 a 48 horas. 
8. **S3 Outposts** -> Ele leva o armazenamento de objetos até o ambiente on-premises. 


# EFS
[[EFS]]


# Amazon Relational Database Service (RDS)
#RDS #Database #RelationalDatabase
É um serviço que permite rodar bancos de dados relacionais na Cloud da AWS. Ele é um serviço gerenciado que provém:
1. Hardware
2. Configuração de banco de dados
3. Patching 
4. Backups

#### Amazon Aurora
#RelationalDatabase #Aurora #RDS
É um banco de dados relacional. Ele é compatível com MySQL e PostgreSQL, sendo até 5x mais rápido do que o primeiro e até 3x mais rápido do que o segundo (supostamente). 
Ele ajuda a reduzir custos de bancos da dados através da redução de operações de IO desnecessárias, enquanto assegura que os recursos de bancos de dados continuem disponíveis e confiáveis. 


# Amazon DynamoDB
Um banco de dados não relacional #NoSQL que utiliza a abordagem chave-valor #KeyValue. Ele promete oferecer performance de um dígito de milissegundo (supostamente) em qualquer escala. Ele é #ServerLesss, o que significa que o usuário não precisa provisionar, atualizar ou gerenciar servidores, tampouco sistemas operacionais.
Ele escala automaticamente. 
**Notas pessoais**: eu tive a curiosidade de pesquisar quais são as diferenças entre ele e o MongoDB, pois ambos são NOSQL. Achei algumas diferenças usando o Perplexity AI. 
1. Mongo usa documentos BSON (um binário do JSON), com suporte a 16MB por documento e usa um tal de "GridFS" para arquivos maiores. Já o DynamoDB usa um modelo híbrido (chave-valor + documentos), com itens limitados a 4000GB
2. O Mongo usa **Schema-on-read**, que é uma estrutura flexível, sem esquema rígido e com validação opcional via schemas embutidos. Já o Dynamo usa **Schema-on-write**, que é uma estrutura básica definida na criação da tabela, e com chave primária obrigatória. No Schema-on-write a estrura é definida na escrita e, caso necessário mudar, é preciso reprocessar os dados já existentes. Isso pode ser custoso em volumes grandes. 
Existem outras diferenças, mas acho que não é necessário detalhar mais. Não acho que vão cobrar isso na prova. Só pesquisei por pura curiosidade e nada mais.


# Redshift
#Redshift
Um serviço que o usuário pode usar para análise de Big Data. Ele pode coletar dados de várias fontes e ajudar a entender relacionamentos e tendências nos dados


# AWS Database Migration Service (AWS DMS)
Habilita o usuário a migrar bases de dados relacionais, não relacionais, ou outros tipos de bases de dados
As bases de destino e origem podem ser do mesmo tipo ou de tipos diferentes. 
Durante a Migração #Migration, a base de dados de origem continua operacional. 


# Outros serviços de Bancos de Dados
1. Amazon DocumentDB #DocumentDB -> Um banco de dados de documentos que suporta cargas de trabalho de MongoDB
2. Amazon Neptune #Neptune -> Serviço de Banco de Dados em Grafos. 
	1. Anotação pessoal: eu já havia ouvido falar sobre bancos de dados em grafos, mas nunca havia usado, e também não sabia ao certo para que serviam. No site do Skillbuilder, há um pequeno trecho de texto que diz que pode ser usado em "Recommendation Engines", o qual acredito (achismo) referir-se à algoritmos de recomendação. Também pode ser usado em detecção de fraudes e "knowledge graphs".
3. Amazon Quantum Ledger Database (Amazon QLDB) #QLDB #QuantumLedgerDatabase -> Um serviço de "Legder Database" (banco de dados de livro-razão). 
	1. **O que é um banco de dados de livro-razão?**: É um tipo de banco de dados projetado para armazenar dados de forma segura, imutável e transparente, mantendo um histórico completo e verificável de todas as alterações feitas nos dados ao longo do tempo.
		1. Usos: registrar transações financeiras, rastrear cadeiras de suprimentos, manter históricos de declarações e centralizar registros digitais, entre outras aplicações que exigem integridade e auditabilidade dos dados
4. Amazon Managed Blackchain #ManagedBlockchain #Blockchain -> feita para criar e gerenciar redes de Blockchain com frameworks open source
5. Amazon Elastic Cache #ElasticCache #Cache -> É um banco de cache. Ele suporta #Redis e #MemCached
6. Amazon DynamoDB Accelerator (DAX) #Cache #DAX #DynamoDB #DynamoDBAccelerator -> Cache em-memória para DynamoDB
