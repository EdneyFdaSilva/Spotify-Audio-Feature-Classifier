# 🎵 Spotify Audio Feature Classifier (Predição de Popularidade)

Este projeto implementa e avalia modelos de Machine Learning (Regressão Linear, Naive Bayes, SVM e KNN) para prever a popularidade de faixas musicais com base em seus atributos de áudio (Danceability, Energy, Tempo, etc.) fornecidos pelo Spotify. O modelo final de classificação é um **K-Nearest Neighbors (KNN)** otimizado via *Randomized Search* e *Cross-Validation*.

---

## 🚀 Setup e Instalação

Para rodar o projeto, você precisará dos arquivos: `Trabalho_M8_final_v3.ipynb`, `app.py` e `best_knn_model_f1_0.7296.joblib`.

### 1. Requisitos de Biblioteca

Use o arquivo `requirements.txt` para instalar todas as dependências:

```bash
# Instala as dependências necessárias
pip install -r requirements.txt


---

## Fonte de Dados

O notebook utiliza o dataset original do Kaggle: Spotify Tracks Dataset.

Link: https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset/data

O arquivo CSV deve ser baixado e nomeado como dataset.csv.


---

## 📚 Passo a Passo: Uso do Notebook (.ipynb)

O notebook Trabalho_M8_final_v3.ipynb contém todas as etapas de EDA (Análise Exploratória de Dados), Pré-processamento, Treinamento e Otimização dos modelos.

Uso no Google Colab
Upload: Faça o upload do notebook (Trabalho_M8_final_v3.ipynb) e do arquivo de dados (dataset.csv) para o seu Google Drive.

Execução: Abra o notebook no Google Colab.

Montar Drive: Execute a primeira célula para montar o Google Drive e garantir o acesso aos dados:

Python

from google.colab import drive
drive.mount('/content/drive')
Ajustar Caminhos: Verifique se o caminho para o pd.read_csv(...) na seção "Importação dos Dados" está correto, apontando para o seu arquivo dataset.csv dentro do /content/drive/MyDrive/.

Execução Sequencial: Execute todas as células em ordem. A otimização final do KNN usará RandomizedSearchCV, que pode ser demorado (veja dicas de otimização no notebook).


---

## Uso em Ambiente Local (Conda/Virtual Env)

Criação do Ambiente (Conda):

Bash

# Cria um novo ambiente
conda create -n spotify-ml python=3.10
# Ativa o ambiente
conda activate spotify-ml
# Instala as dependências
pip install -r requirements.txt
Inicialização: Inicie o Jupyter Notebook ou Jupyter Lab dentro do ambiente ativado.

Execução: Abra e execute todas as células do Trabalho_M8_final_v3.ipynb sequencialmente.


---

## 🌐 Passo a Passo: Uso da Aplicação Streamlit

A aplicação Streamlit permite interagir com o modelo KNN otimizado, inserindo características de áudio e obtendo a previsão de popularidade em tempo real.

⚠️ Requisitos
O arquivo do modelo (best_knn_model_f1_0.7296.joblib) deve estar acessível.

O arquivo app.py deve conter o caminho correto para o arquivo .joblib.

Uso no Google Colab (Recomendado)
Devido às restrições do Colab, o Streamlit deve ser executado com pyngrok para criar um túnel público.

Célula 1: Salvar app.py e Instalar Ngrok Execute a primeira célula que contém a instalação e o comando %%writefile app.py. Certifique-se de que o caminho LOAD_FILENAME está completo (Ex: /content/drive/MyDrive/best_knn_model_f1_0.7296.joblib).

Célula 2: Autenticação Ngrok (Obrigatório) Execute a célula onde você define e configura seu token de autenticação Ngrok.

Python

from pyngrok import ngrok
ngrok.set_auth_token("SEU_NGROK_AUTHTOKEN_AQUI")
Célula 3: Iniciar o Aplicativo Execute a célula final para iniciar o Streamlit em segundo plano e criar o link público. Clique no link fornecido para interagir com a aplicação.

Uso em Ambiente Local
Arquivos: Certifique-se de que app.py e best_knn_model_f1_0.7296.joblib estão na mesma pasta local.

Ajuste de Caminho: No app.py, o LOAD_FILENAME pode ser simplificado para o nome do arquivo, já que ambos estão no mesmo diretório:

Python

LOAD_FILENAME = 'best_knn_model_f1_0.7296.joblib' 
Execução: Abra o terminal na pasta do projeto e execute:

Bash

streamlit run app.py
O navegador abrirá automaticamente a interface (geralmente em http://localhost:8501).