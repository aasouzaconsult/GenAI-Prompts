# 💻> Prompts para Analista de Dados
Abaixo, alguns prompts que podem ajudar no dia a dia de um analista de dados.

Esta dividido nas seguintes seções:
- Excel / Sheets
- Requisitos de Negócios
- KPI´s
- SQL
- Python
- Interpretação de Resultados - Machine Learning
- Power BI | DAX | M
- Criação de Imagem (Extra)

Espero que gostem! Vamos lá?
Mas antes, algumas dicas...

# Dica Inicial

## Independente de Modelo ou Plataforma
Aqui você pode colocar estes prompts no [Gemini](https://gemini.google.com/), no [ChatGPT](https://chat.openai.com/), [Copilot](https://copilot.cloud.microsoft/), [Claude AI](https://claude.ai/) ou qualquer outro que irá funcionar, a resposta vai variar dependendo do modelo.

## Sempre uma Conversa Nova
Sugiro que cada tópico ou assunto que for perguntar para as *generative ai* sejam feitas de forma distinta - sempre abra uma nova conversa, não misturar assuntos!

## Qualidade de Prompts
Sempre detalhe bem sua necessidade! Costumo dizer que se você desenvolver bons prompts eles irão trazer os resultados que estão buscando.

Agora sim, vamos lá...


# No Excel / Sheets 📊📄

## Explicação de comando
```
Você pode me explicar como o comando PROCV funciona no Excel?
```
```
Agora poderia explicar como se estivesse descrevendo para uma criança?
```
```
Você pode fornecer um exemplo usando alguns dados de amostra e mostrar a sintaxe da fórmula?
```

## Vinho
```
Estou analisando uma amostra de dados de vinhos e gostaria de entender a distribuição dos vinhos por faixa de preço. Qual seria a melhor forma de visualizar isso no Excel?
```

## Site
```
Estou analisando os dados do meu website e gostaria de mostrar a evolução do total de exibições de página e das taxas de conversão ao longo do tempo. Qual seria a melhor forma de visualizar isso no Excel?
```

## Acidentes
```
Estou analisando um conjunto de dados contendo registros de acidentes automobilísticos e gostaria de visualizar os dados no Excel para mostrar quando os acidentes têm maior probabilidade de ocorrer, por hora do dia e dia da semana. Você pode sugerir o melhor tipo de visual para usar?
```

## Erro em fórmula ❌🔢
```
Estou usando a fórmula do Excel abaixo para contar o número de palavras na célula D2, mas está retornando um #VALUE! erro no Excel. Você pode me dizer como consertar isso?

=LEN(TRIM(D2))-LEN(SUBSTITUTE(TRIM(D2),"","")+1)
```

```
Estou tentando escrever uma fórmula do Excel para recuperar o preço correto de uma matriz de valores. Aqui são os detalhes:
As células C3:G7 contêm os preços dos produtos
As células B3:B7 contêm tipos de produtos
As células C2:G2 contêm tamanhos

Os usuários podem selecionar um produto na célula B10 e um tamanho na célula C10, e gostaria de retornar o preço correto na célula E10. Você pode me dizer porque a fórmula abaixo não está retornando o valor correto?

= INDEX(C3:G7,MATCH(B10,B3:B7), MATCH(C10,C2:G2))
```

## Montando um passo a passo...
```
Tenho uma tabela Excel contendo os seguintes campos: Order ID Product Quantity Retail Price Revenue Order Size.
Preciso criar uma Tabela Dinâmica mostrando a receita média (average revenue) para cada tamanho de pedido(Order Size), formatada como moeda (USD). Forneça instruções claras e passo a passo para criar a Tabela Dinâmica usando o Excel para Office 365 em um PC.

Aqui esta um exemplo das primeiras 15 linhas de dados...

Order ID Product Quantity Retail Price Revenue Order Size
44016 WORLD WAR 2 GLIDERS ASSTD DESIGNS 5 $0.32 $1.60 Small
24854 JUMBO BAG RED RETROSPOT 25 $247 $6176 Medium
37210 ASSORTED COLOUR BIRD ORNAMENT 75 $1.72 $129.15 Large
14622 POPCORN HOLDER 6 $1.01 $6.07 Small 36868 PACK OF 72 RETROSPOT CAKE CASES 10 $0.76 $7.56 Small
37375 WHITE HANGING HEART T-LIGHT HOLDER 5 $3.20 $16.02 Small
45660 RABBIT NIGHT LIGHT 100 $2.38 $237.54 Large
27305 MINI PAINT SET VINTAGE 15 $0.78 $11.72 Medium
17826 PACK OF 12 LONDON TISSUES 1 $0.45 $0.45 Small
31194 PACK OF 60 PINK PAISLEY CAKE CASES 75 $0.74 $55.59 Large
48711 VICTORIAN GLASS HANGING T-LIGHT 15 $1.65 $24.77 Medium
20858 ASSORTED COLOURS SILK FAN 2 $1.07 $2.13 Small
21517 BROCADE RING PURSE 2 $1.06 $2.13 Small
31271 RED HARMONICA IN BOX 250 Medium
```

## Colabore na preparação de dados e EDA
```
Acabei de exportar um arquivo csv bruto contendo dados de tráfego da web. Você poderia agir como um engenheiro de garantia de qualidade de dados e fornecer um plano passo a passo para me ajudar no controle de qualidade e preparar meus dados para análise?
```
```
Vejo alguns valores ausentes, como devo lidar com eles?
```
```
Ok, meus dados estão bons. Agora, você pode fornecer um plano para conduzir alguns perfis de dados e análises exploratórias no Excel?
```

## Gerar conjuntos de dados de amostra

```
Sou um analista de dados contratado recentemente para uma empresa de RH, procurando dados de amostra que possa usar para praticar. Gere um conjunto de dados de amostra no formato CSV contendo campos comuns que os analistas de RH normalmente encontram no trabalho.

Modifique também a amostra para incluir alguns problemas comuns de controle de qualidade de dados e descreva quais alterações específicas você fez.
```

## Google Sheets - Nome completo do mês
```
Você pode me ajudar a escrever uma fórmula do Planilhas Google (Google Sheets) que retorne o nome completo do mês (janeiro, fevereiro etc.) de uma data na célula B2?
```

## Google Sheets - Um mais complexo e em inglês
```
Can you help me write a Google Sheets formula to "unpivot" data like with Pandas melt method?
```

*"traduzindo" - Você pode me ajudar a escrever uma fórmula do Planilhas Google para "não dinamizar" os dados, como no método de fusão do Pandas?*

```
Awesome! Let me add a bit more context around the situation so the formula contains the right cell references. This is my source data in columns A-H:

Category | Jan | Feb | Mar | Apr | May | Jun | Jul 
Toys 1,918 2,106 | 2,377 | 2,832 2,996 12,597 11,464 
Apparel | 1,431 | 1,334 11,338 | 1,286 | 1,1811 1,160 | 1,146 
Sports | 7491733 176711,037194511,20911,296 
Games 1976 1901 | 895 | 1,002 1892 1,023 | 998 
Outdoors | 351|339|5171653|710|6311657

And this is the output structure I want:

Category | Month | Sales
```
*"Traduzindo" - Incrível!  Deixe-me adicionar um pouco mais de contexto em torno da situação para que a fórmula contenha as referências de célula corretas.  Estes são meus dados de origem nas colunas A-H:...*

# Requisitos ✅📋

## Enquiquecer documentação
```
Fórum Data Lake
- Cultura baseada em dados (data-driven)
- Quanto tempo para consumir dados (Contábil, Receitas)
- Dores
	- Marketing
		- Campanhas
			- Vips
			- Clientes recorrentes
		- perfil de clientes por loja
		- campanha dificuldades
		- análise por produto X, por exemplo
		- Por canal
		- ML?
	- Vendas
		- B2B
			- Falta de acompanhamento
			- Sugerir antes do cliente precisar
Sistemas
- A caminho do Lake
	- Shopify
	- Protheus
- Outros
	- Sellbie

Enriquecer essa especificação de requisitos e colocar num formato padrão de especificação (gerar em formato .md)
```

## Pedindo ajuda sobre requisito...
```
Preciso elaborar perguntas para uma análise de requisitos para um setor de observatório de saúde (sono, absenteismo). Quais perguntas você faria?
```

[mais informações](https://github.com/aasouzaconsult/GenAI-Prompts/blob/main/requisitos_gpt.md)

## Comparar artigos (gerar resumo)

[Cohere Playgrourd](https://dashboard.cohere.com/playground/generate) (modelo específico para sumarização de conteúdo)

Nóticias:
- https://techcrunch.com/2023/08/29/general-motors-to-use-google-ai-chatbot-for-its-onstar-service/
- https://www.theverge.com/23845856/google-notebooklm-tailwind-ai-notes-research

**Colocar o resumo gerado na ferramenta acima no ChatGPT:**

💻> Irei te enviar o resumo de dois conteúdos em inglês e preciso que você extraia as principais entidades e suas relações de cada um dos resumos. A partir disso crie um diagrama, em português brasileiro, no formato mermaid mostrando a relação entre estas entidades dos dois resumos.

Resumo 1:
"
"

Resumo 2:
"
"

**Para visualizar**
- https://mermaid.live/
    - colar o código e remover os parenteses


# KPIS 📊📈🔑
```
Você atuará como um especialista em Análise de Dados. Você estará me treinando, como um colega de trabalho júnior que está aprendendo Análise de Dados. Você pode explicar a diferença entre um KPI e uma métrica?
```

```
Explique como se fosse para uma criança
```

```
O projeto que estamos atuando é um projeto de vendas. Nossas vendas tem informações de data da venda, do cliente, do produto, quantidade vendida, preço unitário, preço total, vendedor, o percentual de comissão do vendedor... Quais os principais KPI´s que podemos tirar deste cenário.

Gentileza montar uma base de dados (SQL Server) fictícia com estes dados e os KPI´s que indicar, crie as fórmulas em SQL para chegarmos neles
```

**KPI de RH**
```
Você como um grande analista de dados do ramo de rh, monte uma pequena base de dados de pessoa em SQL Server, e informe os principais indicadores (KPI´s) de rh e a formula para calcular cada um deles (pode ser um select para cada uns dos KPIs)
```

[mais informações](https://medium.com/blog-do-zouza/decifrando-kpis-a-f%C3%B3rmula-do-sucesso-para-seu-neg%C3%B3cio-d6a34e52ea9)

[exemplo](https://github.com/aasouzaconsult/GenAI-Prompts/blob/main/kpis.md)

# SQL 🗃️🔍

## Conceitos
```
Você atuará como um especialista em SQL. Você estará me treinando, como um colega de trabalho júnior que está aprendendo SQL e precisa de ajuda. Você pode explicar a diferença entre um LEFT JOIN e um INNER JOIN no SQL?
```

```
Explique a diferença entre os tipos de dados int e smallint
```

## Explicação de Comandos
```sql
Você atuará como um Analista Sênior especialista em SQL. Você estará me ajudando, um analista júnior de sua equipe, a entender as consultas SQL que usaremos juntos no trabalho.

Você pode me explicar a seguinte instrução SQL?

SELECT
  sa.attribution_clean,
  COUNT(s.id) AS students,
  SUM(r.dollars) AS total spend, SUM(r.dollars)/COUNT(s.id) AS spend_per_student
FROM Students s
LEFT JOIN StudentAttribution sa ON sa student_id = s.id
LEFT JOIN Revenue r ON r.student_id = s.id
GROUP BY 1
ORDER BY 2 DESC
```

## Documentação 📚📑
```sql 
Documente detalhadamente o que está sendo feito no SQL abaixo e forneça essa documentação em formato de lista com marcadores.

SELECT c.estadocliente                   AS Estado,
       p.nomeproduto                     AS nomeproduto,
       ROUND(AVG(v.quantidadevendas), 4) AS quantidade_media
  FROM dw.dim_cliente c
  JOIN dw.fato_vendas v ON v.codigocliente = c.codigocliente
  JOIN dw.dim_produto p ON p.codigoproduto = v.codigoproduto
 WHERE 1 = 1
   AND v.codigostatusvenda = 1 -- Concluído
 GROUP BY c.estadocliente, p.nomeproduto
 ORDER BY c.estadocliente, p.nomeproduto;
```

## Indentação e Comentários ✍️🗂️

```sql
Você atuará como um Analista Sênior especialista em SQL. Você estará me ajudando, um analista júnior em sua equipe. entender consultas SQL que usaremos juntos no trabalho.

Você poderia adicionar indentação, comentários à consulta a seguir para facilitar o entendimento de outros analistas?

CREATE TEMPORARY TABLE tmp_students AS SELECT id, name FROM students;
CREATE TEMPORARY TABLE tmp_scores AS SELECT student_id, score FROM exam_scores;

WITH score_avg AS (SELECT student_id, AVG(score) OVER (PARTITION BY student_id) AS avg_score FROM tmp_scores)
SELECT s.name, ts.score, sa.attribution, sa.attribution_clean, score_avg.avg_score
FROM tmp_students s
LEFT JOIN tmp_scores ts ON s.id = ts.student_id
LEFT JOIN (SELECT student_id, MAX(attribution) AS attribution, MAX(attribution_clean) AS attribution_clean FROM student_attributions GROUP BY student_id) sa ON s.id = sa.student_id
JOIN score_avg ON ts.student_id = score_avg.student_id
ORDER BY score_avg.avg_score DESC;
```

## Identificação de Erros ❌🔢
```sql
Você atuará como um Analista Sênior especialista em SQL. Você estará me ajudando, um analista júnior de sua equipe, a entender as consultas SQL que usaremos juntos no trabalho.

Estou com um erro na minha consulta sql. Você pode me ajudar a dizer o que pode estar errado?

SELECT s.name,  -- Nome do estudante
       ts.score,  -- Pontuação da nota
       sa.attribution,  -- Atribuição do estudante
       sa.attribution_clean,  -- Atribuição limpa do estudante
       score_avg.avg_score  -- Média de pontuação das notas do estudante
FROM tmp_students s
-- Combinação à esquerda dos estudantes com suas notas
LEFT JOIM tmp_scores ts ON s.id = ts.student_id
-- Combinação à esquerda das atribuições dos estudantes, usando a subconsulta para obter a atribuição máxima
LEFT JOIN (
    SELECT student_id,
           MAX(attribution) AS attribution,
           MAX(attribution_clean) AS attribution_clean
    FROM student_attributions
    GROUP BY student_id
) sa ON s.id_a = sa.student_id
-- Combinação interna (INNER JOIN) com a subconsulta que calcula as médias de pontuação
JOIN score_avg ON ts.student_id = score_avg.student_id
-- Ordena os resultados pela média de pontuação das notas em ordem decrescente
ORDER BY score_avg.avg_score DESC;
```

## Montando um cenário
```
Você atuará como um especialista em SQL e me ajudará, um não especialista em SQL, a criar algumas consultas para extrair relatórios de nosso banco de dados.

Temos 2 tabelas com as quais precisamos trabalhar.
A primeira tabela chama-se Alunos. Tem as seguintes colunas.. 
student_id | created_time | segment | student_goal

A segunda tabela chama-se Receita. Tem as seguintes colunas...
revenue_id | dollars_usd | refunded_dollars_usd | student_id | created_time

Você pode criar uma consulta para obter uma lista dos alunos mais valiosos em termos de quanta receita (revenue) eles geraram?
```
```
Agora você pode escrever uma consulta para obter o número de alunos em cada segmento e quanta receita cada segmento gerou?
```

## Melhoria de Desempenho
```sql
Você atuará como um especialista em SQL e ajudará a mim, um membro júnior de sua equipe, a entender como otimizar minha consulta SQL para melhorar seu desempenho.

Você pode me ajudar com a seguinte consulta. Escreva a consulta da maneira mais eficiente e explique-me as alterações que você fez como se eu fosse alguém muito novo no SQL ...

SELECT
    sa.attribution_clean,
    COUNT(DISTINCT COALESCE(s.student_id, sa.student_id)) AS students,
    SUM(r.dollars) AS total_revenue,
    SUM(r.dollars) / COUNT(DISTINCT s.student_id) AS revenue_per_student
FROM
    Students s
INNER JOIN
    StudentAttribution sa ON sa.first_name = s.first_name
                          AND sa.last_name = s.last_name
                          AND sa.student_id = s.student_id
LEFT JOIN
    Revenue r ON r.student_id = s.student_id
WHERE
    s.student_id BETWEEN 1000000 AND 2000000
    AND StudentAttribution.attribution_clean LIKE 'youtube'
    AND StudentAttribution.attribution_clean = 'youtube'
GROUP BY
    1
ORDER BY
    2 DESC;
```

## Normalização

[Mais informações](https://github.com/aasouzaconsult/GenAI-Prompts/blob/main/da_gpt.md)

## Boas Práticas - SQL

[Mais informações](https://github.com/aasouzaconsult/GenAI-Prompts/blob/main/boas_praticas_sql_gpt.md)

# Python 🐍

## Conceitos e Definições
```
Você pode comparar e contrastar as bibliotecas matplotlib, seaborn e plotly express em Python?
```

## Explicação de Código
```python
Você pode explicar o que o código a seguir está fazendo em alto nível? Certifique-se de incluir também uma saída de amostra. 

import pandas as pd
import numpy as np

students_data = {
    'student_id': [1000001, 1000002, 1000003, 1000004],
    'first_name': ['John', 'Jane', 'Alice', 'Bob'],
    'last_name': ['Doe', 'Smith', 'Johnson', 'Williams']
}

student_attribution_data = {
    'student_id': [1000001, 1000002, 1000003, 1000005],
    'attribution_clean': ['youtube', 'youtube', 'youtube', 'facebook']
}

revenue_data = {
    'student_id': [1000001, 1000002, 1000003],
    'dollars': [50, 100, 75]
}

students_df = pd.DataFrame(students_data)
student_attribution_df = pd.DataFrame(student_attribution_data)
revenue_df = pd.DataFrame(revenue_data)

merged_df = student_attribution_df.merge(students_df, on=['first_name', 'last_name', 'student_id'], how='left')
merged_df = merged_df.merge(revenue_df, on='student_id', how='left')

filtered_df = merged_df[(merged_df['attribution_clean'] == 'youtube') &
                        (merged_df['student_id'].between(1000000, 2000000))]

grouped_df = filtered_df.groupby('attribution_clean').agg(
    students=('student_id', lambda x: np.count_nonzero(x)),
    total_revenue=('dollars', 'sum')
)

grouped_df['revenue_per_student'] = grouped_df['total_revenue'] / grouped_df['students']

result_df = grouped_df.sort_values(by='students', ascending=False)

print(result_df)
```

```
Você poderia comentar o código acima?
```

```
Alguma dica de melhores práticas para o código acima? E com exemplo
```

## Otimização de Código
```python
Você pode otimizar o código a seguir para eficiência?

import pandas as pd
import numpy as np

retail_df = pd.read_csv("retail.csv")
retail df["sales tax"] = retail_df["sales").apply(lambda x x *.05)

retail df.tail()
```

## Erro de Código 
```python
Quando executo o código a seguir, recebo um TypeError: pivot table () obteve um argumento de palavra-chave inesperado 'value.  Por que estou recebendo um erro?

import pandas as pd
import numpy as np

retail_df = pd.read_csv(
"retail.csv",
 parse_dates=["date"), 
 dtype={"store_nbr": "string"}
 )

smaller_retail = retail_df.query(
 "family in ['AUTOMOTIVE BABY CARE, BEAUTY) and store nbr in ['1', '2','3', '4']"
)

smaller retail.pivot_table( 
   index="family", 
   columns="store_nbr", 
   value="sales", 
   aggfunc="sum")
)
```

## Cenário para ele escrever o código
```
Eu tenho um arquivo csv chamado "retail.csv" que contém informações sobre as vendas diárias no varejo. Contém as colunas data, família, vendas, entre outras. Você pode escrever um código Python que represente as 10 principais famílias de produtos por total de vendas, em ordem decrescente?
```

## web scrap
```
Você pode escrever código Python para extrair a lista de municípios da url abaixo e armazená-los em um Pandas DataFrame?
https://www.estadosecidades.com.br/ce/
```
```html
dando um contexto
<table class="table table-striped mt-3">
                    <tbody><tr><th>Cidade</th><th class="text-right">2000</th><th class="text-right">2010</th><th class="text-right">2021</th></tr>
                    <tr><td><a href="https://www.estadosecidades.com.br/ce/fortaleza-ce.html">Fortaleza</a></td><td class="text-right">2.141.402</td><td class="text-right">2.447.409</td><td class="text-right">2.703.391</td></tr><tr><td><a href="https://www.estadosecidades.com.br/ce/caucaia-ce.html">Caucaia</a></td><td class="text-right">250.479</td><td class="text-right">324.738</td><td class="text-right">368.918</td></tr><tr><td><a href="https://www.estadosecidades.com.br/ce/juazeiro-do-norte-ce.html">Juazeiro do Norte</a></td><td class="text-right">212.133</td><td class="text-right">249.936</td><td class="text-right">278.264</td></tr><tr><td><a href="https://www.estadosecidades.com.br/ce/maracanau-ce.html">Maracanaú</a></td><td class="text-right">179.732</td><td class="text-right">209.748</td><td class="text-right">230.986</td></tr><tr><td><a href="https://www.estadosecidades.com.br/ce/sobral-ce.html">Sobral</a></td><td class="text-right">155.276</td><td class="text-right">188.271</td><td class="text-right">212.437</td></tr><tr><td><a href="https://www.estadosecidades.com.br/ce/crato-ce.html">Crato</a></td><td class="text-right">104.646</td><td class="text-right">121.462</td><td class="text-right">133.913</td></tr>s
```
## Interpretação de Resultados
```
Você pode interpretar a seguinte saída de regressão linear de statsmodels? 

OLS Regression Results                            
        ==============================================================================
        Dep. Variable:                      y   R-squared:                       0.669
        Model:                            OLS   Adj. R-squared:                  0.667
        Method:                 Least Squares   F-statistic:                     299.2
        Date:                Mon, 01 Mar 2021   Prob (F-statistic):           2.33e-37
        Time:                        16:19:34   Log-Likelihood:                -88.686
        No. Observations:                 150   AIC:                             181.4
        Df Residuals:                     148   BIC:                             187.4
        Df Model:                           1                                         
        Covariance Type:            nonrobust                                         
        ==============================================================================
                         coef    std err          t      P>|t|      [0.025      0.975]
        ------------------------------------------------------------------------------
        const         -3.2002      0.257    -12.458      0.000      -3.708      -2.693
        x1             0.7529      0.044     17.296      0.000       0.667       0.839
        ==============================================================================
        Omnibus:                        3.538   Durbin-Watson:                   1.279
        Prob(Omnibus):                  0.171   Jarque-Bera (JB):                3.589
        Skew:                           0.357   Prob(JB):                        0.166
        Kurtosis:                       2.744   Cond. No.                         43.4
        ==============================================================================
```		

# Power BI 💼📊

## Entendimentos
```
Sou novo no Power BI, como faço para começar?
```
```
Sou novo no Tableau, como faço para começar?
```
```
Sou novo no Google Looker, como faço para começar?
```
```
Sou novo no AWS Quicksight, como faço para começar?
```

## Conceitos
```
Poderia explicar a diferença entre medidas x colunas calculadas no Power BI?
```
```
Sou um usuário relativamente novo do Power BI. Você pode fornecer um exemplo de uma coluna calculada e uma medida e descrever quando usar cada uma?
```

## Dúvidas - Conexão com BD
```
Acabei de ser contratado como analista de dados da Zouza Factory e preciso importar dados do banco de dados MySQL para o Power Bl. Eu tenho acesso ao MySQL, mas não tenho certeza de como conectar. Pode me ajudar?
```

## Dicionário de Dados
```
Você pode criar um dicionário de dados a partir de um conjunto de dados fornecido?
```
```
Você pode criar um dicionário de dados de 4 colunas que inclua o nome da variável, tipo de dados, descrição de cada variável e um valor de exemplo com base nos dados abaixo?

pedido_id data_criacao website_sessao_id usuario_id produto_id quantidade preco desconto
1 19/03/2012 20 20 1 1 49,99 19,49
2 19/03/2012 104 104 11 49,99 19,49
3 20/03/2012 147 14711 49,99 19,49
4 20/03/2012 160 160 11 49,99 19,49
5 20/03/2012 177 177 1 1 49,99 19,49
6 20/03/2012 232 232 11 49,99 19,49
7 20/03/2012 2412411 1 49,99 19,49
8 20/03/2012 295 295 11 49,99 19,49
9 21/03/2012 304 304 11 49,99 19,49
10 21/03/2012 317 3171 1 49,99 19,49
```

## M
```m
Eu tenho algum código Power Query M. Você pode adicionar comentários, formatar o código e atualizar meus nomes de etapas aplicadas para que sejam mais fáceis de entender?

let
    FonteVendas = Table.FromRecords({
        [ID = 1, data = #datetime(2023, 1, 15), valor = 500],
        [ID = 2, data = #datetime(2023, 2, 20), valor = 700],
        [ID = 3, data = #datetime(2023, 2, 25), valor = 300],
        [ID = 4, data = #datetime(2023, 3, 10), valor = 600]
    }),

    FonteClientes = Table.FromRecords({
        [ID = 1, nome = "Cliente A"],
        [ID = 2, nome = "Cliente B"],
        [ID = 3, nome = "Cliente C"]
    }),

    VendasFiltradas = Table.SelectColumns(FonteVendas, {"ID", "data", "valor"}),

    VendasComClientes = Table.NestedJoin(
        VendasFiltradas,
        {"ID"},
        FonteClientes,
        {"ID"},
        "Clientes",
        JoinKind.LeftOuter
    ),

    VendasAgrupadas = Table.Group(
        VendasComClientes,
        {"Clientes[nome]", "data"},
        {{"ValorTotal", each List.Sum([valor]), type number}}
    ),

    VendasPorCliente = Table.Pivot(
        VendasAgrupadas,
        List.Distinct(VendasAgrupadas[Clientes[nome]]),
        "Clientes[nome]",
        "ValorTotal",
        List.Sum
    ),

    VendasFinalizadas = Table.AddColumn(
        VendasPorCliente,
        "Lucro",
        each [Cliente A] - [Cliente B]
    )
in
    VendasFinalizadas
```

## DAX - Explicar
```
Você pode explicar o que esse código DAX está fazendo e adicionar comentários em linha para que outros usuários possam entender o que está acontecendo?

Taxa de Crescimento Mensal = 
VAR MaxData = MAX('Tabela de Vendas'[Data])
VAR MaxDataAnterior = CALCULATE(MAX('Tabela de Vendas'[Data]), PREVIOUSMONTH('Tabela de Vendas'[Data]))
VAR VendasAtual = CALCULATE(SUM('Tabela de Vendas'[Total Vendas]), 'Tabela de Vendas'[Data] = MaxData)
VAR VendasAnterior = CALCULATE(SUM('Tabela de Vendas'[Total Vendas]), 'Tabela de Vendas'[Data] = MaxDataAnterior)
RETURN IF(ISBLANK(VendasAnterior) || VendasAnterior = 0, BLANK(), (VendasAtual - VendasAnterior) / VendasAnterior)
```

## DAX - Criar
```
Estou usando o Power BI, você poderia me ajudar a escrever uma fórmula DAX para calcular a receita total?
```
```
Que tal uma fórmula DAX para receita ano após ano (year-over-year)?
```
```
e com SAMEPERIODLASTYEAR?
```

## DAX - Correção
```
Poderia me ajudar na correção da seguinte medida DAX?

Total Revenue (GPT) =
SUMX(
    'Sales Data',
    'Sales Data'[Order Quantity] Product Lookup'[ProductPrice]
```

## Visual - Sugestão
```
Estou usando o Power BI e preciso mostrar a tendência total de pedidos de clientes nos últimos 3 anos. Você pode sugerir um visual e descrever como construí-lo?
```

## Visual - Dicas
```
Quais são as práticas recomendadas ao usar um gráfico de pizza?
```

## Visual - Dicas
```
Sou analista de negócios e preciso criar um painel para a alta administração visualizar os KPIs e monitorar o desempenho geral da empresa. Você pode me dizer como criar um painel que forneça uma visão abrangente das métricas críticas para auxiliar na tomada de decisões estratégicas e impulsionar o crescimento dos negócios?
```

## Visual - Dicas de Cores (Paleta de cores)
```
Você conseguiria me ajudar a criar uma paleta de cores se eu te contar um pouco sobre o estilo da empresa?
```

```
Me faça perguntas específicas que te ajudarão a descobrir o estilo da empresa
```

*Responda as perguntas, sendo o mais detalhista possível*

```
Qual seria o código hexadecimal destas cores?
```

```
Gere a lista de cores em markdown e inclua a seguinte imagem:
https://singlecolorimage.com/get/{hex_code}/400x100

Substituindo {hex_code} pelo código hexadecimal da cor, mas não inclua o caracter #
```

# Plano de Estudo 📚🗓️

## SQL
[Mais informações](https://github.com/aasouzaconsult/GenAI-Prompts/blob/main/Plano%20de%20Estudo%20-%20sql.md)

## Pentaho
[Mais informações](https://github.com/aasouzaconsult/GenAI-Prompts/blob/main/Plano%20de%20Estudo%20-%20pentaho.md)

---
## Mais informações
- [Dicas de Prompt](https://github.com/aasouzaconsult/GenAI-Prompts/blob/main/DicasDePrompts.md)
- [Visão Geral - ChatGPT](https://medium.com/blog-do-zouza/chatgpt-vis%C3%A3o-geral-f68ed1d1cf54)
- [ChatGPT - Criando Medidas DAX com ChatGPT](https://www.youtube.com/watch?v=vo9uo6aFLME)
- [Imagens - Leonardo AI 📷🖼️](https://github.com/aasouzaconsult/GenAI-Prompts/tree/main/Leonardo%20AI)

## Atenção
- As GenAI são sujeitas a alucinações
- Sempre revisem o conteúdo, lembrando, vc é o piloto!
