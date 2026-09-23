# Diretorio de Dados (`data/`)

Este diretorio armazena os conjuntos de dados utilizados no projeto de modelagem preditiva de obito por tuberculose em idosos.

---

## Arquivos Disponiveis

1. **`dados_treino_preprocessado.csv`** (~2.6 MB)
   - Base de treino estratificada (75% da coorte filtrada, 7.291 registros de pacientes idosos).
   - Dados devidamente limpos, com tratamento de valores ausentes, idade padronizada (Z-score) e codificacao One-Hot (87 colunas).
   - Pronto para treino imediato dos modelos.

2. **`dados_teste_preprocessado.csv`** (~880 KB)
   - Base de teste independente e estratificada (25% da coorte filtrada, 2.431 registros de pacientes idosos).
   - Utilizada exclusivamente para a avaliacao final e para o calculo dos valores SHAP.
   - Pronto para teste e explicabilidade.

---

## Base de Dados Bruta (`dados_tuberculose.csv`)

O arquivo bruto consolidado possui mais de 260 MB e mais de 770 mil notificacoes compulsorias do SINAN contendo 98 variaveis originais (para consultar o significado de todas as 98 variaveis, consulte o [dicionario_variaveis.md](../dicionario_variaveis.md)). Este arquivo esta listado no `.gitignore` para nao sobrecarregar o repositorio Git.

### Como obter a base bruta:
1. **Pelo Kaggle Datasets (Recomendado):**
   - Acesse diretamente: [Kaggle - SINAN Microdados de Tuberculose (DATASUS)](https://www.kaggle.com/datasets/caulourenovalotto/sinan-microdados-de-tuberculose-datasus)
   - Baixe o arquivo e salve como `dados_tuberculose.csv` dentro desta pasta `data/`.
   - Ou via terminal/Kaggle CLI:
     ```bash
     kaggle datasets download -d caulourenovalotto/sinan-microdados-de-tuberculose-datasus -p data/ --unzip
     ```
2. **Pelo Portal Oficial do DATASUS:**
   - Obtenha os microdados oficiais de Tuberculose disponibilizados pelo Ministerio da Saude / DATASUS no portal do SINAN ou no material didatico do curso *Introducao a Inteligencia Artificial para Predicoes em Vigilancia em Saude e Ambiente* (SVSA/CGDEP/USP).
   - Salve o arquivo CSV com o nome `dados_tuberculose.csv` dentro desta pasta `data/`.
3. Ao executar o notebook `modelagem_tuberculose.ipynb`, as etapas de filtragem e pre-processamento serao executadas a partir desta base.

Nota: Para rodar apenas o treinamento dos modelos e a interpretabilidade com SHAP, nao e necessario baixar a base bruta, pois as bases pre-processadas ja estao versionadas neste diretorio.
