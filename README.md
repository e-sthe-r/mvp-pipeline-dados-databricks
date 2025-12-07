# mvp-pipeline-ecommerce-databricks
# MVP – Pipeline de Dados de E-commerce (Databricks + Kaggle)

O objetivo é construir um pipeline de dados completo na nuvem utilizando **Databricks**, aplicando práticas engenharia de dados, modelagem, análise e documentação.

## Objetivo do Projeto

Criar um pipeline que permita fazer:

- Ingestão de dados brutos de e-commerce (Kaggle)
- Processamento (Bronze → Silver → Gold)
- Modelagem dimensional (Esquema Estrela)
- Construção de um Data Lakehouse
- Análise de vendas, clientes e produtos
- Aplicação de RFM (Recency, Frequency, Monetary)
- Identificar produtos sazonais

Todo o pipeline será documentado e as análises finais respondem às perguntas de negócio definidas no `/docs/objetivo.md`.

## Dataset Utilizado

**Ecommerce Data – Kaggle**  
Link: https://www.kaggle.com/datasets/carrie1/ecommerce-data  
Licença: Domínio público (CC0)

O dataset contém transações reais de um e-commerce internacional, com informações de:
- clientes  
- data de compra  
- produtos  
- quantidade  
- preço unitário  
- cancelamentos  

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

