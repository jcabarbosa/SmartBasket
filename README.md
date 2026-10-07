# 🛒 SmartBasket: Monitorização Inteligente de Preços de Retalho

Projeto desenvolvido no âmbito da unidade curricular de **Integração de Sistemas de Informação (ISI)** — Licenciatura em Engenharia de Sistemas Informáticos (UPCA, 2026/27).

## 📌 Descrição do Projeto
O **SmartBasket** é uma solução de engenharia de dados orientada ao ciclo **ETL (Extract, Transform, Load)**, concebida para a recolha heterogénea, normalização e monitorização contínua de preços de bens de consumo em múltiplos retalhistas.

O ecossistema implementa:
* **Recolha Heterogénea (E):** Ingestão de dados a partir de fluxos contínuos/API REST no Node-RED (JSON), extração remota de catálogos via Servidor FTP (CSV) e ficheiros locais de referência (XML/YAML).
* **Processamento e Normalização (T):** Tratamento no **Pentaho Data Integration (Kettle)** com recurso a Expressões Regulares (Regex) para limpeza e uniformização de nomes e unidades de medida, filtragem de indisponibilidades, lookups e cálculos de variação de preços.
* **Persistência, Orquestração e Visualização (L):** Carga relacional em **PostgreSQL**, orquestração automatizada por **Jobs (.kjb)** com notificações por e-mail e disponibilização de métricas em dashboards **Grafana** sobre infraestrutura contentorizada em **Docker**.
