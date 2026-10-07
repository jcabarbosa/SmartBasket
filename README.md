# SmartBasket: Monitorização Inteligente de Preços de Retalho

Projeto desenvolvido no âmbito da unidade curricular de Integração de Sistemas de Informação (ISI) da Licenciatura em Engenharia de Sistemas Informáticos (UPCA, 2026/27).

## Sobre o Projeto
O SmartBasket é um pipeline de ETL (Extract, Transform, Load) desenhado para recolher, padronizar e acompanhar a evolução dos preços de bens essenciais em diferentes superfícies comerciais.

Toda a infraestrutura corre sobre contentores Docker, garantindo portabilidade e facilidade de execução local.

## Arquitetura ETL

### 1. Extração (Extract)
Recolha de dados através de formatos e origens heterogéneas:
* JSON via API REST simulada em Node-RED.
* CSV descarregado de um servidor FTP remoto.
* XML ou YAML com a lista local de compras pretendida.

### 2. Transformação (Transform)
Processamento no Pentaho Kettle (PDI):
* Normalização de nomes e unidades de medida com Expressões Regulares (Regex).
* Filtragem de registos com valores nulos ou produtos sem stock.
* Joins e Lookups para cruzar catálogos e comparar os valores de mercado.

### 3. Carga e Orquestração (Load)
* Persistência dos dados tratados em PostgreSQL.
* Orquestração por Job (.kjb) com validação de conectividade, execução de transformações, registo de logs e envio de alertas por e-mail.
* Dashboard em Grafana ligado à base de dados para visualização gráfica das variações de preços.

## Tecnologias Utilizadas
* Pentaho Data Integration (Kettle)
* Node-RED
* Docker
* PostgreSQL
* Grafana
* Servidor FTP e SMTP
* Git / GitHub
