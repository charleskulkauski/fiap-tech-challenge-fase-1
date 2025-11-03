# FIAP - Tech Challenge - Fase 1

## **Modelo preditivo para classificação de tumores de câncer de mama**

## Resumo
Este repositório contém um notebook Jupyter (`Tech_Challenge_Fase1.ipynb`) que desenvolve um pipeline completo para classificação de tumores utilizando um dataset tabular (arquivo `data/data.csv`). O objetivo do projeto é comparar técnicas de aprendizado de máquina clássicas para identificar tumores malignos e benignos, realizar avaliação robusta dos modelos e apresentar análises exploratórias e visuais que suportam as decisões de modelagem.

## Estrutura do repositório
```
FIAP-TECH-CHALLENGE-FASE-1/
├─ data/
│  ├─ data.csv
│  ├─ ponto_concavo_massa_tumoral_explicado.jpeg
│  └─ random_forest_tree_plot.png
├─ Tech_Challenge_Fase1.ipynb
├─ README.md
├─ LICENSE
└─ .gitignore
```

## Dataset
- Arquivo: `data/data.csv`
- Observações: trata-se do dataset utilizado no notebook (similar ao Breast Cancer Wisconsin dataset). No notebook há pré-processamento que remove colunas irrelevantes (ex.: `id`, `Unnamed: 32`) e mapeia o rótulo diagnóstico (`M`/`B`) para binário. Algumas features referenciam medidas morfológicas como pontos côncavos, massa tumoral etc. (há uma figura explicativa `ponto_concavo_massa_tumoral_explicado.jpeg`).

## Objetivo
Construir e avaliar modelos de classificação binária que preveem se um tumor é maligno (M) ou benigno (B), comparando diferentes algoritmos e estratégias de validação, e documentar resultados e decisões.

## Metodologia / Pipeline
1. **Carregamento de dados**  
   - Leitura do arquivo CSV para um `DataFrame` pandas e inspeção inicial (`df.head()`).

2. **Análise Exploratória (EDA)**  
   - Estatísticas descritivas, histogramas, boxplots e inspeções visuais das features.
   - Análise de correlações e identificação de features potenciais para seleção.

3. **Pré-processamento**  
   - Remoção de colunas não informativas (ex.: `id`, `Unnamed: 32`).
   - Mapeamento dos rótulos para binário (`M` → 1, `B` → 0).
   - Escalonamento (normalização/standardização) aplicável ao pipeline de treino/teste.

4. **Divisão treino/teste**  
   - Uso de `train_test_split` (com estratificação quando apropriado) para evitar viés no conjunto de validação.

5. **Modelagem e comparação de algoritmos**  
   - Modelos avaliados (detectados no notebook):
     - K-Nearest Neighbors (`KNeighborsClassifier`)
     - Support Vector Machine (SVM) (`SVC`)
     - Random Forest (`RandomForestClassifier`)
   - Aplicação de `GridSearchCV` e `cross_val_score` para busca de hiperparâmetros e validação cruzada (estratificada quando indicado).
   - Possível uso de `PCA` em análises exploratórias (detectado no notebook).

6. **Avaliação**  
   - Métricas: matriz de confusão, classification report (precision, recall, f1-score), acurácia.  
   - Resultados registrados no notebook indicam uma acurácia em torno de **0.89** (dependendo da partição e do modelo), conforme saída do `classification_report` presente no notebook.
   - Visualizações: plot da árvore do Random Forest (`random_forest_tree_plot.png`) e outras figuras explicativas.

## Resultados (síntese)
- Modelos comparados: KNN, SVM, Random Forest.
- Melhores práticas aplicadas: validação cruzada, `GridSearchCV` para tuning, uso de `classification_report` e matriz de confusão para avaliação detalhada por classe.
- Métrica destacada: acurácia observada ~ **0.89** em avaliação reportada no notebook (veja célula que imprime o `classification_report`).
- Observações: o notebook contém visualizações e uma árvore do Random Forest para interpretação.

## Principais arquivos gerados
- `Tech_Challenge_Fase1.ipynb` — notebook com todo o pipeline (EDA, pré-processamento, modelagem, avaliação).
- `data/data.csv` — base de dados utilizada.
- `data/random_forest_tree_plot.png` — figura da árvore gerada a partir do modelo Random Forest.
- `data/ponto_concavo_massa_tumoral_explicado.jpeg` — figura explicativa de features.

## Como reproduzir (instruções)
1. Criar e ativar um ambiente virtual (recomendado):
```bash
python -m venv .venv
source .venv/bin/activate        # Linux / macOS
.venv\Scripts\activate           # Windows (cmd/PowerShell)
```

2. Instalar dependências (exemplo):
```bash
pip install -U pip
pip install pandas numpy scikit-learn matplotlib seaborn jupyterlab
```

3. Abrir e executar o notebook:
```bash
jupyter lab          # ou jupyter-notebook
# Em seguida, abrir Tech_Challenge_Fase1.ipynb e executar células sequencialmente.
```

## Créditos
- Desenvolvimento: Charles Kulkauski.
- Tooling: Python, pandas, scikit-learn, matplotlib, seaborn, Jupyter.

## Licença
Licença MIT.
