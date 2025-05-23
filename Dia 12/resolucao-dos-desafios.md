# Dia 12 - Filas do Mundo Real

## DESAFIO: Fila de atendimento em um Drive Through

**Descrição**: Criar uma fila de atendimento de clientes em uma cafeteria Drive Through. Todo atendimento é realizado a partir de carros que vão entrando no estacionamento da cafeteria e recebendo os pedidos a partir de um totem eletrônico.

```kt
fun main() {
    entrarNaFila("ABC1234", "Café")
    entrarNaFila("XYZ4321", "Chá")
    entrarNaFila("DEF6543", "Sanduíche")

    println("===================================")

    atenderCarro()

    statusDaFila()

    atenderCarro()
    atenderCarro()

    statusDaFila()

    atenderCarro()
}

// Fila do Drive Thru
var filaDriveThru: MutableList<Pair<String, String>> = mutableListOf()

fun entrarNaFila(placaDoCarro: String, pedido: String) {
    filaDriveThru.add(Pair(placaDoCarro, pedido))
    println("O carro $placaDoCarro entrou na fila com o pedido: $pedido")
}

fun atenderCarro() {
    if (filaDriveThru.isEmpty()) {
        println("Não há carros na fila.")
    } else {
        val carroAtendido = filaDriveThru.removeAt(0)
        println("Carro ${carroAtendido.first} com o pedido: ${carroAtendido.second}")
    }
}

// Verifica quantos carros ainda existem na fila
fun statusDaFila() {
    println("Total de carros na fila: ${filaDriveThru.size}")

    if (filaDriveThru.isNotEmpty()) {
        val placas = filaDriveThru.map { it.first }.joinToString(", ")
        println("Fila atual: $placas")
    }
}
```

!["Imagem que mostra a execução do código com funções que simulam o atendimento de uma fila em um Drive Through"](../img/carros-fila.JPG)