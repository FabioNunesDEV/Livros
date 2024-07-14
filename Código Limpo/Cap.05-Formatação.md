**Livro:** Código Limpo
**Autor**: Robert C. Martin

### Conteúdo
----------------
> <u><b>Introdução</b></u>
> Quando as pessoas olham o código, desejamos que fiquem impressionadas com a polidez, a consistência e a atenção aos detalhes presentes. Queremos que reparem na organização. Desejamos que suas sobrancelhas se levantem ao percorrerem os módulos, que percebam que foram profissionais que estiveram ali. Se, em vez disso, virem um emaranhado de código como se tivesse sido escrito por um bando de marinheiros bêbados, então provavelmente concluirão que essa mesma falta de atenção foi perpetuada por todo o projeto.
>
>  *Robert C. Martin*

#### O objetivo da formatação

- **Legibilidade**: A formatação do código deve facilitar a leitura e a compreensão.
- **Comunicação**: Código bem formatado é uma forma de comunicação com outros desenvolvedores.
#### Pequenos Blocos de Código

- **Funções Curtas**: Funções devem ser curtas e focadas em uma única tarefa.

```js
// Função curta e focada em uma única tarefa
function calcularAreaRetangulo(largura, altura) {
    return largura * altura;
}
```

- **Blocos de Código**: Evite funções com muitos blocos de código aninhados. Prefira funções menores e mais específicas.
#### Linhas Pequenas

- **Comprimento das Linhas**: Mantenha o comprimento das linhas de código limitado para evitar a necessidade de rolagem horizontal.
- **Quebra de Linhas**: Use quebras de linha apropriadas para melhorar a legibilidade.

```js
// Linha longa, difícil de ler
let mensagem = "Esta é uma mensagem de exemplo que é muito longa e difícil de ler sem quebras de linha apropriadas.";

// Melhorado com quebra de linha
let mensagem = "Esta é uma mensagem de exemplo que é muito longa e "
             + "difícil de ler sem quebras de linha apropriadas.";
```
#### Espaçamento Vertical

- **Separação de Blocos**: Use espaçamento vertical para separar diferentes blocos de código, como funções, declarações de classe e seções dentro de funções.

```js
function calcularAreaCirculo(raio) {
    return Math.PI * raio * raio;
}

function calcularPerimetroCirculo(raio) {
    return 2 * Math.PI * raio;
}
```

- **Agrupamento Lógico**: Separe logicamente diferentes partes do código para torná-lo mais fácil de seguir.
#### Espaçamento Horizontal

- **Espaço entre Elementos**: Use espaços em branco para separar operadores, variáveis e palavras-chave, tornando o código mais legível.
  
```JS
// Código com bom espaçamento horizontal
let soma = a + b;
```

#### Indentação

- **Indentação Consistente**: Use indentação consistente para indicar a estrutura do código.
- **Padrões de Indentação**: Escolha um padrão de indentação (espaços ou tabs) e seja consistente em todo o projeto.

```js
// Indentação consistente
if (condicao) {
    console.log("Condição verdadeira");
} else {
    console.log("Condição falsa");
}
```

#### Linhas em Branco

- **Uso de Linhas em Branco**: Linhas em branco ajudam a separar blocos de código logicamente distintos, melhorando a legibilidade.

```JS
// Função 1
function funcao1() {
    // Código da função 1
}

function funcao2() {
    // Código da função 2
}
```

#### Declarações de Variáveis

- **Declarações Agrupadas**: Agrupe declarações de variáveis no início de blocos ou funções, para melhorar a clareza.

```JS
// Declarações agrupadas
let x = 10;
let y = 20;
let resultado = x + y;
```

#### Comentários

- **Posicionamento dos Comentários**: Comentários devem ser colocados em posições estratégicas para explicar partes complexas do código sem interromper o fluxo.

```JS
// Função que calcula a área de um círculo
function calcularAreaCirculo(raio) {
    // Fórmula: πr²
    return Math.PI * raio * raio;
}
```

#### Formatação Condicional e de Loop

- **Blocos Condicionais e Loops**: Use uma formatação clara e consistente para estruturas condicionais e loops.

```JS
// Código bem formatado
if (condicao) {
    // Código executado se a condição for verdadeira
} else {
    // Código executado se a condição for falsa
}
```

#### Conclusão

A formatação é crucial para manter o código limpo e legível. Um código bem formatado não só facilita a leitura e manutenção, mas também ajuda na comunicação entre os membros da equipe. A consistência na aplicação dessas práticas de formatação é fundamental para criar um código que seja fácil de entender e modificar.
### Citações
---------

[Código Fonte](https://www.youtube.com/watch?v=XUx0Mb7iUtg&list=PLVc5bWuiFQ8H5P-7QB1_3LOJkOZNMnnpg&index=4) <br>