# Analise_imobiliaria
📊 Análise de Dados de Aluguel com Python e Pandas
Este projeto tem como objetivo realizar uma análise exploratória sobre um conjunto de dados referente a imóveis para aluguel. Utilizamos a biblioteca Pandas para carregar, transformar e visualizar as informações, além de fazer limpezas e agrupamentos estratégicos para compreensão do mercado.

📁 Arquivo utilizado
aluguel.csv: arquivo com os dados brutos contendo informações sobre os imóveis.

🧰 Bibliotecas utilizadas
python
Copy
Edit
import pandas as pd
🔍 Leitura e primeiros insights
📥 Leitura dos dados
python
Copy
Edit
pd.read_csv("aluguel.csv", sep=';')
O separador utilizado no CSV é ;, comum em dados formatados para padrões brasileiros.

👀 Visualização inicial
python
Copy
Edit
dados.head(10)   # Primeiras 10 linhas  
dados.tail(10)   # Últimas 10 linhas  
📌 Informações básicas
python
Copy
Edit
dados.shape       # (linhas, colunas)
dados.columns     # Nomes das colunas
dados.info()      # Tipos de dados e não nulos
🎯 Seleção de colunas específicas
python
Copy
Edit
dados['Tipo']                      # Uma coluna
dados[['Quartos','Valor']]        # Múltiplas colunas
📊 Análise exploratória
💰 Valor médio de aluguel por tipo de imóvel
python
Copy
Edit
dados.groupby('Tipo')['Valor'].mean()
📈 Visualização dos dados
python
Copy
Edit
df_preco_tipo = dados.groupby('Tipo')[['Valor']].mean().sort_values('Valor')
df_preco_tipo.plot(kind='barh', figsize=(14,10), color='purple')
Algumas categorias apresentaram valores discrepantes por serem comerciais, e isso pode interferir em modelos futuros de machine learning. Por isso, decidimos separar imóveis comerciais dos residenciais.

🧹 Limpeza dos dados
🏢 Imóveis comerciais a remover:
python
Copy
Edit
imoveis_comerciais = ['Conjunto Comercial/Sala', 'Prédio Inteiro', 'Loja/Salão',
                      'Galpão/Depósito/Armazém', 'Casa Comercial', 'Terreno Padrão',
                      'Loja Shopping/ Ct Comercial', 'Box/Garagem', 'Chácara',
                      'Loteamento/Condomínio', 'Sítio', 'Pousada/Chalé', 'Hotel', 'Indústria']
📤 Removendo do DataFrame
python
Copy
Edit
df = dados.query('@imoveis_comerciais not in Tipo')
🔁 Repetindo o gráfico com os dados limpos
python
Copy
Edit
df_preco_tipo = df.groupby('Tipo')[['Valor']].mean().sort_values('Valor')
df_preco_tipo.plot(kind='barh', figsize=(14,10), color='purple',
                   xlabel='Valores', ylabel='Tipos de imóvel')
📉 Distribuição percentual por tipo
python
Copy
Edit
df.Tipo.value_counts(normalize=True).to_frame().sort_values('Tipo')
python
Copy
Edit
df_percentual_tipo = df.Tipo.value_counts(normalize=True).to_frame().sort_values('Tipo')
df_percentual_tipo.plot(kind='bar', figsize=(14,10), color='green',
                        xlabel='Tipos', ylabel='Percentual')
Observamos que apartamentos representam cerca de 80% da base. Por isso, decidimos manter apenas eles para análises futuras.

🏠 Foco: Apartamentos
python
Copy
Edit
df_apartamento = df.query('Tipo == "Apartamento"')
✅ Conclusão
Neste projeto:

Fizemos uma análise inicial dos dados de aluguel;

Identificamos distorções causadas por imóveis comerciais;

Limpamos os dados para focar em imóveis residenciais;

Visualizamos distribuições e agrupamos por tipo de imóvel;

Isolamos os apartamentos para aprofundar as análises.

Este dataset agora está pronto para uso em modelos de machine learning, análises preditivas ou dashboards interativos.

🚀 Futuras implementações
Visualização com matplotlib ou seaborn;

Análise geográfica (se houver dados de localização);

Criação de modelos preditivos de preços;

Implementação de dashboards com Plotly Dash ou Streamlit.

📎 Requisitos
Python 3.7+

Pandas

Instalação das dependências:

bash
Copy
Edit
pip install pandas
