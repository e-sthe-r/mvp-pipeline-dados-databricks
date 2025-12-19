# Autoavaliação – MVP Pipeline de Dados de Vendas

## 1. Alcance das Metas
O objetivo principal deste trabalho foi construir um pipeline completo de dados, utilizando tecnologias em nuvem, capaz de transformar dados transacionais em informações analíticas relevantes para tomada de decisão.

Ao final do projeto, considera-se que os objetivos propostos foram **atingidos**, uma vez que foi possível:

- Elaborar um pipeline estruturado nas etapas Bronze → Silver → Gold
- Fazer a absorção de dados de um banco transacional (OLTP)
- Manipular, uniformizar e validar os dados por todo o pipeline
- Construir um modelo dimensional em Esquema Estrela
- Criar um catálogo de dados detalhando colunas, domínios e origens
- Fazer análises de negócio consistentes com as questões definidas desde o inicio

As dúvidas de negócio ligadas a vendas, produtos, clientes, território e tempo foram respondidas de modo coerente pelo modelo analítico edificado. Entretanto, ao longo do desenvolvimento, algumas limitações e desafios foram identificados.

---

## 2. Limitações e Dificuldades Encontradas

###2.1 Segmentação avançada de clientes por perfil de produto

Uma análise inicialmente considerada, mas não totalmente explorada, foi a segmentação de clientes com base nos tipos de produtos adquiridos, com o objetivo de criar perfis mais detalhados, como:

- Clientes focados em produtos de alto valor agregado
- Clientes focados em itens de alto giro
- Clientes com comportamento sazonal de compra

Embora a base de dados permita identificar os produtos comprados por cliente, essa análise exigiria:

- Criação de métricas derivadas adicionais
- Classificação dos produtos por categorias estratégicas
- Regras de negócio mais complexas para definição de perfis

Dado o escopo do MVP e o foco principal na construção do pipeline e do modelo analítico, optou-se por priorizar a estabilidade do modelo dimensional e a resposta às perguntas centrais de negócio, deixando essa segmentação como uma possível evolução futura do projeto.

### 2.2 Tratamento de dados inconsistentes

Os dados retirados do banco de dados transacional exibiram inconsistências, sobretudo valores mostrados como texto `"NULL"` em colunas numéricas. Essa situação demandou atenção extra nas fases de ingestão e tratamento, causando ajustes cuidadosos nas camadas Bronze e Silver, para assegurar compatibilidade de tipos e a integridade dos dados.

A complicação enfatizou a relevância de uma camada de tratamento intermediário bem delineada, impedindo que falhas na qualidade se estendessem para a camada analítica.

---

### 2.3 Alinhamento entre documentação e implementação

Um outro percalço foi garantir que a documentação completa espelhasse exatamente o que foi implementado no pipeline, sem deixar de lado colunas, métricas ou regras existentes na pipeline.

Essa atenção minuciosa demandou revisões repetidas entre notebooks, tabelas criadas e arquivos de documentação, o que também contribuiu para um trabalho mais consistente e preciso.

---

##3. Adaptação à plataforma Databricks

Por se tratar de uma plataforma nova, que nunca havia trabalhado antes, foi necessário um período de adaptação, além de utilizar a versão gratuita do Databricks mudar um pouco a forma de gerenciar catálogos, schemas e volumes, além da devida atenção ao uso correto dos caminhos de armazenamento e na criação de tabelas Delta.
Apesar das limitações, a plataforma funcionou bem, montando o pipeline e realizando as análises de maneira correta.

---

## 3. Aprendizados

Foi possível evoluir bastante na montagem desse MVP, pois porjetos como esse são essenciais para entrar em contato com ferramentas novas e por em prática o que é aprendido nas matérias, como:

- Como é um pipeline de dados end-to-end, na prática.
- A clara separação entre dados crus, tratados e aqueles analíticos
- Usar um modelo dimensional em Esquema Estrela, como ele funciona
- Documentar ser algo muito importante, além de boas práticas é a base da governança de dados
- Entendi como transformar dados do dia a dia em informações valiosas para os negócios

Ademais, ficou claro a importância de dados de boa qualidade, começando desde o início, e o efeito que erros podem causar depois.

---

## 4. Possíveis Evoluções Futuras

Para agregar ao que já foi feito, algumas melhorias podem ser pensadas, como:

- Inclusão de métricas de margem e lucro
- Criação de indicadores de desempenho (KPIs) mais avançados
- Implementação de análises de cohort e ciclo de vida do cliente
- Automatizar o pipeline usando agendamentos
- Integração com ferramentas de visualização, dashboards

Essas extensões contribuiriam ainda mais o valor analítico do pipeline construído.

---

## 5. Considerações Finais

O MVP desenvolvido demonstrou a viabilidade técnica e analítica de um pipeline de dados completo, desde a ingestão até a análise final, atendendo aos requisitos propostos na disciplina. O projeto firmou conceitos fundamentais da engenharia e análise de dados, mostrando a importância da organização, gestão e modelagem, para extrair valor dos dados.
