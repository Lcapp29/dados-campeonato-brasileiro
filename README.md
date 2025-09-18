# ⚽ Projeto de Análise de Dados: O Histórico do Brasileirão (2003-2024)

* **Autor:** Lucas de Andrade Cappola
* **Dashboard Interativo:** **`Dashboard Brasileirão v2 - Tabelas Revisadas.pbix`**

---

## 📄 Sobre o Projeto

Este é um projeto completo de **Análise de Dados** com foco em **Engenharia Analítica**, que explora o histórico completo do Campeonato Brasileiro de futebol na era dos pontos corridos (2003-2024).

O objetivo foi construir um pipeline **ELT (Extract, Load, Transform)** robusto, saindo de dados brutos para a criação de um modelo de dados otimizado e, finalmente, um dashboard interativo no Power BI para a extração de insights.

## 🏗️ Arquitetura de Dados

O fluxo de dados deste projeto segue as melhores práticas de um pipeline ELT moderno:

1.  **Extract & Load (Extração e Carga):** Dados históricos em formato CSV (obtidos do Kaggle) foram carregados em sua forma bruta ("raw") para o Data Warehouse na nuvem, o **Google BigQuery**.
2.  **Transform (Transformação):** Toda a lógica de negócio, limpeza de dados (correção de datas da pandemia, remoção de espaços), enriquecimento (cálculo de pontos por partida) e agregações foram executadas diretamente no **BigQuery** através de um **script SQL avançado**.
3.  **Modeling (Modelagem):** O script SQL materializa os dados transformados em duas tabelas analíticas otimizadas, seguindo princípios de modelagem dimensional:
    * `fact_partidas`: Uma tabela fato com o detalhe de cada partida já limpo e enriquecido.
    * `dim_classificacao_anual`: Uma tabela de dimensão com os dados agregados da classificação de cada time em cada edição.
4.  **Visualize (Visualização):** O **Power BI** se conecta a essas tabelas limpas no BigQuery. A complexidade foi movida para o SQL, permitindo que as medidas **DAX** no Power BI sejam simples e performáticas, focadas apenas na exibição dos resultados.

## 🛠️ Stack de Ferramentas

* **Cloud & Data Warehouse:** Google Cloud Platform (GCP), Google BigQuery
* **Transformação e Modelagem de Dados:** SQL (CTEs, Funções de Janela, Agregações, CASE)
* **Business Intelligence e Visualização:** Microsoft Power BI
* **Cálculos e Medidas no BI:** DAX (Data Analysis Expressions)

## ✨ Destaques do Projeto e Habilidades Demonstradas

* **Engenharia Analítica:** Construção de um pipeline ELT, movendo a lógica de transformação de dados complexa para o SQL no Data Warehouse, otimizando a performance do dashboard.
* **SQL Avançado:** Desenvolvimento de scripts complexos com Common Table Expressions (CTEs) para limpeza, enriquecimento e agregação de dados.
* **Modelagem de Dados:** Criação de um modelo dimensional (tabelas Fato e Dimensão) para servir de base para a análise, garantindo consistência e velocidade.
* **DAX Dinâmico:** Criação de medidas inteligentes no Power BI que se adaptam ao contexto de filtro do usuário (ex: o card de "Clube Destaque" que mostra o líder global ou o campeão da edição selecionada).
* **Visualização de Dados e Storytelling:** Desenvolvimento de um dashboard interativo com múltiplos visuais (tabelas, gráficos de linha, barras, cards) que contam a história do campeonato e permitem a exploração livre dos dados.

## 🔮 Próximos Passos
- [ ] Desenvolver um pipeline de ETL em Python para automatizar a ingestão de dados da temporada atual via API, orquestrando a execução do script SQL de transformação.
- [ ] Implementar um modelo de Machine Learning em Python para prever a probabilidade de vitória de um time com base nos dados históricos.
