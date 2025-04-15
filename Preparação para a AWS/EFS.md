#Storage 
Elástico, escalável e é compartilhado entre várias instâncias EC2. Ele não depende de servidor. 

A entrada e saída de dados é um pouco mais lenta do que um EBS, já que ele usa a rede para trafegar os dados que estão sendo gerenciados

Não precisamos determinar um volume de armazenamento, e só pagamos pelo que usamos.  Ele aumenta e diminui automaticamente conforme adicionamos e removemos arquivos, sem a necessidade de gerenciamento ou provisionamento

A durabilidade e a disponibilidade dos arquivos são muito altas.

A instâncias EC2 precisam estar na mesma VPC do EFS. Ele pode utilizar várias zonas de disponibilidade, caso queira.

### Rede
Ele cria uma placa de rede para cada zona de disponibilidade, e atribui um endereço IP. Ele costuma atribuir grupos de segurança às zonas de disponibilidade. 
Configuro regras de entradas para que as instâncias EC2 possam acessar os recursos do EFS. 