**Livro:** Código Limpo
**Autor**: Robert C. Martin

### Conteúdo
----------------
> <u><b>Introdução</b></u>
> Há nomes por todos os lados em um software. Nomeamos nossas variáveis, funções, parâmetros, classes e pacotes, assim como os arquivos-fonte e os diretórios que os possui. E nomeamos, nomeamos e nomeamos. Como fazemos muito isso, é melhor que façamos bem. 
>
>  *Robert C. Martin*
---
#### Use Nomes que Revelem Intenção

- **Clareza**: Nomes devem revelar a intenção do que a variável, função ou classe faz.
- **Autoexplicativos**: Evite comentários desnecessários ao usar nomes que expliquem claramente o propósito do código.

```JS
// Código Ruim
let d; // número de dias

// Código Bom
let numeroDeDias;
```
#### Evite Desinformação

- **Nomes Precisos**: Evite usar nomes que possam confundir ou desinformar.
- **Consistência**: Use nomes consistentes para evitar mal-entendidos.

```JS
// Código Ruim
let hp; // pontos de saúde ou potência do motor?

// Código Bom
let pontosDeSaude;
let potenciaDoMotor;
```

#### Faça Distinções Significativas

- **Diferença Semântica**: Use nomes que destaquem diferenças significativas.
- **Evite Nomes Genéricos**: Nomes como `dados`, `info`, `item` devem ser evitados.

```JS
// Código Ruim
let dadosProduto;
let infoProduto;

// Código Bom
let detalhesProduto;
let metricasProduto;
```

#### Use Nomes Pronunciáveis

- **Facilidade de Comunicação**: Nomes pronunciáveis facilitam discussões sobre o código.

```JS
// Código Ruim
let genymdhms; // data de geração

// Código Bom
let timestampGeracao;
```

#### Use Nomes Pesquisáveis

- **Facilidade de Localização**: Use nomes que sejam fáceis de pesquisar e encontrar no código.

```JS
// Código Ruim
let a = 5; // constante mágica

// Código Bom
const MAXIMO_USUARIOS = 5;
```

#### Evite Codificação

- **Sem Prefixos e Sufixos Desnecessários**: Não use notações húngaras ou outras codificações que poluem os nomes.

```JS
// Código Ruim
let m_dsc; // descritor

// Código Bom
let descritor;
```

#### Nomes de Classes

- **Substantivos**: Use substantivos para classes, que representem entidades ou conceitos.

```JS
// Código Ruim
class Gerente; // muito genérico

// Código Bom
class GerenteDeUsuarios; // mais específico
```

#### Nomes de Métodos

- **Verbos**: Use verbos para métodos, indicando ações ou comportamentos.

```JS
// Código Ruim
function dados() { ... } // o que faz?

// Código Bom
function buscarDados() { ... } // mais claro
```

#### Evite Mapas Mentais

- **Intuição**: Nomes devem ser intuitivos e não requerer decodificação mental.

```JS
// Código Ruim
function processarRequisicao() { ... } // processa como?

// Código Bom
function validarESalvarRequisicao() { ... } // mais claro
```

#### Consistência de Contexto

- **Contexto Claro**: Nomes devem fornecer contexto suficiente para serem compreendidos sem esforço extra.
- **Agrupamento Lógico**: Agrupe nomes relacionados logicamente.

```JS
// Código Ruim
function adicionarALista(item) {
    this.lista.push(item);
}

// Código Bom
class CarrinhoDeCompras {
    constructor() {
        this.itens = [];
    }
    
    adicionarItem(item) {
        this.itens.push(item);
    }
}

```
### Exemplo de Nomes Significativos

```JS
// Código Ruim
function pegarEles() {
    let lista1 = [];
    for (let x in aLista) {
        if (aLista[x].flag) {
            lista1.push(aLista[x]);
        }
    }
    return lista1;
}

// Código Bom
function pegarCelulasMarcadas() {
    let celulasMarcadas = [];
    for (let celula of tabuleiroJogo) {
        if (celula.estaMarcada) {
            celulasMarcadas.push(celula);
        }
    }
    return celulasMarcadas;
}
```

O capítulo 2 destaca a importância de usar nomes significativos no código, melhorando a clareza, legibilidade e manutenção do software.

### Citações
---------

[Código Fonte TV - Clean Code - Desvendando livros](https://www.youtube.com/watch?v=O5aWwBXPoh4&list=PLVc5bWuiFQ8H5P-7QB1_3LOJkOZNMnnpg)
[Filipe Deschamps -  A importância dos nomes](https://www.youtube.com/watch?v=kw3H7nj9kc4)
[Balta.IO - Clean Code](https://www.youtube.com/watch?v=tfli894kV68&list=PLHlHvK2lnJnfGR8aVpTybsUEFuARZH40U)