**Livro:** Código Limpo<br>
**Autor**: Robert C. Martin

### Conteúdo
----------------
----------------
> <u><b>Introdução</b></u>
> Nada pode ser tão útil quanto um comentário bem colocado. Nada consegue amontoar um módulo mais do que comentários dogmáticos e supérfluos. Nada pode ser tão prejudicial quanto um velho comentário mal feito que dissemina mentiras e informações incorretas.
>
> Comentários não são como a Lista de Schindler. Não são o **"bom puro"**. De fato, eles são, no máximo, um mal necessário, Se nossas linguagens de programação fossem expressivas o suficiente ou se tivéssemos o talento para manipular com destreza tais linguagens  de modo a expressar nossa intenção, não precisaríamos de muitos comentários, quiçá nenhum.   
>
>  *Robert C. Martin*
---

#### Comentários Bons

- **Um mal necessário:** existem alguns comentários que são bem vindos, porém tenha sempre em mente que um comentário na maioria das vezes é um fracasso seu em tornar o código claro. O melhor comentário é aquele que você encontrou uma forma de tornar o código mais expressivo e não teve a necessidade de comentar.

- **Código Autoexplicativo**: Prefira escrever código que se explique por si mesmo, reduzindo a necessidade de comentários.

- **Refatoração em vez de Comentários**: Em muitos casos, melhorar o código é melhor do que adicionar comentários.
##### Comentários Legais e Informativos

- **Licenciamento e Autoria**: Use comentários para informações legais, licenciamento e autoria.

```JS
/*
 * Copyright (c) 2024 Fábio.
 * Licenciado sob a MIT License.
 */
```

##### Informativos

- **Informações não obvias**: As vezes é prático fornecer informações básicas em um comentário, esses comentários devem fornecer informações que não são imediatamente óbvias a partir do código.

```JS
// Calcula a quantidade de dias úteis entre duas datas
// Considera somente dias de segunda a sexta-feira
function calcularDiasUteis(inicio, fim) {
    let diasUteis = 0;
    let dataAtual = new Date(inicio);
    const diaDaSemanaSegunda = 1;
    const diaDaSemanaSexta = 5;

    while (dataAtual <= fim) {
        let diaDaSemana = dataAtual.getDay();
        if (diaDaSemana >= diaDaSemanaSegunda && diaDaSemana <= diaDaSemanaSexta) {
            diasUteis++;
        }
        dataAtual.setDate(dataAtual.getDate() + 1);
    }
    return diasUteis;
}
```

##### Explicações de Intenção

- **Intenção do Desenvolvedor**: Use comentários para explicar a intenção por trás de blocos complexos de código.

```JS
// Código Bom
// Usamos um algoritmo de busca binária para melhorar a performance
function busca(array, item) {
    // implementação
}
```

##### Esclarecedores

- **Explicar parâmetros e retornos**: Traduzir o significado de alguns parâmetros ou valores obscuros retornados para algo inteligível.

```JS
// Código Bom
// Este algoritmo utiliza a aproximação de Newton-Raphson para encontrar a raiz quadrada
function calcularRaizQuadrada(numero) {
    let aproximacao = numero / 2;
    let melhorAproximacao;

    do {
        melhorAproximacao = aproximacao;
        aproximacao = (melhorAproximacao + (numero / melhorAproximacao)) / 2;
    } while (melhorAproximacao !== aproximacao);

    return aproximacao;
}

```

##### Comentários Claros

- **Clareza e Precisão**: Comentários devem ser claros e precisos, evitando ambiguidades.

```JS
// Código Ruim
// Corrige o problema
temp -= 273; // ajuste para Kelvin

// Código Bom
// Converte temperatura de Kelvin para Celsius
temperaturaCelsius = temperaturaKelvin - 273;
```

##### Comentários de Tarefas Pendentes (TODO)

- **Para Melhorias Futuras**: Use comentários TODO para anotar melhorias ou correções futuras que precisam ser feitas.

```JS
// TODO: Refatorar este método para melhorar a performance
function metodoComplexo() {
    // implementação
}
```

##### Comentários de Advertência

- **Atenção para Códigos Perigosos**: Use comentários para advertir sobre partes do código que são arriscadas ou complexas.

```JS
// Cuidado: Este método é crítico para a segurança. Faça mudanças com cautela.
function validarEntrada(usuario) {
    // implementação
}
```


#### Comentários Ruins

- **Comentários ruins**: A maioria dos comentários cai nesta categoria. Geralmente eles são suportes ou desculpas para um código de baixa qualidade.
- **Falta de atualização**: Infelizmente praticamente ninguém atualiza os comentários de um código quando o código é atualizado. Isso faz com o comentário, com o passar do tempo, não explique mais o que o código ao qual ele se refere. O comentário acaba mentindo ou enganando o programador.
- **Mantenha o comentário próximo ao código**: O comentário deve estar imediatamente acima do código que ele descreve.
##### Comentários Redundantes

- **Evite Repetição**: Não repita o que o código já diz.

```JS
// Código Ruim
// Retorna verdadeiro se o usuário estiver autenticado
return usuario.estaAutenticado();

// Código Bom
return usuario.estaAutenticado(); // Sem comentário redundante
```

##### Comentários Supérfluos

- **Evite Comentários Óbvios**: Comentários que descrevem o óbvio são desnecessários e devem ser evitados.

```JS
// Código Ruim
// Define a variável como 10
let x = 10;

// Código Bom
let x = 10; // Sem comentário óbvio
```

##### Comentários Longos ou excessivos

- **Descrição de alterações**: Hoje existe o GitHub para fazer isso, não é necessário escrever comentários como controle de alterações do código.
```JS
// Ultima atualização: 02/07/2024
// 02/07/2024: alteração do argumento documentoId por instanciaId.
// 01/04/2024: retirado if de consistencia e criada nova função para isso.
// 03/02/2024: altualização de API usada na função
function buscarDocumento (instanciaId) { 

	// retante do código
}
```

##### Marcadores de posição

- **Identificação de seções**:  As vezes em códigos longos queremos agrupar funções e usamos comentários de seção para isso. O ideal é separar quando possível o código em arquivos, classes ou funções que contenha os códigos que queremos agrupar.

```JS

// Código ruim
// Funções de requisições AJAX -----------------------------------------------

function buscarUsuario () {...}
function buscarAnexo () {...}
function buscarDocumento () {...}

// Código bom
var requisicoesAjax = {
	buscarUsuario: function () {...},
	buscarAnexo: function () {...},
	buscarDocumento : function () {...}
}
```

##### Códigos como comentários

- **Mantenha o código livre de entulhos**: É bastante comum a necessidade de se reescrever uma função ou variável. Porém por receio acabamos comentando o código antigo, para caso possamos recupera-lo caso saia algo errado. O uso correto do GitHub nos protege desse tipo de coisa. Porém queria manter o código por algum motivo coloque um lembrete **TODO** para que outro programador e até mesmo você saiba o que fazer com esse código.

```JS
// TODO apagar esse código até 02/12/2024 caso não for mais necessário
//function converterHtmlParaObjetoJson (html){
//
//	codigo complexo
//
//}

function converterHtmlParaObjetoJson (html) {

	nova implementação complexa

}
```
##### Cabeçalhos de funções ou métodos

- **Sumaries**: Geralmente esse tipo de comentário faz sentido quando a função ou método em questão será usado diversas vezes pelo código e ter uma explicação de seu uso e de o que colocar em seus argumentos é interessante. Porém funções ou métodos curtos e complementares já não tem essa necessidade.

```CSHARP

/// <summary>
/// Cria um novo registro na tabela Usuario.
/// </summary>
/// <param name="usuarioDTO">Objeto DTO com informações do usuário</param>
[HttpPost]
[ProducesResponseType(typeof(Usuario), (int)HttpStatusCode.Created)]
public IActionResult Criar([FromBody] UsuarioCreateDTO usuarioDTO)
{
	Usuario usuario = _mapper.Map<Usuario>(usuarioDTO);
	usuario.protocolo = this.CriarGuidProtocolo();
	_context.Usuarios.Add(usuario);
	_context.SaveChanges();
	return CreatedAtAction(nameof(GetUsuarioPorId), new { id = usuario.Id }, usuario);
}

private string CriarGuidProtocolo()
{
	return Guid.NewGuid().ToString();
}
```

### Citações
---------
[Felipe Deschamps](https://www.youtube.com/watch?v=2tCX3zXeUAY&list=PLMdYygf53DP5Sc6yFYs6ZmjsuuA2fu0TK&index=5) <br>
[Código Fonte](https://www.youtube.com/watch?v=XUx0Mb7iUtg&list=PLVc5bWuiFQ8H5P-7QB1_3LOJkOZNMnnpg&index=4) <br>
[Balta.IO](https://www.youtube.com/watch?v=tfli894kV68&list=PLHlHvK2lnJnfGR8aVpTybsUEFuARZH40U&index=1) <br>
