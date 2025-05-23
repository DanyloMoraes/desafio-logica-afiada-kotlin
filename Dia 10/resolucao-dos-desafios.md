# Dia 10 - Como Empilhar Coisas te Ensina Sobre Estrutura de Dados

## DESAFIO 01: Braço Mecânico para Empilhar Produtos

**Descrição**: Na linha de produção, um braço mecânico automatizado é encarregado de pegar produtos individuais que chegam através de uma esteira e empilhá-los em caixas para envio.
Cada caixa pode conter até no máximo 10 produtos. Uma vez que a caixa está cheia, ela é enviada para ser selada e despachada.

*Empilhar*. O braço mecânico pega um produto da esteira e o coloca no topo da pilha atual.

*Verificar a Capacidade*. Antes de empilhar um novo produto, o sistema verifica se a pilha já contém 10 produtos.

*Criar uma Nova Pilha*. Uma vez que a pilha atinge 10 produtos, ela é enviada para o próximo estágio do processo (selagem e despacho), e uma nova pilha vazia é iniciada para os próximos produtos.

```kt
fun main() {
    println("Os produtos já foram colocados na esteira.")
    println("==================================================")
    println("Lista de produtos na esteira: $esteira")
    println("==================================================")

    val tamanhoDaEsteira = esteira.size
    for (i in 0 until tamanhoDaEsteira) {
        empilharProdutos()
    }

    criarNovaPilha()
    println("Produtos restantes na esteira: ${esteira.size}")
}

// Variável Global
val caixa = mutableListOf<String>()
val capacidadeMaxima:Int = 10
val esteira = mutableListOf<String>(
    "Caneta",
    "Lápis",
    "Borracha",
    "Apontador",
    "Caderno pequeno",
    "Fones de ouvido",
    "Carregador de celular",
    "Mouse",
    "Cabo USB",
    "Pen drive",
    "Relógio de pulso",
    "Chaveiro",
    "Caixa de clipes",
    "Tesoura pequena",
    "Mini lanterna",
    "Bloquinho de notas",
    "Estojo",
    "Cartucho de tinta",
    "Adaptador de tomada",
    "Bateria portátil"
)

fun verificarCapacidade() {
    if (isFull()) {
        criarNovaPilha()
    }
}

fun isFull(): Boolean {
    return caixa.size >= capacidadeMaxima
}

fun empilharProdutos() {
    verificarCapacidade()

    if (esteira.isNotEmpty()) {
        val produtoEmpilhado = esteira.removeAt(esteira.lastIndex) // Equivalente a pop()
        caixa.add(produtoEmpilhado)
        println("$produtoEmpilhado na caixa")
    } else {
        println("Esteira vazia. Não há mais produtos para empilhar.")
    }
}

fun criarNovaPilha() {
    println("==================================================")
    println("Caixa embalada com os seguintes produtos: $caixa")
    println("==================================================")
    caixa.clear() // Esvazia a pilha
}
```

!["Imagem que mostra a execução do código com a simulação de um braço mecânico que pega produtos em uma esteira e empilha dentro de uma caixa"](../img/pilha-esteira.JPG)