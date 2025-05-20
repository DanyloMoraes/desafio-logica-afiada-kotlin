# Dia 2 - Tudo na Vida são Dados

## DESAFIO 01: Dados de um documento

**Descrição**: Classifique as informações do seu RG ou CPF.

### Resolução do Desafio

    REGISTRO GERAL = String
    DATA DE EXPEDIÇÃO = Date
    VALIDADE = Date
    NOME = String
    FILIAÇÃO = String
    NATURALIDADE = String
    DATA DE NASCIMENTO = Date
    DOC. ORIGEM = String
    CPF = String

## DESAFIO 02: Identificando Tipos em um Formulário da Caixa

**Descrição**: Classifique os tipos de dados do formulário. ([Link do formulário](https://www.caixa.gov.br/Downloads/PDF_formulario_para_atualizacao_de_cadastro_P_B.pdf))

### Resolução do Desafio

    NOME DA FIRMA OU RAZÃO SOCIAL = String
    CNPJ = String
    RECEITA FISCAL - ÚLTIMO EXERCÍCIO ENCERRADO = Float
    ANO REFERÊNCIA = Int
    RECEITA FISCAL - ÚLTIMOS 12 MESES = Float
    QUANTIDADE DE MESES = Int

## DESAFIO 03: Características de um Iphone 14 Plus

**Descrição**: Identifique os campos utilizados para formar essa página.

<p align="center">
    <img src="../img/iphone14plus.JPG" alt="Imagem de uma página de vendas de um Iphone 14 Plus no Mercado Livre" width="700">
</p>

### Resolução do Desafio

    CATEGORIA = String
    ESTADO_PRODUTO = String/Boolean
    QUANTIDADE_VENDAS = Int
    FAVORITO = Boolean
    NOME_PRODUTO = String
    AVALIAÇÃO = Float
    QUANTIDADE_AVALIAÇÃO = Int
    PREÇO_PRODUTO = Float
    DESCONTO_PIX = Int
    QUANTIDADE_PARCELAS = Int
    VALOR_PARCELAS = Float
    MEMORIA_RAM = Int
    COR = String
    DESCRIÇÃO_PRODUTO = String

## DESAFIO 04: Calculo de IMC

**Descrição**: Calcule o seu IMC (Índice de Massa Corporal).

### Resolução do Desafio

```kt
fun main() {
    /* Cálculo do IMC
     *
     * O Índice de Massa Corporal (IMC) é calculado
     * dividindo o peso pela altura ao quadrado.
     */

    var peso = 80
    var altura = 1.75

    // A fórmula é: IMC = peso / (altura * altura)
    var imc = peso / (altura * altura) // O resultado é dado em kg/m²

    // Mostra o resultado
    println("O seu IMC é: ${String.format("%.1f", imc)}")
}
```

Para interpretar o valor, pode-se usar a seguinte tabela:

| IMC | RESULTADO |
| :---: | :---: |
| Abaixo de 18.5 | Abaixo do peso |
| 18.5 a 24.9 | Peso normal |
| 25 a 29.9 | Sobrepeso |
| 30 a 34.9 | Obesidade grau I |
| 35 a 39.9 | Obesidade grau II |
| Acima de 40 | Obesidade grau III (mórbida) |
