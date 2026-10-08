# SmartBasket: Monitorização Inteligente de Preços de Retalho

Projeto desenvolvido no âmbito da unidade curricular de Integração de Sistemas de Informação (ISI) da Licenciatura em Engenharia de Sistemas Informáticos (UPCA, 2026/27).

## Sobre o Projeto
O SmartBasket é um pipeline de ETL (Extract, Transform, Load) concebido para recolher, padronizar e acompanhar a evolução dos preços de bens essenciais em superfícies comerciais concorrentes.

Toda a infraestrutura de suporte corre sobre contentores Docker, garantindo um ambiente isolado, portabilidade e reprodutibilidade.

## Arquitetura ETL

### 1. Extração (Extract)
Recolha de dados através de formatos e origens heterogéneas:
* JSON via API REST simulada em Node-RED (consumida com o nó GET Request).
* CSV descarregado de um servidor FTP remoto através de nós conectores de transferência.
* XML ou YAML com a lista local de compras pretendida, processada através de nós nativos de ficheiro e XML.

### 2. Transformação (Transform)
Processamento analítico em KNIME Analytics Platform:
* Normalização de nomes e unidades de medida com Expressões Regulares (Regex) e nós de manipulação de texto (String Manipulation, Regex Split).
* Filtragem de registos com valores nulos ou artigos sem stock (Missing Value, Row Filter).
* Cruzamento de catálogos e listas de compras via Joiner para apurar variações e comparar preços de mercado.
* Regras de cálculo (Math Formula, Rule Engine) para determinar os artigos mais vantajosos.

### 3. Carga e Orquestração (Load)
* Persistência dos dados tratados em PostgreSQL através dos conectores e nós de escrita de base de dados (DB Writer / DB Insert).
* Orquestração de workflows com controlo de execução (Try/Catch, IF Switch, Flow Variables), registo de logs e envio de alertas por e-mail (Send Email).
* Dashboard em Grafana ligado diretamente ao PostgreSQL para monitorização gráfica das oscilações de preços.

## Tecnologias Utilizadas
* KNIME Analytics Platform
* Node-RED
* Docker & Docker Compose
* PostgreSQL
* Grafana
* Servidor FTP e SMTP
* Git / GitHub
