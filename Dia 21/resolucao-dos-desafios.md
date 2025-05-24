# Dia 21 - Super Desafio Final

## DESAFIO: Simulador de Transações Pix

**Descrição**: Crie um código para simular transações pix em uma conta bancária, utilizando as seguintes regras:

1. O limite diário para transferencias (R$ 10.000), um histórico de transações por Pix e também um total já transferido por chave Pix.
2. Deverá implementar 2 operações Pix, uma para enviar o Pix e outra para cancelar (reembolso).
3. A conta terá um limite máximo diário de R$ 10.000 para realizar o Pix.
4. Existirá um total armazenado de todos os Pix realizados para uma mesma chave `totalPorChave`.

```kt
data class Transacao(
    val tipo: String,
    val chavePix: String,
    val valor: Double,
    val mensagem: String = "",
    val data: String
)

data class Conta(
    var saldo: Double = 50000.0,
    val limiteDiario: Double = 10000.0,
    val historicoTransacoes: MutableList<Transacao> = mutableListOf(),
    val totalPorChave: MutableMap<String, Double> = mutableMapOf()
)

val conta = Conta()

fun enviarPix(chavePix: String, valor: Double, mensagem: String = "", data: String) {
    val totalParaEssaChave = conta.totalPorChave.getOrDefault(chavePix, 0.0)
    val limitePermitido = if (totalParaEssaChave > conta.limiteDiario) totalParaEssaChave else conta.limiteDiario

    val totalHoje = conta.historicoTransacoes
        .filter { it.data == data && it.tipo == "PIX" }
        .sumOf { it.valor }

    if (totalHoje + valor > limitePermitido) {
        println("Limite diário de R$ %.2f excedido para hoje.".format(limitePermitido))
        return
    }

    if (conta.saldo < valor) {
        println("Saldo insuficiente.")
        return
    }

    conta.saldo -= valor
    conta.totalPorChave[chavePix] = totalParaEssaChave + valor

    conta.historicoTransacoes.add(
        Transacao("PIX", chavePix, valor, mensagem, data)
    )

    println("Pix de R$%.2f enviado para %s em %s.".format(valor, chavePix, data))
}

fun cancelarPix(indiceTransacao: Int) {
    val transacao = conta.historicoTransacoes.getOrNull(indiceTransacao)

    if (transacao == null || transacao.tipo != "PIX") {
        println("Transação inválida para cancelamento.")
        return
    }

    val (_, chavePix, valor, _, data) = transacao
    conta.saldo += valor
    conta.totalPorChave[chavePix] = conta.totalPorChave.getOrDefault(chavePix, 0.0) - valor

    conta.historicoTransacoes.add(
        Transacao("REEMBOLSO", chavePix, valor, "Reembolso de Pix", data)
    )

    println("Pix cancelado. Valor de R$ %.2f devolvido para a conta.".format(valor))
}

fun main() {
    // Testes de envio de Pix
    enviarPix("chave_pedro", 4000.0, "Compra de equipamento", "2025-01-02")
    enviarPix("chave_pedro", 5000.0, "Serviço", "2025-02-12")
    enviarPix("chave_pedro", 2000.0, "Extra", "2025-03-09")
    enviarPix("chave_pedro", 3000.0, "Nova transação", "2025-03-25")

    enviarPix("chave_cristina", 6000.0, "Pagamento 1", "2025-04-12")
    enviarPix("chave_cristina", 5000.0, "Pagamento 2", "2025-04-12")
    enviarPix("chave_cristina", 10000.0, "Pagamento 3", "2025-04-13")
    enviarPix("chave_cristina", 16000.0, "Pagamento 4", "2025-04-14")

    println("Saldo Final: R$ %.2f".format(conta.saldo))
    println("Histórico de Transações:")
    conta.historicoTransacoes.forEachIndexed { i, t -> println("[$i] $t") }

    // continua nas outras linhas de código abaixo:
}
```

!["Imagem que mostra o resultado do console.table"](../img/transacao-pix-1.JPG)

```kt
    println("Total por chave:")
    conta.totalPorChave.forEach { (chave, total) -> println("$chave: R$ %.2f".format(total)) }

    // Cancelamentos
    println("Cancelando a transação 1, 4 e 5:")
    cancelarPix(1)
    cancelarPix(4)
    cancelarPix(5)

    enviarPix("chave_cristina", 16000.0, "Pagamento 4", "2025-04-15")

    println("Saldo Atual após o cancelamento: R$ %.2f".format(conta.saldo))
    println("Histórico Atualizado:")
    conta.historicoTransacoes.forEachIndexed { i, t -> println("[$i] $t") }

    println("Total por chave atualizado:")
    conta.totalPorChave.forEach { (chave, total) -> println("$chave: R$ %.2f".format(total)) }
```

!["Imagem que mostra o resultado do console.table com o reembolso incluso"](../img/transacao-pix-2.JPG)

```kt
    println("Total por chave atualizado: ")
    println(conta.totalPorChave)
```

!["Imagem que mostra o resultado final no console.log, o pix enviado, os alertas de limites diários, o histórico de transações e os pix que foram cancelados"](../img/transacao-pix-resultado.JPG)