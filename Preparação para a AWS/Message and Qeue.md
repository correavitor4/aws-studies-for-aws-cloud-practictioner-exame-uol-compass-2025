#Qeue #Message 
Na arquitetura acoplada, se algo falhar, o sistema inteiro ou uma parte grande de inteiro falha junto. Ao contrário, se uma parte falhar, o resto continua funcionando normalmente. 
No serviço de fila, introduzimos um buffer onde mensagens são publicadas e acumuladas até que sejam processadas. Enquanto não forem processadas, elas continuam lá. Isso evita a perdas. Se uma parte falhar, outras funcionam no lugar. 
SQS permite:
Enviar, armazenar e receber mensagens entre diferentes componentes de Software, em qualquer volume. As mensagens possuem payloads, e os SQS possuem filas. 
Também há os SNS, que são os Simple Notification Services. Você pode configurar os publishers e os subscribers. Os subscribers podem ser, por exemplo, endpoints, webhooks, etc.

Enquanto no SQS tudo é colocado na mesma fila, no SNS é possível gerenciar os publishers e os consumers, que subscrevem-se em tópicos. 