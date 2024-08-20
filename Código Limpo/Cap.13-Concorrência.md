**Livro:** Código Limpo
**Autor**: Robert C. Martin

### Conteúdo
----------------
> <u><b>Introdução</b></u>
>“Objetos são abstrações de procedimento. Threads são abstrações de agendamento.”
  James O. Coplien1

O Capítulo 13 do livro *Clean Code* de Robert C. Martin trata da concorrência, um conceito fundamental em programação, especialmente em sistemas que exigem alta performance e escalabilidade. Abaixo está um resumo abordando os principais tópicos mencionados.

#### Mitos e Conceitos Equivocados
- **Mitos e Conceitos Equivocados:** A concorrência é muitas vezes vista como uma solução mágica para melhorar o desempenho. No entanto, adicionar threads não garante automaticamente uma aplicação mais rápida; na verdade, pode introduzir complexidade e erros difíceis de depurar.

#### Desafios
- **Desafios:** A concorrência traz desafios únicos, como condições de corrida, bloqueios e problemas de visibilidade de memória. Esses problemas são difíceis de detectar e corrigir, exigindo um cuidado extra ao projetar e implementar sistemas concorrentes.

#### Princípios para Proteção da Concorrência
- **Princípios para Proteção da Concorrência:** Para proteger o código de problemas comuns na concorrência, é importante limitar o acesso compartilhado a recursos e garantir que as threads sejam corretamente sincronizadas para evitar condições de corrida.

#### Princípio da Responsabilidade Única
- **Princípio da Responsabilidade Única:** Cada thread deve ter uma única responsabilidade clara, o que facilita o isolamento de problemas e a manutenção do código.

#### Soluções para Concorrência

- **Limite o Escopo dos Dados:** Mantenha os dados compartilhados ao mínimo, preferindo variáveis locais ou atributos encapsulados em objetos, o que reduz a possibilidade de condições de corrida.

- **Use Cópias dos Dados:** Sempre que possível, use cópias dos dados ao invés de compartilhá-los entre threads. Isso evita conflitos e simplifica o gerenciamento de dados.

- **As Threads Devem Ser as Mais Independentes Possíveis:** Quanto mais independentes forem as threads, menos problemas de sincronização surgirão, tornando o código mais robusto e fácil de manter.

#### Conheça sua Biblioteca

- **Coleções Seguras para Threads:** Utilize coleções que são seguras para uso em ambientes concorrentes, como as disponíveis no `System.Collections.Concurrent` em C#. Isso evita a necessidade de implementar mecanismos de sincronização manualmente.

- **Conheça Seus Métodos de Execução:** Conhecer as diferentes maneiras de executar tarefas concorrentes, como o uso de `Task`, `ThreadPool`, ou outros mecanismos, ajuda a escolher a melhor ferramenta para cada situação.

#### Padrões de Concorrência

- **Producer-Consumer:** Um padrão comum onde uma ou mais threads produzem dados e outras consomem. O correto uso de filas sincronizadas pode ajudar a implementar esse padrão eficientemente.

- **Leitores e Escritores:** Em cenários onde muitos leitores e poucos escritores precisam acessar os mesmos dados, deve-se permitir que múltiplos leitores acessem simultaneamente, enquanto escritores bloqueiam o acesso.

- **Dining Philosophers (Problema dos Filósofos):** Um problema clássico que demonstra as dificuldades de evitar deadlocks quando várias threads competem por recursos limitados. Soluções incluem o uso de mutexes e algoritmos específicos para evitar deadlocks.

#### Boas Práticas de Sincronização

- **Cuidado com Dependências entre Métodos Sincronizados:** Evite que métodos sincronizados dependam de outros métodos sincronizados, pois isso pode levar a deadlocks.

- **Mantenha Pequenas as Seções Sincronizadas:** Minimize o código dentro de blocos sincronizados para reduzir a contenção e melhorar o desempenho.

#### Teste e Manutenção de Código Concorrente

- **É Difícil Criar Códigos de Desligamento Corretos:** O desligamento ordenado de threads pode ser complicado, exigindo cuidado extra para garantir que todas as threads terminem corretamente.

- **Teste de Código com Threads:** Testar código concorrente é essencial, mas difícil. Falhas intermitentes e não reprodutíveis são comuns, exigindo técnicas específicas para depuração e validação.

- **Trate Falhas Falsas como Questões Relacionadas às Threads:** Muitas vezes, erros que parecem ser aleatórios são, na verdade, falhas nas threads. Considere sempre essa possibilidade ao depurar código concorrente.

#### Estratégias de Implementação

- **Primeiro, Faça com que Seu Código sem Thread Funcione:** Antes de introduzir a concorrência, certifique-se de que o código funciona corretamente em um único thread.

- **Torne Plugável Seu Código com Threads:** O design do código deve permitir a adição ou remoção de threads sem impactar a funcionalidade principal, aumentando a flexibilidade e testabilidade.

- **Torne Ajustável Seu Código com Threads:** Permitir a configuração dinâmica do número de threads ajuda a otimizar o desempenho conforme necessário.

#### Teste de Código Concorrente

- **Execute com Mais Threads do que Processadores:** Para detectar problemas, execute seu código com mais threads do que processadores disponíveis, forçando situações onde problemas de concorrência possam surgir.

- **Execute em Diferentes Plataformas:** Teste seu código em diferentes sistemas operacionais e arquiteturas de hardware para garantir que ele funcione corretamente em todos os ambientes de produção.

- **Altere Seu Código para Testar e Forçar Falhas:** Introduza artificialmente condições de corrida e outros problemas de concorrência para testar a robustez do seu código.

  - **Manualmente:** Insira manualmente delays ou modificações para simular condições adversas.
  
  - **Automatizada:** Use ferramentas que introduzem falhas aleatórias no código concorrente para detectar problemas.

#### Conclusão
O capítulo finaliza enfatizando que, embora a concorrência seja uma poderosa ferramenta para aumentar a performance, ela deve ser usada com cuidado. A complexidade introduzida pode facilmente superar os benefícios, e é essencial seguir boas práticas e princípios sólidos para garantir que o código seja robusto, testável e fácil de manter.


### Citações
---------

