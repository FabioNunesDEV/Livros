**Data:** 2024-11-01
**Livro:**  Entendendo Algoritmos - Um guia ilustrados para programadores e outros curiosos
**Autor**:  Aditya Y. Bhargava

**Tags:** #Algoritmos

### Conteúdo
----------------
No capítulo 10 de *Entendendo Algoritmos*, Aditya Bhargava apresenta o algoritmo de **K-Vizinhos Mais Próximos (KNN)**, uma técnica usada tanto para **classificação** quanto para **regressão**. Este método considera os dados mais próximos para fazer previsões ou categorizações e é amplamente usado em problemas de recomendação e aprendizado de máquina.

### Classificando Laranja versus Toranjas
KNN é exemplificado pela tarefa de classificar frutas: se você deseja diferenciar laranjas de toranjas, pode analisar propriedades como cor, tamanho e peso. O algoritmo KNN analisa os pontos de dados mais próximos do item a ser classificado e calcula as similaridades. Se a maioria dos vizinhos mais próximos de uma fruta nova são laranjas, ela será classificada como laranja. A chave do KNN está em encontrar as distâncias entre os itens e, então, classificá-los com base na maioria dos vizinhos mais próximos (K), onde K é um número pré-definido.

### Criando um Sistema de Recomendações
KNN é útil para sistemas de recomendação, que comparam as características de um item novo com itens que o usuário já gostou, para sugerir algo semelhante.

- **Extração de Características:** Para recomendar, é preciso primeiro extrair características de um item, como gênero de filme, estilo musical ou ingredientes de uma receita. Esses atributos definem as similaridades entre os itens.

- **Regressão:** Além de classificação, KNN pode fazer **regressão**, onde a média dos valores dos vizinhos mais próximos é usada para prever um valor contínuo (por exemplo, nota de um filme).

- **Escolhendo Boas Características:** As características escolhidas devem ser significativas, ou seja, devem ajudar a discriminar ou agrupar itens de maneira lógica. No exemplo de frutas, características como cor e tamanho podem ser mais úteis que, por exemplo, o preço, dependendo do contexto.

### Introdução ao Aprendizado de Máquina
Bhargava aborda como KNN é uma introdução ao aprendizado de máquina (ML), um campo que visa permitir que os sistemas aprendam com dados e melhorem com o tempo.

- **OCR (Reconhecimento Óptico de Caracteres):** KNN pode ser aplicado em OCR, comparando características de pixels em imagens de letras. A letra é identificada pelo caráter mais próximo entre as letras conhecidas no banco de dados.

- **Criando um Filtro de Spam:** Um filtro de spam baseado em KNN compara características de novos emails (como frequência de palavras suspeitas ou presença de links) com emails marcados como spam ou não. O algoritmo aprende a categorizar novos emails com base nas similaridades com emails anteriores.

- **Prevendo a Bolsa de Valores:** KNN também pode ser usado para regressão, como prever preços de ações. Utilizando dados históricos (como preço de fechamento de dias anteriores), o KNN tenta prever o próximo valor, baseando-se em padrões de preço e variação observados anteriormente.

---

### Resumo Final
O KNN é uma técnica simples, porém poderosa, para classificar e prever, sendo intuitiva para problemas onde é possível medir similaridades diretas entre dados. Ao escolher boas características, o algoritmo pode ser usado para diversas aplicações, desde filtros de spam a previsões financeiras e OCR.

---
### 1. Classificação: Laranja vs. Toranja

Vamos usar o KNN para classificar frutas com base em suas características, como diâmetro e peso. Neste exemplo, simularemos um pequeno conjunto de dados para diferenciar laranjas de toranjas.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

class KNNFrutas {
    // Estrutura para representar uma fruta
    public class Fruta {
        public string Nome { get; set; }
        public double Diametro { get; set; }
        public double Peso { get; set; }

        public Fruta(string nome, double diametro, double peso) {
            Nome = nome;
            Diametro = diametro;
            Peso = peso;
        }
    }

    // Função de distância Euclidiana entre duas frutas
    public static double Distancia(Fruta f1, Fruta f2) {
        return Math.Sqrt(Math.Pow(f1.Diametro - f2.Diametro, 2) + Math.Pow(f1.Peso - f2.Peso, 2));
    }

    // Função KNN para classificar a fruta desconhecida
    public static string ClassificarFruta(List<Fruta> frutas, Fruta desconhecida, int k) {
        var vizinhos = frutas.OrderBy(f => Distancia(f, desconhecida)).Take(k);
        var classificacao = vizinhos.GroupBy(f => f.Nome).OrderByDescending(g => g.Count()).FirstOrDefault();
        return classificacao?.Key;
    }

    static void Main() {
        var frutas = new List<Fruta> {
            new Fruta("Laranja", 4.5, 150),
            new Fruta("Laranja", 5.0, 160),
            new Fruta("Toranja", 7.0, 300),
            new Fruta("Toranja", 6.5, 290)
        };

        var desconhecida = new Fruta("", 5.5, 170);
        string resultado = ClassificarFruta(frutas, desconhecida, k: 3);

        Console.WriteLine($"A fruta desconhecida foi classificada como: {resultado}");
    }
}
```

**Explicação:**
- A função `Distancia` calcula a distância Euclidiana entre duas frutas.
- `ClassificarFruta` classifica uma fruta desconhecida, encontrando os `k` vizinhos mais próximos e determinando qual classe é a mais comum entre eles.
- No exemplo, estamos classificando uma fruta desconhecida com diâmetro de 5.5 e peso de 170.

---

### 2. Sistema de Recomendação

Agora, faremos um sistema de recomendação para sugerir filmes com base nas avaliações de outros usuários usando KNN.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

class KNNRecomendacao {
    public class Usuario {
        public string Nome { get; set; }
        public Dictionary<string, double> Avaliacoes { get; set; }

        public Usuario(string nome) {
            Nome = nome;
            Avaliacoes = new Dictionary<string, double>();
        }
    }

    // Função de distância Euclidiana entre dois usuários
    public static double Distancia(Usuario u1, Usuario u2) {
        double soma = 0;
        foreach (var filme in u1.Avaliacoes.Keys.Intersect(u2.Avaliacoes.Keys)) {
            soma += Math.Pow(u1.Avaliacoes[filme] - u2.Avaliacoes[filme], 2);
        }
        return Math.Sqrt(soma);
    }

    // Função para recomendar um filme baseado nos k vizinhos mais próximos
    public static List<string> RecomendarFilmes(List<Usuario> usuarios, Usuario usuarioAtual, int k) {
        var vizinhos = usuarios
            .Where(u => u != usuarioAtual)
            .OrderBy(u => Distancia(u, usuarioAtual))
            .Take(k);

        var recomendacoes = new Dictionary<string, double>();
        foreach (var vizinho in vizinhos) {
            foreach (var filme in vizinho.Avaliacoes.Keys.Except(usuarioAtual.Avaliacoes.Keys)) {
                if (!recomendacoes.ContainsKey(filme)) {
                    recomendacoes[filme] = vizinho.Avaliacoes[filme];
                }
            }
        }

        return recomendacoes.OrderByDescending(r => r.Value).Select(r => r.Key).ToList();
    }

    static void Main() {
        var usuarios = new List<Usuario> {
            new Usuario("Ana") { Avaliacoes = { { "Filme A", 4.0 }, { "Filme B", 5.0 } } },
            new Usuario("Beto") { Avaliacoes = { { "Filme A", 3.5 }, { "Filme C", 4.5 } } },
            new Usuario("Carla") { Avaliacoes = { { "Filme A", 4.5 }, { "Filme C", 5.0 }, { "Filme D", 4.0 } } }
        };

        var usuarioAtual = new Usuario("Voce") { Avaliacoes = { { "Filme A", 4.0 } } };
        List<string> filmesRecomendados = RecomendarFilmes(usuarios, usuarioAtual, k: 2);

        Console.WriteLine("Filmes recomendados:");
        foreach (var filme in filmesRecomendados) {
            Console.WriteLine(filme);
        }
    }
}
```

**Explicação:**
- `Distancia` calcula a distância entre dois usuários com base em filmes que ambos avaliaram.
- `RecomendarFilmes` sugere filmes que o usuário atual ainda não assistiu, baseando-se nos filmes que os vizinhos mais próximos avaliaram bem.

---

### 3. Filtro de Spam Básico

Por fim, um exemplo de como KNN poderia ser usado para classificar emails como "spam" ou "não-spam" com base na frequência de palavras-chave.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

class KNNSpamFilter {
    public class Email {
        public string Categoria { get; set; }
        public Dictionary<string, int> Caracteristicas { get; set; }

        public Email(string categoria) {
            Categoria = categoria;
            Caracteristicas = new Dictionary<string, int>();
        }
    }

    // Função de distância Euclidiana entre dois emails
    public static double Distancia(Email e1, Email e2) {
        double soma = 0;
        foreach (var palavra in e1.Caracteristicas.Keys.Union(e2.Caracteristicas.Keys)) {
            int freq1 = e1.Caracteristicas.ContainsKey(palavra) ? e1.Caracteristicas[palavra] : 0;
            int freq2 = e2.Caracteristicas.ContainsKey(palavra) ? e2.Caracteristicas[palavra] : 0;
            soma += Math.Pow(freq1 - freq2, 2);
        }
        return Math.Sqrt(soma);
    }

    // Classificar email desconhecido
    public static string ClassificarEmail(List<Email> emails, Email desconhecido, int k) {
        var vizinhos = emails.OrderBy(e => Distancia(e, desconhecido)).Take(k);
        var categoria = vizinhos.GroupBy(e => e.Categoria).OrderByDescending(g => g.Count()).FirstOrDefault();
        return categoria?.Key;
    }

    static void Main() {
        var emails = new List<Email> {
            new Email("spam") { Caracteristicas = { { "promoção", 2 }, { "desconto", 1 } } },
            new Email("spam") { Caracteristicas = { { "grátis", 1 }, { "promoção", 1 } } },
            new Email("não-spam") { Caracteristicas = { { "encontro", 1 }, { "documento", 2 } } }
        };

        var desconhecido = new Email("") { Caracteristicas = { { "promoção", 1 }, { "grátis", 1 } } };
        string resultado = ClassificarEmail(emails, desconhecido, k: 3);

        Console.WriteLine($"O email desconhecido foi classificado como: {resultado}");
    }
}
```

**Explicação:**
- `Distancia` calcula a similaridade entre dois emails com base na frequência de palavras.
- `ClassificarEmail` usa os `k` vizinhos mais próximos para classificar o email desconhecido como "spam" ou "não-spam".

---

Esses exemplos demonstram o uso prático do KNN em problemas de **classificação** e **sistemas de recomendação**, usando a linguagem C# para ilustrar o funcionamento do algoritmo.


### Citações
---------

