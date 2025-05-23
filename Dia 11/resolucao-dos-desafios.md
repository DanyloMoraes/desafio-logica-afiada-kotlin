# Dia 11 - Pilhas no Mundo Real

## DESAFIO: Controle de Navegação em Navegadores Web

**Descrição**:

1. Pilha de Voltar:
Quando você navega de uma página para outra, a página atual é empurrada (pushed) para a pilha de voltar. Se você continuar navegando por várias páginas, elas serão empilhadas em ordem. Quando você clica no botão "voltar", o topo da pilha de voltar é retirado (popped) e a página é exibida.

2. Pilha de Avançar:
Quando você clica em "voltar", a página da qual você voltou é empurrada para a pilha de avançar. Se você clicar em "avançar", você tira (pop) da pilha de avançar e navega para a página.

    I - Crie 3 funções, uma que controla o voltar, uma para o avançar e outra para navegar para um endereço.

    II - Controle a partir de 2 pilhas e uma variável que armazena o endereço da página atual.

```kt
fun main() {
    navegarPara("google.com")
    navegarPara("amazon.com")
    navegarPara("microsoft.com")

    voltar() // volta para 'amazon.com'
    voltar() // volta para 'google.com'
    avancar() // volta para 'amazon.com'

    navegarPara("apple.com")
    
    voltar() // volta para 'amazon.com'
    voltar() // volta para 'google.com'
    voltar() // sem páginas anteriores
}

// Variáveis Globais
val pilhaVoltar = mutableListOf<String>()
val pilhaAvancar = mutableListOf<String>()
var paginaAtual: String? = null // Esta variável pode ser nula

fun navegarPara(pagina: String) {
    if (paginaAtual != null) {
        pilhaVoltar.add(paginaAtual!!)
        pilhaAvancar.clear() // Limpa a pilha de avançar
    }

    paginaAtual = pagina
    println("Navegando para: $paginaAtual")
}

fun voltar() {
    if (pilhaVoltar.isEmpty()) {
        println("Não há páginas anteriores.")
        return
    }

    paginaAtual?.let { pilhaAvancar.add(it) }

    paginaAtual = pilhaVoltar.removeAt(pilhaVoltar.lastIndex)
    println("Voltando para: $paginaAtual")
}

fun avancar() {
    if (pilhaAvancar.isEmpty()) {
        println("Não há páginas à frente.")
        return
    }

    paginaAtual?.let { pilhaVoltar.add(it) }

    paginaAtual = pilhaAvancar.removeAt(pilhaAvancar.lastIndex)
    println("Avançando para: $paginaAtual")
}
```

!["Imagem que mostra a execução do código com funções de avançar e voltar que simulam a navegação em páginas web"](../img/navegacao.JPG)