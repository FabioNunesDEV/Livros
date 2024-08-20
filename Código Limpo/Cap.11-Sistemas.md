**Livro:** Código Limpo
**Autor**: Robert C. Martin

### Conteúdo
----------------
> <u><b>Introdução</b></u>
>Complexidade mata. Ela suga a vida dos desenvolvedores, dificulta o planejamento, a construção e o teste dos produtos”.
>
>  *Ray Ozzie, CTO, Microsoft Corporation*

#### Design no Nível de Sistema
   - O design de sistemas vai além do design de classes e métodos. Envolve a organização de módulos, subsistemas e componentes para alcançar um objetivo maior: a criação de um sistema que seja fácil de modificar, entender e manter.
   - **Exemplo em C#:**
   ```csharp
   public class SystemDesign
   {
       private readonly ModuleA _moduleA;
       private readonly ModuleB _moduleB;

       public SystemDesign(ModuleA moduleA, ModuleB moduleB)
       {
           _moduleA = moduleA;
           _moduleB = moduleB;
       }

       public void Execute()
       {
           _moduleA.PerformTask();
           _moduleB.PerformAnotherTask();
       }
   }
   ```

#### Separation of Concerns (Separação de Preocupações)
   - Um dos princípios fundamentais é a separação de preocupações. Isso significa que diferentes aspectos do sistema, como a lógica de negócios e a interface do usuário, devem ser separados em módulos diferentes.
   - **Exemplo em C#:**
   ```csharp
   public class UserController
   {
       private readonly IUserService _userService;

       public UserController(IUserService userService)
       {
           _userService = userService;
       }

       public void CreateUser(string name, string email)
       {
           _userService.Register(name, email);
       }
   }

   public class UserService : IUserService
   {
       private readonly IUserRepository _userRepository;

       public UserService(IUserRepository userRepository)
       {
           _userRepository = userRepository;
       }

       public void Register(string name, string email)
       {
           var user = new User(name, email);
           _userRepository.Save(user);
       }
   }
   ```

#### Camadas de Abstração
   - É essencial criar camadas de abstração que isolam diferentes partes do sistema, permitindo mudanças internas sem afetar outras partes do sistema.
   - **Exemplo em C#:**
   ```csharp
   public interface IDatabase
   {
       void SaveData(string data);
   }

   public class SqlDatabase : IDatabase
   {
       public void SaveData(string data)
       {
           // Implementação do salvamento em um banco de dados SQL
       }
   }

   public class DataAccessLayer
   {
       private readonly IDatabase _database;

       public DataAccessLayer(IDatabase database)
       {
           _database = database;
       }

       public void PersistData(string data)
       {
           _database.SaveData(data);
       }
   }
   ```

**Use of Factories (Uso de Fábricas)**
   - O uso de padrões como Fábricas ajuda a manter a lógica de criação de objetos fora da lógica principal do sistema, promovendo o desacoplamento.
   - **Exemplo em C#:**
   ```csharp
   public class CarFactory
   {
       public ICar CreateCar(string type)
       {
           switch (type)
           {
               case "Sedan":
                   return new Sedan();
               case "SUV":
                   return new SUV();
               default:
                   throw new ArgumentException("Tipo de carro inválido.");
           }
       }
   }

   public class CarService
   {
       private readonly CarFactory _carFactory;

       public CarService(CarFactory carFactory)
       {
           _carFactory = carFactory;
       }

       public void ServiceCar(string type)
       {
           var car = _carFactory.CreateCar(type);
           car.PerformService();
       }
   }
   ```

**Componentes e Coesão**
   - Sistemas são compostos de componentes que devem ser altamente coesos. Cada componente deve ter uma responsabilidade bem definida e ser o mais independente possível dos outros componentes.
   - **Exemplo em C#:**
   ```csharp
   public class AuthenticationService
   {
       private readonly IUserRepository _userRepository;
       private readonly IPasswordHasher _passwordHasher;

       public AuthenticationService(IUserRepository userRepository, IPasswordHasher passwordHasher)
       {
           _userRepository = userRepository;
           _passwordHasher = passwordHasher;
       }

       public bool Authenticate(string username, string password)
       {
           var user = _userRepository.GetByUsername(username);
           if (user == null)
               return false;

           return _passwordHasher.VerifyPassword(password, user.HashedPassword);
       }
   }
   ```

#### Conclusão

No capítulo 11, Robert C. Martin reforça a importância de pensar em sistemas de maneira arquitetônica, não apenas em termos de código, mas em termos de componentes, módulos e como eles interagem entre si. Ele sugere que, para construir sistemas robustos e flexíveis, devemos aplicar princípios como a separação de preocupações, camadas de abstração, e garantir que cada componente seja coeso e desacoplado, utilizando padrões de design quando necessário. Esses princípios ajudam a manter a simplicidade e a clareza na arquitetura do sistema, facilitando a manutenção e a evolução futura.
### Citações
---------

