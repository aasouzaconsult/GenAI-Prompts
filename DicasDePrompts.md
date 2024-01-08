# Dicas de Prompts 💻>

## Persona
Pense em quem você quer que a IA seja ao responder. Pode ser um especialista, um recrutador, um escritor, um profissional de dados ou até mesmo um personagem fictício. 

**Por exemplo**: Você é um especialista em análise de dados e trabalha no setor financeiro de bigtechs...

## Clear Instructions
Gere instruções claras e seja específico, forneça mais detalhes (ela (IA) não sabe o que você tá precisando). Seja claro sobre qual é o seu objetivo final. 

*Comece sua pergunta com um verbo de ação, como “gerar”, “dar”, “escrever” ou “analisar”.

**Por exemplo:** Escreva um resumo do relatório de vendas trimestrais. Um exemmplo se encontra abaixo...

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

# Técnicas de Prompts 💻>
[Mais informações e detalhes](https://www.promptingguide.ai/techniques)

## Zero-Shot Prompts
Quando não é necessário nenhum exemplo, o próprio modelo já pode lhe dar respostas corretas.

**Por exemplo:** When is Christmas in America?

## Few-Shot Prompts
Quando você dá um contexto, dá exemplos para que a resposta saia ou seja mais precisa

**Por exemplo:** 
- What is Alex´s favourite type of foods?
  - Não saberá responder, pois ele não conhece meus gostos!
- Alex´s favourite type of foods include: Burges, Pizza, Fries, Chocolate
- What restaurant should I take Alex to in Dubai this weekend? (aqui ele deve escolher restaurantes do meu gosto e indicar)

## Chain-of-Thought (CoT) Prompting
prompt = """
The odd numbers in this group add up to an even number: 4,  8, 9,  15, 12, 1.
A: Adding all the odd numbers (9,15,1). The answer is false.

The odd numbers in this group add up to an even number: 15,32,5,13,82,7,1.
"""

## Self-Consistency
## Generate Knowledge Prompting
## Program-aided Language Model (PAL)
## ReAct

# Ferramentas
- Dyno (Prompt Enginnering IDE)
- Dust
- LangChain
- Prompttable
   
# Mais informações
- [Engenharia de Prompts](https://medium.com/blog-do-zouza/genai-o-que-%C3%A9-engenharia-de-prompt-6d416afe1323)
- [Dicas de Prompt - OpenAI](https://platform.openai.com/docs/guides/prompt-engineering)
- [Dicas de Prompt](https://www.promptingguide.ai/pt/introduction/basics)
- [Mais dicas de Prompts](https://medium.com/@petrusje/domine-a-arte-de-criar-prompts-eficientes-para-chatgpt-e-outras-ias-uma-base-s%C3%B3lida-b78f3b30fd9a)
