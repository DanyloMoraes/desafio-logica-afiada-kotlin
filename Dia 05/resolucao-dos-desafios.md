# Dia 5 - Estrutura de Controle de Repetição (Loops)

## DESAFIO 01: Rendimento de Aplicação Financeira

**Descrição**: Suponha que você investiu R$ 1.000 em uma aplicação financeira que rende 12% ao ano. Usando um loop for, calcule como esse investimento cresce ao longo do tempo, nos próximos 10 anos.

Mostre o valor no console por ano.

```kt
fun main() {
    val capitalInicial = 1000.0 // Capital a ser investido
    val taxaJuros = 0.12        // Taxa de juros (12% ao ano)
    val tempoInvestido = 10     // Número de anos investindo

    var valorFuturo = capitalInicial

    for (i in 1..tempoInvestido) {
        valorFuturo = valorFuturo * (1 + taxaJuros)
        println("Ano $i -> R$ ${String.format("%.2f", valorFuturo)}")
    }

    // Mostra o retorno do valor investido
    println("Retorno do investimento: R$ ${String.format("%.2f", valorFuturo)}")
}
```

!["Imagem que mostra a execução do código com o retorno do investimento ao longo do tempo"](../img/retorno-investimento.JPG)

## DESAFIO 02: Contagem Regressiva para lançamento de foguete

**Descrição**: Faça a contagem regressiva a partir de 10 até o lançamento de um foguete.

Ao chegar nos últimos 3 segundos, é importante dar um aviso, então inclua o texto "Atenção!" junto a contagem. Quando a contagem terminar mostre a mensagem: "Lançamento do foguete".

```kt
fun main() {
    // Contagem regressiva
    for (i in 10 downTo 0) {
        if (i <= 3) {
            println("Atenção! - $i")
        } else {
            println("$i")
        }
    }

    // Mostra a mensagem de lançamento
    println("")
    println("Lançamento do foguete")
}
```

!["Imagem que mostra a execução do código com uma contagem regressiva para o lançamento de um foguete"](../img/contagem-regressiva.JPG)

## DESAFIO 03: Cálculo de Juros

**Descrição**: Calcule quanto tempo (em anos) levará para que um investimento inicial dobre, considerando uma taxa de juros de 5% ao ano.

```kt
fun main() {
    var valorInvestido = 1000.0 // Capital inicial
    val taxaJuros = 0.05 // Taxa de juros anual
    var investimentoDesejado = valorInvestido * 2

    var anosInvestindo = 0

    while (valorInvestido < investimentoDesejado) {
        valorInvestido += valorInvestido * taxaJuros
        anosInvestindo++
    }

    // Mostra o tempo que levará até o investimento dobrar de valor
    println("Seu investimento levará $anosInvestindo anos para dobrar.")
}
```

!["Imagem que mostra a execução do código com o tempo necessário para o investimento dobrar"](../img/investimento-dobro.JPG)

## DESAFIO 04: Compra Parcelada

**Descrição**: Você comprou um produto e optou por parcelar o valor em 12x sem juros. Escreva um código que imprima o valor de cada parcela e o valor restante a ser pago.

```kt
fun main() {
    var valorProduto = 1200.0
    val numeroParcelas = 12

    var valorParcela = valorProduto / numeroParcelas

    // Mostra o valor restante a ser pago
    for (i in 1..numeroParcelas) {
        valorProduto -= valorParcela

        println("${i}ª parcela - R$ ${String.format("%.2f", valorParcela)}")
        println("Valor restante - R$ ${String.format("%.2f", valorProduto)}")
        println("---------------------------")
    }
}
```

!["Imagem que mostra a execução do código com o abatimento das parcelas e o valor restante"](../img/parcelas.JPG)