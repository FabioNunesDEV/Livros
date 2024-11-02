**Data:** 2024-09-11
**Livro:**  Entendendo Algoritmos - Um guia ilustrados para programadores e outros curiosos
**Autor**:  Aditya Y. Bhargava

**Tags:** #Algoritmos

### Conteúdo
----------------
#### Recursão
A **recursão** ocorre quando uma função chama a si mesma para resolver um problema. Essa técnica é útil quando o problema pode ser quebrado em pedaços menores e similares. Um exemplo clássico é o cálculo de fatorial, onde o fatorial de um número `n` é o produto de `n` pelos fatoriais de seus antecessores até `n = 1`.

#### Caso-base e caso recursivo
Para que uma função recursiva não entre em um loop infinito, é necessário definir:
- **Caso-base**: É a condição que encerra a recursão. Ele define o ponto em que a função não chama mais a si mesma, fornecendo uma solução direta.
- **Caso recursivo**: É a situação em que a função continua chamando a si mesma com uma versão reduzida do problema original.

Um exemplo dado no livro é o de calcular o fatorial de um número. O caso-base seria quando `n = 1`, que retorna 1, e o caso recursivo é a multiplicação do número atual pelo fatorial de `n-1`.

#### A pilha
A **pilha** é uma estrutura de dados que funciona com o princípio "último a entrar, primeiro a sair" (*Last In, First Out* - LIFO). No contexto de algoritmos recursivos, ela é fundamental para armazenar as chamadas de função.

#### A pilha de chamada
A **pilha de chamada** é onde as funções são armazenadas enquanto estão sendo executadas. Cada vez que uma função chama outra (ou a si mesma, no caso de recursão), uma nova entrada é adicionada à pilha. Quando uma função termina, sua entrada é removida da pilha, e o controle é devolvido à função anterior.

#### A pilha de chamada com recursão
Quando uma função recursiva é chamada, cada nova chamada adiciona uma nova camada à pilha de chamadas, e isso continua até atingir o caso-base. Uma vez que o caso-base é alcançado, as funções começam a ser removidas da pilha conforme suas execuções são concluídas, resolvendo os subproblemas até chegar à solução final.

#### Recapitulando
O capítulo fecha com uma revisão dos conceitos:
- A recursão envolve dividir problemas em subproblemas menores até que eles se tornem simples o suficiente para serem resolvidos diretamente (caso-base).
- A pilha de chamadas ajuda a controlar o fluxo de execução de funções recursivas, permitindo que cada chamada seja armazenada e resolvida na ordem correta.
  
O autor destaca como a recursão e a pilha estão intrinsecamente conectadas, e entender essas bases é fundamental para resolver problemas complexos de forma elegante.

---

Esse resumo abrange os principais pontos que você mencionou! Se quiser mais detalhes de algum tópico específico, posso aprofundar mais.




### Citações
---------
[Lógica de Programação - Recursividade](https://www.youtube.com/watch?v=M7c-m2xN9FQ&t=105s)
