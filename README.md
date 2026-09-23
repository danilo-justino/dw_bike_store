
# Bike Store Data Platform

Projeto de engenharia e transformação de dados da **Bike Store**, desenvolvido utilizando **Snowflake** e **dbt Core**.

O objetivo do projeto é construir uma plataforma de dados organizada em camadas, permitindo a ingestão, transformação, validação e disponibilização dos dados para análises e consumo posterior.

## 🏗️ Arquitetura

O projeto utiliza uma arquitetura baseada em camadas:

                    ┌─────────────────┐
                    │   Fonte de Dados│
                    │      CSV/CRM     │
                    │      / ERP       │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │     DEV_RAW     │
                    │  Dados brutos   │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │   DEV_STAGING   │
                    │ Limpeza e       │
                    │ padronização    │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ DEV_INTERMEDIATE│
                    │ Transformações  │
                    │ intermediárias  │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │    DEV_MARTS    │
                    │ Dados analíticos│
                    └─────────────────┘

### Camadas

| Camada | Objetivo |
|---|---|
| `RAW` | Armazenar os dados originais das fontes |
| `STAGING` | Limpeza, padronização e renomeação dos dados |
| `INTERMEDIATE` | Transformações e regras intermediárias |
| `MARTS` | Modelos finais para análise e consumo |

## ☁️ Data Warehouse

O projeto utiliza o **Snowflake** como plataforma de armazenamento e processamento.

Database:

BIKE_STORE

Ambiente de desenvolvimento:

BIKE_STORE.DEV_RAW
BIKE_STORE.DEV_STAGING
BIKE_STORE.DEV_INTERMEDIATE
BIKE_STORE.DEV_MARTS

## 📊 Fontes de Dados

Atualmente o projeto possui seis tabelas na camada `DEV_RAW`.

### CRM

- `CRM_CUST_INFO`
- `CRM_PRD_INFO`
- `CRM_SALES_DETAILS`

### ERP

- `ERP_CUST_AZ12`
- `ERP_LOC_A101`
- `ERP_PX_CAT_G1V2`

## 🛠️ Tecnologias

- **Snowflake** — Data Warehouse
- **dbt Core** — Transformação e modelagem
- **Python** — Ambiente de desenvolvimento
- **Git** — Controle de versão
- **GitHub** — Repositório e colaboração

## 📁 Estrutura do Projeto

bike_store/
├── dbt_project.yml
├── models/
│   ├── staging/
│   │   ├── crm/
│   │   └── erp/
│   ├── intermediate/
│   └── marts/
├── macros/
├── tests/
├── seeds/
├── snapshots/
├── analyses/
└── README.md

## 🔄 Fluxo de Desenvolvimento

O desenvolvimento segue um fluxo baseado em branches e Pull Requests.

main
 │
 ├── feature/raw-sources
 │
 ├── feature/staging-crm
 │
 ├── feature/staging-erp
 │
 ├── feature/intermediate
 │
 ├── feature/marts
 │
 └── feature/tests-documentation

Cada nova etapa deve ser desenvolvida em uma branch própria e posteriormente integrada à `main` através de um Pull Request.

### Fluxo padrão

git checkout main
git pull origin main

git checkout -b feature/nome-da-feature

# Desenvolvimento

git add .
git commit -m "feat: descrição da alteração"
git push -u origin feature/nome-da-feature

Depois, abrir um Pull Request:

feature/nome-da-feature → main

## 🧪 Testes e Qualidade

O projeto utiliza os recursos de testes e documentação do dbt para validar a qualidade dos dados.

Exemplos de validações:

- `not_null`
- `unique`
- `relationships`
- `accepted_values`

Os testes serão adicionados progressivamente conforme os modelos forem desenvolvidos.

## 📚 Modelagem

Os modelos seguem uma separação por responsabilidade.

### Staging

Responsável por:

- Padronização de nomes
- Conversão de tipos
- Tratamento de valores nulos
- Limpeza inicial
- Aplicação de regras simples

### Intermediate

Responsável por:

- Combinação de diferentes fontes
- Regras de negócio intermediárias
- Preparação dos dados para os modelos finais

### Marts

Responsável por:

- Modelos analíticos
- Métricas
- Entidades de negócio
- Dados preparados para consumo

## 🚀 Status do Projeto

**Em desenvolvimento**

Etapas planejadas:

- [x] Configuração inicial do Snowflake
- [x] Configuração do dbt Core
- [x] Conexão dbt Core + Snowflake
- [x] Criação da estrutura inicial do projeto
- [x] Criação da camada `DEV_RAW`
- [ ] Configuração dos sources
- [ ] Modelos `STAGING`
- [ ] Modelos `INTERMEDIATE`
- [ ] Modelos `MARTS`
- [ ] Testes de qualidade
- [ ] Documentação dos modelos
- [ ] Automação do pipeline
- [ ] Configuração do ambiente PROD

## 🔐 Segurança

Credenciais e informações sensíveis não devem ser armazenadas neste repositório.

Arquivos como `profiles.yml` e credenciais do Snowflake devem permanecer fora do controle de versão.

O arquivo `.gitignore` é utilizado para evitar o versionamento de arquivos sensíveis e arquivos gerados localmente.

## 👤 Projeto

**Bike Store Data Platform**

Projeto desenvolvido para prática e aplicação de conceitos de:

- Data Engineering
- Analytics Engineering
- Data Modeling
- ELT
- Data Quality
- Version Control

