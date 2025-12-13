# MVP – Pipeline de Dados de Vendas

Este repositório contém o desenvolvimento de um MVP de pipeline de dados. O projeto tem como foco a construção de um pipeline completo de dados, a partir de um banco de dados transacional, com o objetivo de transformar dados operacionais em informações analíticas capazes de apoiar análises de negócio.


## Objetivo do Projeto

Desenvolver um pipeline de dados estruturado nas camadas **Bronze → Silver → Gold**, contemplando:

- Ingestão de dados brutos provenientes de um banco transacional (OLTP)
- Organização e transformação dos dados para fins analíticos
- Construção de um modelo dimensional (Esquema Estrela)
- Avaliação da qualidade dos dados
- Realização de análises exploratórias e de negócio
- Identificação de padrões relacionados a vendas, produtos e clientes

O detalhamento completo do objetivo e das perguntas de negócio encontra-se em `/docs/objetivo.md`.

## Dataset Utilizado

**AdventureWorks2017**  
Fonte: Microsoft  
Tipo: Banco de dados transacional (OLTP)  
Uso: Educacional  

O banco representa operações de uma empresa fictícia de vendas, contendo dados de pedidos, produtos, clientes, territórios e datas.

As tabelas relevantes são extraídas do SQL Server, exportadas para arquivos CSV e posteriormente carregadas na plataforma Databricks.

## Arquitetura do Pipeline

O pipeline é implementado na plataforma **Databricks**, seguindo uma arquitetura em camadas:

- **Bronze:** ingestão dos dados brutos, sem alterações estruturais  
- **Silver:** limpeza, padronização, ajustes de tipos, validações e enriquecimentos  
- **Gold:** construção do modelo dimensional (Esquema Estrela) e tabelas analíticas  

Essa arquitetura permite rastreabilidade, organização e governança dos dados ao longo de todo o processo.

## Estrutura do Repositório
````
mvp-pipeline-ecommerce-databricks/
|── README.md
|── docs/
│   |── objetivo.md
│   |── modelagem.md
│   |── catalogo-dados.md
│   |── analises.md
|   |── autoavaliacao.md
|── notebooks/
│   |── nb_01_ingestao_bronze
│   |── nb_02_tratamento_silver
│   |── nb_03_modelagem_gold
│   |── nb_04_analises
└── evidencias/
    |── capturas-telas/
````

## Tecnologias Utilizadas

- Databricks (Free Edition)
- SQL (Spark SQL)
- Python (quando necessário)
- Delta Lake
- SQL Server (fonte de dados)
- GitHub (versionamento e documentação)



