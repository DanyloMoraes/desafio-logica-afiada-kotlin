# Dia 16 - Desafio da Playlist de Música

## DESAFIO: Playlist de Músicas em um App

**Descrição**:

1. Capacidade de adicionar e remover músicas.
2. Mostrar todas as músicas da playlist.
3. Toda vez que uma música é adicionada, ela é colocada no início da playlist.
4. É possível mover a posição da música na playlist a qualquer momento.
5. Função para tocar a playlist do início ao fim.
6. Capacidade para tocar apenas uma música da playlist.
7. As músicas devem ter os seguintes atributos: nome da música, nome do artista, número de reproduções e tempo total da música
8. Cada vez que uma música é tocada é preciso incrementar o número de reproduções.

```kt
data class Musica(
    val nome: String,
    val artista: String,
    val tempo: String,
    var reproducoes: Int = 0
)

class Playlist {
    private val musicas = mutableListOf<Musica>()

    fun adicionarMusica(nome: String, artista: String, tempo: String) {
        val novaMusica = Musica(nome, artista, tempo)
        musicas.add(0, novaMusica) // Insere no início
        println("Música \"$nome\" adicionada à playlist!")
    }

    fun removerMusica(nome: String) {
        val index = musicas.indexOfFirst { it.nome == nome }

        if (index == -1) {
            println("Música \"$nome\" não encontrada.")
            return
        }

        musicas.removeAt(index)
        println("Música \"$nome\" removida da playlist.")
    }

    fun moverMusica(nome: String, novaPosicao: Int) {
        val index = musicas.indexOfFirst { it.nome == nome }

        if (index == -1) {
            println("Música \"$nome\" não encontrada.")
            return
        }

        val musica = musicas.removeAt(index)

        if (novaPosicao in 0 until musicas.size) {
            musicas.add(novaPosicao, musica)
            println("Música \"$nome\" movida para a posição ${novaPosicao + 1}.")
        } else {
            musicas.add(musica)
            println("Posição inválida. Música \"$nome\" reinserida no fim.")
        }
    }

    fun tocarPlaylist() {
        if (musicas.isEmpty()) {
            println("A playlist está vazia.")
            return
        }

        println("Tocando a playlist:")
        for (musica in musicas) {
            musica.reproducoes++
            println("Tocando: ${musica.nome} - ${musica.artista} (${musica.tempo})")
        }
    }

    fun tocarMusica(nome: String) {
        val musica = musicas.find { it.nome == nome }

        if (musica != null) {
            musica.reproducoes++
            println("Tocando: ${musica.nome} - ${musica.artista} (${musica.tempo})")
        } else {
            println("Música \"$nome\" não encontrada.")
        }
    }

    fun mostrarPlaylist() {
        if (musicas.isEmpty()) {
            println("A playlist está vazia.")
        } else {
            println("Playlist Atual: ")
            for ((index, musica) in musicas.withIndex()) {
                println("${index + 1}. ${musica.nome} - ${musica.artista} | Reproduções: ${musica.reproducoes}")
            }
        }
    }

}

fun main() {
    val playlist = Playlist()

    playlist.adicionarMusica("Fear of The Dark", "Iron Maiden", "7:18")
    playlist.adicionarMusica("Always Somewhere", "Scorpions", "4:57")
    playlist.adicionarMusica("Poison", "Alice Cooper", "4:29")

    println("==================================================")
    playlist.mostrarPlaylist()

    println("==================================================")
    playlist.tocarMusica("Always Somewhere")

    println("==================================================")
    playlist.tocarPlaylist()

    println("==================================================")
    playlist.moverMusica("Poison", 1)

    println("==================================================")
    playlist.removerMusica("Fear of The Dark")

    println("==================================================")
    playlist.mostrarPlaylist()
}
```

!["Imagem que mostra a execução do código com exemplos de funções que simulam uma playlist com a lista de músicas"](../img/playlist.JPG)