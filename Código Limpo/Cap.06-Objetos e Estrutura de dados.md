**Livro:** Código Limpo
**Autor**: Robert C. Martin

### Conteúdo
----------------
> <u><b>Introdução</b></u>
>Há um motivo para declararmos nossas variáveis como privadas. Não queremos que ninguém dependa delas. Desejamos ter a liberdade para alterar o tipo ou a implementação, seja por capricho ou impulso. Por que, então, tantos programadores adicionam automaticamente métodos de acesso (escrita, ou setters, e leitura, ou getters) em seus objetos, expondo suas variáveis privadas como se fossem públicas?
>
>  *Robert C. Martin*

#### Dados Ocultos

- **Encapsulamento**: Esconda os dados internos dos objetos e forneça métodos para acessá-los. Isso protege a integridade dos dados e facilita a manutenção.

```js
class Circulo {
    constructor(raio) {
        this._raio = raio; // Dados ocultos
    }

    get raio() {
        return this._raio;
    }

    set raio(novoRaio) {
        if (novoRaio > 0) {
            this._raio = novoRaio;
        }
    }

    calcularArea() {
        return Math.PI * this._raio * this._raio;
    }
}

const circulo = new Circulo(5);
console.log(circulo.calcularArea()); // Acessa dados através de métodos
```

#### Dados Explicítos

- **Estruturas de Dados**: Use estruturas de dados para expor dados diretamente, facilitando o acesso aos dados.

```js
// Estrutura de dados simples
const retangulo = {
    largura: 10,
    altura: 5
};

function calcularAreaRetangulo(retangulo) {
    return retangulo.largura * retangulo.altura;
}

console.log(calcularAreaRetangulo(retangulo)); // Acessa dados diretamente
```

#### Objetos vs Estruturas de Dados

- **Objetos**: Escondem dados e expõem comportamentos.
- **Estruturas de Dados**: Exibem dados e não têm comportamento significativo.

#### Princípio da Lei de Demeter

- **Conhecimento Limitado**: Um objeto deve conhecer apenas seus componentes diretos, não os detalhes internos de outros objetos.

```js
class Motor {
    ligar() {
        console.log("Motor ligado");
    }
}

class Carro {
    constructor() {
        this.motor = new Motor();
    }

    ligarCarro() {
        this.motor.ligar();
    }
}

const meuCarro = new Carro();
meuCarro.ligarCarro(); // O Carro sabe apenas que precisa ligar o motor, sem acessar diretamente o motor
```

#### Objetos de Transferência de Dados (DTOs)

- **DTOs**: Estruturas simples usadas para transferir dados entre diferentes partes de um sistema. Normalmente, não têm comportamento.

```js
class ClienteDTO {
    constructor(nome, idade) {
        this.nome = nome;
        this.idade = idade;
    }
}

const cliente = new ClienteDTO('Fábio', 30);
console.log(cliente.nome); // Acesso direto aos dados do DTO
```

#### Acesso a Dados

- **Métodos de Acesso**: Utilize métodos de acesso (getters e setters) para manipular dados de objetos, mantendo a flexibilidade e o controle.

```js
class ContaBancaria {
    constructor(saldo) {
        this._saldo = saldo;
    }

    get saldo() {
        return this._saldo;
    }

    depositar(valor) {
        if (valor > 0) {
            this._saldo += valor;
        }
    }

    sacar(valor) {
        if (valor > 0 && valor <= this._saldo) {
            this._saldo -= valor;
        }
    }
}

const minhaConta = new ContaBancaria(1000);
minhaConta.depositar(500);
console.log(minhaConta.saldo); // Acesso através de métodos
```

#### Conclusão

O design de objetos e estruturas de dados deve focar na ocultação de dados e na exposição de comportamentos ou na exposição clara de dados. A escolha entre objetos e estruturas de dados deve ser baseada no contexto e nas necessidades específicas do sistema. Encapsular dados dentro de objetos e usar métodos de acesso proporciona flexibilidade e manutenção mais fácil, enquanto estruturas de dados simples podem ser usadas para facilitar a transferência de dados.
### Citações
---------
[Código Fonte](https://www.youtube.com/watch?v=kKjU57F1Zf8&list=PLVc5bWuiFQ8H5P-7QB1_3LOJkOZNMnnpg&index=6)
