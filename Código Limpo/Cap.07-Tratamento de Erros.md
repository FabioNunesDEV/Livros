**Livro:** Código Limpo<br>
**Autor**: Robert C. Martin

### Conteúdo
----------------
> <u><b>Introdução</b></u>
>Pode parecer estranho ter uma seção sobre tratamento de erro num livro sobre código limpo, mas essa tarefa é uma das quais todos temos de fazer quando programamos. A entrada pode estar errada e os dispositivos podem falhar. Em suma, as coisas podem  dar  errado, e  quando 
>isso  ocorre, nós, como  programadores, somos  responsáveis  por  certificar que nosso código 
>faça o que seja preciso fazer.
>
>  *Robert C. Martin*


#### Usar Exceções em vez de Códigos de Retorno

- **Princípio**: As exceções são preferíveis aos códigos de retorno para o tratamento de erros, pois tornam o código mais limpo e a lógica principal mais fácil de entender.

```JS
function divide(a, b) {
    if (b === 0) {
        throw new Error('Divisão por zero');
    }
    return a / b;
}
```

#### Criar Exceções Significativas

- **Princípio**: As mensagens de exceção devem ser claras e descritivas para facilitar a identificação e resolução dos problemas.

```JS
class InvalidOperationException extends Error {
    constructor(message) {
        super(message);
        this.name = 'InvalidOperationException';
    }
}

function withdraw(account, amount) {
    if (amount > account.balance) {
        throw new InvalidOperationException('Saldo insuficiente.');
    }
    account.balance -= amount;
}
```

#### Usar Try-Catch-Finally para Gerenciamento de Recursos

- **Princípio**: Utilizar blocos `try-catch-finally` para garantir que os recursos sejam liberados corretamente, mesmo quando ocorrem erros.

```JS
function readFile(filePath) {
    let file;
    try {
        file = openFile(filePath);
        // Processar o arquivo
    } catch (e) {
        console.error('Erro ao ler o arquivo:', e.message);
    } finally {
        if (file) {
            closeFile(file);
        }
    }
}
```

#### Definir as Bordas: Converter Exceções para Códigos de Retorno

- **Princípio**: Nas bordas do sistema (interfaces, bibliotecas de terceiros), converter exceções para códigos de retorno, se necessário, para manter a consistência.

```js
function parseJSON(jsonString) {
    try {
        return JSON.parse(jsonString);
    } catch (e) {
        return null;
    }
}
```

#### Evitar Tratamento de Exceções Silenciosas

- **Princípio**: Evitar capturar exceções sem tratá-las ou sem pelo menos registrar o erro.

```js
try {
    riskyOperation();
} catch (e) {
    console.error('Erro inesperado:', e.message);
}
```

#### Revelar Intenção com Exceções Personalizadas

- **Princípio**: Criar exceções personalizadas para tornar o código mais legível e expressivo.

```js
class UnauthorizedAccessException extends Error {
    constructor(message) {
        super(message);
        this.name = 'UnauthorizedAccessException';
    }
}

function accessResource(user) {
    if (!user.isAuthorized) {
        throw new UnauthorizedAccessException('Acesso não autorizado');
    }
    // Acessar recurso
}
```

#### Separar Construção de Objetos e Tratamento de Erros

- **Princípio**: Separar a lógica de construção de objetos e a lógica de tratamento de erros para manter o código organizado e de fácil manutenção.

```js
function createUser(data) {
    if (!data.name) {
        throw new Error('Nome é obrigatório');
    }
    return new User(data.name, data.age);
}

try {
    let user = createUser({ name: 'John', age: 30 });
} catch (e) {
    console.error('Erro ao criar usuário:', e.message);
}
```

### Citações
---------
[Código Fonte](https://www.youtube.com/watch?v=IQyKUpfWZ_0&list=PLVc5bWuiFQ8H5P-7QB1_3LOJkOZNMnnpg&index=7)<br>
[Sharpax  - Try/Catch](https://www.youtube.com/watch?v=j1T800-3Gow)<br>
[Microsoft Learn](https://learn.microsoft.com/pt-br/dotnet/standard/exceptions/best-practices-for-exceptions)<br>