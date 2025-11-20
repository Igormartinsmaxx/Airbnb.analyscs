%pip install pandas
"""Projeto Airbnb"""

import os
import pandas as pd

# Definir o caminho correto do arquivo CSV (substitua pelo nome correto do arquivo se necessário)
file_path = r"C:\\Users\silva\\OneDrive\\Área de Trabalho\\Aula Python\\Exe_Igor.py\\testeprecificacao.csv"
# Verificar se o arquivo existe
if os.path.exists(file_path):
    # Carregar os dados no pandas
    df = pd.read_csv(file_path)
    if os.path.exists(file_path):
    # Carregar os dados no pandas
    df = pd.read_csv(file_path)
else:
    display("Erro: Arquivo não encontrado. Verifique o caminho.")
    # Exibir as primeiras 5 linhas do DataFrame
df = pd.read_csv(file_path)    
display("Primeiras 5 linhas do dataset:")
display(df.head())
# Exibir informações gerais do dataset (tipos de dados e valores não nulos)
display("\nInformações gerais do dataset:")
display(df.info())
# Exibir estatísticas descritivas do dataset (apenas para colunas numéricas)
display("\nEstatísticas descritivas:")
display(df.describe())
display("Erro: Arquivo não encontrado. Verifique o caminho.")
#1. Faça uma análise exploratória dos dados (EDA), demonstrando as principais
#características entre as variáveis e apresentando algumas hipóteses de negócio
#relacionadas. 
import matplotlib.pyplot as plt
import seaborn as sns

# Configuração do estilo do gráfico
sns.set_style("whitegrid")

# Criando o histograma da distribuição de preços
plt.figure(figsize=(10, 5))
sns.histplot(df['price'], bins=50, kde=True)

# Limitando o eixo x para melhor visualização (opcional)
plt.xlim(0, 500)

# Adicionando títulos e rótulos
plt.title("Distribuição dos preços dos imóveis")
plt.xlabel("Preço (USD)")
plt.ylabel("Frequência")

# Exibindo o gráfico
plt.show()
import matplotlib.pyplot as plt
import seaborn as sns

# Configuração do estilo do gráfico
sns.set_style("whitegrid")

# Criando o gráfico de barras para os tipos de acomodação
plt.figure(figsize=(8, 4))
sns.countplot(data=df, x='room_type', palette="pastel", order=df['room_type'].value_counts().index)

# Adicionando títulos e rótulos
plt.title("Distribuição dos Tipos de Acomodação")
plt.xlabel("Tipo de Acomodação")
plt.ylabel("Quantidade de Imóveis")

# Exibindo o gráfico
plt.show()
import matplotlib.pyplot as plt
import seaborn as sns

# Configuração do estilo do gráfico
sns.set_style("whitegrid")

# Criando o boxplot para visualizar a distribuição de preços por grupo de bairro
plt.figure(figsize=(10, 5))
sns.boxplot(data=df, x='bairro_group', y='price', showfliers=False, palette="pastel")

# Limitando o eixo y para melhor visualização (opcional)
plt.ylim(0, 500)

# Adicionando títulos e rótulos
plt.title("Preço dos Imóveis por Grupo de Bairro")
plt.xlabel("Grupo de Bairro")
plt.ylabel("Preço (USD)")

# Exibindo o gráfico
plt.show()
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Selecionar apenas colunas numéricas
numeric_df = df.select_dtypes(include=['number'])

# Calcular a matriz de correlação
correlation_matrix = numeric_df.corr()

# Criar o mapa de calor
plt.figure(figsize=(10, 6))
sns.heatmap(correlation_matrix, annot=True, fmt=".2f", cmap="coolwarm", linewidths= 0.5)

# Exibir o gráfico
plt.title("Matriz de Correlação")
plt.show()
