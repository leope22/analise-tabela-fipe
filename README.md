# Análise de Dados da Tabela FIPE

Este projeto consiste na criação de um Data Warehouse (DW) para analisar a evolução dos preços de veículos no Brasil, utilizando como fonte de dados a Tabela FIPE. A análise abrange três categorias de veículos: carros, motos e caminhões.

## 🎯 Objetivo

O principal objetivo é construir uma solução de dados que permita monitorar e analisar a variação de preços de veículos ao longo do tempo. As principais análises que o projeto busca responder são:

* **Variação Temporal:** Qual foi a variação percentual no preço de um determinado modelo em um período específico?
* **Comparação de Mercado:** Qual a média de preço dos veículos de uma marca X no ano Y?

## 🛠️ Metodologia

O projeto foi estruturado seguindo um pipeline de dados padrão:

1.  **Web Scraping:** A coleta de dados foi realizada diretamente da API do site da Tabela FIPE. Um script Python foi desenvolvido para automatizar as requisições HTTP e extrair as informações.

2.  **ETL (Extração, Transformação e Carga):** Os dados brutos foram processados através de um fluxo de ETL que incluiu:
    * Importação dos arquivos CSV gerados pelo scraper.
    * Merge das bases de dados (veículos e preços por mês de referência).
    * Limpeza, formatação e padronização dos dados.
    * Tratamento de valores nulos.

3.  **Data Warehouse (DW) e Carga:** Os dados tratados foram consolidados e carregados em um Data Warehouse, modelado para permitir análises OLAP eficientes.

4.  **Análise e Visualização:** Com o DW populado, foram realizadas análises para responder às perguntas de negócio, gerando visualizações e gráficos que ilustram, por exemplo, o aumento percentual dos preços.

O principal desafio encontrado foi o **volume de dados e a lentidão do processo de web scraping**. A extração de dados para um único mês de referência demorou cerca de 20 horas. Tentativas de otimizar o processo com paralelismo (`multithreading`) resultaram em bloqueios da API (erro 429).

Para viabilizar o projeto, foi adotada uma abordagem híbrida:
* **Carros:** Utilizamos um dataset já existente do [Kaggle](https://www.kaggle.com/datasets/franckepeixoto/tabela-fipe) com dados dos anos de 2020 e 2021.
* **Motos e Caminhões:** Utilizamos os dados parciais coletados pelo nosso script de scraping.

## 📂 Arquivos do Projeto

Os arquivos de suporte, como scripts de inserção, dados em CSV e o backup do banco de dados, estão disponíveis no seguinte repositório:

* **[Tabela-Fipe-DW](https://github.com/BeatrizPat/Tabela-Fipe-DW)**

### 👨‍💻 Autores

* **Leonardo Pedro** - [GitHub](https://github.com/leope22)
* **Beatriz Patricio** - [GitHub](https://github.com/BeatrizPat)
