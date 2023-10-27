# Atividade-M8

## Arquitetura proposta 
![image](https://github.com/gaebizinha/Atividade-M8/blob/main/atividadeS1.drawio.png)

## 1 Entrada de dados

Como o projeto consiste na construção de um cubo de dados, existem 3 entradas de dados, sendo eles de 2 tipos:

1.  Dados da API do Cliente: Os dados são recebidos por meio da API do cliente e são encaminhados para processamento.
2.  Dados Públicos CSV: Dados em formato CSV são fornecidos como fontes de entrada.

## 2 Srcipts em Python

Após o recebimento de dados pela API do cliente, os dados passam pelo script em python para serem atualizados quando necessário. Já no caso dos dados em CSV, o script em python facilita a integração com o Cassandra DB, estes dados são agrupados no Cassandra para garantir a escalabilidade e o desempenho do sistema.

## 3 Gerenciador de Servidor (Lambda)

Os dados recebidos pela API são encaminhados para um gerenciador de servidor, Lambda da AWS, que gerencia o fluxo de dados e encaminha-os para o Dynamo DB, um banco de dados NoSQL altamente escalável da AWS.

## 4 AWS Glue

Após serem armazenados no Cassandra DB os dados são submetidos a um processo de ETL no AWS Glue. Os passos típicos do ETL são geralmente:
1. Extração: Os dados são extraídos do Cassandra DB.
2. Transformação: Os dados são transformados para atender aos requisitos do cubo de dados, como agregação, filtragem e enriquecimento.
3. Carregamento: Os dados transformados são carregados em outra camada de armazenamento ou banco de dados, que no caso é o DynamoDB.

## DynamoDB

Após o processo de ETL, os dados já processados são enviados para o DynamoDB, onde se juntam aos dados previamente agrupados pela API, neste momento ocorre a consolidação dos dados, e o cubo de dados é gerado com informações mais ricas e prontas para análises futuras.

## AWS QuickSight

Por fim , a análise dos dados é realizada usando o AWS QuickSight, uma ferramenta de visualização de dados da AWS. A conexão entre o QuickSight e o cubo de dados é estabelecida a partir do Apache Spark, que pode ser usado para processamento de big data e análise avançada.

## Segurança

A segurança básica da arquitetura do cubo é feita pela Virtual Private Cloud (VPC), garantindo segurança e isolamento dos recursos.
