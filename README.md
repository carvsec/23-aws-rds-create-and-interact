# AWS RDS Lab: Provisionamento de Banco de Dados Resiliente e Integração Web

Registro prático da construção de um ambiente de banco de dados relacional MySQL com tolerância a falhas na AWS. O projeto aborda desde o isolamento da camada de dados até a comunicação segura com uma aplicação web hospedada no Amazon EC2.

## Visão Geral da Arquitetura

* Rede VPC: Segmentação do ambiente em subredes públicas para a camada web e subredes privadas para a camada de dados distribuídas em duas Zonas de Disponibilidade.
* Servidor de Aplicação: Instância EC2 pública responsável por processar a interface e a lógica da aplicação.
* Base de Dados: Instância Amazon RDS MySQL configurada com réplica de failover automática em modo Multi AZ.
* Controle de Acesso: Políticas de firewall Security Groups baseadas no princípio do menor privilégio, liberando a porta 3306 exclusivamente para a camada web.

## Recursos e Tecnologias

* Serviços AWS: Amazon RDS, Amazon EC2, Virtual Private Cloud VPC, DB Subnet Groups, Security Groups.
* Engine de Dados: MySQL 8
* Tecnologias Web: PHP, HTML, CSS.

## Procedimento de Execução

1. Definição de Regras de Firewall: Configuração do Security Group do banco para aceitar tráfego de entrada na porta 3306 vindo unicamente do Security Group da instância EC2.
2. Agrupamento de Subredes: Alocação de subredes privadas de diferentes zonas no DB Subnet Group para habilitar o suporte à alta disponibilidade.
3. Provisionamento do Banco: Deploy do banco de dados MySQL lab db ativando o recurso Multi AZ.
4. Validação e Conectividade: Apontamento da aplicação web para o Endpoint gerado pelo RDS e teste de persistência dos dados inseridos no formulário.

## Validação e Evidências

### 1. Liberação de Tráfego no Security Group
![Security Group](./images/01_security_group.png)
Configuração da regra de entrada permitindo acesso à porta 3306 via Security Group da aplicação web.

### 2. Endpoint de Conexão do Amazon RDS
![Endpoint RDS](./images/02_rds_endpoint.png)
Painel de gerenciamento mostrando os dados de conectividade do banco de dados.

### 3. Confirmação do Status Multi AZ
![Status Multi AZ](./images/03_multi_az.png)
Verificação dos parâmetros do banco confirmando a redundância ativa em múltiplas zonas.

### 4. Persistência de Dados no App Web
![Aplicação Funcionando](./images/04_address_book.png)
Interface da aplicação web gravando e listando registros com sucesso no banco RDS.
