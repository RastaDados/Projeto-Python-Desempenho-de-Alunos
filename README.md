<h1>Projeto Dados - Desempenho de Alunos</h1>

<h1>Introdução</h1>

Este projeto tem como objetivo analisar dados acadêmicos de estudantes, explorando fatores que influenciam o desempenho escolar e criando um modelo preditivo de notas. 

<hr>
<br>

<h1>Entendendo a base de Dados</h1>

Os dados contêm as seguintes colunas:

<br>

<b>Socioeconomic Score:</b> 

- Índice socioeconômico dos alunos.

<b>Study Hours:</b> 

- Horas de estudo diárias.

<b>Sleep Hours:</b> 

- Horas de sono diárias.

<b>Attendance (%):</b> 

- Percentual de presença nas aulas.

<b>Grades:</b> 

- Notas dos alunos.

<hr>
<br>

<h1>Estrutura do Dashboard</h1>

O dashboard possui três páginas:

<b>Desempenho Acadêmico:</b> 

- Análise geral das notas e presença dos alunos.

<b>Hábitos dos Alunos:</b> 

- Estudo do impacto das horas de estudo, sono e nível socioeconômico nas notas.

<b>Predição de Notas:</b> 

- Uso de Machine Learning para prever notas com base em diferentes fatores.

<hr>
<br>

<h1>Estrutura do Código</h1>

<h2><b>Importação de Bibliotecas</b></h2>

O projeto utiliza as seguintes bibliotecas:

```python
import streamlit as st
import pandas as pd
import plotly.express as px
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_absolute_error
```

<br>

<h2><b>Leitura dos Dados</h2></b>

Os dados são carregados diretamente de um arquivo CSV:

```python
df = pd.read_csv("datacsv.csv")
```

<br>

<h2><b>Criação do Menu Lateral</b></b>

A interface possui um menu lateral para seleção das páginas:

```python
st.sidebar.title("Dashboard Educacional")
pagina = st.sidebar.radio("Escolha uma página:", ["Desempenho Acadêmico", "Hábitos dos Alunos", "Predição de Notas"])
```

<h1>Detalhamento das Páginas</h1>

<h2><b>Desempenho Acadêmico</b></h2>

<h3><b>Distribuição de Notas</b></h3>

```python
 fig1 = px.histogram(df, x="Grades", nbins=20, title="Distribuição de Notas")
    st.plotly_chart(fig1)
```
![Graf 1 pag 1](https://github.com/user-attachments/assets/b004a902-141d-4660-9baf-6fc6f4fed384)

<br>

<h3><b>Relação entre Presença e Notas</b></h3> 

```python
 fig2 = px.scatter(df, x="Attendance (%)", y="Grades", trendline="ols", title="Relação entre Presença e Notas")
    st.plotly_chart(fig2)
``` 
![Graf 2 pag 1](https://github.com/user-attachments/assets/0fc3b7bb-c034-4ce4-b474-dfa7bc8feae0)

<br>

<h3><b>Distribuição geral das notas</b></h3>

```python
fig3 = px.box(df, y="Grades", title="Boxplot das Notas")
    st.plotly_chart(fig3)
```
![Graf 3 pag 1](https://github.com/user-attachments/assets/1a3f7415-b334-4237-b6de-cc7235c8e822)

<br>

<h2><b>Hábitos dos Alunos</b></h2>

<h3><b>Impacto das Horas de Estudo nas Notas</b></h3>

```python
 fig4 = px.scatter(df, x="Study Hours", y="Grades", trendline="ols", title="Impacto das Horas de Estudo nas Notas")
    st.plotly_chart(fig4)
```
![Graf 1 pag 2](https://github.com/user-attachments/assets/349d5730-7e59-4de3-ae18-0cc59aae6fb5)

<h3><b>Impacto das Horas de Sono nas Notas</b></h3>

```python
fig5 = px.scatter(df, x="Sleep Hours", y="Grades", trendline="ols", title="Impacto das Horas de Sono nas Notas")
    st.plotly_chart(fig5)
```
![Graf 2 pag 2](https://github.com/user-attachments/assets/a90a7a9b-6868-4c12-9d07-392bc15d8aa4)

<br>

<h3><b>Impacto do Nível Socioeconômico nas Notas</b></h3>

```python
fig6 = px.scatter(df, x="Socioeconomic Score", y="Grades", trendline="ols", title="Impacto do Nível Socioeconômico nas Notas")
    st.plotly_chart(fig6)

```
![Graf 3 pag 2](https://github.com/user-attachments/assets/2f530d13-a19a-441a-9b88-cc703ed985c4)


<hr>
<br>

<h2><b>Predição de Notas</b></h2>

- <b>Treinamento do Modelo:</b> Uso de Random Forest.

- <b>Erro Médio Absoluto:</b> Avaliação do modelo.

- <b>Interface de Previsão:</b> Entrada de dados e retorno da nota prevista.

<br>

<h2><b>Modelo de Machine Learning</b></h2>

O modelo preditivo é um Random Forest Regressor, treinado da seguinte forma:

```python
X = df[["Socioeconomic Score", "Study Hours", "Sleep Hours", "Attendance (%)"]]
y = df["Grades"]
```

<h3><b>Após a divisão dos dados:</b></h3>

```python
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
model = RandomForestRegressor(n_estimators=100, random_state=42)
model.fit(X_train, y_train)
```

<h3><b>A avaliação do modelo é feita com o erro médio absoluto (MAE):</b></h3>

```python
mae = mean_absolute_error(y_test, y_pred)
st.write(f"Erro Médio Absoluto do Modelo: {mae:.2f}")
```

<br>

<h3><b>Resultado do modelo</b></h3>
![Graf 1 pag 3](https://github.com/user-attachments/assets/6cbccd38-2f87-402e-b3c1-d72543e3fc47)

<hr>
