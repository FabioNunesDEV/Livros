**Livro:** Código Limpo
**Autor**: Robert C. Martin

### Conteúdo
----------------
> <u><b>Introdução</b></u>
> O livro Código Limpo fala sobre programação e está repleto  de códigos que  examinaremos a partir de diferentes perspectivas: de baixo para cima, de cima para baixo e de dentro para fora. Ao terminarmos, teremos um amplo conhecimento sobre códigos e seremos capazes de distinguir entre um código bom e um código ruim. Saberemos como escrever um bom código e como tornar um ruim em um bom.
>
>  *Robert C. Martin*
---
#### A Importância do Código Limpo

- **Qualidade e Manutenibilidade**: Código limpo é essencial para garantir a qualidade e a manutenibilidade do software ao longo do tempo.
- **Custo de Código Sujo**: Código sujo pode funcionar inicialmente, mas se torna difícil de entender, modificar e manter, aumentando o custo e o tempo de desenvolvimento e , manutenção.

#### Características do Código Limpo

- **Legibilidade**: Código limpo deve ser fácil de ler e entender.
- **Simplicidade**: Código deve ser simples, evitando complexidades desnecessárias.
- **Ausência de Duplicação**: Código limpo evita a repetição de lógica ou trechos de código.
- **Testabilidade**: Código limpo deve ser fácil de testar.

#### Percepções de Profissionais sobre Código Limpo

- **Opiniões Variadas**: Diversos desenvolvedores experientes têm suas próprias definições de código limpo, enfatizando diferentes aspectos como clareza, elegância e simplicidade.
- **Exemplos de Definições**: Alguns profissionais descrevem código limpo como algo que pode ser lido e melhorado por qualquer outro desenvolvedor, independentemente de sua familiaridade com o código original.

#### Método Boy Scout

- **Melhoria Contínua**: Aplique o princípio dos escoteiros ("Boy Scout Rule"), que sugere deixar o código melhor do que foi encontrado.
- **Pequenas Melhorias**: Faça pequenas melhorias constantes no código para aumentar sua qualidade geral.

#### Código como Arte

- **Beleza e Elegância**: Escrever código é visto como uma forma de arte onde a beleza, simplicidade e elegância são valorizadas.
- **Código Funcional e Estético**: Desenvolvedores devem buscar criar código que não apenas funcione bem, mas que também seja agradável de ler.

#### Demonstração de Código Limpo

- **Exemplos Práticos**: O autor fornece exemplos de código sujo e limpo, demonstrando como pequenas mudanças podem melhorar a legibilidade e a mantenabilidade.
- **Transformação de Código**: Mostra como transformar código confuso em código claro e fácil de entender.

```JS
// Código Sujo
function processData(data) {
    for (let key in data) {
        if (key === 'a') {
            data[key] += 1;
        } else if (key === 'b') {
            data[key] -= 1;
        }
    }
    return data;
}

// Código Limpo
function incrementA(data) {
    data['a'] += 1;
    return data;
}

function decrementB(data) {
    data['b'] -= 1;
    return data;
}

function processData(data) {
    data = incrementA(data);
    data = decrementB(data);
    return data;
}

```