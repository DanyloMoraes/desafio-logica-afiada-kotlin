# Dia 4 - Tomando Decisões com Estrutura de Controle Condicional

## DESAFIO 01: Renovação CNH

**Descrição**: Calcule em quanto tempo a carteira de motorista irá vencer de acordo com a legislação.

1. Se você está tirando a carteira pela 1ª vez, o tempo de vencimento é de 1 ano;
2. Se você tem idade inferior a 50 anos, o vencimento é de 10 anos;
3. Se for igual ou superior a 50 anos ou inferior a 70 anos, o vencimento é de 5 anos;
4. Se for igual ou superior a 70 anos, o vencimento será de 3 anos;

```kt
fun main() {
    var idade: Int = 25
    var primeiraHabilitacao: Boolean = false
    var validade: String = ""

    // Verifica se é a primeira habilitação e a idade
    if (primeiraHabilitacao) {
        validade = "1 ano"
    } else if ((idade >= 18) && (idade < 50)) {
        validade = "10 anos"
    } else if ((idade >= 50) && (idade < 70)) {
        validade = "5 anos"
    } else if (idade >= 70) {
        validade = "3 anos"
    } else {
        println("Você não pode tirar a habilitação")
    }
    
    // Mostra uma mensagem com a validade da habilitação
    println("A validade da sua Carteira Nacional de Habilitação (CNH) é de ${validade}")
}
```

!["Imagem que mostra a execução do código com a verificação da idade e primeira habilitação"](../img/habilitacao.JPG)

## DESAFIO 02: Performance de Aluno

**Descrição**: Informe para um aluno a sua performance em uma prova a partir da sua nota.

1. Se a nota for menor que 5, então mostra que foi "Insuficiente";
2. Se foi menor que 6, então mostre "Regular";
3. Se foi menor que 7.5, mostre "Bom";
4. Se foi menor que 9, "Muito Bom";
5. Se for maior ou igual a 9, mostre "Excelente".

```js
fun main() {
    var notaDoAluno = 8.5
    var resultado: String = ""

    // Verifica a nota do aluno
    if (notaDoAluno < 5) {
        resultado = "Insuficiente"
    } else if (notaDoAluno < 6) {
        resultado = "Regular"
    } else if (notaDoAluno < 7.5) {
        resultado = "Bom"
    } else if (notaDoAluno < 9) {
        resultado = "Muito bom"
    } else if (notaDoAluno >= 9) {
        resultado = "Excelente"
    }

    // Mostra a nota e o resultado do aluno
    println("Nota da prova: $notaDoAluno")
    println("Resultado do Aluno: $resultado")
}
```

!["Imagem que mostra a execução do código com a verificação da nota do aluno"](../img/nota-aluno.JPG)

## DESAFIO 03: Transforme o Código em uma Condição Ternária

**Descrição**: Converta essa forma de condicional em uma condição ternária.

### Código Anterior:

```kt
fun main() {
    var nota = 85
    var status = ""
    
    if (nota >= 70) {
        status = "Aprovado"
    } else {
        status = "Reprovado"
    }
    
    println("Resultado da prova: $status")
}
```

### Código Usando Condição Ternária:

> ❌ Kotlin não tem operador ternário
>
> ✅ Kotlin usa `if` como expressão para o mesmo propósito

```kt
var nota = 85

    // Kotlin não possui "Condição Ternária"
    var status = if (nota >= 70) "Aprovado" else "Reprovado"

    println("Resultado da prova: $status")
```

!["Imagem que mostra a execução do código com o uso da Condição Ternária"](../img/resultado-prova.JPG)

## DESAFIO 04: Condição ternária com expressão mais complexa

**Descrição**: Escreva um código que determina se o cliente pode fazer compras com sua conta. As condições para poder comprar são:

1. A conta precisa estar ativa;
2. Saldo deve ser maior que R$500;
3. Use a condição ternária para isso.

> ❌ Kotlin não tem operador ternário
>
> ✅ Kotlin usa `if` como expressão para o mesmo propósito

```js
fun main() {
    var contaAtiva = true
    var contaSaldo = 550

    // Verifica se a conta está ativada e se possui saldo superior a R$500
    var verificacao = if (contaAtiva && (contaSaldo > 500)) "Aprovado" else "Negado"

    println("Autorização de compra: $verificacao")
}
```

!["Imagem que mostra a execução do código com a verificação de compra"](../img/verificacao-compra.JPG)

## DESAFIO 05: Cancela de Estacionamento

**Descrição**: Crie um código usando switch que imprima uma mensagem adequada para o motorista. O sistema tem três possíveis estados: "Aberta", "Fechada" e "Manutenção".

> `when` é similar ao `switch` em outras linguagens de programação

```kt
fun main() {
    var estadoDaCancela = "Aberta"

    // Exibe a mensagem a depender do estado da cancela
    when (estadoDaCancela) {
        "Aberta" -> println("Prossiga com a sua viagem")
        "Fechada" -> println("Aguarde a sua verificação")
        "Manutenção" -> println("Estamos realizando manutenção preventiva")
        else -> println("Fora de serviço")
    }
}
```

!["Imagem que mostra a execução do código com a verificação do estado da cancela"](../img/cancela-estacionamento.JPG)

## DESAFIO 06: Sistema de PDV (Ponto de Venda)

**Descrição**: Crie um código usando switch que calcule e imprima o valor final do produto após a aplicação do desconto, com base no tipo do produto.

O desconto é dado com base no tipo do produto:

- "Alimentos" têm um desconto de 5%;
- "Eletrônicos" têm um desconto de 10%;
- "Roupas" têm um desconto de 20%;
- "Livros" têm um desconto de 50%;
- Se o tipo do produto não estiver na lista, não há desconto;

```kt
fun main() {
    val nomeProduto = "Smart TV A360"
    val tipoDoProduto = "Eletrônicos"
    var valorProduto: Double = 1299.0
    var descontoPorTipo: Double

    // Verifica o tipo do produto e aplica o desconto
    when(tipoDoProduto) {
        "Alimentos" -> descontoPorTipo = 5.0
        "Eletrônicos" -> descontoPorTipo = 10.0
        "Roupas" -> descontoPorTipo = 20.0
        "Livros" -> descontoPorTipo = 50.0
        else -> descontoPorTipo = 0.0
    }

    println("Produto: $nomeProduto")
    println("Preço: R$${String.format("%.2f", valorProduto)}")

    if (descontoPorTipo != 0.0) {
        var valorDesconto = (descontoPorTipo / 100.0) * valorProduto
        var descontoDoProduto = valorProduto - valorDesconto

        println("Desconto: ${String.format("%.0f", descontoPorTipo)}%")
        println("Total: R$${String.format("%.2f", descontoDoProduto)} no Pix")
    } else {
        println("Este produto não possui desconto")
    }
}
```

!["Imagem que mostra a execução do código com o valor do desconto aplicado"](../img/desconto-por-tipo.JPG)