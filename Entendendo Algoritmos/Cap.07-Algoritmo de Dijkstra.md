**Data:** 2024-10-31
**Livro:**  Entendendo Algoritmos - Um guia ilustrados para programadores e outros curiosos
**Autor**:  Aditya Y. Bhargava

**Tags:** #Algoritmos

### Conteúdo
----------------
No capítulo 7 de *Entendendo Algoritmos*, Aditya Bhargava explica o algoritmo de Dijkstra, uma técnica de busca em grafos que encontra o caminho mais curto (ou seja, com menor custo total) entre dois pontos em um grafo ponderado. A seguir, exploramos como o algoritmo funciona, sua terminologia e os principais passos para implementá-lo.

### Trabalhando com o Algoritmo de Dijkstra
O algoritmo de Dijkstra é ideal para grafos com arestas ponderadas positivas, onde se deseja encontrar o caminho mais curto em termos de custo. Ele é utilizado em aplicações como navegação por GPS, otimização de rotas e em redes de computadores, onde o objetivo é minimizar o tempo ou a distância entre pontos.

O Dijkstra funciona expandindo o nó com o menor custo conhecido, atualizando continuamente o custo para alcançar seus vizinhos até que todos os nós tenham sido visitados e o menor caminho para cada nó tenha sido determinado.

### Terminologia
O capítulo introduz alguns termos chave:
- **Grafo Ponderado**: Um grafo onde as arestas têm "pesos" que representam o custo de se mover entre dois nós.
- **Tabela de Custos**: Uma estrutura que armazena o custo mínimo atual para cada nó.
- **Tabela de Pais**: Armazena o nó anterior no caminho mais curto para cada nó, o que permite reconstruir o caminho final quando o destino é alcançado.

### Adquirindo um Piano
O autor usa um exemplo prático de “adquirir um piano” para ilustrar como Dijkstra funciona. Imagine precisar transportar um piano entre diferentes pontos, e cada aresta no grafo representa uma rota com um custo associado (tempo, esforço, ou dinheiro). O objetivo é encontrar o caminho mais barato para transportar o piano.

### Arestas com Pesos Negativos
O algoritmo de Dijkstra não lida bem com **arestas de peso negativo**, pois esses pesos podem causar um ciclo de diminuição infinita, levando o algoritmo a resultados incorretos. Nesses casos, Bhargava menciona que o **algoritmo de Bellman-Ford** é uma alternativa adequada para grafos com pesos negativos.

### Implementação
A implementação do algoritmo de Dijkstra envolve:
1. **Inicializar** a tabela de custos com infinito para todos os nós, exceto o nó inicial (com custo zero).
2. **Explorar** o nó com o menor custo atual, atualizando os custos para alcançar seus vizinhos.
3. **Atualizar** a tabela de pais para cada vizinho cujo custo foi reduzido, para registrar o caminho mínimo.
4. **Repetir** até que todos os nós tenham sido processados.

A seguir, uma implementação básica do Dijkstra em C#:

```csharp
using System;
using System.Collections.Generic;

class Dijkstra {
    public static Dictionary<string, int> Executar(Grafo grafo, string inicio) {
        var custos = new Dictionary<string, int>();
        var pais = new Dictionary<string, string>();
        var visitados = new HashSet<string>();

        // Inicialização dos custos e pais
        foreach (var no in grafo.ObterNos()) {
            custos[no] = int.MaxValue;
            pais[no] = null;
        }
        custos[inicio] = 0;

        string noAtual = EncontrarMenorCusto(custos, visitados);
        while (noAtual != null) {
            int custo = custos[noAtual];
            foreach (var vizinho in grafo.ObterVizinhos(noAtual)) {
                int novoCusto = custo + grafo.ObterCusto(noAtual, vizinho);
                if (novoCusto < custos[vizinho]) {
                    custos[vizinho] = novoCusto;
                    pais[vizinho] = noAtual;
                }
            }
            visitados.Add(noAtual);
            noAtual = EncontrarMenorCusto(custos, visitados);
        }

        return custos;
    }

    private static string EncontrarMenorCusto(Dictionary<string, int> custos, HashSet<string> visitados) {
        int menorCusto = int.MaxValue;
        string menorNo = null;
        foreach (var no in custos.Keys) {
            int custo = custos[no];
            if (custo < menorCusto && !visitados.Contains(no)) {
                menorCusto = custo;
                menorNo = no;
            }
        }
        return menorNo;
    }
}
```

Essa implementação considera cada nó e seus vizinhos, atualizando os custos conforme encontra um caminho mais curto. A função `EncontrarMenorCusto` retorna o próximo nó de menor custo a ser explorado.

### Conclusão
O algoritmo de Dijkstra é uma ferramenta poderosa para encontrar o caminho mais curto em grafos com pesos positivos. Ele utiliza uma abordagem sistemática de atualização de custos e tabelas de pais para registrar o caminho ideal. A limitação principal é que não pode lidar com arestas de peso negativo, mas dentro dessas restrições, ele oferece uma solução eficiente e robusta.

### Citações
---------

