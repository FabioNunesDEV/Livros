**Data:** 2024-10-29
**Livro:**  Entendendo Algoritmos - Um guia ilustrados para programadores e outros curiosos
**Autor**:  Aditya Y. Bhargava

**Tags:** #Algoritmos

### Conteúdo
----------------
No capítulo 5 de *Entendendo Algoritmos*, Aditya Bhargava introduz as tabelas hash, uma estrutura de dados eficiente para pesquisas e armazenamento rápido de dados. Vamos examinar os principais conceitos, como funções hash, usos práticos, colisões e desempenho, conforme apresentados no livro.

### Funções Hash
Uma função hash transforma uma entrada (como uma string) em um número inteiro, chamado índice. Esse índice é então usado para localizar o valor em uma tabela (array). A ideia é que a função hash distribua bem os valores para garantir que as buscas sejam rápidas.

Por exemplo, se quisermos transformar uma palavra em um índice para uma tabela:

```csharp
int HashFunction(string key, int tableSize) {
    int hash = 0;
    foreach (char c in key) {
        hash += (int)c; // converte caracteres em inteiros e soma
    }
    return hash % tableSize; // usa o módulo para caber na tabela
}
```

### Utilização
Tabelas hash têm várias aplicações práticas, incluindo:

#### Usando Tabelas Hash para Pesquisas
Pesquisas em tabelas hash são rápidas, com complexidade média de **O(1)**. Isso significa que a busca é praticamente instantânea, tornando as tabelas hash ideais para cenários que requerem acesso rápido, como encontrar um número de telefone associado a um nome.

#### Evitando Entradas Duplicadas
Tabelas hash ajudam a evitar duplicações. Se uma entrada já existe, o hash retorna o mesmo índice, então a duplicação é fácil de detectar. Esse recurso é útil em cenários como listas de verificação, onde queremos impedir a entrada de itens repetidos.

#### Utilizando Tabelas Hash como Cache
Tabelas hash são ideais para implementar cache, armazenando resultados de cálculos ou buscas que precisam ser acessados repetidamente. O cache usa a tabela hash para recuperar rapidamente os valores armazenados, economizando processamento.

### Colisões
Uma colisão ocorre quando dois valores diferentes produzem o mesmo índice na tabela. Colisões são inevitáveis com funções hash, então é necessário tratá-las para que dados distintos não sejam sobrescritos.

Uma abordagem para resolver colisões é o **encadeamento**, que armazena valores que causam colisão em uma lista vinculada no mesmo índice:

```csharp
class HashTable {
    List<int>[] table;
    public HashTable(int size) {
        table = new List<int>[size];
        for (int i = 0; i < size; i++) table[i] = new List<int>();
    }
    
    public void Insert(int value) {
        int index = HashFunction(value.ToString(), table.Length);
        table[index].Add(value);
    }
}
```

### Desempenho
O desempenho de uma tabela hash depende de dois fatores principais: o fator de carga e a qualidade da função hash.

#### Fator de Carga
O **fator de carga** é a razão entre o número de itens e o tamanho da tabela. Um fator de carga baixo (ex.: 0,5) significa mais espaço disponível, reduzindo o risco de colisões. Tabelas hash geralmente operam melhor com fatores de carga abaixo de 0,7.

#### Uma Boa Função Hash
Uma boa função hash distribui valores uniformemente para minimizar colisões. Funções que levam em consideração características distintas das entradas (como somar valores ASCII dos caracteres e aplicar operações matemáticas adicionais) ajudam a evitar clusters e melhoram o desempenho.

### Conclusão
Tabelas hash são extremamente eficientes para buscas, checagem de duplicados e cache, desde que implementadas com uma boa função hash e mantidas com um fator de carga adequado. O tratamento de colisões é essencial para garantir que o desempenho não se degrade mesmo quando múltiplas entradas mapeiam para o mesmo índice.

### Citações
---------

