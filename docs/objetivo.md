# Objetivo do MVP – Pipeline de Dados de Vendas

# 1. Objetivo Geral

Desenvolver um pipeline completo de dados, estruturado nas camadas **Bronze → Silver → Gold**, a partir de um banco de dados transacional, com o objetivo de transformar dados operacionais em informações analíticas.

- Ingerir dados brutos provenientes de um banco OLTP  
- Organizar e transformar esses dados para fins analíticos  
- Construir um modelo dimensional (Esquema Estrela)  
- Avaliar a qualidade dos dados em cada etapa do processo  
- Realizar análises exploratórias e de negócio  
- Identificar padrões de vendas, produtos e clientes ao longo do tempo   

# 2. Perguntas de Negócio

O MVP busca responder às seguintes questões a partir do modelo analítico construído:

## 2.1 Vendas e Países
1. Quais territórios e países geram maior volume de receita?  
2. Qual é o ticket médio de vendas por território?  
3. Como as vendas evoluem ao longo do tempo (anos e meses)?

## 2.2 Produtos
4. Quais produtos e categorias geram maior faturamento?  
5. Quais produtos apresentam maior volume de vendas?  
6. Existem produtos ou categorias com comportamento sazonal ao longo do ano?

## 2.3 Clientes
7. Quais clientes apresentam maior recorrência de compras?  
8. Quais clientes geram maior valor financeiro ao longo do tempo?  
9. Como o comportamento de compra dos clientes varia entre diferentes períodos?

# 3. Escopo Técnico do MVP

O projeto engloba:

### 3.1 Fonte dos Dados
O dataset utilizado é o **AdventureWorks2017**, um banco de dados transacional (OLTP) disponibilizado pela Microsoft para fins educacionais. Os dados representam operações de uma empresa fictícia de vendas, contendo informações sobre pedidos, produtos, clientes, territórios e datas.

### 3.2 Busca e Coleta dos Dados
As tabelas relevantes do banco AdventureWorks2017 serão extraídas do SQL Server e exportadas para arquivos CSV.  
Esses arquivos serão então carregados na plataforma Databricks, constituindo a camada **Bronze** do pipeline.


### 3.3 Pipeline de Dados na Plataforma Databricks
O pipeline será implementado na plataforma **Databricks**, utilizando principalmente **SQL** e, quando necessário, **Python**, seguindo as seguintes camadas:

- **Bronze:** ingestão dos dados brutos, sem alterações estruturais  
- **Silver:** limpeza, padronização, ajustes de tipos, validações e enriquecimentos  
- **Gold:** construção do modelo dimensional (Esquema Estrela) e tabelas analíticas  


### 3.4 Modelagem dos Dados
A partir do banco transacional, será construído um **modelo analítico em Esquema Estrela**

### 3.5 Análises
As análises realizadas incluem:

- Avaliação da qualidade dos dados (nulos, inconsistências, valores extremos)  
- Análises de vendas por tempo, produto e território  
- Identificação de padrões de comportamento de clientes  
- Análise de recorrência e valor dos clientes ao longo do tempo  
- Identificação de produtos e categorias com comportamento sazonal  

As respostas às perguntas de negócio serão apresentadas em formato de **relatórios descritivos**, em linguagem natural, acompanhadas das consultas e resultados obtidos.

### 3.6 Documentação e Governança de Dados
O projeto inclui documentação completa, composta por:

- Catálogo de dados, descrevendo cada coluna das tabelas analíticas  
- Descrição da modelagem e da linhagem dos dados  
- Relatórios de análise  
- Autoavaliação do projeto  

Essa documentação visa garantir transparência, rastreabilidade e compreensão do pipeline desenvolvido.

# 4. Dataset Utilizado

**AdventureWorks2017**  
Fonte: Microsoft  
Tipo: Banco de dados transacional (OLTP)  
Uso: Educacional  

Os dados serão extraídos do SQL Server e transformados para fins analíticos no contexto deste MVP.



