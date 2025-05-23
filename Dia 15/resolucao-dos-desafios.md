# Dia 15 - Lista Encadeada com Objeto Literal

## DESAFIO: Lista encadeada de um trem

**Descrição**: Terminar de implementar as outras funções que estão faltando para trabalhar com lista encadeada como:

- `insertLast` que inclui um nó no final da lista;
- `insertAt` que inclui um nó em uma determinada posição;
- `deleteAt` que exlui um nó em uma determinada posição;
- `searchAt` que encontra um nó de acordo com a posição;
- `traversal` que percorre todos os nós;
- `indexOf` que retorna a posição de acordo com o elemento do nó.

```kt
// Nó da lista encadeada
data class No(var data: String, var next: No? = null)

// Classe Lista Encadeada
class ListaEncadeada {
    private var head: No? = null

    // Inserir no início
    fun insertFirst(elemento: String): String {
        val novoNo = No(elemento)
        if (head == null) {
            head = novoNo
        } else {
            novoNo.next = head
            head = novoNo
        }
        return elemento
    }

    // Inserir no fim
    fun insertLast(elemento: String): String {
        val novoNo = No(elemento)
        if (head == null) {
            head = novoNo
        } else {
            var atual = head
            while (atual?.next != null) {
                atual = atual.next
            }
            atual?.next = novoNo
        }
        return elemento
    }

    // Inserir em uma posição específica
    fun insertAt(elemento: String, posicao: Int): String? {
        val novoNo = No(elemento)

        if (posicao == 0) {
            novoNo.next = head
            head = novoNo
            return elemento
        }

        var atual = head
        var anterior: No? = null
        var contador = 0

        while (contador < posicao && atual != null) {
            anterior = atual
            atual = atual.next
            contador++
        }

        return if (contador == posicao) {
            anterior?.next = novoNo
            novoNo.next = atual
            elemento
        } else {
            println("Posição inválida.")
            null
        }
    }

    // Deleta elemento em uma posição específica
    fun deleteAt(posicao: Int): String? {
        if (head == null) {
            println("A lista está vazia.")
            return null
        }

        if (posicao == 0) {
            val removido = head?.data
            head = head?.next
            return removido
        }

        var atual = head
        var anterior: No? = null
        var contador = 0

        while (contador < posicao && atual != null) {
            anterior = atual
            atual = atual.next
            contador++
        }

        return if (atual != null) {
            anterior?.next = atual.next
            atual.data
        } else {
            println("Posição inválida.")
            null
        }
    }

    // Busca um elemento em uma posição
    fun searchAt(posicao: Int): String? {
        var atual = head
        var contador = 0

        while (contador < posicao && atual != null) {
            atual = atual.next
            contador++
        }

        return if (atual != null) {
            atual.data
        } else {
            println("Posição inválida.")
            null
        }
    }

    // Percorre todos os nós
    fun traversal(): List<String> {
        val resultado = mutableListOf<String>()
        var atual = head

        while (atual != null) {
            resultado.add(atual.data)
            atual = atual.next
        }

        return resultado
    }

    // Retorna a posição de um elemento
    fun indexOf(elemento: String): Int {
        var atual = head
        var contador = 0

        while (atual != null) {
            if (atual.data == elemento) return contador
            atual = atual.next
            contador++
        }

        println("Elemento não encontrado.")
        return -1
    }
}

fun main() {
    val lista = ListaEncadeada()

    println(lista.insertFirst("Laptop"))       // Insere no início
    println(lista.insertLast("Keyboard"))      // Insere no fim
    println(lista.insertLast("Mouse"))         // Insere no fim
    println(lista.insertAt("WebCam", 1))       // Insere na posição 1
    println("Conteúdo da lista: ${lista.traversal()}")                 // Exibe a lista
    println(lista.searchAt(2))                 // Busca na posição 2
    println(lista.indexOf("Mouse"))            // Índice do elemento
    println("Item deletado: ${lista.deleteAt(1)}")                 // Remove da posição 1
    println("Conteúdo da lista: ${lista.traversal()}")                 // Exibe a lista novamente
}
```

!["Imagem que mostra a execução do código com exemplos de funções de uma lista encadeada"](../img/lista-encadeada.JPG)