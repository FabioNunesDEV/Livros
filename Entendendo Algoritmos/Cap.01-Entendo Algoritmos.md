**Data:** 2024-08-26
**Livro:**  Entendendo Algoritmos - Um guia ilustrados para programadores e outros curiosos
**Autor**:  Aditya Y. Bhargava

**Tags:** #Algoritmos

### Conteúdo
----------------
Aqui está o resumo do primeiro capítulo do livro "Entendendo Algoritmos" de Aditya Y. Bhargava, abordando os tópicos que você mencionou:

#### 1. Introdução a Algoritmos
Este capítulo introduz o conceito de algoritmos e a sua importância no campo da programação e na solução de problemas de forma eficiente.

#### Introdução
O autor apresenta algoritmos como sequências de passos definidos para resolver problemas. Ele destaca que algoritmos eficientes são essenciais para o bom desempenho de programas.

#### O que você aprenderá sobre desempenho
Você aprenderá a avaliar o desempenho de algoritmos, compreendendo como o tempo de execução pode impactar a eficiência de um programa.

#### O que você aprenderá sobre a solução de problemas
O capítulo ensina como algoritmos ajudam a abordar problemas de maneira estruturada e eficaz, otimizando a solução.

#### Pesquisa Binária
A pesquisa binária é apresentada como um exemplo de algoritmo eficiente para encontrar um elemento em uma lista ordenada. O autor explica como o algoritmo reduz significativamente o número de comparações necessárias.

A pesquisa binária é um algoritmo eficiente para encontrar um item em uma lista ordenada. Ela funciona dividindo repetidamente a lista ao meio até encontrar o item desejado ou determinar que ele não está presente.

Aqui está um exemplo de código em C# que demonstra a pesquisa binária em uma lista de 100 nomes:

```csharp
using System;

class Program
{
    static void Main()
    {
        // Lista de 100 nomes ordenados alfabeticamente
        string[] nomes = new string[]
        {
            "Alice", "Amanda", "Ana", "Bruno", "Carlos", "Clara", "Daniel", "Diego", "Eduardo", "Elena",
            "Fabio", "Fernanda", "Gabriel", "Giovanna", "Gustavo", "Helena", "Igor", "Isabela", "João", "Julia",
            "Karina", "Larissa", "Leonardo", "Letícia", "Lucas", "Luiza", "Marcos", "Mariana", "Matheus", "Melissa",
            "Nicolas", "Patricia", "Paulo", "Pedro", "Rafael", "Renata", "Roberto", "Rodrigo", "Sabrina", "Samuel",
            "Sara", "Sophia", "Thais", "Thiago", "Vanessa", "Victor", "Vinicius", "Yasmin", "Zoe", // até aqui 50 nomes
            "Abigail", "Beatriz", "Camila", "Cristina", "Diana", "Emanuel", "Evelyn", "Fabiana", "Felipe", "Fernando",
            "Gabriela", "Giulia", "Guilherme", "Heloisa", "Henrique", "Isadora", "Jorge", "Júlio", "Kevin", "Larissa",
            "Lúcia", "Marcio", "Miguel", "Mirella", "Natália", "Olivia", "Pietro", "Rafaela", "Ricardo", "Sofia",
            "Stella", "Tatiana", "Tomás", "Valentina", "Vitor", "Wallace", "William", "Xavier", "Yago", "Zara" // até 100 nomes
        };

        // Nome que queremos encontrar
        string nomeProcurado = "Felipe";

        // Executar pesquisa binária
        int resultado = PesquisaBinaria(nomes, nomeProcurado);

        // Mostrar o resultado
        if (resultado != -1)
        {
            Console.WriteLine($"O nome '{nomeProcurado}' foi encontrado na posição {resultado}.");
        }
        else
        {
            Console.WriteLine($"O nome '{nomeProcurado}' não foi encontrado na lista.");
        }
    }

    static int PesquisaBinaria(string[] nomes, string nomeProcurado)
    {
        int esquerda = 0;
        int direita = nomes.Length - 1;

        while (esquerda <= direita)
        {
            int meio = (esquerda + direita) / 2;

            int comparacao = string.Compare(nomeProcurado, nomes[meio], StringComparison.OrdinalIgnoreCase);

            if (comparacao == 0)
            {
                return meio; // Nome encontrado
            }
            else if (comparacao < 0)
            {
                direita = meio - 1; // Procurar na metade esquerda
            }
            else
            {
                esquerda = meio + 1; // Procurar na metade direita
            }
        }

        return -1; // Nome não encontrado
    }
}
```

#### **Como funciona:**
1. **Lista ordenada**: A lista de nomes deve estar ordenada para que a pesquisa binária funcione.
2. **Divisão da lista**: O algoritmo começa dividindo a lista ao meio.
3. **Comparação**: Compara o nome procurado com o nome no meio da lista.
   - Se for igual, o nome foi encontrado.
   - Se for menor, o algoritmo continua a busca na metade esquerda.
   - Se for maior, continua na metade direita.
4. **Repetição**: Esse processo se repete até encontrar o nome ou até que a porção da lista a ser pesquisada seja nula.

Esse exemplo deve ajudar a entender o conceito de pesquisa binária! Se precisar de mais alguma explicação, é só avisar.

#### Uma maneira melhor de buscar
A pesquisa binária é comparada com a busca linear, mostrando como a primeira é muito mais eficiente, especialmente em grandes conjuntos de dados.

#### Tempo de Execução
O tempo de execução de um algoritmo é discutido como um critério crucial para avaliar sua eficiência. O autor apresenta a ideia de medir quanto tempo um algoritmo leva para ser executado com base no número de operações que realiza.

#### Notação Big O
A notação Big O é introduzida como uma maneira de expressar o tempo de execução de um algoritmo em termos de sua relação com o tamanho da entrada. Essa notação ajuda a entender a eficiência de algoritmos em cenários de pior caso.

#### Tempo de execução dos algoritmos cresce a taxas diferentes
O autor explica que diferentes algoritmos têm diferentes taxas de crescimento de tempo de execução, dependendo de como são projetados. Isso impacta diretamente sua eficiência em grandes volumes de dados.

#### Vendo diferentes tempos de execução Big O
Exemplos visuais são usados para ilustrar como o tempo de execução dos algoritmos pode variar e como a notação Big O pode ser usada para comparar essas variações.

#### A notação Big O estabelece o tempo de execução para a pior hipótese
O capítulo destaca que a notação Big O é usada para expressar o tempo de execução no pior cenário possível, o que é importante para garantir que o algoritmo seja confiável sob qualquer circunstância.

#### Alguns exemplos comuns de tempo de execução Big O
São apresentados exemplos comuns de notações Big O, como O(1), O(log n), O(n), O(n log n) e O(n²), que descrevem diferentes tipos de algoritmos e seus tempos de execução.

#### O Caixeiro-Viajante
O problema do Caixeiro-Viajante é mencionado como um exemplo de problema clássico que desafia algoritmos eficientes devido à sua complexidade.

#### Recapitulando
O capítulo termina com uma revisão dos principais conceitos discutidos, reforçando a importância de entender algoritmos, desempenho, e a notação Big O para a resolução eficiente de problemas.

### Citações
---------

