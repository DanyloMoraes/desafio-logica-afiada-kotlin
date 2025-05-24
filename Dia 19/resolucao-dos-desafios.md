# Dia 19 - Recursão ("Inception" na Estrutura de Dados)

## DESAFIO: Parcelas Fatura Cartão de Crédito

**Descrição**: Crie um sistema que simula o cálculo do valor total de uma fatura de cartão de crédito.

O sistema deve considerar compras feitas no cartão, sendo que algumas delas podem ser parceladas, e cada parcela pode ter sub-parcelas (compras dentro de compras).

Utilize `recursão` para calcular o valor total da fatura, levando em consideração todas as compras, parcelas e sub-parcelas, até o nível mais profundo.

<img src="../img/fatura-template.jpg" height="600" alt="Imagem que mostra o template pronto da fatura fornecido pelo Desafio Lógica Afiada">

```kt
data class Item(
    val descricao: String,
    val valor: Double,
    val parcelas: List<Item>? = null
)

val fatura = listOf(
    Item(
        descricao = "Celular",
        valor = 1200.00,
        parcelas = listOf(
            Item(descricao = "Seguro", valor = 100.00),
            Item(descricao = "Película", valor = 30.00)
        )
    ),
    Item(
        descricao = "Laptop",
        valor = 3000.00,
        parcelas = listOf(
            Item(
                descricao = "Assistência técnica",
                valor = 200.00,
                parcelas = listOf(
                    Item(descricao = "Visita técnica", valor = 50.00)
                )
            )
        )
    ),
    Item(
        descricao = "Livro",
        valor = 89.90
    )
)

fun calcularTotal(fatura: List<Item>): Double {
    var total = 0.0

    for (item in fatura) {
        total += item.valor
        if (!item.parcelas.isNullOrEmpty()) {
            total += calcularTotal(item.parcelas)
        }
    }

    return total
}

fun main() {
    val totalDaFatura = calcularTotal(fatura)
    println("Valor total da fatura: R$ %.2f".format(totalDaFatura))
}
```

!["Imagem que mostra o resultado da função que soma o total das parcelas e suas sub-parcelas"](../img/total-fatura.JPG)