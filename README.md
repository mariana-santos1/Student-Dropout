# Aplicação de Machine Learning na Prevenção da Evasão Escolar

## Sobre o projeto

Este projeto tem como objetivo aplicar técnicas de Machine Learning para analisar dados estudantis e avaliar modelos de classificação na identificação de possíveis casos de evasão escolar.

A proposta consiste em treinar e comparar três algoritmos de classificação, analisando seu desempenho por meio de métricas de avaliação, matrizes de confusão e análises de correlação.

## Base de dados

O projeto utiliza o conjunto de dados **Student Dropout Analysis and Prediction Dataset**, disponibilizado na plataforma Kaggle.

- **Fonte:** [Kaggle – Student Dropout Analysis and Prediction Dataset](https://www.kaggle.com/datasets/abdullah0a/student-dropout-analysis-and-prediction-dataset)
- **Arquivo utilizado:** `student dropout.csv`
- **Variável-alvo:** `Dropped_Out`

A variável `Dropped_Out` representa a situação de evasão dos estudantes:
- `0`: Não evadiu.
- `1`: Evadiu.

A coluna `Final_Grade` foi removida das variáveis preditoras durante a preparação dos dados com o objetivo de evitar vazamento de dados (_data leakage_).

## Tecnologias e bibliotecas

O projeto foi desenvolvido em Python, utilizando as seguintes bibliotecas:

- **Pandas:** manipulação e análise dos dados.
- **NumPy:** operações matemáticas e cálculos estatísticos.
- **Matplotlib:** construção de gráficos.
- **Seaborn:** visualização de dados e matrizes de confusão.
- **Scikit-learn:** preparação dos dados, treinamento e avaliação dos modelos de Machine Learning.

## Modelos de Machine Learning

Foram utilizados três algoritmos de classificação:

### 1. Árvore de Decisão (Decision Tree)

Algoritmo que utiliza uma estrutura de decisões para classificar os estudantes de acordo com suas características.

Parâmetros utilizados:
- `max_depth=5`
- `min_samples_split=10`
- `min_samples_leaf=5`

### 2. K-Vizinhos Mais Próximos (KNN)

Algoritmo que realiza classificações considerando a proximidade entre os registros, utilizando os cinco vizinhos mais próximos.

Parâmetro utilizado:
- `n_neighbors=5`

### 3. Máquina de Vetores de Suporte (SVM)

Algoritmo que busca encontrar um hiperplano capaz de separar as classes. Foi utilizado o kernel RBF (Radial Basis Function), adequado para identificar relações não lineares entre os dados.

Parâmetro utilizado:
- `kernel='rbf'`

## Metodologia

O treinamento e a avaliação dos modelos foram realizados seguindo as seguintes etapas:

1. **Carregamento dos dados:** leitura do arquivo CSV utilizando Pandas.
2. **Preparação dos dados:** separação das variáveis preditoras (`X`) e da variável-alvo (`y`), com remoção das colunas `Dropped_Out` e `Final_Grade` das variáveis preditoras.
3. **Codificação das variáveis categóricas:** utilização de `pd.get_dummies()` com `drop_first=True`.
4. **Divisão dos dados:** separação em conjuntos de treinamento (70%) e teste (30%), utilizando estratificação para preservar a proporção das classes.
5. **Normalização:** aplicação do `StandardScaler`, ajustado com os dados de treinamento e aplicado aos dados de teste.
6. **Treinamento e avaliação:** execução dos três algoritmos em 20 divisões diferentes dos dados, com `random_state` variando de 0 a 19.
7. **Análise dos resultados:** cálculo das métricas de avaliação, médias e desvios padrão das 20 execuções.

## Métricas de avaliação

Para comparar o desempenho dos modelos, foram utilizadas quatro métricas:

- **Acurácia (Accuracy):** proporção de classificações corretas em relação ao total de previsões.
- **Precisão (Precision):** proporção de estudantes classificados como evadidos que realmente pertencem a essa classe.
- **Revocação (Recall):** proporção de estudantes que realmente evadiram e foram corretamente identificados pelo modelo.
- **F1-Score:** média harmônica entre precisão e revocação, permitindo avaliar o equilíbrio entre essas duas métricas.

Além das métricas individuais, foram calculadas as médias e os desvios padrão dos resultados obtidos nas 20 execuções, permitindo analisar o desempenho e a variação dos modelos.

## Visualizações e análises

O projeto gera diferentes visualizações para auxiliar na interpretação dos resultados:

### Gráfico de comparação dos modelos

Apresenta as médias das métricas de acurácia, precisão, revocação e F1-Score para os três algoritmos, permitindo comparar seus desempenhos.

### Matrizes de confusão médias

São calculadas a partir das matrizes de confusão obtidas nas 20 execuções de cada modelo. Os resultados são apresentados em percentuais por classe, permitindo visualizar a proporção de classificações corretas e incorretas.

### Matriz de correlação

Apresenta a correlação entre as variáveis numéricas e categóricas após a codificação, permitindo observar as associações entre as características dos estudantes.

### Gráfico das variáveis mais correlacionadas com a evasão

Apresenta as cinco variáveis com menor correlação e as cinco com maior correlação em relação à variável `Dropped_Out`, destacando as associações negativas e positivas.

A análise de correlação permite identificar associações entre as variáveis, mas não estabelece relações de causalidade.

## Como acessar e executar o projeto

O projeto está disponibilizado em formato Jupyter Notebook (`.ipynb`), permitindo visualizar o código-fonte, os resultados das execuções, as métricas de avaliação, as tabelas e os gráficos gerados.

**Acessar o notebook:**

- **GitHub:** [Visualizar o notebook](https://github.com/mariana-santos1/Student-Dropout/blob/main/StudentDropout.ipynb)
- **Google Colab:** [Abrir no Google Colab](https://colab.research.google.com/drive/1AnNrX67K5qc_OF3i7aUAwasM3yc71pMX)

### Como executar no Google Colab

Para reproduzir a análise, siga os passos:

1. Acesse o notebook pelo link do Google Colab.
2. Baixe o arquivo `student dropout.csv` na [página original da base de dados no Kaggle](https://www.kaggle.com/datasets/abdullah0a/student-dropout-analysis-and-prediction-dataset).
3. Faça o upload do arquivo CSV para o ambiente do Google Colab.
4. Execute as células do notebook em sequência.

**Observação:** o arquivo CSV deve estar disponível no ambiente do Colab com o nome `student dropout.csv`, conforme especificado no código.
## Resultados

Os resultados permitem comparar o desempenho dos três algoritmos na identificação de possíveis casos de evasão escolar.

As médias das métricas e os desvios padrão auxiliam na análise comparativa, enquanto as matrizes de confusão permitem observar os acertos e erros de classificação para cada classe.

As análises de correlação complementam a investigação, apresentando as variáveis que possuem maiores associações com a ocorrência de evasão.

## Considerações finais

O projeto busca demonstrar como técnicas de Machine Learning podem contribuir para a análise de dados educacionais e para a identificação de padrões associados à evasão escolar.

A comparação entre diferentes algoritmos permite investigar suas capacidades de classificação e fornecer informações que podem auxiliar na elaboração de estratégias de acompanhamento e prevenção da evasão.

## Colaboradores
Projeto desenvolvido em equipe por:
- [Jaqueline Silva](https://github.com/jaqueline-silva4).
- [Mariana Santos](https://github.com/mariana-santos1).
- [Mickaelly Silva](https://github.com/Mickaellysilva).
- [Roberta Bezerra](https://github.com/roberta-bez).
