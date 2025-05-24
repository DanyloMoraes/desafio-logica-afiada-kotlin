# Dia 20 - Busca é a Mágica da Programação

## DESAFIO 01: Busca Binária com Recursividade

**Descrição**: Implemente a `busca binária` de um array de números, porém utilizando `recursividade`, assim como mostramos na busca linear.

Teste também com um array com nomes para ver como funcionará.

!["Imagem que mostra uma função de busca linear"](../img/busca-linear.jpg)

```kt
fun main() {
    val numeros = listOf(5, 10, 15, 20, 25, 30, 35, 40)
    println("Saída: ${buscaBinariaRecursiva(numeros, 25)}") // Saída: 4
    println("Saída: ${buscaBinariaRecursiva(numeros, 13)}") // Saída: -1

    println("---------")

    val nomes = listOf("Ana", "Bruno", "Carlos", "Daniel", "Eduarda", "Fernanda", "Gabriel")
    println("Saída: ${buscaBinariaRecursiva(nomes, "Daniel")}") // Saída: 3
    println("Saída: ${buscaBinariaRecursiva(nomes, "João")}")   // Saída: -1
}

fun <T: Comparable<T>> buscaBinariaRecursiva(
    lista: List<T>,
    valor: T,
    inicio: Int = 0,
    fim: Int = lista.size - 1
): Int {
    if (inicio > fim) return -1

    val meio = (inicio + fim) / 2

    return when {
        lista[meio] == valor -> meio
        valor < lista[meio] -> buscaBinariaRecursiva(lista, valor, inicio, meio - 1)
        else -> buscaBinariaRecursiva(lista, valor, meio + 1, fim)
    }
}
```

!["Imagem que mostra a execução da função de busca binaria recursiva e o seu retorno"](../img/busca-recursiva.JPG)

## DESAFIO 02: Busca Linear Recursiva com Múltiplos Resultados

Realize uma `busca linear`, utilizando `recursividade`, porém ao invés de retornar o índice do primeiro que foi encontrado apenas, quero que você retorne todos os índices que contém uma determinada palavra.

```kt
data class Mensagem(
    val nome: String,
    val mensagem: String,
    val telefone: String,
    val data: String
)

fun buscarMensagensPorPalavra(
    lista: List<Mensagem>,
    palavra: String,
    indice: Int = 0,
    encontrados: MutableList<Int> = mutableListOf()
): List<Int> {
    if (indice >= lista.size) return encontrados

    val msg = lista[indice].mensagem.lowercase()
    val termo = palavra.lowercase()

    if (msg.contains(termo)) {
        encontrados.add(indice)
    }

    return buscarMensagensPorPalavra(lista, palavra, indice + 1, encontrados)
}

fun main() {
    val mensagens = listOf(
        Mensagem("Ana", "Oi, você viu o relatório que mandei ontem?", "11999999999", "2025-04-01"),
        Mensagem("Bruno", "Vamos almoçar juntos amanhã?", "11988888888", "2025-04-09"),
        Mensagem("Carlos", "Segue o relatório atualizado.", "11977777777", "2025-04-15"),
        Mensagem("Daniela", "Relatório final enviado. Verifique!", "11966666666", "2025-04-18"),
        Mensagem("Vanessa", "Está chegando ao fim do Desafio do Código Fonte TV", "12977445588", "2025-04-21")
    )

    val resultado = buscarMensagensPorPalavra(mensagens, "relatório")

    // Exibe em qual mensagens foram encontradas a palavra específica
    for (index in resultado) {
        val (nome, _, telefone, data) = mensagens[index]
        println("Encontrado em $nome ($telefone) em $data")
    }
}
```

!["Imagem que mostra a execução de uma função recursiva que busca por uma determinada palavra"](../img/busca-recursiva-por-palavra.JPG)