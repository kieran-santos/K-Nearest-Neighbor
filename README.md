# KNN - Classificação de Tumores

Trabalho desenvolvido para a disciplina de **Machine Learning**, com o objetivo de implementar o algoritmo **K-Nearest Neighbors (KNN)** do zero, sem o uso de bibliotecas de Machine Learning (como `scikit-learn`), apenas com `numpy`.

O projeto utiliza um dataset simplificado de tumores para classificá-los como **benignos** ou **malignos** com base em duas características: tamanho e pontuação de textura.

## Estrutura do projeto

```
.
├── knn.ipynb        # Implementação do algoritmo KNN do zero
└── tumores.csv       # Dataset com características e classificação dos tumores
```

## Notebook

### `knn.ipynb`

Implementação completa do algoritmo **KNN (K-Nearest Neighbors)**, um classificador baseado em distância, dividida nas seguintes etapas:

#### 1. Preparando o dataset
- Leitura do `tumores.csv` com `numpy` (`np.loadtxt`), pulando as linhas de cabeçalho/comentário
- Separação das features (`X_train`: tamanho e pontuação de textura) e dos rótulos (`y_train`: 0 = Benigno, 1 = Maligno)

#### 2. Visualização dos dados
- Gráfico de dispersão (`matplotlib`) mostrando a distribuição dos tumores benignos e malignos no plano tamanho x textura, antes de aplicar o algoritmo

#### 3. Implementação do algoritmo KNN
- **`calcular_distancia_euclidiana`** — calcula a distância euclidiana entre dois pontos
- **`encontrar_vizinhos`** — calcula a distância do ponto de teste para todos os pontos de treino, ordena e retorna os `k` vizinhos mais próximos
- **`prever_classificacao`** — define a classe prevista pelo **voto majoritário** entre os `k` vizinhos encontrados (usando `collections.Counter`)

#### 4. Realizando uma previsão
- Classificação de um novo tumor (`[5.5, 6.0]`) com `k = 5`
- Exibição das classes dos vizinhos mais próximos e da previsão final (Benigno/Maligno)

#### 5. Visualização do resultado
- Gráfico final mostrando o novo ponto classificado, destacado em verde, e um círculo delimitando a vizinhança considerada (os `k` vizinhos mais próximos usados na votação)

## Tecnologias utilizadas

- Python 3
- [NumPy](https://numpy.org/)
- [Matplotlib](https://matplotlib.org/)
- `collections.Counter` (módulo padrão do Python)

## Como executar

> Este notebook foi originalmente desenvolvido no **Google Colab**, lendo o `tumores.csv` a partir do Google Drive (`drive.mount`). Para rodar localmente (Jupyter), remova a célula de `drive.mount` e ajuste o caminho do `np.loadtxt` para apontar diretamente para `tumores.csv` na pasta do projeto.

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/knn-classificacao-tumores.git
   cd knn-classificacao-tumores
   ```

2. Instale as dependências:
   ```bash
   pip install numpy matplotlib
   ```

3. Abra o notebook com Jupyter:
   ```bash
   jupyter notebook
   ```

4. Execute as células de `knn.ipynb` em ordem (ajustando o caminho do `tumores.csv` se estiver rodando localmente, conforme observação acima).

> O arquivo `tumores.csv` precisa estar acessível no caminho informado em `np.loadtxt()` para que a leitura dos dados funcione corretamente.

## Sobre o dataset `tumores.csv`

Dataset simplificado com 19 amostras de tumores, contendo:

- **tamanho** (cm)
- **pontuacao_textura**
- **classe** (0 = Benigno, 1 = Maligno)

Usado para classificar um novo tumor com base na similaridade (distância euclidiana) com os tumores já conhecidos no dataset.

## Observações

Este projeto tem fins **didáticos**, com foco em compreender o funcionamento do algoritmo KNN (cálculo de distância, seleção dos vizinhos mais próximos e classificação por voto majoritário) implementando a lógica manualmente, em vez de utilizar bibliotecas prontas de Machine Learning. O valor de `k` (número de vizinhos considerados) foi fixado em 5 para o exemplo de previsão.
