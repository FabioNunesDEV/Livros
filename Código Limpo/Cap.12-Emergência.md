**Livro:** Código Limpo
**Autor**: Robert C. Martin

### Conteúdo
----------------
> <u><b>Introdução</b></u>
>De acordo com Kent, um projeto é “simples” se seguir as seguintes regras:
• Efetuar todos os testes
• Sem duplicação de código
• Expressar o propósito do programador
• Minimizar o número de classes e métodos
>
>  *Kent Beck*

### Emergências

---
#### Regra 1 de Projeto Simples: Efetue todos os testes
- **Prioridade dos testes:** Em qualquer projeto, mesmo sob pressão, garantir que todos os testes sejam executados e aprovados é crucial. Testes garantem que o código funciona conforme o esperado, evitando que problemas se acumulem. Em emergências, a tendência pode ser ignorar testes para economizar tempo, mas isso geralmente resulta em mais problemas e retrabalho.
  
  - **Exemplo em C#:**
    ```csharp
    public class CalculatorTests
    {
        [Fact]
        public void Should_ReturnSum_When_AddingTwoNumbers()
        {
            var calculator = new Calculator();
            var result = calculator.Add(2, 3);
            Assert.Equal(5, result);  // Efetuar todos os testes
        }
    }
    ```

#### Regras de 2 a 4 de Projeto Simples: Refatoração
- A refatoração é essencial para manter o código simples e limpo. Mesmo durante emergências, refatorar o código para remover duplicações, melhorar a expressividade e reduzir a complexidade deve ser uma prioridade.

#### Sem repetição de código
- **Eliminação de duplicações:** Código duplicado é um dos maiores inimigos de um design simples. Ele torna o sistema mais difícil de manter e mais propenso a erros. Mesmo em situações críticas, é importante buscar eliminar a duplicação, refatorando para centralizar a lógica compartilhada.

  - **Exemplo em C#:**
    ```csharp
    public class InterestCalculator
    {
        public decimal Calculate(decimal principal, decimal rate, int time, bool isCompound)
        {
            if (isCompound)
                return principal * (decimal)Math.Pow((double)(1 + rate / 100), time) - principal;
            else
                return (principal * rate * time) / 100;  // Sem repetição de código
        }
    }
    ```

#### Expressividade
- **Clareza no código:** O código deve ser escrito de forma que seu propósito seja claro para qualquer desenvolvedor que o leia. Nomes de variáveis, métodos e classes devem ser escolhidos para expressar claramente o que o código faz. Em emergências, a tentação de escrever código rapidamente pode levar à perda de expressividade, o que torna o sistema mais difícil de manter.

  - **Exemplo em C#:**
    ```csharp
    public class User
    {
        public string Name { get; }
        public string Email { get; }

        public User(string name, string email)
        {
            Name = name;
            Email = email;
        }

        public void SendWelcomeEmail(IEmailService emailService)
        {
            emailService.Send(Email, "Welcome " + Name + "!");
        }
    }
    ```

#### Poucas classes e métodos
- **Redução da complexidade:** Minimizar o número de classes e métodos é essencial para manter o design simples e fácil de entender. Classes devem ser responsáveis por uma única coisa e métodos devem ser curtos e específicos. Isso é especialmente importante durante uma emergência, quando a simplicidade do código pode fazer a diferença entre resolver um problema rapidamente ou criar novos problemas.

  - **Exemplo em C#:**
    ```csharp
    public class OrderProcessor
    {
        private readonly IPaymentService _paymentService;
        private readonly IInventoryService _inventoryService;

        public OrderProcessor(IPaymentService paymentService, IInventoryService inventoryService)
        {
            _paymentService = paymentService;
            _inventoryService = inventoryService;
        }

        public void ProcessOrder(Order order)
        {
            _paymentService.ProcessPayment(order);
            _inventoryService.UpdateInventory(order);
        }
    }
    ```

### Conclusão
---

Mesmo em situações de emergência, é crucial seguir as regras de um design simples: garantir que todos os testes sejam realizados, eliminar duplicações, escrever código expressivo e manter o número de classes e métodos ao mínimo necessário. Esses princípios, se seguidos, ajudarão a criar um código que não só resolve a emergência atual, mas também mantém o sistema sustentável e fácil de manter no longo prazo.



### Citações
---------

