# Dia 18 - Ordenando a Playlist de Música

## DESAFIO: Ordenando a playlist

**Descrição**: Na playlist de músicas do dia 16, acrescente o que já foi feito. Utilize os algoritmos para *ordenar a playlist pelo título da música e também pelo número de reproduções.*

> **Observação**: Ordene por título utilizando o `Bubble Sort` e por número de reproduções com o `Selection Sort`.

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

    fun ordenarPorNome() {
        val n = musicas.size
        var trocado: Boolean

        do {
            trocado = false
            for (i in 0 until n - 1) {
                if (musicas[i].nome > musicas[i + 1].nome) {
                    val temp = musicas[i]
                    musicas[i] = musicas[i + 1]
                    musicas[i + 1] = temp
                    trocado = true
                }
            }
        } while (trocado)

        println("Playlist ordenada por nome.")
    }

    fun ordenarPorReproducoes() {
        val n = musicas.size

        for (i in 0 until n - 1) {
            var maxIndex = i

            for (j in i + 1 until n) {
                if (musicas[j].reproducoes > musicas[maxIndex].reproducoes) {
                    maxIndex = j
                }
            }

            val temp = musicas[i]
            musicas[i] = musicas[maxIndex]
            musicas[maxIndex] = temp
        }

        println("Playlist ordenada por número de reproduções.")

    }

}

fun main() {
    val playlist = Playlist()

    // Testando a playlist
    playlist.adicionarMusica("Fear of The Dark", "Iron Maiden", "7:18")
    playlist.adicionarMusica("Always Somewhere", "Scorpions", "4:57")
    playlist.adicionarMusica("Poison", "Alice Cooper", "4:29")
    playlist.adicionarMusica("Breaking The Law", "Judas Priest", "2:45")
    playlist.adicionarMusica("Livin' On A Prayer", "Bon Jovi", "4:08")
    playlist.adicionarMusica("I Was Made For Lovin' You", "KISS", "4:30")
    playlist.adicionarMusica("With or Without You", "U2", "4:52")
    playlist.adicionarMusica("Thunderstruck", "ACDC", "4:50")
    playlist.adicionarMusica("The Final Countdown", "Europe", "5:10")
    playlist.adicionarMusica("Eye Of The Tiger", "Survivor", "4:03")

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

    println("==================================================")
    playlist.ordenarPorNome()
    println("--------------------------------------------------")
    playlist.mostrarPlaylist()

    println("==================================================")
    playlist.ordenarPorReproducoes()
    println("--------------------------------------------------")
    playlist.mostrarPlaylist()
}
```

### Adição de novas músicas na playlist para um resultado mais realista.

!["Imagem que mostra uma playlist de músicas, seu estado atual, e sua organização por nome e por número de reproduções"](../img/playlist-completa.JPEG)