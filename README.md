

🧠 Simulador de Escalonamento de Processos (SRT e Round Robin)

📘 Descrição do Projeto

Este programa em linguagem C simula dois dos principais algoritmos de escalonamento de processos utilizados em sistemas operacionais:

SRT (Shortest Remaining Time) — Executa sempre o processo com o menor tempo restante de CPU, podendo haver preempção quando chega um processo menor.

Round Robin (RR) — Distribui o tempo da CPU de forma justa e cíclica, utilizando um quantum (tempo máximo de execução) para cada processo.


O objetivo é visualizar, de maneira didática, como cada algoritmo organiza os processos ao longo do tempo, exibindo uma timeline detalhada do estado da CPU e da fila de prontos.


---

⚙️ Como Compilar

No terminal (Linux, macOS) ou no Prompt de Comando (Windows), digite:

gcc simulador.c -o simulador

Para executar o programa:

./simulador


---

🧩 Estruturas Utilizadas

O programa usa um vetor estático de até 15 processos, definidos pela seguinte estrutura:

typedef struct {
    char nome[16];
    int chegada;
    int cpu_total;
    int restante;
    int finalizado;
} Processo;

Cada campo representa:

nome → Nome do processo (ex: "P1", "TarefaA")

chegada → Tempo em que o processo chega ao sistema

cpu_total → Tempo total necessário de CPU

restante → Tempo restante até a conclusão

finalizado → Flag (0 = em execução / 1 = concluído)



---

🧮 Algoritmos Implementados

🔹 1. SRT (Shortest Remaining Time)

Escolhe o processo com menor tempo restante.

Se um processo novo chega com tempo menor, ocorre preempção imediata.

A contagem de tempo é feita unidade por unidade (1 unidade = 1 ciclo de CPU).


Características:

Algoritmo preemptivo.

Minimiza o tempo médio de espera.

Pode causar injustiça com processos longos.



---

🔹 2. Round Robin (RR)

Cada processo recebe um quantum, que é o tempo máximo de execução por ciclo.

Quando o tempo do quantum termina e o processo ainda não acabou, ele volta para o final da fila.

Ideal para sistemas multitarefa e ambientes interativos.


Características:

Algoritmo justo (todos os processos têm oportunidade de rodar).

O desempenho depende do tamanho do quantum.

Implementação simples e eficiente.



---

🧾 Exemplo de Execução

🔸 Entrada:

1              ← algoritmo (1 = SRT, 2 = RR)
3              ← número de processos
P1
0
5
P2
2
3
P3
4
2

🔸 Saída esperada (SRT):

===== INICIO DA SIMULACAO SRT =====

Tempo 0 | Na fila: P1(restante:5) | Executando: P1
Tempo 1 | Na fila: P1(restante:4) | Executando: P1
Tempo 2 | Na fila: P1(restante:3) P2(restante:3) | Executando: P2
Tempo 3 | Na fila: P1(restante:3) | Executando: P2
Tempo 4 | Na fila: P1(restante:3) P3(restante:2) | Executando: P3
Tempo 5 | Na fila: P1(restante:3) | Executando: P3
Tempo 6 | Na fila:  | Executando: P1
Tempo 7 | Na fila:  | Executando: P1
Tempo 8 | Na fila:  | Executando: P1

===== FIM DA SIMULACAO SRT =====
Tempo total de execução: 9 unidades.


---

📊 Saída Explicada

Cada linha da simulação mostra o tempo atual, os processos prontos e o processo em execução:

Tempo X | Na fila: [processos prontos com tempo restante] | Executando: [processo atual]

Exemplo:

Tempo 2 | Na fila: P1(restante:3) | Executando: P2

➡ Significa que no tempo 2, o processo P2 está em execução, enquanto P1 aguarda na fila com 3 unidades restantes.


---

🧠 Diferenciais do Código

✅ Estrutura modular e organizada (funções separadas por responsabilidade)
✅ Validações completas — impede entradas inválidas e repete perguntas até serem válidas
✅ Saída visual e explicativa (excelente para apresentações acadêmicas)
✅ Não reseta variáveis — simulações independentes e coerentes
✅ Código compatível com qualquer compilador C
✅ Pronto para expansão (ex: FCFS, SJF, Prioridades, etc.)


---

👨‍💻 Autor(a)

Drika Silva
💡 Simulador acadêmico desenvolvido para fins educacionais.
