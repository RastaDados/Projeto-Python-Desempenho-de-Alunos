<h1>Projeto Dados - Desempenho de Alunos</h1>

<h1>Introdução</h1>

Este projeto tem como objetivo analisar dados acadêmicos de estudantes, explorando fatores que influenciam o desempenho escolar e criando um modelo preditivo de notas. 

<hr>
<br>

<h1>Entendendo a base de Dados</h1>
Os dados contêm as seguintes colunas:

<b>Socioeconomic Score:</b> 

– Índice socioeconômico dos alunos.

<b>Study Hours:</b> 

– Horas de estudo diárias.

<b>Sleep Hours:</b> 

– Horas de sono diárias.

<b>Attendance (%):</b> 

– Percentual de presença nas aulas.

<b>Grades:</b> 

– Notas dos alunos.

2. Estrutura do Dashboard

O dashboard possui três páginas principais:

Desempenho Acadêmico - Análise geral das notas e presença dos alunos.

Hábitos dos Alunos - Estudo do impacto das horas de estudo, sono e nível socioeconômico nas notas.

Predição de Notas - Uso de Machine Learning para prever notas com base em diferentes fatores.

3. Instalação e Execução

Para rodar este projeto, siga os passos:

3.1. Instalar dependências

pip install streamlit pandas plotly scikit-learn

3.2. Executar o dashboard

streamlit run nome_do_arquivo.py

4. Estrutura do Código

4.1. Importação de Bibliotecas

O projeto utiliza as seguintes bibliotecas:

import streamlit as st
import pandas as pd
import plotly.express as px
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_absolute_error

4.2. Leitura dos Dados

Os dados são carregados diretamente de um arquivo CSV:

df = pd.read_csv("datacsv.csv")

4.3. Criação do Menu Lateral

A interface possui um menu lateral para seleção das páginas:

st.sidebar.title("Dashboard Educacional")
pagina = st.sidebar.radio("Escolha uma página:", ["Desempenho Acadêmico", "Hábitos dos Alunos", "Predição de Notas"])

5. Detalhamento das Páginas

5.1. Página 1: Desempenho Acadêmico

Distribuição de Notas: Histograma das notas.

Relação entre Presença e Notas: Gráfico de dispersão com regressão.

Boxplot das Notas: Distribuição geral das notas.

5.2. Página 2: Hábitos dos Alunos

Impacto das Horas de Estudo nas Notas: Gráfico de dispersão.

Impacto das Horas de Sono nas Notas: Análise de correlação.

Impacto do Nível Socioeconômico nas Notas: Relação entre situação financeira e desempenho.

5.3. Página 3: Predição de Notas

Treinamento do Modelo: Uso de Random Forest.

Erro Médio Absoluto: Avaliação do modelo.

Interface de Previsão: Entrada de dados e retorno da nota prevista.

6. Modelo de Machine Learning

O modelo preditivo é um Random Forest Regressor, treinado com os seguintes recursos:

X = df[["Socioeconomic Score", "Study Hours", "Sleep Hours", "Attendance (%)"]]
y = df["Grades"]

Após a divisão dos dados:

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
model = RandomForestRegressor(n_estimators=100, random_state=42)
model.fit(X_train, y_train)

A avaliação do modelo é feita com o erro médio absoluto (MAE):

mae = mean_absolute_error(y_test, y_pred)
st.write(f"Erro Médio Absoluto do Modelo: {mae:.2f}")

7. Conclusão

Este projeto fornece uma visão detalhada do desempenho acadêmico e oferece uma ferramenta interativa para análise e previsão de notas. O uso de Streamlit garante uma experiência dinâmica e intuitiva para os usuários. 🚀
