# Modelagem dos Dados – MVP Pipeline de Dados de Vendas

## 1. Visão Geral da Modelagem

A modelagem de dados deste MVP foi construída com base em um **modelo dimensional no padrão Esquema Estrela**, a partir de um banco de dados transacional (OLTP) **AdventureWorks2017**.

O modelo analítico foi desenvolvido na camada **Gold** do pipeline e é composto por:

* **1 tabela fato**, responsável por armazenar as métricas de negócio
* **4 tabelas dimensão**, responsáveis por fornecer contexto descritivo para as análises

Essa abordagem permite análises eficientes de vendas sob diferentes perspectivas, como produto, cliente, território e tempo.

---

## 2. Contexto da Modelagem

O banco de dados AdventureWorks2017 possui uma modelagem **normalizada**, típica de sistemas transacionais (OLTP), entretanto, esse tipo de modelagem não é ideal para diagnósticos analíticos e históricos, pois:

* Exige múltiplos *joins* complexos
* Possui tabelas altamente normalizadas
* Não é otimizada para consultas agregadas

Dessa forma, optou-se pela construção de um **modelo dimensional em Esquema Estrela**, com foco no processo de **vendas**, permitindo:

* Facilidade de entendimento do modelo
* Melhor desempenho em consultas analíticas
* Clareza na separação entre as métricas e os atributos descritivos
* Adequação às perguntas de negócio definidas no objetivo do MVP

---

## 3. Modelo Dimensional – Esquema Estrela

O modelo analítico possui uma tabela fato central (`fact_sales`) conectada a quatro dimensões:

* `dim_product`
* `dim_customer`
* `dim_territory`
* `dim_date`

---

## 4. Tabela Fato

### 4.1 `fact_sales`

A tabela `fact_sales` representa o **evento central de negócio**, que é a venda de um produto para um cliente, em um determinado território e data.

#### Granularidade

* **Linha de item do pedido** (nível mais detalhado da venda)

#### Principais características

* Contém métricas quantitativas aditivas
* Possui chaves estrangeiras para todas as dimensões
* Permite análises por produto, cliente, território e tempo

#### Principais atributos

* **sales_order_id** – identificador do pedido
* **sales_order_detail_id** – identificador do item do pedido
* **order_date** – data da venda
* **customer_id** – referência ao cliente
* **product_id** – referência ao produto
* **territory_id** – referência ao território
* **order_qty** – quantidade vendida
* **unit_price** – preço unitário do produto
* **line_total** – valor total da linha de venda

> O campo **line_total** representa o valor financeiro total da venda do item, calculado a partir da quantidade vendida e do preço unitário, sendo uma métrica fundamental para análises de faturamento.

#### Origem dos dados (OLTP)

* `Sales.SalesOrderHeader`
* `Sales.SalesOrderDetail`

---

## 5. Tabelas Dimensão

### 5.1 `dim_product`

Dimensão responsável por armazenar informações descritivas dos produtos comercializados.

#### Principais atributos

* **product_id** – identificador do produto
* **product_name** – nome do produto
* **product_number** – código do produto
* **standard_cost** – custo padrão
* **list_price** – preço de venda
* **sell_start_date** – data de início de venda
* **sell_end_date** – data de término de venda
* **product_subcategory_id** – identificador da subcategoria
* **subcategory_name** – nome da subcategoria
* **product_category_id** – identificador da categoria
* **category_name** – nome da categoria

#### Origem dos dados (OLTP)

* `Production.Product`
* `Production.ProductSubcategory`
* `Production.ProductCategory`

---

### 5.2 `dim_customer`

Dimensão responsável por armazenar informações descritivas dos clientes.

#### Principais atributos

* **customer_id** – identificador do cliente
* **first_name** – primeiro nome
* **last_name** – sobrenome
* **person_type** – tipo de cliente
* **email_address** – e-mail de contato

#### Origem dos dados (OLTP)

* `Sales.Customer`
* `Person.Person`
* `Person.EmailAddress`

---

### 5.3 `dim_territory`

Dimensão geográfica, utilizada para análises regionais e territoriais.

#### Principais atributos

* **territory_id** – identificador do território
* **territory_name** – nome do território
* **country_region_code** – código do país
* **territory_group** – agrupamento regional

#### Origem dos dados (OLTP)

* `Sales.SalesTerritory`

---

### 5.4 `dim_date`

Dimensão de tempo, utilizada para análises históricas e agregações temporais.

#### Principais atributos

* **date** – data completa
* **year** – ano
* **month** – número do mês
* **month_name** – nome do mês
* **day** – dia do mês

#### Origem dos dados

* Datas derivadas do campo **order_date** da tabela fato (`fact_sales`)

---

## 6. Relacionamentos do Modelo

O modelo apresenta relacionamentos do tipo **N:1**, partindo da tabela fato para as dimensões:

* `fact_sales.product_id` → `dim_product.product_id`
* `fact_sales.customer_id` → `dim_customer.customer_id`
* `fact_sales.territory_id` → `dim_territory.territory_id`
* `fact_sales.order_date` → `dim_date.date`

Esses relacionamentos garantem consistência e integridade analítica do modelo.

---

## 7. Justificativa da Modelagem

A escolha do **Esquema Estrela** se justifica por:

* Melhor desempenho em consultas analíticas
* Facilidade de entendimento do modelo
* Adequação às perguntas de negócio propostas no MVP
* Clareza na separação entre métricas e atributos descritivos
* Facilidade de manutenção e expansão futura

---

## 8. Considerações Finais

O modelo dimensional construído na camada **Gold** serve como base para todas as análises realizadas no projeto, permitindo responder às perguntas de negócio de forma clara, consistente e performática.

Detalhes adicionais sobre domínios, tipos de dados, valores esperados e qualidade das informações estão documentados no **Catálogo de Dados**.

