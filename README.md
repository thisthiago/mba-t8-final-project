# 📘 Projeto Final — Módulo: Arquiteturas de ETL e ELT (MBA)

## 🎯 Objetivo

Desenvolver uma **pipeline completa de dados** baseada na **Medallion Architecture** (camadas Bronze, Silver e Gold), utilizando tecnologias modernas de processamento e orquestração de dados. O projeto será baseado em dados reais do futebol europeu, que estão disponíveis no seguinte bucket:

```
s3://dev-lab-02-us-east-2-landing/soccer/
```

Pode escolher:

* **Local**: Jupyter + MinIO + Docker
* **Nuvem**: AWS S3 + AWS Glue (ou JupyterLab no SageMaker) + Athena

Em ambos os casos, todo código (notebooks + scripts) deve ser versionado em Git, ou caso não tenha familiaridade pode empacotado no formato ZIP e enviar via email.

**Devem ultilizar o formato Delta nas Tabelas da silver e da Gold**
---

## 🛠️ Tecnologias Esperadas

Os alunos devem utilizar **pelo menos os seguintes componentes** no projeto:

| Componente       | Opções locais              | Opções em nuvem (AWS)                |
| ---------------- | -------------------------- | ------------------------------------ |
| Armazenamento    | MinIO (via Docker)         | S3                                   |
| Processamento    | Spark local via Jupyter    | AWS Glue ou Jupyter em EC2/SageMaker |
| Formato de dados | Delta Lake                 | Delta Lake                           |
| Consulta         | Spark SQL, Athena          | Athena (obrigatório na Gold)         |
| Orquestração     | Scripts manuais ou Jupyter | Terraform (infraestrutura), opcional |
| Versão final     | GitHub ou envio por email  | GitHub ou envio por email            |

# 🧱 Arquitetura Esperada: Medallion Architecture

### 🥉 Bronze 

* Ingestão bruta dos dados do bucket `s3://dev-lab-02-us-east-2-landing/soccer/`
* Formato de entrada: JSON, CSV ou outro
* Apenas leitura e **armazenamento como Delta Table**
* Nenhuma transformação é esperada nessa camada, apenas parsing simples, e inclusão de colunas de metadados como por exemplo arquivo de origem e horário de ingestão

> **Requisito mínimo:** usar **pelo menos 3 tabelas diferentes** (ex: `match`, `player`, `team`)
> **Entrega obrigatória:** 
- Notebook ou script utilizado para a ingestão
---

### 🥈 Silver 

* Transformações aplicadas: normalização, limpeza, renomeação de colunas, tratamento de nulos
* Pode envolver joins entre tabelas
* Colunas desnecessárias podem ser descartadas
* Gravar como **Delta Tables particionadas** se fizer sentido (ex: por `season` ou `year`)

> **Requisito mínimo:** usar **pelo menos 2 tabelas da camada Bronze**

> **Entrega obrigatória:** 
- Dicionário de dados em formato markdown (`.md`) para as tabelas **Silver**
- Notebook ou script utilizado para a ingestão
---

### 🥇 Gold 

* Dados prontos para análise
* Dataset analítico/agregado (por ex: média de gols por temporada e time)
* Pode ser uma tabela com dados já prontos para Athena ou dashboards

> **Requisito mínimo:** usar **pelo menos 1 tabela derivada da camada Silver**

> **Entrega obrigatória:**
- Dicionário de dados em formato markdown (`.md`) para as tabelas **Gold**
- Notebook ou script utilizado para a ingestão
- Create table da tabela athena

---

## 💼 Entregas Esperadas

### 📁 Organização do Projeto

Você deve organizar os notebooks ou scripts com as seguintes partes:

```
project/
│
├── README.md                          
├── dicionario_dados/
│   ├── silver.md
│   └── gold.md
│
├── notebooks/                         
│   ├── 01_bronze.ipynb
│   ├── 02_silver.ipynb
│   └── 03_gold.ipynb
├── athena/
|   └── gold.sql
└── terraform/                         # Se utilizar infraestrutura como código
    └── main.tf
```
---

# ✅ Requisitos de Avaliação

| Critério                               | Peso |
| -------------------------------------- | ---- |
| Ingestão correta na Bronze             | 20%  |
| Transformações corretas na Silver      | 20%  |
| Dataset analítico final (Gold)         | 20%  |
| Dicionários de dados (Silver + Gold)   | 20%  |
| Organização e documentação do projeto  | 20%  |


## Pontuação Extra
| Critério                               | Peso |
| -------------------------------------- | ---- |
| Uso de Terraform                       | 15%  |
| Uso de merge/upsert nas tabelas delta  | 15%  |

---

## 🧪 Exemplos de Projetos Possíveis

* **Análise de desempenho de times por temporada**
* **Ranking de jogadores por média de atributos ao longo dos anos**
* **Comparativo entre ligas e países com mais gols**
* **Evolução tática dos times baseada em formações de jogadores**
* **Correlação entre odds de apostas e resultados reais**

---
## 📦 Entrega

### ✅ Preferencial: Repositório no GitHub

* Submeta o link no AVA ou por email
* O repositório deve conter os notebooks e o README explicando as decisões

### 📨 Alternativa: Envio por Email

* Compacte os arquivos (`.zip`)
* Envie para o email do professor com o assunto: `Projeto Final - ETL MBA - SeuNome`

---

## 🧭 Dicas Finais

* Atenção com os **tipos de dados** (inteiros, datas, strings)
* Particionar tabelas da Silver e Gold ajuda no desempenho com Athena e Spark
* Faça commits frequentes se for usar GitHub
* Evite colunas desnecessárias nas tabelas da Gold
* **Testem as queries no Athena antes da entrega!**

---