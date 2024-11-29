# Lista de Prompts

## Dicas gerais
Menos eficaz ❌:
```
Resuma o texto abaixo como uma lista de pontos principais.

A Amazon e a Microsoft têm liderado o mercado de computação em nuvem, enquanto empresas como a OpenAI e a DeepMind avançam em inteligência artificial. Sam Altman, CEO da OpenAI, destacou recentemente a importância de pesquisas éticas no campo da IA. Ao mesmo tempo, Sundar Pichai, da Alphabet, mencionou os desafios da implementação de sistemas de machine learning em larga escala. Além disso, tópicos como geração de linguagem natural, redes neurais e modelos de difusão têm ganhado espaço nos debates. No entanto, questões éticas e regulamentares continuam sendo temas amplamente discutidos, especialmente no contexto do impacto da tecnologia no mercado de trabalho.
```

Mais eficaz ✅:
```
Resuma o texto abaixo como uma lista de pontos principais.

Texto: """
A Amazon e a Microsoft têm liderado o mercado de computação em nuvem, enquanto empresas como a OpenAI e a DeepMind avançam em inteligência artificial. Sam Altman, CEO da OpenAI, destacou recentemente a importância de pesquisas éticas no campo da IA. Ao mesmo tempo, Sundar Pichai, da Alphabet, mencionou os desafios da implementação de sistemas de machine learning em larga escala. Além disso, tópicos como geração de linguagem natural, redes neurais e modelos de difusão têm ganhado espaço nos debates. No entanto, questões éticas e regulamentares continuam sendo temas amplamente discutidos, especialmente no contexto do impacto da tecnologia no mercado de trabalho.
"""
```
---

Menos eficaz ❌:
```
Escreva um poema sobre a OpenAI.
```

Mais eficaz ✅:
```
Escreva um poema curto e inspirador sobre a OpenAI, focando no lançamento recente do produto DALL-E (DALL-E é um modelo de ML que transforma texto em imagem), no estilo de Fernando Pessoa.
```

---

Menos eficaz ❌:
```
Extraia as entidades mencionadas no texto abaixo. Extraia os seguintes 4 tipos de entidades: nomes de empresas, nomes de pessoas, tópicos específicos e temas gerais.

Texto: """
A Amazon e a Microsoft têm liderado o mercado de computação em nuvem, enquanto empresas como a OpenAI e a DeepMind avançam em inteligência artificial. Sam Altman, CEO da OpenAI, destacou recentemente a importância de pesquisas éticas no campo da IA. Ao mesmo tempo, Sundar Pichai, da Alphabet, mencionou os desafios da implementação de sistemas de machine learning em larga escala. Além disso, tópicos como geração de linguagem natural, redes neurais e modelos de difusão têm ganhado espaço nos debates. No entanto, questões éticas e regulamentares continuam sendo temas amplamente discutidos, especialmente no contexto do impacto da tecnologia no mercado de trabalho.
"""
```

Melhor ✅:
```
Extraia as entidades importantes mencionadas no texto abaixo. Primeiro, extraia todos os nomes de empresas; depois, extraia todos os nomes de pessoas; em seguida, extraia tópicos específicos que se encaixam no conteúdo e, finalmente, extraia temas gerais abrangentes.

Formato desejado:
Nomes de empresas: <lista_de_nomes_de_empresas_separados_por_vírgula>
Nomes de pessoas: <lista_de_nomes_de_pessoas_separados_por_vírgula>
Tópicos específicos: <lista_de_tópicos_específicos_separados_por_vírgula>
Temas gerais: <lista_de_temas_gerais_separados_por_vírgula>

Texto: """
A Amazon e a Microsoft têm liderado o mercado de computação em nuvem, enquanto empresas como a OpenAI e a DeepMind avançam em inteligência artificial. Sam Altman, CEO da OpenAI, destacou recentemente a importância de pesquisas éticas no campo da IA. Ao mesmo tempo, Sundar Pichai, da Alphabet, mencionou os desafios da implementação de sistemas de machine learning em larga escala. Além disso, tópicos como geração de linguagem natural, redes neurais e modelos de difusão têm ganhado espaço nos debates. No entanto, questões éticas e regulamentares continuam sendo temas amplamente discutidos, especialmente no contexto do impacto da tecnologia no mercado de trabalho.
"""
```

---
## Técnicas de Prompts

### Zero-shot
Quando não é necessário fornecer nenhum exemplo, o próprio modelo de linguagem pode gerar respostas corretas com base em seu conhecimento prévio.


```
Extraia palavras-chave importantes do texto abaixo.

Texto: """
A Amazon e a Microsoft têm liderado o mercado de computação em nuvem, enquanto empresas como a OpenAI e a DeepMind avançam em inteligência artificial. Sam Altman, CEO da OpenAI, destacou recentemente a importância de pesquisas éticas no campo da IA. Ao mesmo tempo, Sundar Pichai, da Alphabet, mencionou os desafios da implementação de sistemas de machine learning em larga escala. Além disso, tópicos como geração de linguagem natural, redes neurais e modelos de difusão têm ganhado espaço nos debates. No entanto, questões éticas e regulamentares continuam sendo temas amplamente discutidos, especialmente no contexto do impacto da tecnologia no mercado de trabalho.
"""

Palavras-chave:
```

#### Zero-shot-CoT
CoT é a abreviação de chain of thought (cadeia de raciocínio)

A inclusão de "*Let's think step by step*" (pense passo a passo) no fim do prompt permite que o modelo resolva problemas de raciocínio mais complicado.

```
Extraia palavras-chave importantes do texto abaixo.

Texto: """
A Amazon e a Microsoft têm liderado o mercado de computação em nuvem, enquanto empresas como a OpenAI e a DeepMind avançam em inteligência artificial. Sam Altman, CEO da OpenAI, destacou recentemente a importância de pesquisas éticas no campo da IA. Ao mesmo tempo, Sundar Pichai, da Alphabet, mencionou os desafios da implementação de sistemas de machine learning em larga escala. Além disso, tópicos como geração de linguagem natural, redes neurais e modelos de difusão têm ganhado espaço nos debates. No entanto, questões éticas e regulamentares continuam sendo temas amplamente discutidos, especialmente no contexto do impacto da tecnologia no mercado de trabalho.
"""

Palavras-chave:

Pense passo a passo
```

---

### Few-shot
Nessa técnica, você fornece um **contexto** e **alguns exemplos** para que a resposta seja mais precisa e relevante.

```
Extraia palavras-chave dos textos correspondentes abaixo.

Texto 1: A Stripe fornece APIs que desenvolvedores web podem usar para integrar o processamento de pagamentos em seus sites e aplicativos móveis.
Palavras-chave 1: Stripe, processamento de pagamentos, APIs, desenvolvedores web, sites, aplicativos móveis

Texto 2: A OpenAI treinou modelos de linguagem de ponta que são muito bons em entender e gerar texto. Nossa API fornece acesso a esses modelos e pode ser usada para resolver praticamente qualquer tarefa que envolva processamento de linguagem.
Palavras-chave 2: OpenAI, modelos de linguagem, processamento de texto, API

Texto 3: """
A Amazon e a Microsoft têm liderado o mercado de computação em nuvem, enquanto empresas como a OpenAI e a DeepMind avançam em inteligência artificial. Sam Altman, CEO da OpenAI, destacou recentemente a importância de pesquisas éticas no campo da IA. Ao mesmo tempo, Sundar Pichai, da Alphabet, mencionou os desafios da implementação de sistemas de machine learning em larga escala. Além disso, tópicos como geração de linguagem natural, redes neurais e modelos de difusão têm ganhado espaço nos debates. No entanto, questões éticas e regulamentares continuam sendo temas amplamente discutidos, especialmente no contexto do impacto da tecnologia no mercado de trabalho.
"""
Palavras-chave 3:

```

Outro exemplo:
```
Qual a minha comida favorita?
```

E agora?
```
Gosto de carnes, massas e frutos do mar, me indique 5 restaurantes próximo a Avenida Dom Luis na Aldeota (Fortaleza-CE)
```

### Self-Consistency
É uma abordagem avançada usada em modelos de linguagem para aumentar a confiabilidade e a precisão das respostas. Em vez de gerar uma única resposta a partir de um prompt, o modelo cria várias respostas diferentes, todas baseadas no mesmo input.

Prompt (Simples): 
```
Quem é considerado o inventor da lâmpada elétrica moderna? Explique brevemente.
```

Prompt (*Self-Consistency*): 
```
Quem é considerado o inventor da lâmpada elétrica moderna? Por favor, forneça uma resposta clara e breve. Gere a resposta considerando diferentes maneiras de explicar o mesmo conceito.
```

Outro exemplo:
```
Imagine que você está resolvendo este problema em etapas, considerando diferentes abordagens para chegar à resposta. Vou comparar as respostas ao final para escolher a mais comum. Aqui está o problema:
"Maria é proprietária de uma padaria que produz 40 pães por dia. Todos os dias, ela reserva 10 pães para o café da manhã da equipe e vende o restante. Cada pão vendido gera uma receita de R$ 3,00. Além disso, se os pães não forem vendidos até o final do dia, ela doa metade dos pães restantes para um abrigo e guarda a outra metade para o dia seguinte. Em um dia típico, ela vende 25 pães. Qual é a receita diária média de Maria com as vendas, considerando que ela doa os pães não vendidos todos os dias?"

Instruções para o modelo:
- Resolva o problema passo a passo, detalhando seu raciocínio em cada etapa.
- Explique qualquer suposição que esteja fazendo, se aplicável.
- Explore diferentes abordagens para o cálculo, se houver mais de uma maneira de resolver o problema.
- Forneça uma resposta final para cada caminho de raciocínio.

Exemplo de Respostas:
- Caminho 1: [Descreva o cálculo e a resposta, explicando cada etapa e assumindo uma abordagem específica]
- Caminho 2: [Descreva o cálculo e a resposta, explicando cada etapa com uma abordagem ligeiramente diferente]
- Caminho 3: [Descreva o cálculo e a resposta, detalhando um terceiro possível caminho]

No final, eu escolherei a resposta mais comum entre as abordagens.
```

### Tree-of-Thought (ToT)
Expande a abordagem Chain-of-Thought (CoT), promovendo a exploração de vários caminhos de raciocínio possíveis para resolver problemas complexos.

```
Quem inventou a lâmpada elétrica moderna? Considere todas as contribuições históricas, explore os passos intermediários e avalie diferentes possibilidades antes de concluir.
```

Outro exemplo:
```
Três especialistas estão discutindo onde a bola foi deixada. Cada especialista irá registrar um raciocínio por vez e, em seguida, compartilhará com os outros. Após cada rodada, eles podem ajustar suas respostas com base no que observaram. Se algum especialista perceber que está em um caminho errado, ele abandonará a discussão.

A situação é a seguinte:

"Bob está na sala.
Ele caminha até a cozinha carregando uma xícara.
Ele coloca uma bola na xícara e leva a xicara para o quarto.
Ele vira a xícara de cabeça para baixo e vai até o jardim.
Ele coloca a xícara no jardim e vai até a garagem.
Onde está a bola? "

Narre o pensamento dos especialistas!
```

## Mais dicas gerais
### Reduza descrições vagas: Seja claro e específico.
Menos eficaz ❌:
```
A descrição deste produto deve ser bastante curta, com apenas algumas frases, e não muito mais.
```

Melhor ✅:
```
Use um parágrafo de 3 a 5 frases para descrever este produto.
```

### Diga o que fazer ao invés do que não fazer.
Menos eficaz ❌:
```
A seguir está uma conversa entre um Agente e um Cliente. NÃO PERGUNTE O NOME DE USUÁRIO OU SENHA. NÃO REPITA.

Cliente: Não consigo acessar minha conta.
Agente:
```

Melhor ✅:
```
A seguir está uma conversa entre um Agente e um Cliente. O agente tentará diagnosticar o problema e sugerir uma solução, abstendo-se de fazer perguntas relacionadas a credencial. Em vez de pedir as credenciais, como nome de usuário ou senha, encaminhe o usuário para o artigo de ajuda www.siteexemplo.com/ajuda/faq

Cliente: Não consigo acessar minha conta.
Agente: …
```

### Para geração de código, use palavras iniciais apropriadas.

Menos eficiente ❌:

```python
# Write a simple python function that  
# 1. Ask me for a number in mile  
# 2. It converts miles to kilometers  
```

Melhor ✅:
```python
# Write a simple python function that  
# 1. Ask me for a number in mile  
# 2. It converts miles to kilometers  

import
```

[Prompt Engineering - OpenAI](https://platform.openai.com/docs/guides/prompt-engineering)


### TL;DR
TL;DR significa "Too Long; Didn't Read" ("Muito Longo; Não Li" em português). É usado para resumir um texto longo em uma versão curta e concisa, destacando os pontos principais.
#dica

### ELI5
"Explain Like I’m 5 Years Old".

```
Sobre IA Generativa, me explique como se fosse uma criança de 5 anos.
```

### Instrua o modelo para que faça mais perguntas.
```
O que é Arquitetura?

Você entendeu minha solicitação claramente? Se não entender totalmente minha solicitação, faça perguntas sobre o contexto para que, quando eu responder, você possa realizar a tarefa solicitada de forma mais eficiente.
```

### Dicas amplas
- Você pode querer a saída em um formato específico, tabela, documento, json, csv...
- Repetir instruções gera bons resultados principalmente quando o prompt é longo.
- **Prompts negativos** no contexto da geração de texto são uma maneira de guiarmos o modelo especificando o que não queremos ver na saída.
- Restringir o tamanho é uma boa idéia: independentemente de se esperar uma resposta com uma única palavra ou com 10 frases, adicione isso ao prompt.

### Um prompt deve ter cinco itens: Persona, Público, Atividade, Limitações e Metas.
#### Persona
A persona refere-se à identidade ou ao estilo a ser adotado pelo ChatGPT. Ao definir uma persona, você está instruindo o modelo a seguir determinado tom de voz, estilo de escrita ou características específicas.

```
Você é um editor-chefe de uma revista digital de notícias (Persona).
```

#### Público
Diferentes públicos requerem comunicações completamente diferentes sobre o mesmo contexto. É importante definir o público que irá ler o texto que está sendo feito.

```
Seu público-alvo são jornalistas em início de carreira e leitores interessados em notícias explicativas (Público). 
```

#### Atividade 
São as ações ou tarefas específicas que você deseja que o ChatGPT execute. Pode incluir responder a perguntas, criar histórias, elaborar roteiros, redigir e-mails e assim por diante...

```
Sua tarefa é escrever um texto curto e direto sobre a importância de checar informações antes de publicá-las, usando exemplos práticos (Atividade).
```

####  Limitações
São restrições específicas que você deseja impor à resposta do ChatGPT. Isso pode incluir ou excluir certos tópicos, estabelecer um limite de palavras, evitar informações sensíveis e assim por diante.


```
Você deve evitar linguagem técnica excessiva e referências a ferramentas específicas (Limitações)
```

#### Metas
As metas orientam o ChatGPT sobre o objetivo principal da resposta.

```
Garantir que o texto seja compreensível, educativo e incentive boas práticas jornalísticas (Metas)
```

#### Juntando tudo (no mínimo 3)
```
Você é um editor-chefe de uma revista digital de notícias (Persona). Seu público-alvo são jornalistas em início de carreira e leitores interessados em notícias explicativas (Público). Sua tarefa é escrever um texto curto e direto sobre a importância de checar informações antes de publicá-las, usando exemplos práticos (Atividade). Você deve evitar linguagem técnica excessiva e referências a ferramentas específicas (Limitações) e garantir que o texto seja compreensível, educativo e incentive boas práticas jornalísticas (Metas).
```

#### Outros
- Exemplo
    - Incluir exemplos na sua pergunta é uma prática recomendada. Exemplos tornam mais fácil para a IA entender o que você deseja.
        - Por exemplo: "Dê um KPI relacionado ao setor financeiro referente a margem bruta por semana e que seja rápido de implementar..."
- Tom
    - O tom da resposta é importante. Você pode pedir um tom formal, casual, entusiástico ou até pessimista.
        - exemplo: "Forneça as informações em formato de lista com marcadores, escreva com um tom motivador e entusiasmado!"