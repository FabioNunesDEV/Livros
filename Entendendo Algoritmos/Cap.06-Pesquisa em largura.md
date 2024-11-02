**Data:** 2024-10-29
**Livro:**  Entendendo Algoritmos - Um guia ilustrados para programadores e outros curiosos
**Autor**:  Aditya Y. Bhargava

**Tags:** #Algoritmos


### Conteúdo
----------------
No capítulo 6 de *Entendendo Algoritmos*, Aditya Bhargava explora a pesquisa em largura (BFS, do inglês *Breadth-First Search*), uma técnica de busca usada em grafos para encontrar o caminho mínimo entre dois pontos. O capítulo também introduz grafos, descreve como representá-los e como implementar a pesquisa em largura.

### Introdução a Grafos
Grafos são estruturas de dados compostas por **nós** (ou **vértices**) e **arestas**. Cada nó representa um elemento, enquanto as arestas representam a relação ou caminho entre esses elementos. Grafos são úteis para modelar redes como mapas, relações sociais e estruturas de dependência.

### O que é um Grafo?
Um grafo consiste em um conjunto de nós conectados por arestas. Ele pode ser:
- **Dirigido**, se as arestas tiverem direção (como seguir de A para B, mas não de B para A).
- **Não-dirigido**, se as arestas permitirem movimentação em ambas as direções.

### Pesquisa em Largura
A pesquisa em largura é uma técnica para explorar os nós de um grafo nível a nível. É útil para encontrar o **caminho mínimo** entre dois pontos (menor número de arestas entre um nó inicial e um nó de destino) e também pode verificar se existe uma conexão entre dois nós.

#### Encontrando o Caminho Mínimo
A pesquisa em largura encontra o caminho mínimo ao explorar todos os nós em uma ordem crescente de distância a partir do nó inicial. Isso garante que o primeiro caminho encontrado entre dois nós é o mais curto em termos de número de arestas.

#### Filas
A BFS usa uma **fila** para gerenciar a ordem dos nós a serem visitados. Ao adicionar nós vizinhos à fila, BFS visita os nós em um nível antes de prosseguir para o próximo nível. Essa abordagem garante que encontramos o caminho mínimo primeiro.

### Implementando o Grafo
Um grafo pode ser implementado em C# usando uma lista de adjacências, onde cada nó tem uma lista de seus vizinhos:

```csharp
using System.Collections.Generic;

class Grafo {
    private Dictionary<string, List<string>> adjacencias = new();

    public void AdicionarAresta(string origem, string destino) {
        if (!adjacencias.ContainsKey(origem)) {
            adjacencias[origem] = new List<string>();
        }
        adjacencias[origem].Add(destino);
    }

    public List<string> ObterVizinhos(string no) {
        return adjacencias.ContainsKey(no) ? adjacencias[no] : new List<string>();
    }
}
```

### Implementando o Algoritmo
Para implementar a pesquisa em largura, usamos uma fila para armazenar nós a serem visitados e um conjunto para rastrear os nós já visitados, evitando ciclos. 

Aqui está uma implementação básica de BFS em C# para encontrar o caminho mais curto em um grafo:

```csharp
using System;
using System.Collections.Generic;

class PesquisaLargura {
    public static bool Buscar(Grafo grafo, string inicio, string destino) {
        Queue<string> fila = new Queue<string>();
        HashSet<string> visitados = new HashSet<string>();

        fila.Enqueue(inicio);
        visitados.Add(inicio);

        while (fila.Count > 0) {
            string atual = fila.Dequeue();
            if (atual == destino) return true;

            foreach (string vizinho in grafo.ObterVizinhos(atual)) {
                if (!visitados.Contains(vizinho)) {
                    fila.Enqueue(vizinho);
                    visitados.Add(vizinho);
                }
            }
        }
        return false;
    }
}
```

#### Tempo de Execução
O tempo de execução da BFS é **O(V + E)**, onde:
- **V** representa o número de vértices (nós).
- **E** representa o número de arestas.

Isso ocorre porque cada nó e cada aresta são visitados uma única vez. Esse desempenho é eficiente para encontrar caminhos mínimos em grafos não ponderados.

### Conclusão
A pesquisa em largura é uma técnica fundamental para grafos, permitindo a descoberta do caminho mínimo em termos de número de arestas. Ela usa uma fila para controlar o fluxo da busca e é ideal para resolver problemas de conexão e caminho mínimo em redes ou mapas.

### Citações
---------

