**Data:** 2024-10-29
**Livro:**  Entendendo Algoritmos - Um guia ilustrados para programadores e outros curiosos
**Autor**:  Aditya Y. Bhargava

**Tags:** #Algoritmos

### Conteúdo
----------------

No capítulo 4 do livro *Entendendo Algoritmos* de Aditya Y. Bhargava, o autor explica o algoritmo de Quicksort, um dos métodos mais rápidos e eficientes para ordenar listas. A abordagem envolve a técnica "Dividir para Conquistar" e detalha o cálculo de complexidade usando Notação Big O, comparando-o com o Merge Sort e explorando os cenários de desempenho médio e pior caso. Vamos revisar cada seção em detalhes:

### Dividir para Conquistar
A técnica "Dividir para Conquistar" é central no Quicksort. Ela consiste em:
1. Dividir o problema em subproblemas menores;
2. Resolver cada subproblema de forma independente;
3. Combinar as soluções dos subproblemas para resolver o problema maior.

No caso do Quicksort, a lista é dividida em duas partes, o que simplifica o processo de ordenação. O livro usa um exemplo de C# para ilustrar esse conceito.

```csharp
// Exemplo de dividir para conquistar
int Soma(int[] arr) {
    if (arr.Length == 0) return 0; // caso base
    return arr[0] + Soma(arr[1..]); // recursão
}
```

Neste exemplo, a soma de uma lista é realizada ao dividir o array e resolver o problema menor até que todos os elementos sejam somados.

### Quicksort
O Quicksort seleciona um elemento "pivô" e divide a lista entre itens menores e maiores que o pivô. Em seguida, aplica-se o Quicksort recursivamente nas sublistas. Essa abordagem recursiva é eficiente porque, com o pivô certo, o problema é rapidamente reduzido.

**Passo-a-passo do Quicksort em C#:**

1. Escolher um pivô (usualmente o primeiro elemento ou um aleatório).
2. Dividir a lista com base nesse pivô.
3. Recursivamente aplicar o Quicksort nas sublistas.

```csharp
void QuickSort(int[] arr, int left, int right) {
    if (left >= right) return;

    int pivotIndex = Partition(arr, left, right);
    QuickSort(arr, left, pivotIndex - 1);
    QuickSort(arr, pivotIndex + 1, right);
}

int Partition(int[] arr, int left, int right) {
    int pivot = arr[right];
    int i = left - 1;
    for (int j = left; j < right; j++) {
        if (arr[j] <= pivot) {
            i++;
            (arr[i], arr[j]) = (arr[j], arr[i]);
        }
    }
    (arr[i + 1], arr[right]) = (arr[right], arr[i + 1]);
    return i + 1;
}
```

### Notação Big O Revisada
Bhargava também revisa a notação Big O para analisar a complexidade do Quicksort e do Merge Sort. 

- **Quicksort** tem uma complexidade média de **O(n log n)**, pois em média a lista é dividida ao meio a cada iteração.
- **Merge Sort** também tem complexidade **O(n log n)**, mas é mais previsível, pois sempre divide a lista pela metade e depois combina as partes ordenadas.

### Merge Sort versus Quicksort
A diferença chave está no tipo de divisão:
- **Merge Sort** é estável e sua complexidade não muda, pois ele sempre divide e combina, independentemente da distribuição dos elementos.
- **Quicksort**, porém, pode ser mais rápido, pois não exige a fase de combinação, mas pode ser mais lento no pior caso (lista já ordenada ou pivô mal escolhido).

### Caso Médio versus Pior Caso
Bhargava finaliza explicando que o pior caso do Quicksort ocorre quando o pivô não divide a lista de forma equilibrada. Nesse caso, a complexidade se torna **O(n²)**, pois o algoritmo realiza divisões menos eficientes. Para evitar isso, é comum escolher o pivô de forma aleatória ou usar a técnica de "mediana de três".

### Conclusão
Quicksort é um algoritmo eficiente que se beneficia da técnica de dividir e conquistar, mas exige um bom controle do pivô para evitar seu pior caso.




### Citações
---------

