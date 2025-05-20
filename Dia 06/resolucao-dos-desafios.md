# Dia 6 - Encaixotando Códigos com Funções e Procedimentos

## DESAFIO 01:

**Descrição**: Crie uma função que utiliza o peso e a altura como parâmetros para calcular o **IMC** (Índice de Massa Corporal) de uma pessoa.

```kt
fun main() {
    var peso = 85.0
    var altura = 1.75

    // Executa a função "calcularIMC()"
    calcularIMC(peso, altura)
}

fun calcularIMC(peso: Double, altura: Double) {
    var imc = peso / (altura * altura)
    var resultado: String

    if (imc < 18.5) {
        resultado = "Abaixo do peso"
    } else if ((imc >= 18.5) && (imc < 24.9)) {
        resultado = "Peso normal"
    } else if ((imc >= 24.9) && (imc < 29.9)) {
        resultado = "Sobrepeso"
    } else {
        resultado = "Obesidade"
    }

    // Mostra o valor do seu IMC e o resultado
    println("Seu IMC é: ${String.format("%.2f", imc)}")
    println("Resultado: $resultado")
}
```

!["Imagem que mostra a execução do código com o resultado do IMC"](../img/imc-funcao.JPG)

## DESAFIO 02: Dia da Semana por Extenso

**Descrição**: Transforme o código que criamos no dia 4 sobre os dias de semana em uma função chamada `obterDiaDaSemana`.

Receba um número que representa o dia da semana que vai de 1 a 7 e retorne esse dia por extenso.

```kt
fun main() {
    obterDiaDaSemana(7)
}

fun obterDiaDaSemana(diaNumero: Int) {
    var diaDaSemana: String

    if ((diaNumero > 0) && (diaNumero < 8)) {
        when (diaNumero) {
            1 -> diaDaSemana = "Domingo"
            2 -> diaDaSemana = "Segunda-Feira"
            3 -> diaDaSemana = "Terça-Feira"
            4 -> diaDaSemana = "Quarta-Feira"
            5 -> diaDaSemana = "Quinta-Feira"
            6 -> diaDaSemana = "Sexta-Feira"
            7 -> diaDaSemana = "Sábado"
            else -> diaDaSemana = "Dia da semana inexistente"
        }

        // Mostra a mensagem com o dia da semana
        println("Dia da semana: $diaDaSemana")
    } else {
        println("O dia da semana está errado!")
    }
}
```

!["Imagem que mostra a execução do código que recebe um número e returna sua representação do dia da semana por extenso"](../img/dia-semana.JPG)

## DESAFIO 03: Aplicação Financeira

**Descrição**: Volte ao dia 5, no desafio 1, e crie um função que fará todo o cálculo que detalhamos no desafio.

Você tem um valor inicial de uma aplicação financeira que rende um percentual ao ano. Calcule como esse investimento cresce no decorrer do ano.

```kt
fun main() {
    // Executa a função "investimento()"
    investimento(1000.0, 0.12, 10)
}

// Função que faz o cálculo do "Desafio 1 do Dia 5"
fun investimento(capitalInicial: Double, taxaJuros: Double, tempoInvestido: Int) {
    var valorFuturo = capitalInicial

    for (i in 1..tempoInvestido) {
        valorFuturo = valorFuturo * (1 + taxaJuros)
        println("Ano $i -> R$ ${String.format("%.2f", valorFuturo)}")
    }

    // Mostra o retorno do valor investido
    println("Retorno do investimento: R$ ${String.format("%.2f", valorFuturo)}")
}
```

!["Imagem que mostra a execução do código que mostra o retorno de uma aplicação financeira"](../img/funcao-returno-investimento.JPG)