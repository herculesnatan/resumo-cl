

# **Circuitos Sequenciais – Resumo Completo**  

## **1. Introdução aos Circuitos Sequenciais**  
Diferente dos **circuitos combinacionais**, que dependem apenas das entradas atuais, os **circuitos sequenciais** dependem **das entradas e do estado anterior do sistema**. Isso significa que eles possuem **memória** e podem armazenar informações.  

Os circuitos sequenciais são amplamente usados em contadores, registradores, máquinas de estado finito e sistemas digitais em geral.  

---

## **2. Flip-Flops: Elementos Básicos da Memória**  
Os **flip-flops** são os principais blocos de memória dos circuitos sequenciais. Eles armazenam **um bit** e podem ser síncronos (controlados por um clock) ou assíncronos.  

### **2.1 Flip-Flop SR (Set-Reset)**  
O flip-flop **SR (Set-Reset)** pode armazenar um bit e funciona com as seguintes regras:  

| **S** | **R** | **Q⁺ (Próximo Estado)** | **Situação**            |
|-------|-------|--------------------------|-------------------------|
| 0     | 0     | Q (mantém)               | Estado de memória       |
| 0     | 1     | 0                        | Reset (zera)            |
| 1     | 0     | 1                        | Set (ativa)             |
| 1     | 1     | Indeterminado            | Estado proibido         |

- **Problema:** O estado \( S = 1 \) e \( R = 1 \) é inválido.  

---

### **2.2 Flip-Flop D (Data ou Delay)**  
Evita estados proibidos do SR ao ter apenas **uma entrada (D)**:  

| **D** | **Q⁺ (Próximo Estado)** |
|-------|--------------------------|
| 0     | 0                        |
| 1     | 1                        |

- **Aplicação:** Usado em **registradores e armazenamento de dados**.  

---

### **2.3 Flip-Flop JK**  
Resolve o problema do estado proibido do SR:  

| **J** | **K** | **Q⁺ (Próximo Estado)** |
|-------|-------|--------------------------|
| 0     | 0     | Q (mantém)               |
| 0     | 1     | 0 (reset)                |
| 1     | 0     | 1 (set)                  |
| 1     | 1     | \( \overline{Q} \) (toggle - inverte) |

- **Aplicação:** Usado em **contadores síncronos**.  

---

### **2.4 Flip-Flop T (Toggle)**  
Funciona como um divisor de frequência, alternando o estado a cada pulso de clock:  

| **T** | **Q⁺ (Próximo Estado)** |
|-------|--------------------------|
| 0     | Q (mantém)               |
| 1     | \( \overline{Q} \) (inverte) |

- **Aplicação:** Usado em **contadores binários**.  

---

## **3. Máquinas de Estado Finito (FSM – Finite State Machines)**  
Os circuitos sequenciais podem ser modelados como **FSMs (Finite State Machines)**, divididas em:  

### **3.1 Máquina de Moore**  
A saída depende **apenas do estado atual**.  

- **Exemplo:** Máquina de uma catraca de metrô (abre apenas após o pagamento).  

### **3.2 Máquina de Mealy**  
A saída depende **do estado atual e das entradas**.  

- **Exemplo:** Um detector de sequência que emite um sinal assim que encontra um padrão.  

---

## **4. Contadores e Registradores**  

### **4.1 Contadores**  
Os contadores são circuitos sequenciais que geram sequências de números binários.  

#### **Contadores Assíncronos (Ripple Counter)**  
Cada flip-flop é acionado pelo **estado do anterior**, resultando em um atraso na propagação dos sinais.  

#### **Contadores Síncronos**  
Todos os flip-flops mudam de estado **simultaneamente**, eliminando o problema do atraso.  

| **Estado Atual** | **Estado Futuro** |
|------------------|-------------------|
| 000              | 001               |
| 001              | 010               |
| 010              | 011               |
| 011              | 100               |

- **Aplicação:** Relógios digitais, timers.  

---

### **4.2 Registradores de Deslocamento**  
Registradores que armazenam e movem bits, podendo operar em diferentes modos:  

| **Tipo** | **Descrição**               |
|----------|-----------------------------|
| SISO     | Serial-in, Serial-out       |
| SIPO     | Serial-in, Parallel-out     |
| PISO     | Parallel-in, Serial-out     |
| PIPO     | Parallel-in, Parallel-out   |

- **Aplicação:** Comunicação de dados, buffers, criptografia.  

---

## **5. Aplicações Práticas**  
- **Controladores de elevadores** (FSM)  
- **Semáforos inteligentes**  
- **Memórias e armazenamento de dados**  
- **Sistemas embarcados**  
- **Máquinas industriais automatizadas**  

---


## **Passo a Passo para Montar um Circuito Sequencial no Papel**


### **1. Escolha os Componentes**
Os principais componentes de um circuito sequencial são:
- **Flip-flops** (SR, D, JK, T) para armazenar estados.
- **Portas lógicas** (AND, OR, NOT, etc.) para controlar as entradas e saídas.
- **Clock** (sinal de temporização) para sincronizar as transições de estado.

Escolha os componentes com base no objetivo do circuito.

---

### **2. Desenhe o Diagrama de Estados (FSM)**
Se o circuito for uma máquina de estados finitos, desenhe o **diagrama de estados**. Ele mostra:
- **Estados** (círculos) representando as condições do sistema.
- **Transições** (setas) indicando como o sistema muda de um estado para outro.
- **Entradas e saídas** associadas a cada transição.

Exemplo simples de um semáforo:
- Estados: Vermelho, Amarelo, Verde.
- Transições: Mudanças de cor com base no tempo ou sensores.

---

### **3. Projete a Tabela de Estados**
Crie uma tabela que mostre:
- **Estado atual**.
- **Entradas**.
- **Próximo estado**.
- **Saídas**.

Exemplo para um flip-flop JK:

| **Estado Atual (Q)** | **J** | **K** | **Próximo Estado (Q⁺)** | **Saída** |
|----------------------|-------|-------|--------------------------|-----------|
| 0                    | 0     | 0     | 0                        | 0         |
| 0                    | 0     | 1     | 0                        | 0         |
| 0                    | 1     | 0     | 1                        | 1         |
| 0                    | 1     | 1     | 1                        | 1         |
| 1                    | 0     | 0     | 1                        | 1         |
| 1                    | 0     | 1     | 0                        | 0         |
| 1                    | 1     | 0     | 1                        | 1         |
| 1                    | 1     | 1     | 0                        | 0         |

---

### **4. Desenhe o Circuito no Papel**
Agora, siga estas etapas para desenhar o circuito:

#### **a. Desenhe os Flip-Flops**
- Represente os flip-flops como blocos retangulares.
- Identifique as entradas (D, J, K, T, etc.) e saídas (Q e \( \overline{Q} \)).

#### **b. Conecte as Entradas e Saídas**
- Use linhas para conectar as entradas dos flip-flops às portas lógicas ou ao clock.
- Conecte as saídas dos flip-flops às entradas de outros flip-flops ou às saídas do circuito.

#### **c. Adicione o Clock**
- Desenhe o sinal de clock e conecte-o aos flip-flops que precisam de sincronização.

#### **d. Inclua Portas Lógicas**
- Use portas lógicas para implementar a lógica de controle do circuito.
- Por exemplo, se você está projetando um contador, use portas AND e OR para controlar quando os flip-flops devem mudar de estado.

#### **e. Identifique as Saídas**
- Desenhe as saídas do circuito e conecte-as aos flip-flops ou portas lógicas.

---

### **5. Exemplo Prático: Contador Binário de 2 Bits**
Vamos desenhar um contador binário de 2 bits usando flip-flops JK.

#### **a. Tabela de Estados**
| **Estado Atual (Q1 Q0)** | **Próximo Estado (Q1⁺ Q0⁺)** |
|--------------------------|------------------------------|
| 00                       | 01                           |
| 01                       | 10                           |
| 10                       | 11                           |
| 11                       | 00                           |

#### **b. Diagrama do Circuito**
1. Desenhe dois flip-flops JK (um para cada bit: Q1 e Q0).
2. Conecte o clock aos dois flip-flops.
3. Use portas lógicas para implementar a lógica de contagem:
   - Para Q0: \( J = 1 \), \( K = 1 \) (toggle a cada pulso de clock).
   - Para Q1: \( J = Q0 \), \( K = Q0 \) (muda apenas quando Q0 é 1).
4. Conecte as saídas Q1 e Q0 às saídas do circuito.

---

### **Dicas para Desenhar no Papel**
- Use **símbolos padrão** para flip-flops e portas lógicas.
- Mantenha o layout organizado, com entradas à esquerda e saídas à direita.
- Use cores diferentes para diferenciar sinais de clock, entradas e saídas.
- Anote as equações lógicas ao lado do circuito, se necessário.

---

