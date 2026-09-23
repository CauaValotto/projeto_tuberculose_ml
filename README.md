# Predicao de Obito por Tuberculose em Idosos no Sudeste do Brasil

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.4%2B-orange.svg)](https://scikit-learn.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-2.0%2B-red.svg)](https://xgboost.readthedocs.io/)
[![SHAP](https://img.shields.io/badge/SHAP-0.44%2B-purple.svg)](https://shap.readthedocs.io/)
[![Kaggle](https://img.shields.io/badge/Kaggle-Dataset-20BEFF.svg?logo=kaggle&logoColor=white)](https://www.kaggle.com/datasets/caulourenovalotto/sinan-microdados-de-tuberculose-datasus)
[![Status](https://img.shields.io/badge/Status-Concluido-brightgreen.svg)]()

Projeto de Ciencia de Dados e Machine Learning em Saude Publica voltado a predicao do risco de obito por tuberculose em pacientes idosos (>= 60 anos) notificados no Sistema de Informacao de Agravos de Notificacao (SINAN / DATASUS) na Regiao Sudeste do Brasil.

O objetivo do modelo e identificar precocemente individuos com maior vulnerabilidade clinico-epidemiologica, auxiliando na tomada de decisao na Atencao Primaria a Saude e na Vigilancia Epidemiologica do SUS.

---

## Sumario
1. [Origem dos Dados e Contexto](#origem-dos-dados-e-contexto)
2. [Como Executar (Quickstart)](#-como-executar-quickstart)
3. [Estrutura do Repositorio](#estrutura-do-repositorio)
4. [Metodologia e Pipeline](#metodologia-e-pipeline)
5. [Variaveis Utilizadas](#variaveis-utilizadas)
6. [Destaques dos Resultados e Relatorio](#destaques-dos-resultados-e-relatorio)
7. [Creditos](#creditos)

---

## Origem dos Dados e Contexto

O projeto baseia-se nos ensinamentos metodologicos e nos microdados disponibilizados pelo curso oficial:

* **Curso:** Introducao a Inteligencia Artificial para Predicoes em Vigilancia em Saude e Ambiente
* **Promocao:** Ministerio da Saude do Brasil - Secretaria de Vigilancia em Saude e Ambiente (SVSA), por meio do Departamento de Acoes Estrategicas de Epidemiologia e Vigilancia em Saude e Ambiente (Daevs) e da Coordenacao-Geral de Desenvolvimento da Epidemiologia em Servicos (CGDEP).
* **Universidade que promoveu o curso:** Universidade de Sao Paulo (USP) - Laboratorio de Big Data e Analise Preditiva em Saude (Labdaps/USP).
* **Docente Responsavel:** Prof. Dr. Alexandre Dias Porto Chiavegatto Filho e equipe de pesquisadores do Labdaps/USP.

### Recorte Epidemiologico
* **Base Primaria:** Microdados abertos de notificacoes de Tuberculose (SINAN / DATASUS). A base consolidada de 250 MB com mais de 770 mil registros esta disponivel no [Kaggle Datasets](https://www.kaggle.com/datasets/caulourenovalotto/sinan-microdados-de-tuberculose-datasus).
* **Regiao:** Sudeste (Sao Paulo, Rio de Janeiro, Minas Gerais e Espirito Santo).
* **Faixa Etaria:** Idosos (>= 60 anos).
* **Periodo:** Notificacoes a partir do ano de 2022.
* **Coorte Final:** 9.722 pacientes idosos (7.291 no treino e 2.431 no teste).
* **Desfecho Binario (Target):** 0 = Nao Obito (Cura) vs. 1 = Obito por Tuberculose.

---

## Como Executar (Quickstart)

### 1. Clonar o repositorio
```bash
git clone https://github.com/CauaValotto/projeto_tuberculose_ml.git
cd projeto_tuberculose_ml
```

### 2. Criar e ativar o ambiente virtual
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Linux / macOS
python3 -m venv venv
source venv/bin/activate
```

### 3. Instalar as dependencias
```bash
pip install -r requirements.txt
```

### 4. Executar o Notebook
```bash
jupyter notebook modelagem_tuberculose.ipynb
```

> **Execucao Imediata:** Os dados ja devidamente limpos e pré-processados encontram-se versionados na pasta [`data/`](data/) (`dados_treino_preprocessado.csv` e `dados_teste_preprocessado.csv`), permitindo treinar os modelos e rodar o SHAP imediatamente sem necessidade de baixar a base bruta de 250 MB. Caso deseje executar a etapa de filtragem a partir dos microdados brutos do DATASUS, baixe o arquivo via [Kaggle Datasets](https://www.kaggle.com/datasets/caulourenovalotto/sinan-microdados-de-tuberculose-datasus) e salve como `data/dados_tuberculose.csv`.

---

## Estrutura do Repositorio

```text
projeto_tuberculose_ml/
│
├── data/
│   ├── README.md                          # Instrucoes dos conjuntos de dados
│   ├── dados_treino_preprocessado.csv     # Base de treino processada (7.291 registros)
│   └── dados_teste_preprocessado.csv      # Base de teste processada (2.431 registros)
│
├── .gitignore
├── README.md                              # Apresentacao geral e instrucoes de execucao
├── modelagem_tuberculose.ipynb            # Pipeline completo com graficos e explicabilidade SHAP
├── relatorio.md                           # Relatorio completo de resultados e discussao clinica
├── dicionario_variaveis.md                # Dicionario oficial com os 98 campos do SINAN
└── requirements.txt                       # Dependencias do projeto
```

---

## Metodologia e Pipeline

1. **Tratamento de Dados e Missings:**
   - Imputacao pela media na idade continua (`IDADE_ANOS`);
   - Preservacao das categorias '9' (Ignorado) e tratamento dos campos categoricos ausentes;
   - Padronizacao Z-score da idade (`StandardScaler`);
   - Codificacao One-Hot das variaveis categoricas com tratamento para valores nao vistos no teste (`handle_unknown='ignore'`).

2. **Treinamento e Validacao Cruzada (5-Fold CV):**
   - **Regressao Logistica:** `GridSearchCV` com regularizacao L2 e busca pelo melhor hiperparametro de penalizacao $C$;
   - **Random Forest:** `RandomizedSearchCV` com 20 iteracoes variando profundidade, folhas e numero de arvores;
   - **XGBoost Classifier:** `RandomizedSearchCV` com 20 iteracoes, ajuste fino de regularizacoes (`reg_alpha`, `reg_lambda`) e `scale_pos_weight`.

3. **Avaliacao Independente e Explicabilidade:**
   - Avaliacao cega no conjunto de teste independente (2.431 pacientes);
   - Metricas de discriminacao: AUC-ROC e PR-AUC;
   - Curva de Calibracao de probabilidades via Plotly;
   - Calibracao do threshold de decisao clinica (0.30 vs 0.50);
   - Interpretabilidade global e local com SHAP TreeExplainer.

---

## Variaveis Utilizadas

Para a relacao completa e detalhada dos 98 campos da ficha de notificacao do SINAN, consulte o arquivo dedicado: [dicionario_variaveis.md](dicionario_variaveis.md).

No pipeline de modelagem preditiva, foram selecionadas as seguintes caracteristicas:

* **Demograficas:** Idade (anos), Sexo biologico (F/M), Raca/cor (Branca, Preta, Parda, Amarela, Indigena, Ignorada), Estado de notificacao (SP, RJ, MG, ES).
* **Determinantes Sociais:** Grau de escolaridade, Populacao em situacao de rua, Populacao privada de liberdade (sistema prisional).
* **Clinicas e Diagnosticas:** Forma clinica (Pulmonar, Extrapulmonar, Mista), Baciloscopia de escarro inicial, Radiografia de torax (suspeito, normal, outra patologia), Sorologia HIV.
* **Comorbidades:** Diabetes Mellitus, Alcoolismo / Etilismo cronico, Tabagismo, Uso de outras drogas.
* **Acompanhamento:** Tipo de ingresso no sistema e Tratamento Diretamente Observado (TDO).

---

## Destaques dos Resultados e Relatorio

A avaliacao dos modelos foi conduzida na base de teste independente com 2.431 idosos (2.051 curas e 380 obitos confirmados):

### 1. Desempenho Global dos Algoritmos

| Modelo | Metodo de Otimizacao | AUC-ROC | PR-AUC | Destaque |
| :--- | :--- | :---: | :---: | :--- |
| **Regressao Logistica** | `GridSearchCV` ($C=0.1$) | 0.81 | 0.54 | Modelo linear interpretavel e estavel. |
| **Random Forest** | `RandomizedSearchCV` | 0.83 | 0.55 | Ensemble com alta precisao na classe minoritaria. |
| **XGBoost Classifier** | `RandomizedSearchCV` | **0.84** | **0.57** | **Melhor discriminacao global e maior precisao media.** |

### 2. Calibracao do Limiar Clinico (Threshold 0.30)
* No limiar estatistico padrao (**0.50**), o XGBoost detecta apenas 95 dos 380 obitos reais (Recall de 25,0%), deixando escapar 75% dos pacientes criticos.
* Ao adotar o limiar preventivo de **0.30**, o modelo quase dobra as deteccoes, alcancando **176 obitos identificados** (+81 idosos resgatados sob vigilancia ativa, aumento de **+85,3%** na sensibilidade), com precisao de **52,4%** e $F_1\text{-score} = 0.49$.
* O Tratamento Supervisionado (**TDO**) emergiu como o preditor individual mais expressivo de sobrevida na analise SHAP, reforcando a diretriz de garantia do TDO para idosos diagnosticados com tuberculose no SUS.

> 📊 **Acesse o Relatorio Completo de Resultados:**  
> Para consultar a analise tecnica e epidemiologica aprofundada — com todas as **matrizes de confusao detalhadas**, discussao sobre a **curva de calibracao**, graficos de explicabilidade **SHAP (Beeswarm, Bar Plot e Waterfall individual)** e diretrizes assistenciais para o SUS —, leia o documento dedicado:  
> 👉 [**relatorio.md**](relatorio.md)

---

## Creditos

Projeto desenvolvido a partir dos ensinamentos e dados disponibilizados pelo Ministerio da Saude do Brasil (SVSA/CGDEP) e pela Universidade de Sao Paulo (Labdaps/USP) no curso *Introducao a Inteligencia Artificial para Predicoes em Vigilancia em Saude e Ambiente*.
