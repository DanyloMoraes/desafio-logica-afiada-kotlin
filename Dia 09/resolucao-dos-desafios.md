# Dia 9 - Super Poderes na Manipulação de Arrays

## DESAFIO 01: Recrie funções úteis em Arrays

**Descrição**: Reescrevendo as funções: `indexOf()`, `includes()` e o `lastIndexOf()` no JavaScript.

> Funções sendo reescritas no Kotlin

### Função recriada para `indexOf()`

```kt
fun main() {
    val redesSociais = arrayOf(
        "Instagram",
        "YouTube",
        "Facebook",
        "TikTok",
        "LinkedIn",
        "Pinterest",
        "Bluesky"
    )
    // Mostra índice do elemento na lista
    println("Index: [${meuIndexOf(redesSociais, "LinkedIn")}]")
}

fun meuIndexOf(array: Array<String>, redeSocial: String): Int {
    /* Verifica se a rede social existe na lista
    * e retorna o seu índice, caso contrário,
    * retorna -1
    */
    for (i in 0 until array.size) {
        if (array[i] == redeSocial) {
            return i
        }
    }
    return -1
}
```

### Função recriada para `includes()`

> A função `includes()` não existe no Kotlin, apenas no JavaScript

```kt
fun main() {
    val redesSociais = arrayOf(
        "Instagram",
        "YouTube",
        "Facebook",
        "TikTok",
        "LinkedIn",
        "Pinterest",
        "Bluesky"
    )

    // Mostra uma mensagem e o retorno booleano
    println("Includes: [${meuIncludes(redesSociais, "LinkedIn")}]")
}

fun meuIncludes(array: Array<String>, redeSocial: String): Boolean {
    /* Verifica se a rede social existe na lista
     * e retorna "true" se existir e "false" caso contrário
     */
    for (i in 0 until array.size) {
        if (array[i] == redeSocial) {
            return true
        }
    }
    return false
}
```

### Função recriada para `lastIndexOf()`

```kt
fun main() {
    val redesSociais = arrayOf(
        "Instagram",
        "YouTube",
        "Facebook",
        "TikTok",
        "LinkedIn",
        "YouTube",
        "Pinterest",
        "Bluesky"
    )

    // Mostra uma mensagem e o índice da rede social
    println("lastIndexOf: [${meuLastIndexOf(redesSociais, "YouTube")}]")
}

fun meuLastIndexOf(array: Array<String>, redeSocial: String): Int {
    /* Verifica se a rede social existe na lista
     * começando pelo fim. Ao achar a rede social
     * retorna o seu índice
     */
    for (i  in array.size - 1 downTo 0) {
        if (array[i] == redeSocial) {
            return i
        }
    }
    return -1
}
```

## DESAFIO 02: Um Novo Slice

**Descrição**: Recrie o `slice()`, fazendo o seu da sua maneira.

```kt
fun main() {
    // Os 10 carros mais vendidos no Brasil em 2024
    val carrosMaisVendidos = arrayOf(
        "Fiat Strada",
        "Volkswagen Polo",
        "Chevrolet Onix",
        "Hyundai HB20",
        "Fiat Argo",
        "Volkswagen T-Cross",
        "Fiat Mobi",
        "Hyundai Creta",
        "Chevrolet Tracker",
        "Chevrolet Onix Plus"
    )
    // Mostra uma lista organizada com os 5 primeiros carros
    meuSlice(carrosMaisVendidos, 0, 5)
}

fun meuSlice(array: Array<String>, inicio: Int = 0, fim: Int = array.size) {
    val getTop5 = mutableListOf<String>()
    // Impede que o valor do inicio seja menor que zero
    var inicioEfetivo = if (inicio < 0) array.size + inicio else inicio
    inicioEfetivo = maxOf(0, inicioEfetivo)
    inicioEfetivo = minOf(array.size, inicioEfetivo)

    // Impede que o valor do fim seja menor que zero
    var fimEfetivo = if (fim < 0) array.size + fim else fim
    fimEfetivo = maxOf(0, fimEfetivo)
    fimEfetivo = minOf(array.size, fimEfetivo)

    // Armazena na variável "getTop5" os cinco primeiros carros
    for (i in inicioEfetivo until fimEfetivo) {
        getTop5.add(array[i])
        println("${i + 1}: ${getTop5[i]}")
    }
}
```

!["Imagem que mostra a execução do código com o retorno da função slice() recriada"](../img/slice.JPG)