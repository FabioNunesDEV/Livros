**Data:** 2024-09-06
**Livro:**  Entendendo Algoritmos - Um guia ilustrados para programadores e outros curiosos
**Autor**:  Aditya Y. Bhargava

**Tags:** #Algoritmos

### Conteúdo
----------------
Aqui está um resumo do Capítulo 2 do livro **"Entendendo Algoritmos"** de Aditya Y. Bhargava, abordando os tópicos que você mencionou:

#### Como funciona a memória
O capítulo começa explicando como a memória é organizada em um computador. A memória é composta de muitos endereços, cada um armazenando um valor. Arrays e listas encadeadas, duas estruturas de dados fundamentais, utilizam a memória de maneiras diferentes. Arrays ocupam blocos contínuos de memória, enquanto listas encadeadas utilizam blocos de memória não contíguos, onde cada elemento aponta para o próximo.

#### Arrays e listas encadeadas
Essa seção compara e contrasta arrays e listas encadeadas. Arrays têm acesso rápido aos elementos porque os endereços de memória são contínuos, mas inserções e deleções são lentas, pois pode ser necessário mover muitos elementos. Listas encadeadas, por outro lado, permitem inserções e deleções rápidas, mas o acesso aos elementos é mais lento, pois é necessário percorrer a lista.

#### Listas encadeadas
Listas encadeadas consistem em nós, onde cada nó contém um valor e um ponteiro para o próximo nó. Elas permitem inserções e deleções eficientes, especialmente no início ou no meio da lista, mas o acesso a um elemento específico exige percorrer a lista desde o início.

#### Arrays
Arrays armazenam elementos em blocos de memória contíguos, permitindo acesso rápido a qualquer elemento usando um índice. No entanto, adicionar ou remover elementos no meio de um array é ineficiente, pois pode exigir o deslocamento de muitos elementos.

#### Terminologia
O livro define termos importantes, como "índice", que é a posição de um elemento em um array, e "nó", que é um elemento de uma lista encadeada. Ele também explica a diferença entre tempo de execução \(O(1)\) (constante) e \(O(n)\) (linear), enfatizando como essas medidas afetam o desempenho de operações em arrays e listas encadeadas.

#### Inserindo algo no meio da lista
Inserir um elemento no meio de uma lista encadeada é eficiente. Basta alterar os ponteiros de dois nós para incluir o novo elemento. Em arrays, isso é mais complicado, pois é necessário deslocar todos os elementos à direita do ponto de inserção, resultando em um tempo de execução \(O(n)\).

#### Deleções
Remover elementos de uma lista encadeada também é eficiente, pois envolve apenas a modificação dos ponteiros. Em arrays, a remoção exige o deslocamento dos elementos para preencher o espaço vazio, o que, novamente, resulta em um tempo de execução \(O(n)\).

#### Ordenação por seleção
O capítulo também aborda a ordenação por seleção, um algoritmo simples que organiza os elementos de um array encontrando repetidamente o menor (ou maior) elemento e movendo-o para a posição correta. Embora seja fácil de entender, sua complexidade é \(O(n^2)\), o que o torna ineficiente para grandes conjuntos de dados.

#### Recapitulando
O capítulo termina com um resumo dos principais pontos abordados: a diferença entre arrays e listas encadeadas, as vantagens e desvantagens de cada uma em diferentes operações (inserção, deleção, acesso), e uma introdução à ordenação por seleção. A compreensão desses conceitos é essencial para escolher a estrutura de dados e o algoritmo mais apropriado para diferentes situações.

Esse capítulo é fundamental para entender como escolher e usar as estruturas de dados básicas em diferentes cenários, considerando a eficiência e a necessidade do problema em questão.
### Citações
---------

