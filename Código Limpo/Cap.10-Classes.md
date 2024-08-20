**Livro:** Código Limpo<br>
**Autor**: Robert C. Martin

### Conteúdo
----------------
> <u><b>Introdução</b></u>
>Até agora, este livro se focou em como escrever bem linhas e blocos de código. 
>Mergulhamos na composição apropriada para funções e como elas se interrelacionam. 
>Mas apesar de termos falado bastante sobre a expressividade das instruções do código e as funções que o compõem, ainda não teremos um código limpo até discutirmos sobre os níveis mais altos da organização do código. Vamos falar agora sobre classes limpas.
>
>  *Robert C. Martin*

#### Princípios das Classes Limpa

- **Responsabilidade Única**: Cada classe deve ter uma única responsabilidade ou propósito específico, facilitando a manutenção e compreensão do código.
  
- **Coesão**: Os métodos e variáveis dentro de uma classe devem estar intimamente relacionados, garantindo que a classe faça bem seu trabalho específico.

- **Encapsulamento**: As variáveis devem ser privadas e acessíveis apenas por métodos públicos, protegendo o estado interno da classe.

#### Organização das Classes

- **Estrutura Clara**: Métodos públicos no topo, seguidos por métodos privados e variáveis. Isso facilita a leitura e a compreensão da classe.

- **Uso de Pequenas Classes**: Em vez de criar classes grandes e complexas, divida a lógica em classes menores e mais específicas, melhorando a reutilização e a testabilidade.

#### Exemplos em C#

- **Responsabilidade Única**
  ```csharp
  public class CustomerService
  {
      private CustomerRepository _repository;

      public CustomerService(CustomerRepository repository)
      {
          _repository = repository;
      }

      public void AddCustomer(Customer customer)
      {
          _repository.Add(customer);
      }
  }
  ```

- **Coesão**
  ```csharp
  public class Invoice
  {
      public decimal Amount { get; private set; }
      public DateTime Date { get; private set; }

      public Invoice(decimal amount, DateTime date)
      {
          Amount = amount;
          Date = date;
      }

      public decimal CalculateTax()
      {
          return Amount * 0.1m;
      }
  }
  ```

- **Encapsulamento**
  ```csharp
  public class BankAccount
  {
      private decimal _balance;

      public BankAccount(decimal initialBalance)
      {
          _balance = initialBalance;
      }

      public void Deposit(decimal amount)
      {
          _balance += amount;
      }

      public void Withdraw(decimal amount)
      {
          if (amount <= _balance)
          {
              _balance -= amount;
          }
          else
          {
              throw new InvalidOperationException("Saldo insuficiente.");
          }
      }

      public decimal GetBalance()
      {
          return _balance;
      }
  }
  ```

- **Estrutura Clara**
  ```csharp
  public class OrderProcessor
  {
      public void Process(Order order)
      {
          if (IsValid(order))
          {
              Save(order);
              NotifyCustomer(order);
          }
      }

      private bool IsValid(Order order)
      {
          return true;
      }

      private void Save(Order order)
      {
          // Salvar o pedido no banco de dados
      }

      private void NotifyCustomer(Order order)
      {
          // Notificar o cliente sobre o pedido
      }
  }
  ```

- **Uso de Pequenas Classes**
  ```csharp
  public class Address
  {
      public string Street { get; set; }
      public string City { get; set; }
      public string State { get; set; }
      public string ZipCode { get; set; }
  }

  public class Person
  {
      public string Name { get; set; }
      public Address Address { get; set; }
  }
  ```

#### Conclusão

Seguir os princípios e práticas de design de classes apresentados neste capítulo é fundamental para criar um código mais limpo, legível e fácil de manter. Classes com responsabilidade única, coesas, bem encapsuladas e organizadas de forma clara não apenas facilitam o entendimento e a manutenção do código, mas também tornam o desenvolvimento mais eficiente e colaborativo. Ao adotar a abordagem de dividir a lógica em pequenas classes especializadas, você melhora a reutilização, testabilidade e robustez do seu software, garantindo que ele seja sustentável e adaptável a mudanças futuras.
### Citações
---------

