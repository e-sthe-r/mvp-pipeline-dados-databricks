# Catálogo de Dados – MVP Pipeline de Dados de Vendas

## 1. Introdução

Este Catálogo de Dados documenta todas as tabelas analíticas geradas na **camada Gold** do pipeline de dados desenvolvido nesse MVP, a partir do banco transacional **AdventureWorks2017**.

O objetivo deste catálogo é descrever detalhadamente cada tabela e coluna, informar tipo de dado, significado e uso analítico, apoiar governança, rastreabilidade e entendimento do modelo, além de garantir transparência sobre a origem e transformação dos dados

O modelo segue o padrão **Esquema Estrela**, composto por uma tabela fato central e quatro tabelas dimensão.

---

## 2. Visão Geral do Modelo Analítico

### Camada: Gold

### Tipo: Modelo Dimensional (Esquema Estrela)

**Tabelas existentes:**

* `fact_sales`
* `dim_product`
* `dim_customer`
* `dim_territory`
* `dim_date`

---

## 3. Tabela Fato

## 3.1 `fact_sales`

Tabela central do modelo analítico, responsável por armazenar os eventos de venda.

### Granularidade

Uma linha por **item de pedido vendido** (nível de detalhe do pedido).

### Origem dos Dados

* `Sales.SalesOrderHeader`
* `Sales.SalesOrderDetail`

### Colunas

| Coluna                  | Tipo          | Descrição                                                |
| ----------------------- | ------------- | -------------------------------------------------------- |
| `sales_order_id`        | int           | Identificador do pedido de venda                         |
| `sales_order_detail_id` | int           | Identificador do item do pedido                          |
| `order_date`            | date          | Data em que o pedido foi realizado                       |
| `customer_id`           | int           | Identificador do cliente                                 |
| `product_id`            | int           | Identificador do produto                                 |
| `territory_id`          | int           | Identificador do território de venda                     |
| `order_qty`             | int           | Quantidade vendida do produto                            |
| `unit_price`            | decimal(18,2) | Preço unitário do produto                                |
| `line_total`            | decimal(18,2) | Valor total da linha de venda (`order_qty * unit_price`) |

### Métricas Principais

* Receita total
* Quantidade vendida
* Ticket médio
* Receita por cliente, produto, território e período

---

## 4. Tabelas Dimensão

---

## 4.1 `dim_product`

Dimensão responsável por armazenar informações descritivas dos produtos.

### Origem dos Dados

* `Production.Product`
* `Production.ProductSubcategory`
* `Production.ProductCategory`

### Colunas

| Coluna                   | Tipo          | Descrição                          |
| ------------------------ | ------------- | ---------------------------------- |
| `product_id`             | int           | Identificador do produto           |
| `product_name`           | string        | Nome do produto                    |
| `product_number`         | string        | Código do produto                  |
| `standard_cost`          | decimal(18,2) | Custo padrão do produto            |
| `list_price`             | decimal(18,2) | Preço de tabela                    |
| `sell_start_date`        | date          | Data de início da comercialização  |
| `sell_end_date`          | date          | Data de término da comercialização |
| `product_subcategory_id` | int           | Identificador da subcategoria      |
| `subcategory_name`       | string        | Nome da subcategoria               |
| `product_category_id`    | int           | Identificador da categoria         |
| `category_name`          | string        | Nome da categoria                  |

### Uso Analítico

* Análise de faturamento por produto
* Análise por categoria e subcategoria
* Identificação de produtos estratégicos
* Análise de sazonalidade

---

## 4.2 `dim_customer`

Dimensão responsável por armazenar informações descritivas dos clientes.

### Origem dos Dados

* `Sales.Customer`
* `Person.Person`
* `Person.EmailAddress`

### Colunas

| Coluna          | Tipo   | Descrição                                   |
| --------------- | ------ | ------------------------------------------- |
| `customer_id`   | int    | Identificador do cliente                    |
| `first_name`    | string | Primeiro nome do cliente                    |
| `last_name`     | string | Sobrenome do cliente                        |
| `person_type`   | string | Tipo de cliente (individual ou corporativo) |
| `email_address` | string | Endereço de e-mail do cliente               |

### Uso Analítico

* Identificação de clientes recorrentes
* Análise de clientes de alto valor financeiro
* Segmentação de clientes
* Programas de fidelidade

---

## 4.3 `dim_territory`

Dimensão geográfica, responsável por informações territoriais das vendas.

### Origem dos Dados

* `Sales.SalesTerritory`

### Colunas

| Coluna                | Tipo   | Descrição                    |
| --------------------- | ------ | ---------------------------- |
| `territory_id`        | int    | Identificador do território  |
| `territory_name`      | string | Nome do território           |
| `country_region_code` | string | Código do país               |
| `territory_group`     | string | Grupo regional do território |

### Uso Analítico

* Análise de faturamento por região
* Comparação de desempenho territorial
* Análise de ticket médio por território

---

## 4.4 `dim_date`

Dimensão de tempo, utilizada para análises históricas e temporais.

### Origem dos Dados

* Datas derivadas do campo `order_date` da tabela de vendas

### Colunas

| Coluna       | Tipo   | Descrição     |
| ------------ | ------ | ------------- |
| `date`       | date   | Data completa |
| `year`       | int    | Ano           |
| `month`      | int    | Mês (1–12)    |
| `month_name` | string | Nome do mês   |
| `day`        | int    | Dia do mês    |

### Uso Analítico

* Análise temporal de vendas
* Identificação de sazonalidade
* Comparação de períodos

---

## 5. Relacionamentos do Modelo

Todos os relacionamentos seguem o padrão **N:1**, partindo da tabela fato para as dimensões:

* `fact_sales.product_id` → `dim_product.product_id`
* `fact_sales.customer_id` → `dim_customer.customer_id`
* `fact_sales.territory_id` → `dim_territory.territory_id`
* `fact_sales.order_date` → `dim_date.date`

---

## 6. Governança e Rastreabilidade

* Todos os dados foram extraídos do **AdventureWorks2017**
* As transformações foram realizadas via pipeline **Bronze → Silver → Gold**
* O catálogo garante entendimento completo do modelo
* Permite auditoria, manutenção e expansão futura

---

## 7. Considerações Finais

Este Catálogo de Dados consolida o entendimento do modelo analítico construído, assegurando clareza sobre a estrutura, significado e uso de cada dado disponível para análise.
