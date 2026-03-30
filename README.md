# 📊 Performance Comercial e Operacional — Marketplace Olist

Projeto de análise de dados com foco em performance comercial, logística e satisfação do cliente, utilizando dados reais de um marketplace brasileiro.

---

## 🔗 Dashboard

👉 [Acessar Dashboard no Looker Studio](https://lookerstudio.google.com/reporting/50d89fd3-e4c8-497a-b73e-06670a0ddfed)

---

## 🎯 Contexto

A [Olist](https://olist.com/) é uma plataforma brasileira de e-commerce que conecta lojistas a múltiplos marketplaces. Este projeto analisa dados reais de pedidos, produtos, clientes e avaliações da plataforma entre 2016 e 2018, com o objetivo de responder perguntas estratégicas sobre o negócio.

---

## ❓ Perguntas de Negócio

Este dashboard foi construído para responder:

- **A empresa está vendendo bem?** — Evolução do volume de pedidos ao longo do tempo
- **Está lucrando?** — Receita total, ticket médio e custo logístico
- **O frete está alto?** — Análise do frete por categoria e sua proporção sobre a receita
- **Qual produto vende mais?** — Ranking de categorias por receita e quantidade
- **Como as vendas evoluem no tempo?** — Sazonalidade e tendência de crescimento
- **De onde vêm os clientes?** — Distribuição geográfica dos pedidos por estado
- **Os clientes estão satisfeitos?** — Nota média e distribuição das avaliações

---

## 📁 Fonte de Dados

Os dados utilizados são públicos e estão disponíveis no Kaggle:

👉 [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

### Tabelas utilizadas

| Tabela | Descrição |
|--------|-----------|
| `olist_orders_dataset` | Pedidos, status e datas |
| `olist_order_items_dataset` | Itens dos pedidos, preços e frete |
| `olist_products_dataset` | Produtos e categorias |
| `olist_customers_dataset` | Clientes e localização |
| `olist_order_reviews_dataset` | Avaliações e notas dos pedidos |
| `olist_order_payments_dataset` | Formas de pagamento |

---

## 🔗 Modelagem e Relacionamento entre Tabelas

As tabelas foram relacionadas através de mesclagens (JOINs) no Looker Studio:

- `olist_order_items` ligada a `olist_orders` via order_id
- `olist_order_items` ligada a `olist_products` via product_id
- `olist_orders` ligada a `olist_customers` via customer_id
- `olist_orders` ligada a `olist_order_reviews` via order_id
- `olist_orders` ligada a `olist_order_payments` via order_id

Todas as mesclagens utilizam **JOIN Interno (Inner Join)**, retornando apenas registros com correspondência em ambas as tabelas.

---

## 📐 Métricas Criadas

| Métrica | Fórmula | Fonte |
|---------|---------|-------|
| Receita Total | SUM(CAST(price AS NUMBER)) | order_items |
| Frete Total | SUM(freight_value) | order_items |
| Frete Médio | AVG(freight_value) | order_items |
| Ticket Médio | SUM(price) / COUNT(order_id) | order_items |
| Total de Pedidos | COUNT(order_id) | orders |
| % Frete sobre Receita | (Frete Total / Receita Total) * 100 | order_items |
| Nota Média | AVG(review_score) | order_reviews |

---

## 📊 Estrutura do Dashboard

O dashboard é composto por 4 páginas, cada uma com um tema analítico específico.

### Página 1 — Visão Executiva

Visão geral do negócio com os principais indicadores financeiros e operacionais.

- 5 cards com KPIs: Receita Total, Frete Médio, Frete Total, Total de Pedidos e Ticket Médio
- Gráfico de linha: Evolução da Receita Mensal (set/2016 a set/2018)
- Tabela: Status dos Pedidos
- Gráfico de rosca: Distribuição por Forma de Pagamento

### Página 2 — Análise de Produtos

Análise de performance por categoria de produto.

- Gráfico de barras: Top 10 categorias por Receita Total
- Tabela com heatmap: Top 10 categorias por Quantidade Vendida
- Gráfico de pizza: Frete Total por Categoria
- Gráfico de barras: % do Frete sobre a Receita por Categoria

### Página 3 — Análise Geográfica

Distribuição dos pedidos por estado brasileiro.

- Mapa geográfico do Brasil com intensidade de pedidos por estado
- Ranking de todos os estados por volume de pedidos

### Página 4 — Satisfação do Cliente

Análise das avaliações dos clientes.

- Card: Nota Média Geral
- Gráfico de barras: Distribuição das Avaliações (notas 1 a 5)
- Gráfico de linha: Evolução da Nota Média ao longo do tempo

---

## 💡 Principais Insights

### Comercial
- A Receita Total no período foi de **R$ 13,57 milhões**, com Ticket Médio de **R$ 120,46**
- As vendas cresceram de forma consistente entre 2016 e 2018, com pico em **agosto de 2018**
- **73,9%** dos pagamentos foram realizados via cartão de crédito

### Produtos
- A categoria **beleza_saude** lidera em receita, enquanto **cama_mesa_banho** lidera em quantidade vendida
- O frete representa em média **~7% da receita** nas categorias com maior custo logístico

### Geográfico
- **São Paulo** concentra a maior parte dos pedidos com **41.746 pedidos**
- Os estados do Sudeste (SP, RJ, MG) dominam o volume de pedidos

### Satisfação
- Nota média geral de **4,09 / 5,00** — alta satisfação dos clientes
- Mais de **60% dos pedidos** receberam nota máxima (5)
- A satisfação se manteve estável ao longo de todo o período

### Operacional
- **96,5 mil pedidos entregues** — taxa de entrega de **~97%**
- Apenas **625 pedidos cancelados** — operação eficiente

---

## 🛠️ Ferramentas

| Ferramenta | Uso |
|------------|-----|
| **Looker Studio** | Construção do dashboard, mesclagens e campos calculados |
| **Google Sheets** | Armazenamento e conexão das fontes de dados |
| **Kaggle** | Fonte dos dados públicos |

---

## 📌 Sobre este projeto

Este projeto foi desenvolvido como parte do meu portfólio de transição para a área de Dados, com foco em análise de e-commerce usando ferramentas de BI. O objetivo foi aplicar conceitos de modelagem de dados, criação de métricas e storytelling visual para extrair insights acionáveis de dados reais.

---

## 👩‍💻 Autora

**Bethina Alvernaz**

[LinkedIn](https://linkedin.com/in/bethinaalvernaz) • [GitHub](https://github.com/bethinaalvernaz)
