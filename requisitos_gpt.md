## Objetivo
O objeto foi dar uma estudada em como GEN-AI, pode auxiliar no dia a dia do analista de dados. Agora, com Especificação de Requisitos.
Segue uma breve descrição...

## Serão dados rascunhos (reais) e iremos observar como serão os retornos


## EU 🤓
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

---
## GPT 🤖

# Especificação de Requisitos - Fórum Data Lake

## Visão Geral

O Fórum Data Lake é uma iniciativa que busca promover uma cultura baseada em dados (data-driven) dentro da organização. O objetivo é centralizar e disponibilizar os dados de diferentes sistemas para análise e tomada de decisões estratégicas. Nessa especificação de requisitos, serão abordados os principais pontos relacionados ao Fórum Data Lake, incluindo suas funcionalidades, dores identificadas e sistemas envolvidos.

## Funcionalidades

### Consumo de Dados

- O Fórum Data Lake deve permitir o consumo de dados de forma ágil e eficiente.
- É importante avaliar o tempo necessário para consumir dados específicos, como os dados contábeis e de receitas, em conjunto com a equipe responsável, representada por XXXXXX.

### Dores Identificadas

#### Marketing

- Campanhas:
  - O Fórum Data Lake deve auxiliar na análise de campanhas, permitindo identificar clientes VIPs e clientes recorrentes.
  - É desejável ter informações sobre o perfil dos clientes por loja.
  - O Fórum Data Lake deve fornecer insights e métricas relacionadas às campanhas, visando identificar dificuldades e oportunidades de melhoria.
  - Análise segmentada por características específicas, como por exemplo, análise por produto X.
  - Análise por canal de comunicação utilizado nas campanhas.
  - Possibilidade de aplicação de técnicas de Machine Learning (ML) para análise preditiva.

#### Vendas

- B2B:
  - Identificou-se a falta de acompanhamento adequado nas vendas B2B.
  - É desejável sugerir ações antes mesmo do cliente precisar solicitar, com base em análises e insights obtidos a partir dos dados do Fórum Data Lake.

## Sistemas Envolvidos

### A caminho do Lake

- Shopify:
  - Dados do sistema Shopify devem ser integrados ao Fórum Data Lake, permitindo análises relacionadas ao comércio eletrônico.
- Protheus:
  - Dados do sistema Protheus devem ser integrados ao Fórum Data Lake, possibilitando análises relacionadas a processos internos e vendas.
  
### Outros Sistemas

- Sellbie:
  - O sistema Sellbie também está envolvido no processo de dados, porém, informações mais detalhadas sobre a integração e funcionalidades específicas devem ser fornecidas pela equipe responsável.

---

Observações: É fundamental realizar uma análise mais detalhada dos requisitos em conjunto com as equipes envolvidas para validar a viabilidade técnica e identificar possíveis ajustes necessários. A especificação acima serve como ponto de partida e pode ser refinada ao longo do processo de desenvolvimento e implementação do Fórum Data Lake.

---
## EU 🤓
Isso abaixo é um levantamento de requisitos, teria como montar algo mais completo com base nestas informações?

Time de produtos (Responsável: XXXX XXXX XXX)

	Arquivos
		Acompanhamento de vendas*
		Top Products ERP Comercial*
			Receita com franquias	
				Formula é importante
		Depletion master
		De-para produtos*
			Base com informações de produtos
			SKU
				2 últimos são safras
				Cada bloco do código, uma informação
			As últimas abas, irão ver onde pega no Protheus
		Campanha - Volta ao Mundo


---
## GPT 🤖

Levantamento de Requisitos - Time de Produtos (Responsável: XXXX XXXX XXX)

1. Acompanhamento de vendas:
   - Requisitos:
     - Acompanhar e analisar as vendas de produtos.
     - Gerar relatórios e métricas relacionadas às vendas.
     - Identificar tendências e padrões de vendas.

2. Top Products ERP Comercial:
   - Requisitos:
     - Calcular a receita gerada pelas franquias.
     - Fórmula para cálculo da receita é importante, mas não foi especificada.
     - Monitorar o desempenho dos principais produtos no ERP Comercial.

3. Depletion Master:
   - Requisitos:
     - Gerenciar o depletion (esgotamento) dos produtos.
     - Controlar a disponibilidade dos produtos no estoque.
     - Garantir reposição adequada dos produtos esgotados.

4. De-Para Produtos:
   - Requisitos:
     - Manter uma base de informações de produtos.
     - Utilizar um sistema de referência SKU.
     - O SKU contém informações específicas, onde cada bloco do código representa uma informação.
     - As últimas abas do arquivo devem indicar onde as informações serão buscadas no sistema Protheus.

5. Campanha - Volta ao Mundo:
   - Requisitos:
     - Gerenciar campanhas promocionais relacionadas a uma volta ao mundo.
     - Planejar e executar atividades de marketing relacionadas à campanha.
     - Monitorar o desempenho e o impacto da campanha nas vendas.

Observações:
- Os requisitos foram levantados com base nas informações fornecidas, mas podem precisar de refinamentos adicionais.
- É recomendado que a especificação dos requisitos seja realizada em conjunto com a equipe responsável pelo desenvolvimento do sistema, para garantir uma compreensão clara e completa das necessidades.

---
## EU 🤓
	Retorno
	- Carregar base inteira de clientes da Sellbie diariamente
	- comunicação, encarteiramento e etc
	- via Batch
	Envio via FTP (retorno)
		- JSON
			- 145mil clientes (+-)
			- 20 atributos
	Campanhas por Clientes
		- Quantas campanhas receberam por e-mail
	
	Envio
	- full (3hs)
	- diariamente (4x)


	Possibilidade?
	- Ir só os modificados?

Melhorar essa especificação de requisito acima

---
## GPT 🤖

Levantamento de Requisitos - Integração com Sellbie

1. Carregar base inteira de clientes da Sellbie diariamente:
   - Requisitos:
     - Carregar diariamente a base completa de clientes da Sellbie.
     - Realizar comunicação e encarteiramento dos clientes.
     - Executar o processo de carga via Batch.

2. Envio via FTP (retorno):
   - Requisitos:
     - Enviar os dados em formato JSON.
     - Aproximadamente 145 mil clientes a serem enviados.
     - Cada cliente possui cerca de 20 atributos.
     - Utilizar o protocolo FTP para o envio dos dados.

3. Campanhas por Clientes:
   - Requisitos:
     - Rastrear quantas campanhas cada cliente recebeu por e-mail.
     - Registrar a quantidade de campanhas recebidas por cada cliente.

Envio:
- Opção 1: Envio completo:
   - Realizar o envio completo da base de clientes.
   - Tempo estimado de processamento: 3 horas.
   - Frequência de envio: diariamente, 4 vezes ao dia.

- Opção 2: Envio apenas dos clientes modificados:
   - Avaliar a possibilidade de enviar apenas os clientes que foram modificados.
   - Reduzir o tempo de processamento, enviando apenas os registros alterados.

Observações:
- É necessário estabelecer uma conexão com a Sellbie para acessar e carregar a base de clientes.
- O envio dos dados via FTP deve ser configurado para permitir a transferência dos arquivos JSON.
- Para o rastreamento das campanhas por clientes, é importante capturar e armazenar as informações relevantes sobre as campanhas recebidas.
- A frequência de envio e o tempo de processamento podem variar de acordo com as necessidades e limitações do ambiente.
- É recomendado que a especificação dos requisitos seja revisada e validada em conjunto com a equipe técnica responsável pela implementação da integração.


---
## EU 🤓
	IRPC (Índice de Rentabilidade de Produto por Canal)
	- Algo mais ativo
		- Receber ao pronto
	- Fonte
		- Metas Margem (onde estão no Protheus)
	- Metas Margem 
		- por canal e subcanal
		- Loja (SP | MG)
			- margem 45%
		- Franquia SP 40%
			- NF Produto
			- NF Serviço
		- Franquia MG 25%
			- NF Produto
			- NF Serviço
	- Previsões
		- imprecisas
		- variações constantes
	- Visualização desejada	
		- Linha Produto	
			- Colunas (4 canais | Consolidado)

	----------------------------------------------------	
	- Vídeo (índice)
	- PBI que mostrou, não temos (Monthly Budget)
		- Budget
			- Arquivo Manual
			- Uma vez com todos os meses
				- (comentaram em disponibilizar em sharepoint para consumir no PowerBI)
			- "Indice Rentabilidade" (%Mg Bruta)
	- Comentaram que mesmo com o Lake, irão ter arquivos manuais
	- Planilha com informações do Shopify (Digital - Ecommerce)
		-	Inventement (google, facebook, media digital), Share App(%) | UPT | Daily | Monthly | ROAS | Sales Cost...
		- 	Creio que essa Planilha não tenha dados somente as 4 tabelas que carregamos hoje do Shopify
			- Ele comentou de: Seções, Carrinho, Checkout, Conversões
	- Objetivo maior, pelo que vi, conectar Shopify e Protheus
	- PBI que mostrou...
		- B2B (Neogrid - Integração futura) | Sell Out (Totvs Chef - ZZ)
		- Dashboard_Regime_Tributário_Franquias
	- Novas tabelas Shopify (ver viabilidade com a Empresa)
		- Carrinho
		- Checkout
		- Observação: No Orders	
			- adicionar os campos: 
				- id
				- "idcarrinho"
				- "idcheckout"

Documentar essa especificação de requisitos

---
## GPT 🤖

Levantamento de Requisitos - IRPC (Índice de Rentabilidade de Produto por Canal)

- Algo mais ativo:
   - Receber ao pronto para análise.

- Fonte:
   - Metas Margem, onde as metas estão armazenadas no sistema Protheus.

- Metas Margem:
   - Definidas por canal e subcanal.
   - Exemplo:
     - Loja (SP | MG):
       - Meta de margem: 45%.
     - Franquia SP:
       - Meta de margem para NF Produto.
       - Meta de margem para NF Serviço.
     - Franquia MG:
       - Meta de margem para NF Produto.
       - Meta de margem para NF Serviço.

- Previsões:
   - Previsões são imprecisas e sofrem variações constantes.

- Visualização desejada:
   - Linha do produto.
   - Colunas: 4 canais e consolidado.

Levantamento de Requisitos - Vídeo (Índice)

- PBI (Power BI) não disponível:
   - Monthly Budget: Arquivo manual com informações de orçamento.
     - Arquivo deve conter informações para todos os meses.
     - Sugestão de disponibilização no SharePoint para consumo no Power BI.
   - "Índice Rentabilidade" (%Mg Bruta): Informação mencionada, mas não disponível no PBI.

- Arquivos manuais mesmo com o Lake:
   - Haverá necessidade de arquivos manuais mesmo com a implementação do Lake.

- Planilha com informações do Shopify (Digital):
   - Planilha contendo informações do Shopify (Digital).
   - Dados relacionados a investimento em Google, Facebook, mídia digital, participação no Share App, UPT, Daily, Monthly, ROAS, Sales Cost, entre outros.
   - Verificar se a planilha possui apenas as 4 tabelas carregadas atualmente do Shopify.
     - Menção a seções, carrinho, checkout e conversões.

- Objetivo maior:
   - Conectar Shopify e Protheus.

- PBI mencionado:
   - B2B (Neogrid - Integração futura).
   - Sell Out (Totvs Chef - ZZ).
   - Dashboard_Regime_Tributário_Franquias.

- Novas tabelas Shopify:
   - Sugestão de avaliação de viabilidade com a Empresa.
   - Tabelas sugeridas: Carrinho, Checkout.
   - Observação: No campo Orders, adicionar os campos: id, idcarrinho, idcheckout.

Observações:
- É recomendado realizar uma análise mais detalhada dos requisitos em conjunto com a equipe técnica para validar a viabilidade e identificar possíveis ajustes necessários.

---
## Mais informações
- [Visão Geral - ChatGPT](https://medium.com/blog-do-zouza/chatgpt-vis%C3%A3o-geral-f68ed1d1cf54)
- [ChatGPT - Criando Medidas DAX com ChatGPT](https://www.youtube.com/watch?v=vo9uo6aFLME)
