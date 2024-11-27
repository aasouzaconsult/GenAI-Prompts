# Arquitetura Transformer 🤖

## Desenho
<img src="https://blogdozouza.wordpress.com/wp-content/uploads/2024/11/transformes_alex.jpg" alt="Imagem WhatsApp" width="500" height="auto">

[Fonte](https://proceedings.neurips.cc/paper_files/paper/2017/file/3f5ee243547dee91fbd053c1c4a845aa-Paper.pdf)

## Visão geral
Abaixo, terá uma visão bem simples do funcionamento do transformer.

Vamos construir um exemplo com **um prompt inicial**, mostrando **todas as etapas do algoritmo**, incluindo **onde e como o modelo decide a próxima palavra**.

---

### **Prompt inicial:**  
**"O gato dorme..."**  
Esse é o texto de entrada, e o modelo precisa prever a próxima palavra para completar a frase.

---

### **Passo a passo do Transformer com o exemplo:**

#### **1. Input Embedding**  
Cada palavra do prompt ("O", "gato", "dorme") é convertida em um vetor numérico. Esses vetores representam o significado da palavra no modelo.  
**Exemplo:**  
- "O" → `[0.5, -0.2, 0.8]`  
- "gato" → `[1.0, 0.3, -0.4]`  
- "dorme" → `[-0.6, 1.2, 0.7]`

---

#### **2. Positional Encoding**  
Adiciona informações sobre a posição de cada palavra no prompt, garantindo que o modelo saiba que "O" é a primeira palavra, "gato" é a segunda, etc.  
**Exemplo:**  
- "O" (posição 1): `[0.5 + 0.1, -0.2 + 0.3, 0.8 + 0.2]`  
- "gato" (posição 2): `[1.0 + 0.2, 0.3 + 0.6, -0.4 + 0.1]`  
- "dorme" (posição 3): `[-0.6 + 0.3, 1.2 + 0.7, 0.7 + 0.5]`

---

#### **3. Multi-Head Attention (Self-Attention)**  
O modelo agora calcula as relações entre as palavras para entender o contexto. Ele analisa como cada palavra se conecta com as outras.  
**Exemplo:**  
- "gato" tem uma relação forte com "dorme" (quem está dormindo).  
- "O" tem menos relevância no contexto imediato.  

O modelo ajusta os vetores com base nessas relações.  
**Resultado:**  
- "O" → ajustado para `[0.4, -0.1, 0.7]`  
- "gato" → ajustado para `[1.2, 0.4, -0.5]`  
- "dorme" → ajustado para `[-0.7, 1.3, 0.8]`

---

#### **4. Feedforward Network**  
Os vetores ajustados passam por uma rede para refinar as representações. Isso ajuda o modelo a capturar nuances mais complexas do texto.  
**Resultado (após refinamento):**  
- "O" → `[0.3, -0.2, 0.6]`  
- "gato" → `[1.1, 0.5, -0.3]`  
- "dorme" → `[-0.6, 1.4, 0.9]`

---

#### **5. Saída do Encoder**
Após essas etapas, o Encoder gera representações contextuais das palavras da entrada, prontos para serem usados no Decodificador.

---

#### **6. Output Embedding (no Decodificador)**  
A sequência parcial gerada até agora no Decodificador é deslocada para a direita (**shifted right**), com um token especial de início (**[START]**) sendo adicionado.  
- **Exemplo:**  
  Se a saída parcial for **"O gato dorme"**, o Decodificador recebe:  
  **[START], O, gato, dorme**.  

Cada palavra é convertida em um vetor numérico:  
- "[START]" → `[0.1, 0.2, 0.3]`  
- "O" → `[0.5, -0.3, 0.7]`  
- "gato" → `[1.0, 0.4, -0.2]`  
- "dorme" → `[-0.6, 0.9, 0.8]`  

---

#### **7. Positional Encoding (no Decodificador)**  
Adiciona informações sobre a posição das palavras geradas, garantindo que o modelo saiba a ordem correta.  
**Exemplo:**  
- "[START]" (posição 1): `[0.1 + 0.2, 0.2 + 0.1, 0.3 + 0.3]`  
- "O" (posição 2): `[0.5 + 0.1, -0.3 + 0.2, 0.7 + 0.1]`  

---

#### **8. Masked Multi-Head Attention (Decodificador)**  
O Decodificador recebe as palavras já processadas: "O gato dorme" (Algo como: **"[START], O, gato, dorme"**)) e tenta prever a próxima palavra. Como é "masked" (mascarado), ele só vê as palavras anteriores.  

**Cálculo:**  
- Baseando-se no contexto de "O gato dorme", o modelo considera que "dorme" está relacionado com um lugar.  

---

#### **9. Multi-Head Attention (Cross-Attention)**  
Aqui, o Decodificador conecta o contexto do Encoder (saída do "O gato dorme") com as palavras que está tentando prever. Ele verifica como o contexto da entrada (quem está dormindo) se relaciona com possíveis saídas (onde está dormindo).  
**Resultado:**  
O modelo entende que a próxima palavra deve ser algo como **"no"**, indicando uma localização.

---

#### **10. Feed Forward (no Decodificador):**
Depois da etapa de *Cross-Attention*, os vetores passam por uma rede *Feed Forward*, que ajusta e refina as representações antes de serem projetadas no vocabulário.
Isso garante que as informações estejam bem processadas e preparadas para a próxima palavra ser prevista.

---

#### **11. Linear**
O vetor gerado para a palavra **"no"** contém informações de todo o contexto aprendido pelo modelo. Isso significa que ele leva em conta:
- O que veio antes (**"O gato dorme"**).  
- O papel que **"no"** desempenha na frase.

Esse vetor pode ser algo abstrato como:  
**"no" → `[0.2, 0.8, -0.1]`**  
Ele é apenas uma representação numérica do que o modelo entende sobre a palavra no contexto da frase.

**O que a camada Linear faz?**

A camada Linear transforma o vetor abstrato **`[0.2, 0.8, -0.1]`** em uma pontuação para cada palavra do vocabulário. Suponha que o vocabulário do modelo tenha 50.000 palavras, como:
- "sofá"  
- "carro"  
- "mesa"  
- Etc...

A camada Linear faz o seguinte:  
- Converte o vetor **`[0.2, 0.8, -0.1]`** em outro vetor, por exemplo:  
  **`[3.0, 1.0, 0.5, ...]`**, onde cada posição do vetor corresponde a uma palavra no vocabulário.  
  - Exemplo:
    - 1ª posição → "sofá" com pontuação 3.0  
    - 2ª posição → "carro" com pontuação 1.0  
    - 3ª posição → "mesa" com pontuação 0.5  
    - ...


#### **12. Softmax (Previsão da Próxima Palavra)**  
As pontuações geradas pela camada Linear não são probabilidades, mas valores brutos. O **Softmax** transforma essas pontuações em probabilidades entre 0 e 1, garantindo que a soma seja 100%.  
**Exemplo:**  
- "sofá" → pontuação 3.0 → probabilidade 70%  
- "carro" → pontuação 1.0 → probabilidade 20%  
- "mesa" → pontuação 0.5 → probabilidade 10%  

Com essas probabilidades, o modelo escolhe a palavra com maior probabilidade, no caso, **"sofá"**.

**Saída:**  
A palavra com maior probabilidade é escolhida: **"sofá"**.  

---

#### **Recomeço do Ciclo:**  
Agora o prompt se torna **"O gato dorme no sofá"**, e o modelo pode continuar prevendo a próxima palavra caso seja solicitado.

---

### **Resumo do Fluxo:**
1. Entrada: **"O gato dorme"** é processada no Encoder.  
2. Decoder prevê a próxima palavra: **"sofá"**, com base no contexto.  
3. O ciclo se repete até completar a saída desejada.

---

### **Outros pontos:**
#### **Add & Norm:**
O **Add & Norm** é uma etapa simples, mas essencial no Transformer. Ele tem duas funções principais:

1. **Residual Connection (Add):**  
   Ele **soma** a entrada original da camada com a saída processada (por exemplo, do Self-Attention ou Feedforward). Isso ajuda a preservar informações importantes da entrada inicial que poderiam ser perdidas no processamento.

2. **Normalização (Norm):**  
   Depois da soma, ele **normaliza os valores** para manter a estabilidade do modelo e garantir que os valores não fiquem muito altos ou muito baixos, facilitando o aprendizado.

**Resumo:**  
O **Add & Norm** age como um "ajuste fino" que combina o que o modelo já sabe (entrada) com o que ele acabou de aprender (saída), garantindo que o aprendizado continue eficiente e estável.

---

Link: [Para aprofundar](https://proceedings.neurips.cc/paper_files/paper/2017/file/3f5ee243547dee91fbd053c1c4a845aa-Paper.pdf) 🤓
