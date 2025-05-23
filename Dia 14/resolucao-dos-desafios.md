# Dia 14 - Super Desafio de Estrutura de Dados

## DESAFIO: Controlar filas de vários caixas de supermercado

**Descrição**: Vamos retomar o desafio de controle de filas de supermercado, mas agora com a diferença de que teremos várias filas ao mesmo tempo, uma para cada caixa.

O objetivo é simular um supermercado com diversos caixas, cada um com sua fila de clientes.

- Um cliente pode ser adicionado a uma das filas (caixas).
- O cliente é atendido e removido da fila correspondente.

```kt
fun main() {
    entrarNaFila("caixa1", "João")
    entrarNaFila("caixa2", "Maria")
    entrarNaFila("caixa3", "Pedro")
    entrarNaFila("caixa1", "Ana")
    entrarNaFila("caixa2", "Carlos")

    println("=================================")
    mostrarFilas()
    println("=================================")

    atenderCliente("caixa1")
    atenderCliente("caixa2")
    atenderCliente("caixa3")

    println("=================================")
    mostrarFilas()
    println("=================================")

    atenderCliente("caixa3")

}

// Variável Global
val filasCaixas: MutableMap<String, MutableList<String>> = mutableMapOf(
    "caixa1" to mutableListOf(),
    "caixa2" to mutableListOf(),
    "caixa3" to mutableListOf(),
    "caixa4" to mutableListOf(),
    "caixa5" to mutableListOf()
)

fun entrarNaFila(caixa: String, nome: String) {
    val fila = filasCaixas[caixa]
    if (fila != null) {
        fila.add(nome)
        println("$nome entrou na fila do $caixa.")
    } else {
        println("O $caixa não existe.")
    }
}

fun atenderCliente(caixa: String) {
    val fila = filasCaixas[caixa]

    if (fila != null) {
        if (fila.isNotEmpty()) {
            val clienteAtendido = fila.removeAt(0)
            println("$clienteAtendido foi atendido no $caixa.")
        } else {
            println("A fila do $caixa está vazia.")
        }
    } else {
        println("O $caixa não existe.")
    }
}

fun mostrarFilas() {
    println("Estado das filas:")
    for ((caixa, fila) in filasCaixas) {
        if (fila.isNotEmpty()) {
            println("$caixa: ${fila.joinToString(", ")}")
        } else {
            println("$caixa: A fila está vazia.")
        }
    }
}
```

!["Imagem que mostra a execução do código com funções que simulam o gerenciamento de várias filas em caixas de supermercado"](../img/caixa-filas.JPG)