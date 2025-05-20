# Dia 3 - Aprenda a Usar os Operadores

## DESAFIO 01:

### Para Soma:

1. Adicione uma nova pontuação a um total de pontos existente em um jogo fictício.

```kt
fun main() {
    var pontuacaoAtual = 1200
    var novosPontos = 500

    // Mostra a pontuação atual e os novos pontos
    println("Pontuação Total: ${pontuacaoAtual} pontos")
    println("Novos Pontos: ${novosPontos} pontos")

    // Soma a pontuação atual com os novos pontos
    pontuacaoAtual = (pontuacaoAtual + novosPontos)

    // Mostra a pontuação total atualizada com os novos pontos
    println("Pontuação Total: ${pontuacaoAtual} pontos")
}
```

!["Imagem que mostra a execução do código da pontuação atualizada"](../img/nova-pontuacao-jogo.JPG)

2. Para cada dia da semana defina a quantidade de horas trabalhadas e some o total.

```kt
fun main() {
    var segundaFeira = 8
    var tercaFeira = 8
    var quartaFeira = 8
    var quintaFeira = 8
    var sextaFeira = 8
    var sabado = 4
    var domingo = 0

    // Soma total das horas trabalhadas na semana
    var totalHorasTrabalhadas = (
            segundaFeira +
            tercaFeira +
            quartaFeira +
            quintaFeira +
            sextaFeira +
            sabado +
            domingo)

    println("Horas trabalhadas na semana: ${totalHorasTrabalhadas} horas.")
}
```

!["Imagem que mostra a execução do código das soma das horas trabalhadas na semana"](../img/horas-trabalhadas-na-semana.JPG)

3. Imagine que na sua casa 3 pessoas ganham salários diferentes, some eles para saber o ganho total.

```kt
fun main() {
    val pedroSalario: Int = 1750
    val jonasSalario: Int = 3860
    val sauloSalario: Int = 4517

    // Soma dos salários
    var somaDosSalarios = (pedroSalario + jonasSalario + sauloSalario)

    // Mostra o salário de cada um
    println("Salário de Pedro: R$ ${String.format("%.2f", pedroSalario.toDouble())}")
    println("Salário do Jonas: R$ ${String.format("%.2f", jonasSalario.toDouble())}")
    println("Salário do Saulo: R$ ${String.format("%.2f", sauloSalario.toDouble())}")

    println("------------------------------") // Linha divisória

    // Mostra a soma dos três salários
    println("Soma dos salários: R$ ${String.format("%.2f", somaDosSalarios.toDouble())}")
}
```

!["Imagem que mostra a execução do código da soma dos salários"](../img/soma-dos-salarios.JPG)

### Para Subtração:

1. Imagine que você tem algumas variáveis com compras no cartão de crédito, e uma com um valor a ser estornado de uma compra errada, calcule o total da fatura atualizado.

```kt
fun main() {
    var valorDasCompras = 475 // valor em Reais
    var valorEstornado = 150  // valor em Reais

    // Valor a ser estornado
    var totalDaFatura = (valorDasCompras - valorEstornado)

    println("Valor total das compras: R$ ${valorDasCompras}")
    println("Valor a ser estornado: R$ ${valorEstornado}")

    println("----------------------------------") // divisória

    println("Total da fatura a ser pago: R$ ${totalDaFatura}")
}
```

!["Imagem que mostra a execução do código do valor atualizado a ser pago"](../img/valor-estornado.JPG)

2. Calcule a sua idade a partir de duas variáveis contendo o ano de nascimento e o ano atual.

```kt
fun main() {
    val anoNascimento: Int = 1990
    var anoAtual: Int = 2025

    // Subtrai o ano atual com o ano de nascimento
    var minhaIdade = (anoAtual - anoNascimento)

    println("Ano de Nascimento: ${anoNascimento}")
    println("Ano Atual: ${anoAtual}")

    // Mostra minha idade atual
    println("Minha idade é: ${minhaIdade} anos")
}
```

!["Imagem que mostra a execução do código do desafio do cálculo da idade"](../img/calculo-da-idade.JPG)

3. Imagine que em um jogo você tenha um total de moedas e para cada vez que você compra um artefato você gasta um determinado número de moedas. Calcule a quantidade final de moedas.

```kt
fun main() {
    var moedasTotais: Int = 3500
    println("Total de Moedas: ${moedasTotais}")

    // Itens comprados
    val precoEspada: Int = 275
    val precoArmadura: Int = 546

    // Subtrai o valor dos itens
    moedasTotais -= precoEspada
    moedasTotais -= precoArmadura

    println("Espada Comprada: $${precoEspada}")
    println("Armadura Comprada: $${precoArmadura}")

    println("-----------------------") // divisória
    
    println("Moedas Restantes: $${moedasTotais}")
}
```

!["Imagem que mostra a execução do código dos itens comprados"](../img/itens-comprados.JPG)

### Para Multiplicação:

1. Vamos supor que você tenha 2 produtos e que queira comprar 2 unidades de cada. Faça a multiplicação para encontrar o total.

```kt
fun main() {
    val camisaPrecoUnidade: Double = 189.90
    val bermudaPrecoUnidade: Double = 149.65

    var valorTotalCamisas = camisaPrecoUnidade * 2
    var valorTotalBermudas = bermudaPrecoUnidade * 2

    var valorTotal = valorTotalCamisas + valorTotalBermudas

    println("Camisa - Preço da Unidade: R$ ${String.format("%.2f", camisaPrecoUnidade)}")
    println("Bermuda - Preço da Unidade: R$ ${String.format("%.2f", bermudaPrecoUnidade)}")

    println("-------------------------------------")

    println("Camisa (2x un.) Total: R$ ${String.format("%.2f", valorTotalCamisas)}")
    println("Bermuda (2x un.) Total: R$ ${String.format("%.2f", valorTotalBermudas)}")

    println("-------------------------------------")

    println("Valor total a ser pago: $ ${String.format("%.2f", valorTotal)}")
}
```

!["Imagem que mostra a execução do código dos produtos comprados"](../img/produtos-comprados.JPG)

2. Calcule a área de um retângulo.

```kt
fun main() {
    val larguraRetangulo = 12
    val alturaRetangulo = 30

    // Área de um retângulo = Largura x Altura
    var areaRetangulo = larguraRetangulo * alturaRetangulo

    println("Largura do Retângulo: ${larguraRetangulo}")
    println("Altura do Retângulo: ${alturaRetangulo}")

    println("----------------------------")

    println("Área Total do Retângulo: ${areaRetangulo}")
}
```

!["Imagem que mostra a execução do código da área de um retângulo"](../img/area-retangulo.JPG)

3. Crie 2 variáveis que contêm o total de horas trabalhadas e o valor por hora. Calcule o total a receber depois de trabalhar 160 horas.

```js
fun main() {
    // Total de horas trabalhadas no mês
    var totalHorasTrabalhadas = 160

    // Valor por hora trabalhada
    var valorHora = 15

    // Total a receber
    var totalReceber = valorHora * totalHorasTrabalhadas

    println("Valor por hora trabalhada: R$ ${String.format("%.2f", valorHora.toDouble())}")
    println("Total de horas trabalhadas: ${totalHorasTrabalhadas}")

    println("-----------------------------------")

    // Mostra o valor total em Reais a receber
    println("Total a receber: R$ ${String.format("%.2f", totalReceber.toDouble())}")
}
```

!["Imagem que mostra a execução do código com o valor total das horas trabalhadas"](../img/total-horas-trabalhadas.JPG)

### Para Divisão:

1. Calcule a média de quatro notas.

```kt
fun main() {
    var portugues = 9.5
    var matematica = 7.0
    var historia = 8.5
    var geografia = 6.5

    // Soma todas as notas e divide pela quantidade
    var notaMedia = (portugues + matematica + historia + geografia) / 4

    println("Português: ${portugues}")
    println("Matemática: ${matematica}")
    println("História: ${historia}")
    println("Geografia: ${geografia}")

    println("------------------------")

    // Mostra a nota média do aluno
    println("A média das notas é: ${String.format("%.1f", notaMedia)}")
}
```

!["Imagem que mostra a execução do código com o resultado da média das notas"](../img/media-notas.JPG)

2. Converta a distância de metros para quilômetros.

```kt
fun main() {
    val quilometros = 1000 // Um quilômetro possui mil metros
    var metros = 250

    var metrosParaQuilometros = (metros.toDouble() / quilometros)

    println("${metros}m será convertido para quilômetros")

    println("-------------------------------------")

    // Mostra a distância de metros para quilômetros
    println("Valor convertido: ${String.format("%.2f", metrosParaQuilometros)}km")
}
```

!["Imagem que mostra a execução do código com a conversão de metros para quilômetros"](../img/metros-quilometros.JPG)

## DESAFIO 02: Par ou Ímpar

**Descrição**: Com o que você já sabe, quero que você crie um código que determine se um número é par. **Dica**: Para isso utilize exatamente o operador de módulo que explicamos.

```kt
fun main() {
    var numeroEscolhido = 5
    var resultado = numeroEscolhido % 2

    // Mostra o resultado se é "par" ou "ímpar"
    if (resultado == 0) {
        println("O número ${numeroEscolhido} é par.")
    } else {
        println("O número ${numeroEscolhido} é ímpar.")
    }
}
```

!["Imagem que mostra a execução do código com o resultado se o número escolhido é par ou ímpar"](../img/par-impar.JPG)

### DESAFIO 03: Cálculo IMC

**Descrição**: Calcule o IMC de uma pessoa (que é peso dividido pela algura ao quadrado).

- Se o resultado ficar menor que 18.5, mostra que está abaixo do peso;
- Se for maior ou igual a 18.5 e menor que 24.9, mostre que está com peso normal;
- Se for maior ou igual a 24.9 e menor que 29.9, mostre que está com sobrepeso, senão mostre que é obesidade.

```kt
fun main() {
    var peso = 75
    var altura = 1.75

    // A fórmula é: IMC = peso / (altura * altura)
    val imc = peso / (altura * altura) // O resultado é dado em kg/m²
    println("Seu IMC é: ${String.format("%.1f", imc)}")

    // Verifica o IMC (Índice de Massa Corporal)
    var resultado: String // Armazena a string do resultado

    if (imc < 18.5) {
        resultado = "Abaixo do peso"
    } else if ((imc >= 18.5) && (imc < 24.9)) {
        resultado = "Peso normal"
    } else if ((imc >= 24.9) && (imc < 29.9)) {
        resultado = "Sobrepeso"
    } else {
        resultado = "Obesidade"
    }

    /* Outra forma de retornar o resultado
     *
     * if (imc < 18.5) resultado = "Abaixo do peso"
     * if ((imc >= 18.5) && (imc < 24.9)) resultado = "Peso normal"
     * if ((imc >= 24.9) && (imc < 29.9)) resultado = "Sobrepeso"
     */

    println("Resultado: $resultado")
}
```

!["Imagem que mostra a execução do código com o resultado do IMC"](../img/imc.JPG)

## DESAFIO 04: Cálculo de distância de viagem e custo de combustível

**Descrição**: Suponha que você está planejando uma viagem de carro. Seu carro faz 12km por litro de gasolina, e você quer calcular o número de litros de combustível que você precisará para a viagem, bem como o custo total do combustível.

- Distrância total da viagem em quilômetros
- Preço do litro de gasolina em reais

1. Quantos litros de gasolina serão necessários para a viagem (considerando que o carro faz 12km por litro)?
2. Quanto vai custar para abastecer o carro para a viagem?

```kt
fun main() {
    var precoGasolina = 6.25     // Preço do litro de gasolina
    var distanciaDaViagem = 600  // Distância da viagem em quilômetros
    var quilometrosPorLitro = 12 // O carro faz 12km por litro

    // Litros necessários para a viagem
    var litrosNecessarios = distanciaDaViagem / quilometrosPorLitro

    // Custo para abastecer o carro
    var valorNecessario = precoGasolina * litrosNecessarios

    // Mostra as informações sobre a viagem
    println("Distância da viagem: ${distanciaDaViagem}km")
    println("Estimativa de consumo de gasolina para a viagem: ${litrosNecessarios} litros")
    println("Valor total do abastecimento do carro: R$ ${String.format("%.2f", valorNecessario)}")
}
```

!["Imagem que mostra a execução do código com o custo da viagem e litros de gasolina necessários"](../img/custo-viagem.JPG)