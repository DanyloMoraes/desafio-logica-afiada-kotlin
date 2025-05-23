# Dia 13 - Desafios Desafiadores com Deques

## DESAFIO: Controle de Tarefas Dinâmicas com Prioridades

**Descrição**: Crie um controle que regencia tarefas com prioridade. O objetivo é simular um ambiente onde tarefas urgentes podem surgir a qualquer momento, exigindo reorganização rápida e eficiente da fila de tarefas.

    Objetivos do desafio:

    - Implementar um Deque para Tarefas
    - Manipulação de Prioridades
    - Testar com Cenários Realistas

```kt
fun main() {
    inserirFim("Comprar café")         // baixa prioridade
    inserirInicio("Responder e-mails") // alta prioridade
    inserirFim("Agendar reunião")      // baixa prioridade

    println("Tarefas atuais: ${obterTarefas()}")

    aumentarPrioridade("Comprar café")
    diminuirPrioridade("Responder e-mails")

    println("Tarefas após ajustes de prioridade: ${obterTarefas()}")

    removerInicio() // remove "Comprar café
    println("Tarefas após remoção: ${obterTarefas()}")
}

val tarefas: MutableList<String> = mutableListOf()

// Tarefa com alta prioridade
fun inserirInicio(tarefa: String) {
    tarefas.add(0, tarefa)
    println("Tarefa '$tarefa' adicionada com alta prioridade.")
}

// Tarefa com baixa prioridade
fun inserirFim(tarefa: String) {
    tarefas.add(tarefa)
    println("Tarefa '$tarefa' adicionada com baixa prioridade.")
}

// Remover tarefa com alta prioridade
fun removerInicio() {
    if (!estaVazio()) {
        val tarefaRemovida = tarefas.removeAt(0)
        println("Tarefa '$tarefaRemovida' com alta prioridade foi removida.")
    } else {
        println("Não há tarefas para remover.")
    }
}

// Remover tarefa com baixa prioridade
fun removerFim() {
    if (!estaVazio()) {
        val tarefaRemovida = tarefas.removeAt(tarefas.size - 1)
        println("Tarefa '$tarefaRemovida' com baixa prioridade foi removida.")
    } else {
        println("Não há tarefas para remover.")
    }
}

// Verifica se a lista de tarefas está vazia
fun estaVazio(): Boolean = tarefas.isEmpty()

// Obtem uma cópia da lista de tarefas
fun obterTarefas(): List<String> = tarefas.toList()

fun aumentarPrioridade(tarefa: String) {
    val index = tarefas.indexOf(tarefa)

    if (index > 0) {
        tarefas[index] = tarefas[index - 1].also {
            tarefas[index - 1] = tarefas[index]
        }
        println("Prioridade da tarefa '$tarefa' foi aumentada.")
    } else {
        println("A tarefa já está com a máxima prioridade ou não existe.")
    }
}

fun diminuirPrioridade(tarefa: String) {
    val index = tarefas.indexOf(tarefa)

    if (index != -1 && index < tarefas.size - 1) {
        tarefas[index] = tarefas[index + 1].also {
            tarefas[index + 1] = tarefas[index]
        }
        println("A tarefa já está com a mínima prioridade ou não existe.")
    }
}
```

!["Imagem que mostra a execução do código com funções que simulam o aumento e a diminuição de prioridade de determinadas tarefas organizadas em um array"](../img/deques.JPG)