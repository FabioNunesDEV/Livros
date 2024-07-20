**Livro:** Código Limpo<br>
**Autor**: Robert C. Martin

### Conteúdo
----------------
> <u><b>Introdução</b></u>
>pacotes de outros fabricantes ou usamos códigos livres, ou dependemos de equipes em nossa própria empresa para construir componentes ou subsistemas para nós. De algum modo, devemos integrar, de forma limpa, esse código externo ao nosso. Neste capítulo veremos as práticas e técnicas para manter limpos os limites de nosso software.
>
>  *Robert C. Martin*

#### Utilizando Código de Terceiros

- **Riscos e Benefícios**: Usar bibliotecas de terceiros pode acelerar o desenvolvimento, mas também pode introduzir riscos, como dependência excessiva ou problemas de manutenção.

- **Encapsulamento**: Encapsule o código de terceiros em uma camada de sua própria aplicação para minimizar o impacto de futuras mudanças na biblioteca.  

```javascript

// Encapsulando uma biblioteca de terceiros 

class BibliotecaEncapsulada {

	constructor() {
		this.biblioteca = new TerceirosBiblioteca();
    }
    
    metodoEncapsulado(param) { 
        return this.biblioteca.metodoOriginal(param);
    } 
}
```

#### Adaptadores e Anticorrupção

- **Padrão de Adaptador**: Utilize adaptadores para conectar seu código com bibliotecas de terceiros, protegendo seu sistema de mudanças nas interfaces externas.
- **Camada Anticorrupção**: Crie uma camada anticorrupção para traduzir conceitos e modelos de dados de bibliotecas externas para os usados internamente.

```js
// Adaptador para uma biblioteca de terceiros
class AdaptadorDeTerceiros {
    constructor() {
        this.biblioteca = new BibliotecaDeTerceiros();
    }

    nossoMetodo(param) {
        // Tradução de parâmetros e resultados
        let resultado = this.biblioteca.metodoDeTerceiros(param);
        return this.traduzirResultado(resultado);
    }

    traduzirResultado(resultado) {
        // Lógica para traduzir resultado
        return resultado;
    }
}
```

#### Aprenda e Entenda o Código de Terceiros

- **Leitura de Código**: Leia o código de bibliotecas de terceiros para entender como funcionam e identificar possíveis problemas.
- **Testes e Documentação**: Crie testes e documente o uso da biblioteca em seu sistema para garantir que você entenda como ela se comporta em diferentes situações.
- 
```js
// Exemplo de teste para uma biblioteca de terceiros
const adaptador = new AdaptadorDeTerceiros();

test('nossoMetodo deve traduzir corretamente o resultado', () => {
    const resultado = adaptador.nossoMetodo('input');
    expect(resultado).toBe('output esperado');
});
```

#### Definindo Limites Claros

- **Interface Clara**: Defina interfaces claras para interagir com bibliotecas de terceiros, de forma que seu código fique protegido de mudanças internas dessas bibliotecas.
- **Separação de Responsabilidades**: Mantenha uma separação clara entre o código de sua aplicação e o código de terceiros.

```js
// Interface clara para uso de biblioteca de terceiros
class ServicoDePagamento {
    constructor(adaptadorDePagamento) {
        this.adaptador = adaptadorDePagamento;
    }

    processarPagamento(dadosPagamento) {
        return this.adaptador.realizarPagamento(dadosPagamento);
    }
}
```

#### Minimizar Dependências

- **Dependências Mínimas**: Reduza ao mínimo as dependências em bibliotecas de terceiros para diminuir o acoplamento e facilitar a manutenção.
- **Versionamento e Controle**: Controle as versões das bibliotecas de terceiros para evitar problemas de compatibilidade e surpresas desagradáveis.

```js
// Gerenciamento de dependências com package.json
{
    "dependencies": {
        "biblioteca-de-terceiros": "^1.2.3"
    }
}
```

### Conclusão

Entender e gerenciar os limites de seu sistema, especialmente quando se trata de integrar bibliotecas de terceiros, é essencial para manter um código limpo e sustentável. Encapsulamento, adaptadores, camadas anticorrupção e uma clara separação de responsabilidades são práticas recomendadas para lidar com essas integrações.

### Citações
---------

