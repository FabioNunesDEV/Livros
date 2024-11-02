**Data:** 2024-11-01
**Livro:**  Entendendo Algoritmos - Um guia ilustrados para programadores e outros curiosos
**Autor**:  Aditya Y. Bhargava

**Tags:** #Algoritmos
### Conteúdo
----------------
No capítulo 9 de *Entendendo Algoritmos*, Aditya Bhargava apresenta a **programação dinâmica (PD)**, uma técnica para resolver problemas complexos quebrando-os em subproblemas e utilizando soluções anteriores para otimizar o processo. A PD é especialmente útil para problemas de otimização, como o **problema da mochila** e o **problema da maior substring comum**, pois evita o recalculo desnecessário, economizando tempo e recursos.

### O Problema da Mochila
No problema da mochila, temos uma mochila com uma capacidade de peso e um conjunto de itens, cada um com seu peso e valor. O objetivo é maximizar o valor total dos itens na mochila sem ultrapassar sua capacidade.

#### Solução Simples
Uma solução de força bruta testa todas as combinações possíveis, calculando o valor total para cada uma e selecionando a de maior valor. Essa abordagem é ineficiente para grandes quantidades de itens, pois a quantidade de combinações cresce exponencialmente.

#### Programação Dinâmica
A PD usa uma tabela para armazenar as melhores soluções para subproblemas menores e, então, combina esses resultados para resolver o problema original. No caso do problema da mochila, a tabela armazena o valor máximo possível para cada capacidade de peso até a capacidade total da mochila, considerando progressivamente cada item.

### Perguntas Frequentes sobre o Problema da Mochila
Bhargava explora várias nuances da PD aplicada ao problema da mochila:

- **O que acontece se você adicionar um item?**  
  A adição de um item altera a tabela, pois novos valores podem surgir ao incluir o novo item nas combinações já existentes.

- **O que acontece se você modificar a ordem das linhas?**  
  Mudar a ordem não altera o resultado, pois cada linha representa um item específico e é processada de forma independente.

- **É possível preencher a tabela a partir das colunas, em vez de a partir das linhas?**  
  Sim, mas preencher por linhas é mais intuitivo, pois cada linha completa considera a inclusão ou não de um item específico.

- **O que acontece se você adicionar um item menor?**  
  Itens menores tendem a caber em mais combinações, impactando os valores em mais posições da tabela e potencialmente aumentando o valor total.

- **Você consegue roubar frações de um item?**  
  A versão padrão do problema da mochila trata itens como indivisíveis; no entanto, existe uma variante “fracionária” onde itens podem ser divididos.

- **Otimizando seu itinerário de viagem**  
  Problemas de otimização de itinerário podem ser resolvidos com programação dinâmica quando envolvem múltiplas paradas e decisões interdependentes, semelhante à escolha de itens na mochila.

- **Lidando com itens com interdependência**  
  Se itens têm dependências, como um item que só pode ser incluído se outro estiver, isso requer modificação do algoritmo para refletir tais restrições.

- **É possível que a solução requeira mais de dois subproblemas?**  
  Sim, problemas podem exigir a combinação de mais de dois subproblemas, embora no caso da mochila, tipicamente só são necessários dois.

- **É possível que a melhor solução não utilize a capacidade total da mochila?**  
  Sim, às vezes a solução ideal não preenche completamente a mochila, mas maximiza o valor total dos itens selecionados.

### Maior Substring Comum
Além do problema da mochila, Bhargava explora o problema da **maior substring comum**, onde o objetivo é encontrar a maior sequência de caracteres compartilhada entre duas strings.

#### Criando a Tabela
A tabela armazena os comprimentos das substrings comuns para cada par de caracteres entre as duas strings. Cada célula contém o tamanho da maior substring comum até aquela posição.

#### Preenchendo a Tabela
A tabela é preenchida seguindo uma regra: se os caracteres das duas strings são iguais, o valor da célula é incrementado a partir do valor da célula anterior (representando a substring até o caractere anterior). Se os caracteres são diferentes, o valor é zero, pois uma nova substring deve começar.

#### A Solução
A maior substring comum é o maior valor presente na tabela. Esse valor representa a posição em que as duas strings têm a maior sequência de caracteres contínuos idênticos.

#### Maior Subsequência Comum
Para a **maior subsequência comum**, o objetivo é encontrar a sequência mais longa de caracteres que aparecem na mesma ordem em ambas as strings, mas não necessariamente consecutivos.

#### Maior Subsequência Comum - Solução
A tabela é preenchida de forma semelhante ao problema da maior substring comum, mas aqui, se os caracteres são iguais, incrementamos o valor da célula anterior. Se são diferentes, escolhemos o maior valor entre as células adjacentes para continuar o cálculo. 

### Conclusão
A programação dinâmica permite otimizar problemas complexos, como o da mochila e da maior substring ou subsequência comum, aproveitando subproblemas resolvidos para construir uma solução de maneira eficiente. Essa técnica é essencial para problemas que têm estrutura repetitiva e são altamente dependentes de valores anteriores.


---

### 1. Problema da Mochila (Versão Indivisível)
O problema da mochila com programação dinâmica armazena os valores máximos possíveis para cada capacidade de peso, considerando cada item progressivamente.

```csharp
using System;

class MochilaPD {
    public static int Mochila(int capacidade, int[] pesos, int[] valores) {
        int n = pesos.Length;
        int[,] tabela = new int[n + 1, capacidade + 1];

        for (int i = 1; i <= n; i++) {
            for (int j = 0; j <= capacidade; j++) {
                if (pesos[i - 1] <= j) {
                    tabela[i, j] = Math.Max(tabela[i - 1, j], valores[i - 1] + tabela[i - 1, j - pesos[i - 1]]);
                } else {
                    tabela[i, j] = tabela[i - 1, j];
                }
            }
        }
        return tabela[n, capacidade];
    }

    static void Main() {
        int[] pesos = { 1, 3, 4, 5 };
        int[] valores = { 1, 4, 5, 7 };
        int capacidade = 7;

        Console.WriteLine($"Valor máximo possível: {Mochila(capacidade, pesos, valores)}");
    }
}
```

**Explicação:**
- `tabela[i, j]` armazena o valor máximo possível usando os primeiros `i` itens e uma capacidade `j`.
- Se o peso do item atual (`pesos[i - 1]`) é menor ou igual à capacidade atual (`j`), escolhemos o maior valor entre incluir o item atual e não incluí-lo.
- Caso contrário, o valor de `tabela[i, j]` é o mesmo que o valor de `tabela[i - 1, j]`, representando a solução sem o item atual.

---

### 2. Maior Substring Comum
Esse problema visa encontrar a maior sequência de caracteres contínua entre duas strings. 

```csharp
using System;

class MaiorSubstringComum {
    public static int MaiorSubstring(string s1, string s2) {
        int m = s1.Length;
        int n = s2.Length;
        int[,] tabela = new int[m + 1, n + 1];
        int maxComprimento = 0;

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (s1[i - 1] == s2[j - 1]) {
                    tabela[i, j] = tabela[i - 1, j - 1] + 1;
                    maxComprimento = Math.Max(maxComprimento, tabela[i, j]);
                } else {
                    tabela[i, j] = 0;  // Reinicia a contagem se os caracteres não coincidem
                }
            }
        }
        return maxComprimento;
    }

    static void Main() {
        string s1 = "ABABC";
        string s2 = "BABC";

        Console.WriteLine($"Maior comprimento de substring comum: {MaiorSubstring(s1, s2)}");
    }
}
```

**Explicação:**
- `tabela[i, j]` armazena o comprimento da maior substring comum até a posição `i` de `s1` e `j` de `s2`.
- Quando os caracteres das strings coincidem, a contagem é incrementada; quando não coincidem, é reiniciada a contagem (valor `0`).
- `maxComprimento` guarda o valor máximo encontrado, que é o comprimento da maior substring comum.

---

### 3. Maior Subsequência Comum
No problema da maior subsequência comum, buscamos a sequência mais longa de caracteres na mesma ordem em ambas as strings, mas que não precisa ser contínua.

```csharp
using System;

class MaiorSubsequenciaComum {
    public static int MaiorSubsequencia(string s1, string s2) {
        int m = s1.Length;
        int n = s2.Length;
        int[,] tabela = new int[m + 1, n + 1];

        for (int i = 1; i <= m; i++) {
            for (int j = 1; j <= n; j++) {
                if (s1[i - 1] == s2[j - 1]) {
                    tabela[i, j] = tabela[i - 1, j - 1] + 1;
                } else {
                    tabela[i, j] = Math.Max(tabela[i - 1, j], tabela[i, j - 1]);
                }
            }
        }
        return tabela[m, n];
    }

    static void Main() {
        string s1 = "ABCBDAB";
        string s2 = "BDCAB";

        Console.WriteLine($"Comprimento da maior subsequência comum: {MaiorSubsequencia(s1, s2)}");
    }
}
```

**Explicação:**
- A `tabela[i, j]` representa o comprimento da maior subsequência comum até a posição `i` de `s1` e `j` de `s2`.
- Se os caracteres de `s1` e `s2` na posição `i-1` e `j-1` coincidem, incrementamos a contagem, somando `1` à solução do subproblema anterior.
- Caso contrário, tomamos o valor máximo entre excluir o caractere atual de `s1` ou de `s2`.

---

Esses exemplos cobrem as abordagens de programação dinâmica para problemas comuns e ilustram como subproblemas resolvidos em uma tabela evitam o recalculo e garantem eficiência na solução final. Esses métodos são altamente aplicáveis em problemas de otimização e subsequência, que são comuns em algoritmos complexos e processamento de strings.
### Citações
---------

