**Data:** 2024-11-01
**Livro:**  Entendendo Algoritmos - Um guia ilustrados para programadores e outros curiosos
**Autor**:  Aditya Y. Bhargava

**Tags:** #Algoritmos

### Conteúdo
----------------
No capítulo 8 de *Entendendo Algoritmos*, Aditya Bhargava apresenta os algoritmos gulosos, uma classe de algoritmos que fazem escolhas locais ótimas na esperança de encontrar uma solução globalmente ótima. Ele ilustra os algoritmos gulosos através de problemas práticos e discute a complexidade dos problemas NP-completos.

### O Problema do Cronograma da Sala de Aula
O problema do cronograma da sala de aula envolve maximizar o número de aulas que podem ser realizadas em uma única sala, dadas as restrições de tempo de cada aula. A abordagem gulosa para resolver isso é sempre escolher a aula com o tempo de término mais cedo entre as opções disponíveis, já que isso deixa o maior tempo livre possível para as próximas aulas.

Esse método permite encontrar uma solução que maximize o número de aulas sem conflitos. Embora o algoritmo guloso funcione bem nesse caso específico, nem sempre gera a melhor solução para todos os problemas.

### O Problema da Mochila
O problema da mochila (ou "knapsack problem") exige selecionar itens com pesos e valores diferentes para colocar em uma mochila de capacidade limitada, maximizando o valor total. Uma abordagem gulosa é selecionar itens com base na **relação valor/peso** mais alta, priorizando itens com o maior "valor por unidade de peso".

Embora essa abordagem funcione bem em uma versão *fracionária* do problema (onde é possível dividir itens), não garante uma solução ótima na versão *inteira* (onde os itens não podem ser divididos).

### O Problema da Cobertura de Conjuntos
Este problema é sobre escolher o menor conjunto possível de subconjuntos para cobrir todos os elementos de um conjunto principal. Por exemplo, imagine cobrir as cidades de um país usando o menor número de estações de rádio possível, onde cada estação cobre algumas cidades.

#### Algoritmo de Aproximação
Como encontrar uma solução exata é muito demorado para conjuntos grandes, um **algoritmo de aproximação guloso** é usado para encontrar uma solução "boa o suficiente" rapidamente. A abordagem é:
1. Escolher a estação que cobre o maior número de cidades não cobertas ainda.
2. Adicionar a estação escolhida ao conjunto de solução.
3. Repetir até que todas as cidades estejam cobertas.

Esse método pode não ser perfeito, mas gera uma solução próxima da ótima e é eficiente para problemas grandes.

### Problemas NP-Completos
O livro também discute problemas NP-completos, uma classe de problemas muito difíceis de resolver de forma exata. Para problemas NP-completos, como o problema do caixeiro-viajante, não se conhece algoritmos eficientes que garantam a melhor solução em um tempo viável para grandes entradas.

#### Caixeiro-Viajante, Passo a Passo
No problema do caixeiro-viajante, o objetivo é encontrar o menor caminho que visite todas as cidades exatamente uma vez e volte ao ponto de partida. A abordagem "força bruta" testa todas as permutações possíveis de rotas, mas isso se torna impraticável para muitas cidades, pois o número de combinações cresce exponencialmente.

#### Como Faço para Saber se um Problema é NP-Completo?
Bhargava oferece alguns critérios para identificar problemas NP-completos:
1. **Nenhuma solução rápida conhecida**: Se não há algoritmo eficiente para resolver o problema.
2. **Fácil de verificar**: Se é fácil verificar se uma solução proposta é correta.
3. **Transformável**: Se o problema pode ser transformado em outro problema NP-completo.

### Conclusão
Algoritmos gulosos são ferramentas poderosas para resolver problemas com soluções aproximadas de forma rápida, mas não garantem sempre a solução ótima. Em problemas NP-completos, onde as soluções exatas são inviáveis para grandes instâncias, algoritmos de aproximação como os gulosos fornecem alternativas práticas.






### Exemplos de Código

Claro! Abaixo estão exemplos em C# para ilustrar cada um dos algoritmos gulosos discutidos no capítulo 8 de *Entendendo Algoritmos*.

### 1. Problema do Cronograma da Sala de Aula
A solução gulosa para o problema de cronograma é escolher a aula com o horário de término mais cedo entre as disponíveis. Isso ajuda a maximizar o número de aulas sem sobreposição.

```csharp
using System;
using System.Collections.Generic;

class CronogramaAulas {
    public class Aula {
        public int Inicio { get; set; }
        public int Fim { get; set; }
    }

    public static List<Aula> MaximoAulas(List<Aula> aulas) {
        aulas.Sort((a, b) => a.Fim.CompareTo(b.Fim)); // Ordena por horário de término

        List<Aula> resultado = new();
        int horarioFimUltimaAula = 0;

        foreach (var aula in aulas) {
            if (aula.Inicio >= horarioFimUltimaAula) {
                resultado.Add(aula);
                horarioFimUltimaAula = aula.Fim;
            }
        }

        return resultado;
    }

    static void Main() {
        var aulas = new List<Aula> {
            new Aula { Inicio = 9, Fim = 10 },
            new Aula { Inicio = 9, Fim = 11 },
            new Aula { Inicio = 10, Fim = 12 },
            new Aula { Inicio = 11, Fim = 13 }
        };

        var maxAulas = MaximoAulas(aulas);
        Console.WriteLine("Máximo de aulas agendadas:");
        foreach (var aula in maxAulas) {
            Console.WriteLine($"Início: {aula.Inicio}, Fim: {aula.Fim}");
        }
    }
}
```

### 2. Problema da Mochila (Versão Fracionária)
No problema fracionário da mochila, selecionamos itens com base na relação valor/peso mais alta.

```csharp
using System;
using System.Collections.Generic;

class Item {
    public double Peso { get; set; }
    public double Valor { get; set; }

    public double ValorPorPeso => Valor / Peso;
}

class MochilaFracionaria {
    public static double Mochila(List<Item> itens, double capacidade) {
        itens.Sort((a, b) => b.ValorPorPeso.CompareTo(a.ValorPorPeso)); // Ordena por valor/peso

        double valorTotal = 0;
        foreach (var item in itens) {
            if (capacidade >= item.Peso) {
                valorTotal += item.Valor;
                capacidade -= item.Peso;
            } else {
                valorTotal += item.ValorPorPeso * capacidade;
                break;
            }
        }
        return valorTotal;
    }

    static void Main() {
        var itens = new List<Item> {
            new Item { Peso = 10, Valor = 60 },
            new Item { Peso = 20, Valor = 100 },
            new Item { Peso = 30, Valor = 120 }
        };

        double capacidade = 50;
        Console.WriteLine($"Valor máximo na mochila: {Mochila(itens, capacidade)}");
    }
}
```

### 3. Problema da Cobertura de Conjuntos
Neste exemplo, selecionamos o menor número possível de estações que cobre todas as cidades.

```csharp
using System;
using System.Collections.Generic;

class CoberturaConjuntos {
    public static List<string> CobrirCidades(Dictionary<string, HashSet<string>> estacoes, HashSet<string> cidadesNecessarias) {
        List<string> estacoesSelecionadas = new();
        
        while (cidadesNecessarias.Count > 0) {
            string melhorEstacao = null;
            var cidadesCobertas = new HashSet<string>();

            foreach (var (estacao, cidades) in estacoes) {
                var cobertura = new HashSet<string>(cidades);
                cobertura.IntersectWith(cidadesNecessarias);

                if (cobertura.Count > cidadesCobertas.Count) {
                    melhorEstacao = estacao;
                    cidadesCobertas = cobertura;
                }
            }

            if (melhorEstacao != null) {
                estacoesSelecionadas.Add(melhorEstacao);
                cidadesNecessarias.ExceptWith(cidadesCobertas);
            }
        }

        return estacoesSelecionadas;
    }

    static void Main() {
        var estacoes = new Dictionary<string, HashSet<string>> {
            { "Estacao1", new HashSet<string> { "Cidade1", "Cidade2", "Cidade3" } },
            { "Estacao2", new HashSet<string> { "Cidade2", "Cidade4" } },
            { "Estacao3", new HashSet<string> { "Cidade4", "Cidade5" } },
            { "Estacao4", new HashSet<string> { "Cidade1", "Cidade5" } }
        };

        var cidadesNecessarias = new HashSet<string> { "Cidade1", "Cidade2", "Cidade3", "Cidade4", "Cidade5" };
        var resultado = CobrirCidades(estacoes, cidadesNecessarias);

        Console.WriteLine("Estações selecionadas:");
        foreach (var estacao in resultado) {
            Console.WriteLine(estacao);
        }
    }
}
```

### 4. Caixeiro-Viajante (Força Bruta para Pequenas Entradas)
O problema do Caixeiro-Viajante é NP-completo, mas podemos resolver instâncias pequenas com força bruta. Aqui, mostramos todas as permutações para encontrar o menor caminho possível.

```csharp
using System;
using System.Collections.Generic;

class CaixeiroViajante {
    public static int DistanciaMinima = int.MaxValue;

    public static void Permutar(List<int> cidades, int[,] distancias, int inicio) {
        if (inicio == cidades.Count - 1) {
            int distanciaTotal = 0;
            for (int i = 0; i < cidades.Count - 1; i++) {
                distanciaTotal += distancias[cidades[i], cidades[i + 1]];
            }
            distanciaTotal += distancias[cidades[cidades.Count - 1], cidades[0]];

            if (distanciaTotal < DistanciaMinima) {
                DistanciaMinima = distanciaTotal;
            }
        } else {
            for (int i = inicio; i < cidades.Count; i++) {
                (cidades[inicio], cidades[i]) = (cidades[i], cidades[inicio]);
                Permutar(cidades, distancias, inicio + 1);
                (cidades[inicio], cidades[i]) = (cidades[i], cidades[inicio]);
            }
        }
    }

    static void Main() {
        int[,] distancias = {
            { 0, 10, 15, 20 },
            { 10, 0, 35, 25 },
            { 15, 35, 0, 30 },
            { 20, 25, 30, 0 }
        };
        
        List<int> cidades = new() { 0, 1, 2, 3 };
        Permutar(cidades, distancias, 0);

        Console.WriteLine($"Menor distância: {DistanciaMinima}");
    }
}
```

### Conclusão
Cada um desses exemplos de algoritmos gulosos oferece uma abordagem prática para resolver problemas específicos, mas com a ressalva de que nem sempre produzem a solução ótima. No caso de problemas NP-completos como o Caixeiro-Viajante, a força bruta é viável apenas para pequenas entradas, ilustrando a dificuldade de resolver tais problemas conforme aumentam de tamanho.

### Citações
---------

