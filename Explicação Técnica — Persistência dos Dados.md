# 📦 Explicação Técnica — Persistência dos Dados

Após os tratamentos e transformações, os dados foram **persistidos em formato Parquet particionado**.  
Essa decisão segue boas práticas de Engenharia de Dados, considerando performance, organização e consumo futuro.

---

## 🎯 Por que **Parquet**
- Formato **colunar**, ideal para cenários analíticos.  
- Suporta **compressão Snappy** (padrão), reduzindo espaço e aumentando eficiência.  
- Permite **leitura seletiva** (apenas colunas necessárias são lidas).  
- É amplamente compatível com ecossistemas de Big Data (Spark, Hive, Presto, BigQuery, etc.).

---

## 🗂️ Por que **Particionamento por ano/mês**
- Otimiza consultas temporais (ex.: `WHERE year=2025 AND month=8`).  
- Evita varrer o dataset inteiro quando se busca um período específico.  
- Estrutura o Data Lake de forma escalável.  
- Reflete práticas reais de organização em pipelines de produção.

---

## 🚀 Contribuição para Escalabilidade
Se o volume de dados crescer para **milhões de registros por dia** (ex.: coleta de clima a cada minuto em todas as capitais):  
- O **particionamento** garante que apenas as pastas necessárias sejam lidas.  
- O **Parquet colunar** garante que apenas as colunas relevantes sejam carregadas em memória.  
- Essa combinação permite performance elevada mesmo em cenários de Big Data.

---

## 🔮 Cenários de Consumo Futuro
- **Spark/Databricks**: leitura direta dos Parquets para análises avançadas.  
- **Ferramentas BI**: Power BI, Looker, Tableau podem se conectar no diretório `processed`.  
- **Pipelines futuros**: agregações semanais/mensais, integração com Data Warehouses (ex.: BigQuery, Snowflake, Redshift).  
- **Armazenamento em nuvem**: estrutura facilmente migrável para buckets em S3, GCS ou Azure Data Lake.

---
