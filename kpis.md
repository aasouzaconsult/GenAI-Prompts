# KPI´s 📊📈🔑

## Prompt 💻>
```
Você atuará como um especialista em Análise de Dados. Você estará me treinando, como um colega de trabalho júnior que está aprendendo Análise de Dados. Você pode explicar a diferença entre um KPI e uma métrica?
```

## Resposta
Quando se trata de análise de dados, entender a diferença entre KPIs e métricas é fundamental. Vamos dar uma olhada:

**KPI (Key Performance Indicator):**
Um KPI, ou Indicador-chave de Desempenho, é uma medida que ajuda a avaliar o sucesso de uma organização, projeto ou processo em relação aos seus objetivos e metas estratégicas. Os KPIs são escolhidos cuidadosamente porque refletem os aspectos mais cruciais do desempenho e progresso de uma empresa. Eles são usados para monitorar o desempenho ao longo do tempo e fornecer insights sobre a eficácia das estratégias adotadas.

Os KPIs normalmente são específicos, mensuráveis, alcançáveis, relevantes e limitados pelo tempo (critérios SMART). Eles estão diretamente relacionados aos principais objetivos de negócios e são usados para tomar decisões informadas.

Exemplos de KPIs incluem a Receita Total, a Taxa de Conversão de Clientes, o Churn Rate (taxa de cancelamento de clientes) e a Satisfação do Cliente.

**Métrica:**
Uma métrica é uma medida quantitativa usada para avaliar um aspecto específico do desempenho. As métricas são geralmente mais detalhadas e podem ser usadas para monitorar diferentes áreas de uma operação, mas nem todas as métricas são necessariamente KPIs. Enquanto os KPIs estão alinhados com os objetivos estratégicos e fornecem uma visão de alto nível do desempenho, as métricas podem ser mais técnicas e operacionais.

As métricas podem ser usadas para calcular ou acompanhar certos aspectos, mas nem todas são tão impactantes quanto os KPIs no contexto das metas globais de uma organização.

Exemplos de métricas incluem o Tempo Médio de Resposta (no atendimento ao cliente), Taxa de Abertura de E-mails, Número de Páginas Visualizadas por Sessão (em um site) e Tempo de Carregamento de Página.

**Diferença:**
Em resumo, a principal diferença entre um KPI e uma métrica é que os KPIs estão diretamente ligados aos objetivos estratégicos e refletem o desempenho geral da organização, enquanto as métricas são medidas mais detalhadas e podem ser usadas para avaliar aspectos específicos do desempenho operacional. KPIs ajudam a responder a pergunta "Como estamos indo em relação aos nossos objetivos?", enquanto métricas fornecem informações mais granulares sobre o desempenho em diferentes áreas.

Como um colega de trabalho júnior, certifique-se de entender a diferença entre KPIs e métricas para garantir que você esteja medindo e reportando os dados de maneira eficaz para apoiar as decisões de negócios.

---

## Prompt 💻>
```
Explique como se fosse para uma criança
```
## Resposta
Vou explicar de uma forma bem simples, como se fosse para uma criança:

Imagine que você está jogando um jogo muito legal, como um jogo de corrida. Agora, você quer saber o quão bem está indo no jogo, certo? Aqui é onde entram os KPIs e as métricas!

**KPI (Key Performance Indicator)** é como um troféu especial que mostra o quão bom você está no jogo. Imagine que você tem um objetivo importante, como chegar em primeiro lugar na corrida. O KPI é como um sinal que te ajuda a entender se você está chegando perto desse objetivo ou não. Se você está ganhando muitas corridas e ficando em primeiro lugar, isso é um sinal muito bom! Os KPIs são como as coisas mais importantes que você olha para saber se está vencendo o jogo da forma que quer.

**Métrica**, por outro lado, é como as peças pequeninas do jogo que você olha para descobrir como está indo em detalhes. Digamos que você quer entender como está indo nas corridas, então você olha para algumas coisas específicas. Por exemplo, quantas vezes você freou nas curvas, quantos itens especiais você pegou durante a corrida ou quanto tempo levou para terminar uma volta. Essas são métricas! Elas são como as partes menores do jogo que ajudam a entender o que você está fazendo bem e o que pode melhorar.

Então, resumindo, os KPIs são como os troféus que mostram se você está ganhando o jogo do jeito que deseja, enquanto as métricas são as partes menores que te contam detalhes sobre como você está jogando. Ambos são muito importantes para saber como você está se saindo e como pode ficar ainda melhor no jogo da vida!

---

## Prompt 💻>
```
O projeto que estamos atuando é um projeto de vendas. Nossas vendas tem informações de data da venda, do cliente, do produto, quantidade vendida, preço unitário, preço total, vendedor, o percentual de comissão do vendedor... Quais os principais KPI´s que podemos tirar deste cenário.

Gentileza montar uma base de dados (SQL Server) fictícia com estes dados e os KPI´s que indicar, crie as fórmulas em SQL para chegarmos neles
```

## Resposta
Primeiro, vou apresentar alguns KPIs relevantes para o cenário de vendas com base nas informações que você forneceu. Em seguida, vou mostrar como criar uma base de dados fictícia no SQL Server e calcular esses KPIs usando consultas SQL.

**Principais KPIs para um Projeto de Vendas:**

1. **Receita Total:** Soma de todos os preços totais das vendas.

2. **Lucro Total:** Soma dos lucros de todas as vendas, onde o lucro é calculado subtraindo o preço total do custo total.

3. **Taxa de Conversão:** Percentual de clientes potenciais que se tornaram clientes efetivos.

4. **Ticket Médio:** Média do valor das vendas, calculada dividindo a receita total pelo número de vendas.

5. **Margem de Lucro:** Percentual de lucro em relação à receita total.

6. **Comissão Total:** Soma das comissões pagas aos vendedores com base nas vendas.

**Criando a Base de Dados Fictícia e Calculando os KPIs:**

Vamos criar uma tabela chamada "Vendas" com as informações que você forneceu. Vou supor que a tabela já exista e você está inserindo os dados nela. A seguir, estão as consultas SQL para calcular os KPIs:

```sql
-- Criação da tabela Vendas
CREATE TABLE Vendas (
    VendaID INT PRIMARY KEY,
    DataVenda DATE,
    Cliente VARCHAR(50),
    Produto VARCHAR(50),
    Quantidade INT,
    PrecoUnitario DECIMAL(10, 2),
    PrecoTotal DECIMAL(10, 2),
    Vendedor VARCHAR(50),
    PercentualComissao DECIMAL(5, 2)
);

-- Inserção de dados fictícios
INSERT INTO Vendas VALUES
(1 , '2023-08-01', 'Cliente A', 'Produto X', 10, 50.00, 500.00, 'Vendedor 1', 0.10),
(2 , '2023-08-02', 'Cliente B', 'Produto Y', 5, 30.00, 150.00, 'Vendedor 2', 0.08),
(3 , '2023-08-02', 'Cliente DB', 'Produto Y', 5, 30.00, 150.00, 'Vendedor 2', 0.08),
(4 , '2023-08-02', 'Cliente DB', 'Produto Y', 5, 30.00, 150.00, 'Vendedor 3', 0.08),
(5 , '2023-08-02', 'Cliente B', 'Produto Y', 5, 30.00, 150.00, 'Vendedor 2', 0.08),
(6 , '2023-08-02', 'Cliente B', 'Produto Y', 5, 30.00, 150.00, 'Vendedor 4', 0.08),
(7 , '2023-08-02', 'Cliente B', 'Produto Y', 5, 30.00, 150.00, 'Vendedor 2', 0.08),
(8 , '2023-08-02', 'Cliente B', 'Produto Y', 5, 30.00, 150.00, 'Vendedor 5', 0.08),
(9 , '2023-08-02', 'Cliente DB', 'Produto Y', 5, 30.00, 150.00, 'Vendedor 2', 0.08),
(10, '2022-06-02', 'Cliente VB', 'Produto Y', 5, 30.00, 150.00, 'Vendedor 6', 0.08),
(11, '2021-08-02', 'Cliente BB', 'Produto Y', 5, 30.00, 150.00, 'Vendedor 2', 0.08),
(12, '2020-08-02', 'Cliente YB', 'Produto Y', 5, 30.00, 150.00, 'Vendedor 7', 0.08),
(13, '2023-05-02', 'Cliente TB', 'Produto Y', 5, 30.00, 150.00, 'Vendedor 2', 0.08),
(14, '2023-08-02', 'Cliente RB', 'Produto Y', 5, 30.00, 150.00, 'Vendedor 8', 0.08),
(15, '2023-04-02', 'Cliente FB', 'Produto Y', 5, 30.00, 150.00, 'Vendedor 2', 0.08),
(16, '2022-01-02', 'Cliente SB', 'Produto Y', 5, 30.00, 150.00, 'Vendedor 9', 0.08),
(17, '2021-05-02', 'Cliente AB', 'Produto Y', 5, 30.00, 150.00, 'Vendedor 10', 0.05)


-- Cálculo dos KPIs
-- Receita Total
SELECT SUM(PrecoTotal) AS ReceitaTotal FROM Vendas;

-- Lucro Total
SELECT SUM(PrecoTotal - (PrecoUnitario * Quantidade)) AS LucroTotal FROM Vendas;

-- Taxa de Conversão
SELECT COUNT(DISTINCT Cliente) / COUNT(*) AS TaxaConversao FROM Vendas;

-- Ticket Médio
SELECT AVG(PrecoTotal) AS TicketMedio FROM Vendas;

-- Margem de Lucro (em percentual)
SELECT (SUM(PrecoTotal - (PrecoUnitario * Quantidade)) / SUM(PrecoTotal)) * 100 AS MargemLucro FROM Vendas;

-- Comissão Total
SELECT SUM(PrecoTotal * PercentualComissao) AS ComissaoTotal FROM Vendas;
```

Lembre-se de adaptar as consultas conforme necessário e ajustar os valores dos KPIs conforme os dados fictícios inseridos na tabela. Esses exemplos de consultas SQL devem ajudar a calcular os KPIs que você mencionou com base nos dados de vendas fornecidos.

Alguns precisam do custo, e nossa base não tem por exemplo.

---

## Prompt 💻>
```
Você como um grande analista de dados do ramo de rh, monte uma pequena base de dados de pessoa em SQL Server, e informe os principais indicadores (KPI´s) de rh e a formula para calcular cada um deles (pode ser um select para cada uns dos KPIs)
```
## Resposta
Vou montar uma base de dados fictícia de pessoas no SQL Server e apresentar alguns indicadores-chave de RH (KPIs) juntamente com as fórmulas e consultas SQL para calcular cada um deles. Vou criar uma tabela chamada "Pessoas" com campos relevantes para os cálculos dos indicadores. Lembre-se de adaptar isso às suas necessidades e à estrutura real do banco de dados.

**Tabela "Pessoas"**
```sql
CREATE TABLE Pessoas (
    ID INT PRIMARY KEY,
    Nome VARCHAR(50),
    DataNascimento DATE,
    Salario DECIMAL(10, 2),
    Cargo VARCHAR(50),
    Departamento VARCHAR(50)
);
```

Agora, vamos calcular alguns KPIs:

**1. Turnover (Taxa de Rotatividade)**
O turnover mede a taxa de entrada e saída de funcionários em uma empresa durante um período específico.

Fórmula: Turnover = (Número de Saídas / Número Médio de Funcionários) * 100

```sql
SELECT 
    (COUNT(*) / (SELECT COUNT(DISTINCT ID) FROM Pessoas)) * 100 AS Turnover
FROM Pessoas
WHERE DataNascimento BETWEEN '2023-01-01' AND '2023-12-31';
```

**2. Absenteísmo**
O absenteísmo mede a proporção de tempo em que os funcionários estão ausentes do trabalho em relação ao tempo total de trabalho.

Fórmula: Absenteísmo = (Horas de Ausência / Horas Totais de Trabalho) * 100

```sql
SELECT 
    (SUM(HorasAusencia) / (COUNT(*) * HorasTrabalho)) * 100 AS Absenteismo
FROM Pessoas;
```

**3. Custo por Funcionário**
O custo por funcionário calcula o gasto médio com cada funcionário.

Fórmula: Custo por Funcionário = (Total de Salários + Benefícios) / Número de Funcionários

```sql
SELECT 
    (SUM(Salario) + SUM(Beneficios)) / COUNT(*) AS CustoPorFuncionario
FROM Pessoas;
```

**4. Índice de Satisfação**
O índice de satisfação mede a satisfação geral dos funcionários, normalmente obtido por meio de pesquisas internas.

Fórmula: Índice de Satisfação = (Número de Respostas Positivas / Número Total de Respostas) * 100

```sql
SELECT 
    (COUNT(CASE WHEN Resposta = 'Positiva' THEN 1 ELSE NULL END) / COUNT(*)) * 100 AS IndiceSatisfacao
FROM PesquisaSatisfacao;
```

Lembre-se de adaptar as consultas acima às suas necessidades específicas, incluindo a estrutura real da sua base de dados e os nomes das tabelas e campos correspondentes.