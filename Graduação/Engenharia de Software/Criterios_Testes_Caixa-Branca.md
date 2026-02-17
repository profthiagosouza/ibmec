# Critérios Testes Caixa-Branca



Critérios Testes Caixa-BrancaAbrir barra lateralChatGPT 4oChatGPT 4oVocê disse:Como um professor de Teste de Software, gere conteúdo no formato Mardown sobre critérios para seleção de testes caixa-branca.O ChatGPT disse:Aqui está um conteúdo em formato Markdown sobre critérios para seleção de testes caixa-branca:markdownCopiarEditar# Critérios para Seleção de Testes Caixa-Branca

Os testes **caixa-branca** (ou **white-box testing**) são uma abordagem de teste de software que avalia a estrutura interna e a lógica do código-fonte de um sistema. A escolha dos testes a serem aplicados nessa abordagem depende de diversos critérios, que garantem uma cobertura eficiente do código.

## 1. Cobertura de Instruções
A **cobertura de instruções** (statement coverage) verifica se cada instrução do código foi executada pelo menos uma vez durante os testes.

### Vantagens:
- Simples de implementar.
- Ajuda a identificar trechos de código não executados.

### Desvantagens:
- Não garante a cobertura de todos os fluxos lógicos do programa.

## 2. Cobertura de Decisões
A **cobertura de decisões** (decision coverage) testa se todas as possíveis decisões (como `if`, `switch`, `while`, etc.) são avaliadas tanto para verdadeiro quanto para falso.

### Vantagens:
- Garante que todas as ramificações do código sejam testadas.
- Melhor que a cobertura de instruções, pois considera os fluxos de execução.

### Desvantagens:
- Pode não cobrir todas as combinações possíveis de condições compostas.

## 3. Cobertura de Condições
A **cobertura de condições** (condition coverage) verifica se cada condição booleana dentro de expressões condicionais foi avaliada como `true` e `false` pelo menos uma vez.

### Vantagens:
- Testa todas as subcondições das decisões do código.

### Desvantagens:
- Pode não garantir a cobertura total dos caminhos de execução.

## 4. Cobertura de Decisão-Condicional (MCC – Multiple Condition Coverage)
A **cobertura de decisão-condicional** combina os critérios de **cobertura de decisão** e **cobertura de condição**, garantindo que todas as combinações de valores booleanos em expressões condicionais sejam testadas.

### Vantagens:
- Maior rigor na validação das decisões lógicas do código.
- Detecta falhas que outros critérios podem não encontrar.

### Desvantagens:
- A complexidade dos testes cresce exponencialmente com o número de condições.

## 5. Cobertura de Caminhos
A **cobertura de caminhos** (path coverage) testa todos os caminhos possíveis de execução dentro do código.

### Vantagens:
- Detecta falhas em fluxos raros ou não triviais.
- Considera todas as combinações possíveis de execução.

### Desvantagens:
- Pode ser impraticável para sistemas grandes devido ao número exponencial de caminhos.

## 6. Cobertura de Fluxo de Dados
A **cobertura de fluxo de dados** analisa como variáveis são inicializadas, utilizadas e descartadas no código.

### Vantagens:
- Identifica possíveis erros relacionados a variáveis não inicializadas ou reutilização indevida de valores.

### Desvantagens:
- Pode exigir grande esforço de análise para código complexo.

## Conclusão
A seleção do critério de teste mais adequado depende do objetivo dos testes e do nível de confiança desejado no código. Para um bom equilíbrio entre custo e qualidade, geralmente combina-se diferentes critérios, priorizando aqueles que oferecem maior cobertura com menos esforço.

### Resumo dos Critérios:
| Critério | O que cobre? | Vantagens | Desvantagens |
|----------|------------|-----------|--------------|
| **Cobertura de Instruções** | Testa todas as instruções pelo menos uma vez | Simples e rápido | Não garante a cobertura de fluxos |
| **Cobertura de Decisões** | Testa todos os ramos de decisões (`if`, `while`) | Considera fluxos lógicos | Pode ignorar condições individuais |
| **Cobertura de Condições** | Testa cada condição booleana de forma independente | Verifica condições dentro de decisões | Não cobre combinações de condições |
| **Cobertura de Decisão-Condicional (MCC)** | Testa todas as combinações de condições | Maior rigor na validação lógica | Muito complexo para múltiplas condições |
| **Cobertura de Caminhos** | Testa todos os caminhos de execução possíveis | Considera todos os fluxos do código | Pode ser inviável em código grande |
| **Cobertura de Fluxo de Dados** | Analisa o uso de variáveis | Detecta erros de inicialização e uso indevido | Pode exigir análise complexa |

O ideal é equilibrar esforço e benefício, adotando critérios que maximizem a detecção de falhas sem tornar o processo de teste inviável.

---
Esse conteúdo pode ser usado como material de aula ou complemento didático para os alunos. Caso queira adicionar exemplos práticos em código, posso ajudar com isso também! 🚀Você disse:Como um professor de Teste de Software, gere conteúdo no formato Mardown sobre critérios para seleção de testes caixa-branca com exemplos práticos em código.O ChatGPT disse:Aqui está um material em formato Markdown sobre critérios para seleção de testes caixa-branca, incluindo explicações e exemplos práticos em código Python.markdownCopiarEditar# Critérios para Seleção de Testes Caixa-Branca

Os **testes caixa-branca** são aqueles que analisam a estrutura interna do código para validar sua lógica e fluxos de execução. Abaixo, exploramos os principais critérios de seleção de testes, cada um acompanhado de exemplos práticos em **Python**.

---

## 1. Cobertura de Instruções
A **cobertura de instruções** verifica se cada linha de código foi executada pelo menos uma vez.

### Exemplo:
```python
def calcular_media(a, b):
    soma = a + b
    media = soma / 2
    return media

# Teste
assert calcular_media(10, 20) == 15
✅ O teste cobre todas as instruções do código.2. Cobertura de DecisõesA cobertura de decisões assegura que todas as ramificações (if, else, while) sejam executadas ao menos uma vez.Exemplo:pythonCopiarEditardef par_ou_impar(n):
    if n % 2 == 0:
        return "Par"
    else:
        return "Ímpar"

# Testes
assert par_ou_impar(4) == "Par"  # Cobre o caminho do `if`
assert par_ou_impar(3) == "Ímpar"  # Cobre o caminho do `else`
✅ Esse conjunto de testes garante cobertura de decisão, pois todas as condições foram verificadas.3. Cobertura de CondiçõesA cobertura de condições verifica se todas as condições booleanas dentro de decisões são testadas para True e False.Exemplo:pythonCopiarEditardef pode_dirigir(idade, tem_carteira):
    if idade >= 18 and tem_carteira:
        return "Pode dirigir"
    else:
        return "Não pode dirigir"

# Testes
assert pode_dirigir(20, True) == "Pode dirigir"  # idade >= 18 e tem_carteira == True
assert pode_dirigir(20, False) == "Não pode dirigir"  # idade >= 18, mas sem carteira
assert pode_dirigir(16, True) == "Não pode dirigir"  # idade < 18, mas com carteira
assert pode_dirigir(16, False) == "Não pode dirigir"  # idade < 18 e sem carteira
✅ Aqui garantimos que todas as condições são testadas isoladamente.4. Cobertura de Decisão-Condicional (MCC – Multiple Condition Coverage)A cobertura de decisão-condicional assegura que todas as combinações de condições sejam testadas.Exemplo:pythonCopiarEditardef aprovar_emprestimo(renda, score_credito):
    if renda > 5000 and score_credito >= 700:
        return "Aprovado"
    return "Negado"

# Testes cobrindo todas as combinações
assert aprovar_emprestimo(6000, 750) == "Aprovado"  # True, True
assert aprovar_emprestimo(6000, 650) == "Negado"  # True, False
assert aprovar_emprestimo(4000, 750) == "Negado"  # False, True
assert aprovar_emprestimo(4000, 650) == "Negado"  # False, False
✅ Todas as combinações das condições foram testadas.5. Cobertura de CaminhosA cobertura de caminhos testa todos os fluxos possíveis de execução.Exemplo:pythonCopiarEditardef classificar_numero(n):
    if n > 0:
        if n % 2 == 0:
            return "Positivo e Par"
        else:
            return "Positivo e Ímpar"
    elif n < 0:
        return "Negativo"
    else:
        return "Zero"

# Testes cobrindo todos os caminhos
assert classificar_numero(10) == "Positivo e Par"
assert classificar_numero(7) == "Positivo e Ímpar"
assert classificar_numero(-3) == "Negativo"
assert classificar_numero(0) == "Zero"
✅ Todos os caminhos possíveis doThe operation was abortedVocê disse:Como um professor de Teste de Software, gere conteúdo no formato Mardown em um único arquivo sobre critérios para seleção de testes caixa-branca com exemplos práticos em pseudocódigo.O ChatGPT disse:Aqui está um conteúdo completo no formato Markdown sobre critérios para seleção de testes caixa-branca, incluindo explicações e exemplos práticos em pseudocódigo.markdownCopiarEditar# Critérios para Seleção de Testes Caixa-Branca

Os **testes caixa-branca** são uma técnica de teste de software que analisa a estrutura interna e a lógica do código. Eles garantem que todas as partes do código sejam verificadas para detectar possíveis erros. A seleção de testes caixa-branca pode seguir diferentes critérios, cada um focado em um aspecto específico da execução do programa.

---

## 1. Cobertura de Instruções
A **cobertura de instruções** verifica se cada linha de código foi executada pelo menos uma vez.

### Exemplo:
```pseudocode
ALGORITMO calcularMedia
  INICIO
    ENTRADA a, b
    soma ← a + b
    media ← soma / 2
    RETORNA media
  FIM
Testes:calcularMedia(10, 20) → 15calcularMedia(5, 5) → 5✅ Todos os comandos do algoritmo são executados.2. Cobertura de DecisõesA cobertura de decisões assegura que todas as ramificações (if, else, while) sejam testadas.Exemplo:pseudocodeCopiarEditarALGORITMO verificarParOuImpar
  INICIO
    ENTRADA n
    SE n MOD 2 = 0 ENTAO
      RETORNA "Par"
    SENAO
      RETORNA "Ímpar"
  FIM
Testes:verificarParOuImpar(4) → "Par" ✅ Caminho do ifverificarParOuImpar(3) → "Ímpar" ✅ Caminho do else✅ Ambas as decisões foram testadas.3. Cobertura de CondiçõesA cobertura de condições verifica se cada condição booleana dentro de decisões foi testada para Verdadeiro e Falso.Exemplo:pseudocodeCopiarEditarALGORITMO podeDirigir
  INICIO
    ENTRADA idade, temCarteira
    SE idade >= 18 E temCarteira = VERDADEIRO ENTAO
      RETORNA "Pode dirigir"
    SENAO
      RETORNA "Não pode dirigir"
  FIM
Testes:podeDirigir(20, VERDADEIRO) → "Pode dirigir" ✅ (idade >= 18 = V, temCarteira = V)podeDirigir(20, FALSO) → "Não pode dirigir" ✅ (idade >= 18 = V, temCarteira = F)podeDirigir(16, VERDADEIRO) → "Não pode dirigir" ✅ (idade >= 18 = F, temCarteira = V)podeDirigir(16, FALSO) → "Não pode dirigir" ✅ (idade >= 18 = F, temCarteira = F)✅ Todas as condições foram testadas isoladamente.4. Cobertura de Decisão-Condicional (MCC – Multiple Condition Coverage)A cobertura de decisão-condicional testa todas as combinações possíveis de condições.Exemplo:pseudocodeCopiarEditarALGORITMO aprovarEmprestimo
  INICIO
    ENTRADA renda, scoreCredito
    SE renda > 5000 E scoreCredito >= 700 ENTAO
      RETORNA "Aprovado"
    SENAO
      RETORNA "Negado"
  FIM
Testes cobrindo todas as combinações:aprovarEmprestimo(6000, 750) → "Aprovado" ✅ (renda > 5000 = V, scoreCredito >= 700 = V)aprovarEmprestimo(6000, 650) → "Negado" ✅ (renda > 5000 = V, scoreCredito >= 700 = F)aprovarEmprestimo(4000, 750) → "Negado" ✅ (renda > 5000 = F, scoreCredito >= 700 = V)aprovarEmprestimo(4000, 650) → "Negado" ✅ (renda > 5000 = F, scoreCredito >= 700 = F)✅ Todas as combinações foram testadas.5. Cobertura de CaminhosA cobertura de caminhos testa todos os fluxos possíveis de execução.Exemplo:pseudocodeCopiarEditarALGORITMO classificarNumero
  INICIO
    ENTRADA n
    SE n > 0 ENTAO
      SE n MOD 2 = 0 ENTAO
        RETORNA "Positivo e Par"
      SENAO
        RETORNA "Positivo e Ímpar"
    SENAO SE n < 0 ENTAO
      RETORNA "Negativo"
    SENAO
      RETORNA "Zero"
  FIM
Testes cobrindo todos os caminhos:classificarNumero(10) → "Positivo e Par"`classificarNumero(The operation was abortedVocê disse:Como um professor de Teste de Software, gere conteúdo no formato Mardown em um único arquivo sobre critérios para seleção de testes caixa-branca com exemplos práticos em Portugol.O ChatGPT disse:Aqui está um conteúdo completo no formato Markdown sobre critérios para seleção de testes caixa-branca, incluindo explicações e exemplos práticos em Portugol.markdownCopiarEditar# Critérios para Seleção de Testes Caixa-Branca

Os **testes caixa-branca** são uma abordagem de teste de software que avalia a estrutura interna e a lógica do código. Esses testes garantem que cada parte do código seja verificada para identificar possíveis erros antes da liberação do software.

## Critérios para Seleção de Testes

Os critérios para testes caixa-branca incluem:

1. **Cobertura de Instruções**
2. **Cobertura de Decisões**
3. **Cobertura de Condições**
4. **Cobertura de Decisão-Condicional (MCC – Multiple Condition Coverage)**
5. **Cobertura de Caminhos**
6. **Cobertura de Fluxo de Dados**

---

## 1. Cobertura de Instruções
A **cobertura de instruções** verifica se todas as linhas do código foram executadas pelo menos uma vez.

### Exemplo:
```portugol
funcao real calcular_media(real a, real b) {
    real soma, media
    soma = a + b
    media = soma / 2
    retorno media
}

// Testes
calcular_media(10, 20)  // Deve retornar 15
calcular_media(5, 5)    // Deve retornar 5
✅ Todas as instruções do código são executadas.2. Cobertura de DecisõesA cobertura de decisões verifica se todas as ramificações (se, senao, enquanto) são testadas.Exemplo:portugolCopiarEditarfuncao caractere verificar_par_ou_impar(inteiro n) {
    se (n % 2 == 0) entao
        retorno "Par"
    senao
        retorno "Ímpar"
}
Testes:verificar_par_ou_impar(4) → "Par" ✅ Testa o caminho do severificar_par_ou_impar(3) → "Ímpar" ✅ Testa o caminho do senao✅ Todas as decisões foram testadas.3. Cobertura de CondiçõesA cobertura de condições verifica se cada condição booleana dentro das decisões é testada tanto para Verdadeiro quanto para Falso.Exemplo:portugolCopiarEditarfuncao caractere pode_dirigir(inteiro idade, logico temCarteira) {
    se (idade >= 18 e temCarteira) entao
        retorno "Pode dirigir"
    senao
        retorno "Não pode dirigir"
}
Testes:pode_dirigir(20, verdadeiro) → "Pode dirigir" ✅ (idade >= 18 = V, temCarteira = V)pode_dirigir(20, falso) → "Não pode dirigir" ✅ (idade >= 18 = V, temCarteira = F)pode_dirigir(16, verdadeiro) → "Não pode dirigir" ✅ (idade >= 18 = F, temCarteira = V)pode_dirigir(16, falso) → "Não pode dirigir" ✅ (idade >= 18 = F, temCarteira = F)✅ Cada condição booleana foi testada isoladamente.4. Cobertura de Decisão-Condicional (MCC)A cobertura de decisão-condicional garante que todas as combinações de valores nas expressões condicionais sejam testadas.Exemplo:portugolCopiarEditarfuncao caractere aprovar_emprestimo(real renda, inteiro score_credito) {
    se (renda > 5000 e score_credito >= 700) entao
        retorno "Aprovado"
    senao
        retorno "Negado"
}
Testes cobrindo todas as combinações:aprovar_emprestimo(6000, 750) → "Aprovado" ✅ (V, V)aprovar_emprestimo(6000, 650) → "Negado" ✅ (V, F)aprovar_emprestimo(4000, 750) → "Negado" ✅ (F, V)aprovar_emprestimo(4000, 650) → "Negado" ✅ (F, F)✅ Todas as combinações de valores possíveis foram testadas.5. Cobertura de CaminhosA cobertura de caminhos testa todos os fluxos possíveis de execução.Exemplo:portugolCopiarEditarfuncao caractere classificar_numero(inteiro n) {
    se (n > 0) entao
        se (n % 2 == 0) entao
            retorno "Positivo e Par"
        senao
            retorno "Positivo e Ímpar"
    senao se (n < 0) entao
        retorno "Negativo"
    senao
        retorno "Zero"
}
Testes cobrindo todos os caminhos:classificar_numero(10) → "Positivo e Par"classificar_numero(7) → "Positivo e Ímpar"classificar_numero(-3) → "Negativo"classificar_numero(0) → "Zero"✅ Todos os fluxos do código foram testados.6. Cobertura de Fluxo de DadosA cobertura de fluxo de dados verifica a inicialização, uso e descarte das variáveis.Exemplo:portugolCopiarEditarfuncao real calcular_area(real base, real altura) {
    real area
    area = base * altura // Definição da variável (D)
    
    se (area > 0) entao  // Uso da variável (U)
        retorno area
    senao
        retorno -1 // Indica valores inválidos
}
Testes garantindo o uso correto da variável:calcular_area(5, 10) → 50 ✅ Uso correto da variável areacalcular_area(0, 10) → -1 ✅ Fluxo de erro tratado✅ Todos os estados possíveis da variável area foram testados.Resumo dos CritériosCritérioO que cobre?ExemploCobertura de InstruçõesTodas as instruções do códigocalcular_mediaCobertura de DecisõesTodos os ramos de se e senaoverificar_par_ou_imparCobertura de CondiçõesTodas as condições booleanas de forma isoladapode_dirigirCobertura de Decisão-CondicionalTodas as combinações de condiçõesaprovar_emprestimoCobertura de CaminhosTodos os fluxos possíveis de execuçãoclassificar_numeroCobertura de Fluxo de DadosUso correto de variáveiscalcular_areaConclusãoA escolha do critério de teste ideal depende do nível de cobertura desejado e do custo-benefício de sua implementação. Para aplicações críticas, recomenda-se combinar vários critérios para garantir a máxima confiabilidade do código.🔍 Agora é sua vez! Experimente modificar os exemplos e adicionar mais testes para explorar diferentes cenários. 🚀cssCopiarEditar
Este material pode ser utilizado diretamente em sala de aula ou como guia de estudo. Se precisar de ajustes ou exemplos adicionais, me avise! 😃
2/2Você disse:Reescreva todo o conteúdo a seguir em Markdown:

# Critérios para Seleção de Testes Caixa-Branca

Os **testes caixa-branca** são uma abordagem de teste de software que avalia a estrutura interna e a lógica do código. Esses testes garantem que cada parte do código seja verificada para identificar possíveis erros antes da liberação do software.

## Critérios para Seleção de Testes

Os critérios para testes caixa-branca incluem:

1. **Cobertura de Instruções**
2. **Cobertura de Decisões**
3. **Cobertura de Condições**
4. **Cobertura de Decisão-Condicional (MCC – Multiple Condition Coverage)**
5. **Cobertura de Caminhos**
6. **Cobertura de Fluxo de Dados**

---

## 1. Cobertura de Instruções
A **cobertura de instruções** verifica se todas as linhas do código foram executadas pelo menos uma vez.

### Exemplo:
portugol
funcao real calcular_media(real a, real b) {
    real soma, media
    soma = a + b
    media = soma / 2
    retorno media
}

// Testes
calcular_media(10, 20)  // Deve retornar 15
calcular_media(5, 5)    // Deve retornar 5
✅ Todas as instruções do código são executadas.

2. Cobertura de Decisões
A cobertura de decisões verifica se todas as ramificações (se, senao, enquanto) são testadas.

Exemplo:
portugol
Copiar
Editar
funcao caractere verificar_par_ou_impar(inteiro n) {
    se (n % 2 == 0) entao
        retorno "Par"
    senao
        retorno "Ímpar"
}
Testes:
verificar_par_ou_impar(4) → "Par" ✅ Testa o caminho do se
verificar_par_ou_impar(3) → "Ímpar" ✅ Testa o caminho do senao
✅ Todas as decisões foram testadas.

3. Cobertura de Condições
A cobertura de condições verifica se cada condição booleana dentro das decisões é testada tanto para Verdadeiro quanto para Falso.

Exemplo:
portugol
Copiar
Editar
funcao caractere pode_dirigir(inteiro idade, logico temCarteira) {
    se (idade >= 18 e temCarteira) entao
        retorno "Pode dirigir"
    senao
        retorno "Não pode dirigir"
}
Testes:
pode_dirigir(20, verdadeiro) → "Pode dirigir" ✅ (idade >= 18 = V, temCarteira = V)
pode_dirigir(20, falso) → "Não pode dirigir" ✅ (idade >= 18 = V, temCarteira = F)
pode_dirigir(16, verdadeiro) → "Não pode dirigir" ✅ (idade >= 18 = F, temCarteira = V)
pode_dirigir(16, falso) → "Não pode dirigir" ✅ (idade >= 18 = F, temCarteira = F)
✅ Cada condição booleana foi testada isoladamente.

4. Cobertura de Decisão-Condicional (MCC)
A cobertura de decisão-condicional garante que todas as combinações de valores nas expressões condicionais sejam testadas.

Exemplo:
portugol
Copiar
Editar
funcao caractere aprovar_emprestimo(real renda, inteiro score_credito) {
    se (renda > 5000 e score_credito >= 700) entao
        retorno "Aprovado"
    senao
        retorno "Negado"
}
Testes cobrindo todas as combinações:
aprovar_emprestimo(6000, 750) → "Aprovado" ✅ (V, V)
aprovar_emprestimo(6000, 650) → "Negado" ✅ (V, F)
aprovar_emprestimo(4000, 750) → "Negado" ✅ (F, V)
aprovar_emprestimo(4000, 650) → "Negado" ✅ (F, F)
✅ Todas as combinações de valores possíveis foram testadas.

5. Cobertura de Caminhos
A cobertura de caminhos testa todos os fluxos possíveis de execução.

Exemplo:
portugol
Copiar
Editar
funcao caractere classificar_numero(inteiro n) {
    se (n > 0) entao
        se (n % 2 == 0) entao
            retorno "Positivo e Par"
        senao
            retorno "Positivo e Ímpar"
    senao se (n < 0) entao
        retorno "Negativo"
    senao
        retorno "Zero"
}
Testes cobrindo todos os caminhos:
classificar_numero(10) → "Positivo e Par"
classificar_numero(7) → "Positivo e Ímpar"
classificar_numero(-3) → "Negativo"
classificar_numero(0) → "Zero"
✅ Todos os fluxos do código foram testados.

6. Cobertura de Fluxo de Dados
A cobertura de fluxo de dados verifica a inicialização, uso e descarte das variáveis.

Exemplo:
portugol
Copiar
Editar
funcao real calcular_area(real base, real altura) {
    real area
    area = base * altura // Definição da variável (D)
    
    se (area > 0) entao  // Uso da variável (U)
        retorno area
    senao
        retorno -1 // Indica valores inválidos
}
Testes garantindo o uso correto da variável:
calcular_area(5, 10) → 50 ✅ Uso correto da variável area
calcular_area(0, 10) → -1 ✅ Fluxo de erro tratado
✅ Todos os estados possíveis da variável area foram testados.

Resumo dos Critérios
Critério	O que cobre?	Exemplo
Cobertura de Instruções	Todas as instruções do código	calcular_media
Cobertura de Decisões	Todos os ramos de se e senao	verificar_par_ou_impar
Cobertura de Condições	Todas as condições booleanas de forma isolada	pode_dirigir
Cobertura de Decisão-Condicional	Todas as combinações de condições	aprovar_emprestimo
Cobertura de Caminhos	Todos os fluxos possíveis de execução	classificar_numero
Cobertura de Fluxo de Dados	Uso correto de variáveis	calcular_area
Conclusão
A escolha do critério de teste ideal depende do nível de cobertura desejado e do custo-benefício de sua implementação. Para aplicações críticas, recomenda-se combinar vários critérios para garantir a máxima confiabilidade do código.

🔍 Agora é sua vez! Experimente modificar os exemplos e adicionar mais testes para explorar diferentes cenários. 🚀

css
Copiar
Editar

Este material pode ser utilizado diretamente em sala de aula ou como guia de estudo. Se precisar de ajustes ou exemplos adicionais, me avise! 😃O ChatGPT disse:Aqui está o conteúdo reescrito corretamente em Markdown:markdownCopiarEditar# Critérios para Seleção de Testes Caixa-Branca

Os **testes caixa-branca** são uma abordagem de teste de software que avalia a estrutura interna e a lógica do código. Esses testes garantem que cada parte do código seja verificada para identificar possíveis erros antes da liberação do software.

## Critérios para Seleção de Testes

Os critérios para testes caixa-branca incluem:

1. **Cobertura de Instruções**
2. **Cobertura de Decisões**
3. **Cobertura de Condições**
4. **Cobertura de Decisão-Condicional (MCC – Multiple Condition Coverage)**
5. **Cobertura de Caminhos**
6. **Cobertura de Fluxo de Dados**

---

## 1. Cobertura de Instruções
A **cobertura de instruções** verifica se todas as linhas do código foram executadas pelo menos uma vez.

### Exemplo:
```portugol
funcao real calcular_media(real a, real b) {
    real soma, media
    soma = a + b
    media = soma / 2
    retorno media
}

// Testes
calcular_media(10, 20)  // Deve retornar 15
calcular_media(5, 5)    // Deve retornar 5
✅ Todas as instruções do código são executadas.2. Cobertura de DecisõesA cobertura de decisões verifica se todas as ramificações (se, senao, enquanto) são testadas.Exemplo:portugolCopiarEditarfuncao caractere verificar_par_ou_impar(inteiro n) {
    se (n % 2 == 0) entao
        retorno "Par"
    senao
        retorno "Ímpar"
}
Testes:verificar_par_ou_impar(4) → "Par" ✅ Testa o caminho do severificar_par_ou_impar(3) → "Ímpar" ✅ Testa o caminho do senao✅ Todas as decisões foram testadas.3. Cobertura de CondiçõesA cobertura de condições verifica se cada condição booleana dentro das decisões é testada tanto para Verdadeiro quanto para Falso.Exemplo:portugolCopiarEditarfuncao caractere pode_dirigir(inteiro idade, logico temCarteira) {
    se (idade >= 18 e temCarteira) entao
        retorno "Pode dirigir"
    senao
        retorno "Não pode dirigir"
}
Testes:pode_dirigir(20, verdadeiro) → "Pode dirigir" ✅ (idade >= 18 = V, temCarteira = V)pode_dirigir(20, falso) → "Não pode dirigir" ✅ (idade >= 18 = V, temCarteira = F)`pode_dirThe operation was abortedVocê disse:Gere um arquivo .md com o conteúdo gerado.O ChatGPT disse:​Você disse:Gere um arquivo .md com o conteúdo gerado.O ChatGPT disse:Criterios Teste Caixa BrancaResponder no chatO arquivo Markdown foi gerado com sucesso! Se precisar de ajustes ou quiser adicionar mais conteúdo, é só me avisar. 🚀InvestigarO ChatGPT pode cometer erros. Considere verificar informações importantes.?Criterios Teste Caixa BrancaCritérios para Seleção de Testes Caixa-BrancaOs testes caixa-branca são uma abordagem de teste de software que avalia a estrutura interna e a lógica do código. Esses testes garantem que cada parte do código seja verificada para identificar possíveis erros antes da liberação do software.Critérios para Seleção de TestesOs critérios para testes caixa-branca incluem:Cobertura de InstruçõesCobertura de DecisõesCobertura de CondiçõesCobertura de Decisão-Condicional (MCC – Multiple Condition Coverage)Cobertura de CaminhosCobertura de Fluxo de Dados1. Cobertura de InstruçõesA cobertura de instruções verifica se todas as linhas do código foram executadas pelo menos uma vez.Exemplo:funcao real calcular_media(real a, real b) {    real soma, media    soma = a + b    media = soma / 2    retorno media}// Testescalcular_media(10, 20)  // Deve retornar 15calcular_media(5, 5)    // Deve retornar 5✅ Todas as instruções do código são executadas.2. Cobertura de DecisõesA cobertura de decisões verifica se todas as ramificações (se, senao, enquanto) são testadas.Exemplo:funcao caractere verificar_par_ou_impar(inteiro n) {    se (n % 2 == 0) entao        retorno "Par"    senao        retorno "Ímpar"}Testes:verificar_par_ou_impar(4) → "Par" ✅ Testa o caminho do severificar_par_ou_impar(3) → "Ímpar" ✅ Testa o caminho do senao✅ Todas as decisões foram testadas.3. Cobertura de CondiçõesA cobertura de condições verifica se cada condição booleana dentro das decisões é testada tanto para Verdadeiro quanto para Falso.Exemplo:funcao caractere pode_dirigir(inteiro idade, logico temCarteira) {    se (idade >= 18 e temCarteira) entao        retorno "Pode dirigir"    senao        retorno "Não pode dirigir"}Testes:pode_dirigir(20, verdadeiro) → "Pode dirigir" ✅ (idade >= 18 = V, temCarteira = V)pode_dirigir(20, falso) → "Não pode dirigir" ✅ (idade >= 18 = V, temCarteira = F)pode_dirigir(16, verdadeiro) → "Não pode dirigir" ✅ (idade >= 18 = F, temCarteira = V)pode_dirigir(16, falso) → "Não pode dirigir" ✅ (idade >= 18 = F, temCarteira = F)✅ Cada condição booleana foi testada isoladamente.Resumo dos CritériosCritérioO que cobre?ExemploCobertura de InstruçõesTodas as instruções do códigocalcular_mediaCobertura de DecisõesTodos os ramos de se e senaoverificar_par_ou_imparCobertura de CondiçõesTodas as condições booleanas de forma isoladapode_dirigirConclusãoA escolha do critério de teste ideal depende do nível de cobertura desejado e do custo-benefício de sua implementação. Para aplicações críticas, recomenda-se combinar vários critérios para garantir a máxima confiabilidade do código.🔍 Agora é sua vez! Experimente modificar os exemplos e adicionar mais testes para explorar diferentes cenários. 🚀Escreva algo…Perguntar ao ChatGPT