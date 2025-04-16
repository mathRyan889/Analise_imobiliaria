# Analise_imobiliaria
📊 Análise de Dados de Aluguel
Este projeto tem como objetivo explorar e entender melhor um conjunto de dados de imóveis para aluguel utilizando a biblioteca Pandas. A ideia é limpar os dados, fazer algumas análises básicas e visualizar informações importantes sobre o mercado de aluguel.

🔍 O que foi feito
Leitura do arquivo de dados: carregamos um arquivo .csv com informações de imóveis disponíveis para aluguel.

Visualização inicial: analisamos as primeiras e últimas linhas para entender a estrutura da base de dados.

Análise geral: identificamos quantas linhas e colunas existem, quais são os nomes das colunas e que tipo de informação cada uma traz.

Seleção de dados: extraímos colunas específicas como tipo de imóvel, número de quartos e valor do aluguel para fazer análises mais focadas.

Cálculo de médias: descobrimos qual o valor médio do aluguel por tipo de imóvel.

Visualização com gráficos: criamos gráficos de barras para visualizar melhor os dados, como a média de preço por tipo de imóvel.

🧹 Limpeza de dados
Durante a análise, percebemos que alguns tipos de imóveis (como salas comerciais, galpões, hotéis etc.) tinham valores muito altos e acabavam distorcendo os resultados. Por isso, removemos esses imóveis da base para focar apenas em residências.

📈 Foco em apartamentos
Após a limpeza, percebemos que a maioria dos imóveis da base são apartamentos — cerca de 80%. Então, decidimos focar só neles para deixar a análise mais consistente e alinhada com futuros projetos, como modelos de machine learning.

🎯 Próximos passos
Explorar mais visualizações;

Criar modelos que prevejam o valor do aluguel com base nas características do imóvel;

Usar ferramentas como Streamlit para criar dashboards interativos.

📁 Requisitos
Ter o Python instalado;

Ter a biblioteca Pandas instalada para manipulação de dados.

Instalação das dependências:

bash
Copy
Edit
pip install pandas
