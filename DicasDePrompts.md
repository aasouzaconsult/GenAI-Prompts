# Dicas de Prompts 💻>

![](https://blogdozouza.wordpress.com/wp-content/uploads/2024/11/contexto.png)

## Persona
Pense em quem você quer que a IA seja ao responder. Pode ser um especialista, um recrutador, um escritor, um profissional de dados ou até mesmo um personagem fictício. 

**Por exemplo**: Você é um especialista em análise de dados e trabalha no setor financeiro de bigtechs...

## Clear Instructions
Gere instruções claras e seja específico, forneça mais detalhes (ela (IA) não sabe o que você tá precisando). Seja claro sobre qual é o seu objetivo final. 

*Comece sua pergunta com um verbo de ação, como “gerar”, “dar”, “escrever” ou “analisar”.

**Por exemplo:** Escreva um resumo do relatório de vendas trimestrais. Um exemplo se encontra abaixo...

## Formato
Visualize como você deseja que a resposta seja formatada. Pode ser uma lista, um e-mail, um resumo ou qualquer formato que você precise. Ou ainda, o tamanho da mensagem de retorno...

**Por exemplo**: Forneça as informações em formato de lista com marcadores.

## Contexto (Limit the scope)
O contexto é fundamental para restringir as possibilidades. Forneça informações sobre o histórico do usuário, o que define o sucesso e o ambiente em que estão. 

**Por exemplo:** Você é um analista de dados e tem um cliente que deseja minimizar custos.

## Exemplos (*Few-Shot Prompts*)
Incluir exemplos na sua pergunta é uma prática recomendada. Exemplos tornam mais fácil para a IA entender o que você deseja.

**Por exemplo:** Dê um KPI relacionado ao setor financeiro referente a margem bruta por semana e que seja rápido de implementar...

## Tom
O tom da resposta é importante. Você pode pedir um tom formal, casual, entusiástico ou até pessimista. 

**Por exemplo:** Forneça as informações em formato de lista com marcadores, escreva com um tom motivador e entusiasmado!

[mais dicas](https://github.com/aasouzaconsult/GenAI-Prompts/blob/main/DicasDePrompts_mais.md)

# Técnicas de Prompts 💻>
[Mais informações e detalhes](https://www.promptingguide.ai/techniques)

## Zero-Shot Prompts
Quando não é necessário nenhum exemplo, o próprio modelo já pode lhe dar respostas corretas.

**Por exemplo:** 
```
When is Christmas in America?
```

## Few-Shot Prompts
Quando você dá um contexto, dá exemplos para que a resposta saia ou seja mais precisa. [more informations](https://www.promptingguide.ai/techniques/fewshot) | [artigo](https://arxiv.org/pdf/2005.14165)

**Por exemplo:** 
```
What is Alex´s favourite type of foods?
```
*Não saberá responder, pois ele não conhece meus gostos!*

```
Alex´s favourite type of foods include: Burges, Pizza, Fries, Chocolate
What restaurant should I take Alex to in Dubai this weekend?
```
*O prompt acima, provavelmente irá lhe retornar um resultado mais assertivo.*

## Chain-of-Thought (CoT) Prompting
Introduzido em Wei et al. (2022), a solicitação de cadeia de pensamento ([CoT](https://www.promptingguide.ai/techniques/cot)) permite recursos de raciocínio complexos por meio de etapas intermediárias de raciocínio. Você pode combiná-lo com solicitações rápidas para obter melhores resultados em tarefas mais complexas que exigem raciocínio antes de responder. [artigo](https://arxiv.org/abs/2201.11903)

```
Os números ímpares neste grupo somam um número par: 4, 8, 9, 15, 12, 2, 1.
R: Somando todos os números ímpares (9, 15, 1) dá 25. A resposta é falsa.

Os números ímpares neste grupo somam um número par: 17, 10, 19, 4, 8, 12, 24.
R: Somando todos os números ímpares (17, 19) dá 36. A resposta é Verdadeira.

Os números ímpares neste grupo somam um número par: 16, 11, 14, 4, 8, 13, 24.
R: Somando todos os números ímpares (11, 13) dá 24. A resposta é Verdadeira.

Os números ímpares neste grupo somam um número par: 17, 9, 10, 12, 13, 4, 2.
R: Somando todos os números ímpares (17, 9, 13) dá 39. A resposta é falsa.

Os números ímpares neste grupo somam um número par: 15, 32, 5, 13, 82, 7, 1.
A:
```
Result: Adding all the odd numbers (15, 5, 13, 7, 1) gives 41. The answer is False.


## Self-Consistency
Talvez uma das técnicas mais avançadas disponíveis para *engenharia de prompt* seja a autoconsistência. Proposto por [Wang et al. (2022) - artigo](https://arxiv.org/abs/2203.11171), a autoconsistência visa "substituir a decodificação ingênua e gananciosa usada na estimulação da cadeia de pensamento". A ideia é provar múltiplos e diversos caminhos de raciocínio por meio de CoT de poucas tentativas e usar as gerações para selecionar a resposta mais consistente. Isso ajuda a aumentar o desempenho das solicitações do CoT em tarefas que envolvem raciocínio aritmético e de bom senso.

```
Quando eu tinha 6 anos, minha irmã tinha metade da minha idade. Agora
Tenho 70 anos, quantos anos tem minha irmã?
```
Talvez dê uma resposta errada, no meu teste deu certo kkk - GTP 3.5 Turbo

Aqui dando alguns exemplos, a ideia é rodar algumas vezes, e pegar a resposta que mais apareceu (o meu todas as respostas foram iguais)
```
P: Existem 15 árvores no bosque. Os trabalhadores do bosque plantarão árvores no bosque hoje. Depois de terminarem,
haverá 21 árvores. Quantas árvores os trabalhadores do bosque plantaram hoje?
R: Começamos com 15 árvores. Mais tarde temos 21 árvores. A diferença deve ser o número de árvores plantadas.
Então, eles devem ter plantado 21 – 15 = 6 árvores. A resposta é 6.
P: Se houver 3 carros no estacionamento e chegarem mais 2 carros, quantos carros estão no estacionamento?
R: Já existem 3 carros no estacionamento. Chegam mais 2. Agora existem 3 + 2 = 5 carros. A resposta é 5.
P: Leah comeu 32 chocolates e sua irmã 42. Se elas comeram 35, quantos pedaços sobraram no total?
R: Leah tinha 32 chocolates e a irmã de Leah tinha 42. Isso significa que originalmente havia 32 + 42 = 74
chocolates. 35 foram comidos. Então, no total, eles ainda têm 74 – 35 = 39 chocolates. A resposta é 39.
P: Jason comeu 20 pirulitos. Ele deu alguns pirulitos para Denny. Agora Jason tem 12 pirulitos. Quantos pirulitos
Jason deu para Denny?
R: Jason comeu 20 pirulitos. Como ele só tem 12 agora, deve ter dado o resto para Denny. O número de
os pirulitos que ele deu ao Denny devem ter sido 20 - 12 = 8 pirulitos. A resposta é 8.
P: Shawn tem cinco brinquedos. No Natal, ele ganhou dois brinquedos da mãe e do pai. Quantos brinquedos tem
ele tem agora?
R: Ele tem 5 brinquedos. Ele ganhou 2 da mãe, então depois disso ele tem 5 + 2 = 7 brinquedos. Então ele ganhou mais 2 do pai, então
no total ele tem 7 + 2 = 9 brinquedos. A resposta é 9.
P: Havia nove computadores na sala do servidor. Mais cinco computadores foram instalados por dia, desde
segunda a quinta. Quantos computadores estão agora na sala do servidor?
R: São 4 dias de segunda a quinta. 5 computadores foram adicionados a cada dia. Isso significa no total 4 * 5 =
20 computadores foram adicionados. No início havia 9 computadores, então agora existem 9 + 20 = 29 computadores.
A resposta é 29.
P: Michael tinha 58 bolas de golfe. Na terça-feira, ele perdeu 23 bolas de golfe. Na quarta-feira, ele perdeu mais 2. Quantos
bolas de golfe ele tinha no final da quarta-feira?
R: Michael inicialmente tinha 58 bolas. Ele perdeu 23 na terça-feira, então depois disso ele tem 58 - 23 = 35 bolas. Sobre
Quarta-feira ele perdeu mais 2, então agora tem 35 - 2 = 33 bolas. A resposta é 33.
P: Olivia tem $ 23. Ela comprou cinco bagels por US$ 3 cada. Quanto dinheiro ela ainda tem?
R: Ela comprou 5 bagels por US$ 3 cada. Isso significa que ela gastou US$ 15. Ela ainda tem $ 8.
P: Quando eu tinha 6 anos, minha irmã tinha metade da minha idade. Agora tenho 70 anos, quantos anos minha irmã tem?
R:
```

## Generate Knowledge Prompting
No veu ver, é dar contexto - [More informattion](https://www.promptingguide.ai/techniques/knowledge)

## Prompt Chaining (Encadeamento de prompt)
Usar o resultado de um prompt para entrada em outro

## Tree of Thoughts (ToT)
Para tarefas complexas que exigem exploração ou visão estratégica, as técnicas de solicitação tradicionais ou simples são insuficientes. Yao e outros. (2023) e Longo (2023)propôs recentemente a Árvore de Pensamentos (ToT), uma estrutura que generaliza a sugestão de cadeia de pensamentos e incentiva a exploração de pensamentos que servem como etapas intermediárias para a resolução geral de problemas com modelos de linguagem.

ToT mantém uma árvore de pensamentos, onde os pensamentos representam sequências de linguagem coerentes que servem como etapas intermediárias para a resolução de um problema. Esta abordagem permite que um LM autoavalie o progresso que os pensamentos intermediários fazem para resolver um problema através de um processo de raciocínio deliberado. A capacidade do LM de gerar e avaliar pensamentos é então combinada com algoritmos de busca (por exemplo, busca em largura e busca em profundidade) para permitir a exploração sistemática de pensamentos com antecipação e retrocesso. [artigo](https://arxiv.org/abs/2305.10601)

```
Imagine que três especialistas diferentes estejam respondendo a essa pergunta.
Todos os especialistas anotarão uma etapa de seu pensamento,
depois compartilhe com o grupo.
Em seguida, todos os especialistas passarão para a próxima etapa, etc.
Se algum especialista perceber que está errado em algum momento, ele vai embora.
A questão é...

Bob está na sala.
Ele caminha até a cozinha carregando uma xícara.
Ele coloca uma bola na xícara e leva a xícara para o quarto.
Ele vira a xícara de cabeça para baixo e vai até o jardim.
Ele coloca a xícara no jardim e vai até a garagem.
Onde está a bola?
```
*Answer:* A bola esta no Quarto

ou 
```
"Três especialistas estão discutindo onde a bola foi deixada. Cada especialista irá registrar um raciocínio por vez e, em seguida, compartilhará com os outros. Após cada rodada, eles podem ajustar suas respostas com base no que observaram. Se algum especialista perceber que está em um caminho errado, ele abandonará a discussão.

A situação é a seguinte:

Bob está na sala.
Ele caminha até a cozinha carregando uma xícara.
Ele coloca uma bola na xícara e leva a xicara para o quarto.
Ele vira a xícara de cabeça para baixo e vai até o jardim.
Ele coloca a xícara no jardim e vai até a garagem.
Onde está a bola? "

Narre o pensamento dos especialistas!
```
* [Gemini](https://g.co/gemini/share/334eb85f6e7d) | [ChatGPT](https://chatgpt.com/share/67293253-eb04-800a-b6e7-f80ddd830158)

## Directional Stimulus Prompting
- [artigo](https://arxiv.org/abs/2302.11520)
- [more](https://www.promptingguide.ai/techniques/dsp)

## Skeleton of Thought
- [artigo](https://arxiv.org/abs/2307.15337)
  
## Generated Knowledge Prompting
- [artigo](https://arxiv.org/abs/2110.08387)
  
## Maieutic Prompting
- [artigo](https://arxiv.org/abs/2205.11822)

## Automatic Reasoning and Tool-use (ART) - Raciocínio Automático e Uso de Ferramentas
Combinar sugestões e ferramentas CoT de maneira intercalada mostrou ser uma abordagem forte e robusta para abordar muitas tarefas com LLMs. Essas abordagens normalmente exigem demonstrações específicas de tarefas elaboradas manualmente e intercalação cuidadosamente planejada de gerações de modelos com o uso de ferramentas. Paranjape et al., (2023)propor uma nova estrutura que usa um LLM congelado para gerar automaticamente etapas intermediárias de raciocínio como um programa.

## Automatic Prompt Engineer (APE)
[Este artigo](https://www.promptingguide.ai/techniques/ape) aborda um tópico importante relacionado à engenharia de prompts, que é a ideia de otimizar prompts automaticamente. Embora não nos aprofundemos neste tópico neste guia, aqui estão alguns artigos importantes se você estiver interessado no tópico:
- [Prompt-OIRL](https://arxiv.org/abs/2309.06553)- propõe o uso de aprendizagem por reforço inverso offline para gerar prompts dependentes de consulta.
- [OPRO](https://arxiv.org/abs/2309.03409)- apresenta a ideia de usar LLMs para otimizar prompts: deixe os LLMs "Respirar fundo" melhora o desempenho em problemas matemáticos.
- [AutoPrompt](https://arxiv.org/abs/2010.15980)- propõe uma abordagem para criar automaticamente prompts para um conjunto diversificado de tarefas com base na pesquisa guiada por gradiente.
- [Prefix Tuning](https://arxiv.org/abs/2101.00190)- uma alternativa leve ao ajuste fino que precede um prefixo contínuo treinável para tarefas NLG.
- [Prompt Tuning](https://arxiv.org/abs/2104.08691)- propõe um mecanismo para aprender soft prompts por meio de retropropagação.

## Active Prompt
Os métodos de cadeia de pensamento (CoT) dependem de um conjunto fixo de exemplares anotados por humanos. O problema com isto é que os exemplares podem não ser os exemplos mais eficazes para as diferentes tarefas. Para resolver isso, Diao et al., (2023)propôs recentemente uma nova abordagem de prompt chamada Active-Prompt para adaptar LLMs a diferentes exemplos de prompts específicos de tarefas (anotados com raciocínio CoT projetado por humanos).

![Veja a Ilustração](https://www.promptingguide.ai/_next/image?url=%2F_next%2Fstatic%2Fmedia%2Factive-prompt.f739657b.png&w=1200&q=75)
O primeiro passo é consultar o LLM com ou sem alguns exemplos de CoT. k respostas possíveis são geradas para um conjunto de perguntas de treinamento. Uma métrica de incerteza é calculada com base nas k respostas (discordância utilizada). As questões mais incertas são selecionadas para anotação por humanos. Os novos exemplares anotados são então usados ​​para inferir cada questão.

## Program-aided Language Model (PAL)
- [artigo](https://arxiv.org/abs/2211.10435)
- [more](https://www.promptingguide.ai/techniques/pal)

### Example 
*Não testei a fundo (deu erro no primeiro trecho)*

```python
import openai
from datetime import datetime
from dateutil.relativedelta import relativedelta
import os
from langchain.llms import OpenAI
from dotenv import load_dotenv
```

```python
load_dotenv()
 
# API configuration
openai.api_key = os.getenv("OPENAI_API_KEY")
 
# for LangChain
os.environ["OPENAI_API_KEY"] = os.getenv("OPENAI_API_KEY")
```

```python
llm = OpenAI(model_name='text-davinci-003', temperature=0)
```

```python
question = "Today is 27 February 2023. I was born exactly 25 years ago. What is the date I was born in MM/DD/YYYY?"
 
DATE_UNDERSTANDING_PROMPT = """
# Q: 2015 is coming in 36 hours. What is the date one week from today in MM/DD/YYYY?
# If 2015 is coming in 36 hours, then today is 36 hours before.
today = datetime(2015, 1, 1) - relativedelta(hours=36)
# One week from today,
one_week_from_today = today + relativedelta(weeks=1)
# The answer formatted with %m/%d/%Y is
one_week_from_today.strftime('%m/%d/%Y')
# Q: The first day of 2019 is a Tuesday, and today is the first Monday of 2019. What is the date today in MM/DD/YYYY?
# If the first day of 2019 is a Tuesday, and today is the first Monday of 2019, then today is 6 days later.
today = datetime(2019, 1, 1) + relativedelta(days=6)
# The answer formatted with %m/%d/%Y is
today.strftime('%m/%d/%Y')
# Q: The concert was scheduled to be on 06/01/1943, but was delayed by one day to today. What is the date 10 days ago in MM/DD/YYYY?
# If the concert was scheduled to be on 06/01/1943, but was delayed by one day to today, then today is one day later.
today = datetime(1943, 6, 1) + relativedelta(days=1)
# 10 days ago,
ten_days_ago = today - relativedelta(days=10)
# The answer formatted with %m/%d/%Y is
ten_days_ago.strftime('%m/%d/%Y')
# Q: It is 4/19/1969 today. What is the date 24 hours later in MM/DD/YYYY?
# It is 4/19/1969 today.
today = datetime(1969, 4, 19)
# 24 hours later,
later = today + relativedelta(hours=24)
# The answer formatted with %m/%d/%Y is
today.strftime('%m/%d/%Y')
# Q: Jane thought today is 3/11/2002, but today is in fact Mar 12, which is 1 day later. What is the date 24 hours later in MM/DD/YYYY?
# If Jane thought today is 3/11/2002, but today is in fact Mar 12, then today is 3/12/2002.
today = datetime(2002, 3, 12)
# 24 hours later,
later = today + relativedelta(hours=24)
# The answer formatted with %m/%d/%Y is
later.strftime('%m/%d/%Y')
# Q: Jane was born on the last day of Feburary in 2001. Today is her 16-year-old birthday. What is the date yesterday in MM/DD/YYYY?
# If Jane was born on the last day of Feburary in 2001 and today is her 16-year-old birthday, then today is 16 years later.
today = datetime(2001, 2, 28) + relativedelta(years=16)
# Yesterday,
yesterday = today - relativedelta(days=1)
# The answer formatted with %m/%d/%Y is
yesterday.strftime('%m/%d/%Y')
# Q: {question}
""".strip() + '\n'
```

```python
llm_out = llm(DATE_UNDERSTANDING_PROMPT.format(question=question))
print(llm_out)
```

```python
exec(llm_out)
print(born)
```

## ReAct
- [artigo](https://arxiv.org/abs/2210.03629)
- [more](https://www.promptingguide.ai/techniques/react)

![](https://blogdozouza.files.wordpress.com/2024/01/screenshot_14.png)

![](https://blogdozouza.files.wordpress.com/2024/01/screenshot_15.png)

## Multimodal CoT Prompting
- [more](https://www.promptingguide.ai/techniques/multimodalcot)
- [article](https://arxiv.org/abs/2302.00923)

## GraphPrompt
- [article](https://arxiv.org/abs/2302.08043)

# Ferramentas
- Dyno (Prompt Enginnering IDE)
- Dust
- LangChain
- Prompttable

---

## RAG - Retrieval Augment Generation (Geração Aumentada de Recuperação)
RAG combina um componente de recuperação de informação com um modelo gerador de texto. O RAG pode ser ajustado e seu conhecimento interno modificado de forma eficiente e sem a necessidade de retreinamento de todo o modelo. [more informations](https://medium.com/blog-do-zouza/rag-retrieval-augmented-generation-8238a20e381d)

A técnica de Retrieval-Augmented Generation (RAG) aprimora os resultados de um LLM ao integrar informações específicas e atualizadas, sem a necessidade de alterar o modelo de IA subjacente. 
Enriquece seus prompts com informações/documentos da sua empresa...
![](https://blogdozouza.wordpress.com/wp-content/uploads/2024/11/rag.png)

## Fine tunning
É como dar um "treinamento especial" para que ele se torne especialista em uma tarefa específica. Isso permite que o modelo aprenda a realizar tarefas complexas com mais precisão e criatividade, como escrever textos no estilo de um autor específico ou gerar código de programação para diferentes aplicações.

![](https://blogdozouza.wordpress.com/wp-content/uploads/2024/11/finetunning1.png)

![](https://blogdozouza.wordpress.com/wp-content/uploads/2024/11/finetunning2-1.png)

---
   
# Mais informações
- [Engenharia de Prompts](https://medium.com/blog-do-zouza/genai-o-que-%C3%A9-engenharia-de-prompt-6d416afe1323)
- [Dicas de Prompt - OpenAI](https://platform.openai.com/docs/guides/prompt-engineering)
- [Dicas de Prompt](https://www.promptingguide.ai/pt/introduction/basics)
- [Mais dicas de Prompts](https://medium.com/@petrusje/domine-a-arte-de-criar-prompts-eficientes-para-chatgpt-e-outras-ias-uma-base-s%C3%B3lida-b78f3b30fd9a)
