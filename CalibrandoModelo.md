# Calibrando o Modelo

**Temperature | Max Tokens | Stop Sequences | Top p | Top k** | Seed | Frequency penalty | Presence penalty

## Temperature
Ajusta a criatividade das respostas geradas pelo modelo. Um valor mais alto incentiva respostas mais inovadoras e menos previsíveis.

![](https://blogdozouza.wordpress.com/wp-content/uploads/2024/11/screenshot_32.png)

![](https://blogdozouza.wordpress.com/wp-content/uploads/2024/11/screenshot_33.png)


## Max Tokens
Define o limite máximo de tokens (palavras ou partes de palavras) para a resposta gerada, garantindo que o conteúdo produzido não exceda um comprimento específico.

![](https://blogdozouza.wordpress.com/wp-content/uploads/2024/11/screenshot_35.png)


## Stop Sequences
São palavras ou símbolos que indicam ao modelo de linguagem quando encerrar a geração de texto, permitindo um maior controle sobre o resultado final.

![](https://blogdozouza.wordpress.com/wp-content/uploads/2024/11/screenshot_37.png)

## Top k e Top p
### Top_k
limita o número de palavras (ou tokens) que o modelo considera ao gerar a próxima palavra.
Um Top-k de 1 significa que o próximo token selecionado é o mais provável entre todos os tokens no vocabulário do modelo, enquanto um Top-k de 3 significa que o próximo token está selecionado entre os três tokens mais prováveis usando a temperatura.
Números menores tornam a resposta mais precisa; números maiores deixam o modelo explorar mais!

![](https://blogdozouza.wordpress.com/wp-content/uploads/2024/11/screenshot_38.png)
- [link](https://cloud.google.com/vertex-ai/generative-ai/docs/model-reference/gemini?hl=pt-br)

### Top_p
considera as palavras até que a soma das suas probabilidades alcance um certo limiar (probabilidade acumulada).
Mantém o modelo nas escolhas mais prováveis, mas pode abrir espaço para variações conforme o valor de p aumenta.

![](https://blogdozouza.wordpress.com/wp-content/uploads/2024/11/screenshot_39.png)

![](https://blogdozouza.wordpress.com/wp-content/uploads/2024/11/screenshot_40.png)

### Relacionando com Temperature
Você pode usar os três juntos para ajustar a resposta: baixa temperature com baixo Top_k/p para precisão, ou alta temperature com alto Top K/P para respostas mais criativas.

---
## Seed

A **Seed** (semente) é um valor numérico usado para inicializar geradores de números pseudoaleatórios, tornando processos estocásticos reprodutíveis. Em alguns sistemas de geração de texto, definir uma seed permite obter a mesma saída para a mesma entrada e configurações.

No entanto, **atualmente o ChatGPT e os modelos da OpenAI não oferecem suporte ao parâmetro seed na API pública**. A geração de texto nesses modelos é não determinística por padrão, e mesmo com os mesmos parâmetros, as respostas podem variar entre execuções.

### Exemplo Prático

Embora não seja possível definir uma seed no ChatGPT, você pode controlar a aleatoriedade ajustando outros parâmetros como **Temperature**, **Top_p**, **Frequency Penalty** e **Presence Penalty** para obter resultados mais consistentes.

### Links Úteis

- [Documentação da OpenAI sobre a API](https://platform.openai.com/docs/api-reference/introduction)

## Frequency Penalty

A **Frequency Penalty** (penalidade de frequência) ajusta a probabilidade de o modelo repetir tokens com base na frequência de sua ocorrência no texto gerado até o momento. Essa penalidade desencoraja o modelo de reutilizar palavras ou frases que já apareceram, promovendo respostas mais diversas e evitando repetições indesejadas.

- **Valores Mais Altos**: Reduzem a tendência do modelo de repetir tokens frequentes, aumentando a variedade lexical.
- **Valores Mais Baixos ou Zero**: Permitem que o modelo repita tokens com mais frequência, o que pode ser adequado em contextos onde a repetição é natural ou necessária.

### Exemplo usando ChatGPT

**Sem Penalidade de Frequência** (`frequency_penalty=0`):

**Pergunta**: "Escreva um parágrafo sobre os benefícios de caminhar."

**Resposta**:

"Caminhar é uma atividade física simples que traz muitos benefícios para a saúde. Caminhar regularmente pode melhorar a saúde cardiovascular. Além disso, caminhar ajuda na perda de peso e melhora o humor."

**Com Penalidade de Frequência Alta** (`frequency_penalty=1`):

**Resposta**:

"Caminhar é uma forma acessível de exercício que oferece diversos benefícios. A prática regular pode fortalecer o coração, auxiliar na gestão do peso e elevar o bem-estar emocional."

### Links Úteis

- [Documentação da OpenAI sobre Frequency Penalty](https://platform.openai.com/docs/api-reference/parameter-details)

## Presence Penalty

A **Presence Penalty** (penalidade de presença) influencia a probabilidade de o modelo mencionar novamente tokens que já apareceram, independentemente de quantas vezes eles foram usados. Diferentemente da penalidade de frequência, que considera a frequência de ocorrência, a penalidade de presença considera apenas se o token já foi usado ou não.

- **Valores Mais Altos**: Desencorajam o modelo de reutilizar qualquer token já mencionado, promovendo a introdução de novos tópicos ou ideias.
- **Valores Mais Baixos ou Zero**: Permitem que o modelo retome tokens já utilizados, mantendo a coesão em torno de determinados assuntos.

### Exemplo usando ChatGPT

**Sem Penalidade de Presença** (`presence_penalty=0`):

**Pergunta**: "Descreva as características de um smartphone moderno."

**Resposta**:

"Um smartphone moderno possui uma tela sensível ao toque de alta resolução, câmeras avançadas, conectividade à internet e uma variedade de aplicativos para diversas tarefas."

**Com Penalidade de Presença Alta** (`presence_penalty=1`):

**Resposta**:

"Os dispositivos móveis atuais oferecem telas interativas nítidas, recursos fotográficos sofisticados, acesso online e múltiplas aplicações para diferentes necessidades."

### Links Úteis

- [Documentação da OpenAI sobre Presence Penalty](https://platform.openai.com/docs/api-reference/parameter-details)

### Combinando Penalidades

A combinação estratégica da **Frequency Penalty** e **Presence Penalty** permite um controle refinado sobre a geração de texto:

- **Originalidade**: Penalidades altas incentivam o modelo a explorar novas palavras e ideias.
- **Coesão**: Penalidades baixas mantêm o texto focado e coeso, útil quando se deseja aprofundar em um tópico específico.

### Dica Prática com ChatGPT

Embora a interface padrão do ChatGPT não permita ajustar diretamente esses parâmetros, desenvolvedores podem utilizar a [API da OpenAI](https://platform.openai.com/docs/api-reference/completions/create) para personalizar essas configurações e observar como elas afetam as respostas do modelo.

**Exemplo de Chamada de API**:

```json
{
  "model": "text-davinci-003",
  "prompt": "Escreva um conto curto sobre uma aventura no espaço.",
  "max_tokens": 200,
  "temperature": 0.7,
  "frequency_penalty": 0.5,
  "presence_penalty": 0.5
}
```

Isso configura o modelo para gerar um conto curto sobre uma aventura no espaço, aplicando penalidades de frequência e presença para aumentar a originalidade e criatividade da narrativa.

---

**Nota**: Ajustar esses parâmetros permite que você controle a criatividade e a repetição na saída do modelo, adaptando-o às necessidades específicas do seu projeto.