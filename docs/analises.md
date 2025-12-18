# Análises – MVP Pipeline de Dados de Vendas
**1. Introdução**

O objetivo dessa fase é responder às perguntas de negócio definidas na etapa de planejamento, utilizando exclusivamente dados tratados, modelados e validados ao longo das camadas Bronze → Silver → Gold.

As análises foram realizadas na plataforma Databricks a partir de dados tratados e modelados no próprio pipeline desenvolvido nesse trabalho, com o auxílio de consultas SQL, o que garante rastreabilidade, reprodutibilidade e clareza nos resultados obtidos.

**2. Visão Geral dos Dados**

A base analítica é composta por uma tabela fato central (fact_sales) e quatro tabelas dimensão:

- `dim_product`

- `dim_customer`

- `dim_territory`

- `dim_date`

Segue o padrão "Esquema Estrela", permitindo boas análises sobre vendas, produtos, clientes, território e tempo. A tabela fato concentra métricas quantitativas como:

- Quantidade vendida **(order_qty)**

- Preço unitário **(unit_price)**

- Valor total da linha de venda **(line_total)**

**3. Análises de Vendas por Território**

  *3.1 Territórios com maior volume de receita*

A análise de faturamento por território mostrou diferenças significativas entre as regiões que a base de dados abrangia. Conforme observado pode ser observado na imagem "nb_04_analises_03_receita_por_territorio", o território Southwest (Sudoeste-EUA) apresentou o maior volume de receita total, ultrapassando 24 milhões em faturamento. Em seguida, destacam-se Canada (Canadá) e Northwest (Noroeste-EUA), ambos com valores superiores a 16 milhões.

Por outro lado, territórios como Germany (Alemanha) e Northeast (Nordeste-EUA) apresentaram os menores volumes de receita dentro do conjunto analisado. Com esses resultados é possível identificar os mercados mais consolidados e com maior participação no faturamento global, fornecendo subsídios para decisões estratégicas como:

- Priorização de investimentos

- Expansão comercial

- Definição de estratégias regionais de vendas

*3.2 Ticket médio por território*

Ao analisar o ticket médio por território, foi possível identificar um comportamento diferente do observado no volume total de receita, regiões com menor volume de vendas, porém com valor médio por pedido mais elevado. O território Central (EUA) apresentou o maior ticket médio com valor superior a $1.350,00, conforme evidenciado na imagem "nb_04_analises_04_ticket_medio_territorio", mesmo não figurando entre os maiores em faturamento total.

Em contrapartida, territórios como Southwest, embora liderem em faturamento total, possuem ticket médio inferior, em torno de $943,00, indicando maior volume de pedidos com valores individuais menores.

O que pode facilitar para traçar perfis de consumidores diferentes, produtos com maior valor agregado, atingindo, assim, possíveis estratégias de precificação utilizadas para maximizar a lucratividade e a competitividade, levando em consideração diversos fatores locais.

**4.Evolução das Vendas ao Longo do Tempo**

A análise temporal das vendas, considerando ano e mês, com evidências em "nb_04_analises_05_evolucao_vendas_tempo" e "nb_04_analises_05_evolucao_vendas_tempo_planilha", indicou padrões de crescimento e variação ao longo dos anos e meses. Por exemplo, no ano de 2011, observa-se um aumento significativo da receita a partir do mês de julho, que atinge aproximadamente 204 mil, mantendo-se elevada nos meses seguintes. Já em dezembro de 2011, a receita alcança um pico superior a 1,3 milhão, indicando forte concentração de vendas no final do ano.

Em 2012, esse padrão se repete, com crescimento progressivo ao longo do ano e picos relevantes nos meses de junho e julho, reforçando a existência de sazonalidade associada a períodos específicos do calendário. O que indica e reforça que em datas festivas e comemorações de fim de ano as pessoas se dispõe a fazer mais compras, sendo assim, como é feito no Brasil há tentativas do melhor implementar datas comemorativas ao longo de todo ano afim de aumentar as vendas.

**5. Análises de Produtos**
*5.1 Produtos com maior faturamento*

A análise de faturamento por produto evidenciou que os modelos da linha *Mountain-200* concentram a maior parte da receita do negócio. Em especial, os produtos *Mountain-200 Black*, *38* e *Mountain-200 Black*, *42* apresentaram faturamento individual superior a 400 mil, conforme ilustrado na evidência "nb_04_analises_07_produtos_mais_vendidos".

Esse resultado indica que o faturamento elevado desses produtos não está associado a um alto volume de vendas, mas sim a um valor unitário significativamente maior, característica típica de produtos de maior valor agregado, como bicicletas de alto desempenho.

Quando comparados a produtos de giro rápido e baixo preço unitário, como *AWC Logo Cap ou Water Bottle – 30 oz*, observa-se um comportamento distinto,
enquanto esses últimos lideram em quantidade vendida, os produtos da linha *Mountain-200* são responsáveis por uma parcela desproporcional da receita total.

Esse padrão sugere que o portfólio do negócio apresenta forte concentração de faturamento em poucos produtos premium, o que traz implicações estratégicas importantes:

- Risco de dependência excessiva de uma linha específica de produtos
- Necessidade de atenção especial à cadeia de suprimentos desses itens, dado seu impacto financeiro
- Oportunidade de estratégias de cross-selling, utilizando produtos de alto giro para impulsionar a venda de produtos premium

Além disso, o destaque recorrente de diferentes variações do mesmo modelo (tamanhos e cores da linha Mountain-200) indica que o sucesso não está limitado a um único SKU isolado, mas sim a uma família de produtos bem posicionada no mercado, reforçando a importância estratégica dessa categoria para o negócio.

*5.2 Produtos mais vendidos em quantidade*

Ao observar a quantidade vendida, tanto na imagem "nb_04_analises_08_produtos_sazonalidade_produtos", quanto da planilha "nb_04_analises_08_produtos_sazonalidade_produtos_planilha", nota-se que os produtos mais vendidos nem sempre são os mais lucrativos, como AWC Logo Cap e Water Bottle – 30 oz lideram em unidades vendidas, com volumes superiores a 6.000 unidades, apesar de não figurarem entre os produtos com maior faturamento. 

Ou seja, produtos de menor valor unitário podem ter alto giro, enquanto produtos de maior valor agregado, como bicicletas, geram maior impacto financeiro mesmo com menor volume de vendas. Isso destaca a diferença entre volume e valor financeiro, essa distinção é essencial, permitindo entender a gestão de estoque que pode ser feita, a estratégia de preço, avaliando a margem de lucro dos produtos no mercado.

*5.3 Sazonalidade de produtos*

Com a análise mensal por produto foi possível perceber comportamentos sazonais com determinados produtos, com concentrações de vendas em determinados meses. Um bom exemplo disso foi o produto *Produto Classic Vest, M*, os meses com maior faturamento foram:

- Maio: 15.541,52
- Março: 13.250,70
- Junho: 12.328,16
- Julho: 10.809,98

Observa-se que o pico de vendas ocorre principalmente entre março e julho, indicando forte demanda no primeiro semestre do ano.

Já os meses com menor faturamento foram:

- Abril: 1.143,00
- Fevereiro: 1.143,00
- Novembro: 4.254,50

Esse comportamento sugere que o produto sofre queda significativa de demanda no início e no final do ano, caracterizando um padrão sazonal consistente.

O produto Classic Vest, S apresentou comportamento semelhante, porém com valores absolutos mais elevados, indicando maior procura de mercado em relação ao tamanho M.

Meses com maior faturamento:

- Maio: 25.841,45
- Março: 25.277,10
- Junho: 18.326,70
- Julho: 16.834,05

Assim como no tamanho M, o período entre março e julho concentra os maiores volumes de receita, reforçando a existência de sazonalidade recorrente para essa categoria de produto.

Meses com menor faturamento:

- Fevereiro: 698,50
- Abril: 1.524,00
- Novembro: 7.984,24

Informações como essa são muito valiosas para planejamento de estoque, otimização de logística, campanhas de marketing sazonais e até mesmo antecipação de demandas.

OBS: Essa análise considera todos os anos disponíveis na base, e o padrão se mantém quando observados os dados agregados por mês.

**6. Análises de Clientes (Clientes Recorrente x Clientes de Valor Financeiro)**

A recorrência mostrou os clientes com maior frequência de pedidos ao longo do tempo, clientes recorrentes tendem a representar maior fidelização, menor custo de aquisição, base estável de receita.

Ao analisar o valor total gerado por cliente, foi possível identificar clientes com alto impacto financeiro no negócio, mesmo que não sejam os mais recorrentes. 

Fazendo um paralelo com mercado brasileiro, serviços como:

- Assaí Atacadista
- Pão de Açúcar Mais
- Droga Raia / Drogasil

Esses mercados usam muito programas de fidelidade, frequentam a base de clientes recorrentes, e transitam muito entre clientes com compras pequenas e semanais (que podem gearar mais lucro, por sempre estarem frequentando e vendo novas ofertas) e clientes menos frequentes, mas que fazem grandes compras em um único ticket.

Portanto, os resultados da análise ilustrada no meu modelo estrela mostram a existência de dois perfis distintos de clientes, os altamente recorrentes e os de alto valor financeiro, que podem variar entre quem gera mais receita e volume de vendas. Com essa informação é essencial para estratégias de programas de fidelidade, segmentação de clientes e estratégias de atendimento personalizado.

**7. Validação do Modelo Analítico**

A validação final do modelo confirmou:

- 121.317 registros na tabela fato
- 1.919 clientes distintos
- 266 produtos distintos
- 10 territórios distintos

Ou seja, a integridade entre a tabela fato e as dimensões, consistência das chaves de relacionamento e capacidade do modelo em responder às perguntas de negócio propostas. O uso do "Esquema Estrela" mostrou-se adequado para o cenário analisado, oferecendo simplicidade, desempenho e clareza analítica.

**8. Considerações Finais**

As análises realizadas atenderam aos objetivos definidos no início do projeto, revelando assim a importância de um pipeline bem estruturado. 

Foi possível identificar:

- Sazonalidade clara de produtos
- Diferenças regionais de receita e ticket médio
- Clientes recorrentes e clientes de alto valor
- Padrões consistentes de comportamento ao longo do tempo

O MVP desenvolvido atendeu grande parte dos objetivos propostos.
