

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
