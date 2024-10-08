**Livro:** Código Limpo <br>
**Autor**: Robert C. Martin

### Conteúdo
----------------
> <u><b>Introdução</b></u>
> Nos primórdios da programação, formávamos nossos sistemas com rotinas e sub-rotinas. Já na era do Fortran e do PL/I, usávamos programas, subprogramas e funções. De tudo isso, apenas função prevaleceu. As funções são a primeira linha de organização em qualquer programa. >
>
>  *Robert C. Martin*
---
#### Funções devem ser pequenas e fazer apenas uma única tarefa

- **Tamanho**: Funções devem ser trechos de código pequenos.
- **Responsabilidade única**: Cada função deve realizar apenas uma tarefa. Indicativos de que uma função está fazendo mais de uma coisa incluem:
    - Mais de um nível de abstração.
    - Argumentos booleanos.
    - Excesso de argumentos.
    - Uso de `switch/case`.
    - Seções distintas dentro da função.

#### Argumentos em Funções

- **Sem argumentos**: Idealmente, uma função não deve ter argumentos. Quando isso não for possível, utilize poucos argumentos.
- **Encapsulamento de argumentos**: Se muitos argumentos forem necessários, encapsule-os em um objeto ou lista para melhorar a legibilidade e facilitar os testes.

#### Nível de Abstração

- **Um único nível de abstração**: Evite códigos verbosos e mantenha um único nível de abstração por função.

#### Controle de Fluxo

- **Instruções de controle**: Se precisar usar `if`, `switch`, `for`, etc., o escopo dessas instruções deve ser apenas uma linha. Se mais linhas forem necessárias, crie outra função.
- **Switch/Case**: Procure evitar o uso de switch/case, invés disso use objetos do tipo _dictionary_ (chave/valor) ou coloque o `switch/case` em um _abstract factory_.

#### Nomes Descritivos

- **Nomes descritivos**: Use nomes descritivos para funções e argumentos.
- **Estrutura Verbo/Palavra-Chave**: Exemplos:
```js
// O argumento complementa o nome da função
function adicionar(cliente) {
	//faz alguma coisa
}
```
#### Ordem de Leitura

- **Leitura de cima para baixo**: Organize as funções de forma ordenada, onde a função chamadora fica acima da função chamada. Isso facilita a leitura do código.

#### Parâmetros de Saída

- **Evite alterar parâmetros por referência**: Em linguagens como C#, onde é possível alterar objetos passados por parâmetro, evite essa prática. Isso torna a funcionalidade e o retorno da função/método confusos.
- **Separação Comando-Consulta**: Uma função ou faz algo ou retorna algo, nunca as duas coisas ao mesmo tempo.
```js
class User {
  constructor(name, balance) {
    this.name = name;
    this.balance = balance;
  }

  // Função que deveria apenas consultar o saldo, mas também modifica o estado
  getBalanceAndUpdate() {
    this.balance -= 10;  // Comando: Modificação de estado
    return this.balance; // Consulta: Retorno do saldo
  }
}

const user = new User('Fábio', 100);
console.log(user.getBalanceAndUpdate()); // 90
console.log(user.getBalanceAndUpdate()); // 80

```
#### Tratamento de Erros

- **Exceções**: Use _exceptions_ em vez de códigos de erro.
- **Try/Catch**: Coloque _try/catch_ em funções próprias. Assim como outras instruções de controle, _try/catch_ deve ter uma única instrução dentro de seu escopo. O tratamento de erro também é uma tarefa única e deve ter sua própria função.

#### Reutilização de Código

- **Reaproveitamento**: Crie funções que possam ser reaproveitadas e evite a repetição de código.
### Citações
---------
[Felipe Deschamps](https://www.youtube.com/watch?v=gB5Gej0O400&list=PLMdYygf53DP5Sc6yFYs6ZmjsuuA2fu0TK&index=4) <br>
[Código Fonte](https://www.youtube.com/watch?v=wr8n2J4Sqs4&list=PLVc5bWuiFQ8H5P-7QB1_3LOJkOZNMnnpg&index=3) <br>
