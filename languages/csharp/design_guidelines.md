# Convenções de Design

## Classes Abstratas

- Não definir construtores públicos ou privados, apenas protected ou internal.
- Não definir classes abstratas sem possuir pelo menos uma implementação da mesma.

## Interfaces

- Evite marked Interfaces(interfaces sem membros):

```c#
public interface IEntity{}
```
- Fornecer pelo menos uma implementação da interface criada
- A declaração das chaves deve ser abaixo da linha de criação da interface:

```c#
// do not
public interface IEntity{
    ...
}

// do
public interface IEntity
{
    ...
}
```

## Enum
- Utilizar para parâmetros que devem ser fortemente tipados como gênero, Tipo de usuário etc.
- Favorecer Enum no lugar de constantes estáticas.
- Evite enums que só possuem um único item
- Considere utilizar a nomenclatura ` None ` para caso de valores não apropriados para o enum específico, 
- Utilize potência de 2 para flag enums

```c#
[Flags]
public enum MyFlags
{
    None = 0,
    Red = 1,
    Yellow = 2,
    Green = 4,
    Orange = 8
}
```

## Propriedades

- Utilizar o ` set ` apenas quando a propriedade puder ser alterada
- Utilizar `private set ` quando o valor da propriedade não puder ser inserido diretamente pela propriedade (casos como quando é inicializada pelo construtor ou possui certas regras para receber novos valores)
- O set não deve ter acessibilidade mais ampla que o get 
- Evite lançar exceções em getters

## Construtores

- Considere utilizar factory estáticos quando a construção de um objeto é um pouco complexa
- Defina no construtor os parâmetros obrigatórios para a criação de uma classe
- Faça o mínimo de trabalho no construtor, ele deve servir basicamente para atribuir valores às propriedades iniciais.
- Evite definir construtores padrão nas classes
- Evite atribuir valores a membros virtuais nos construtores
- Não lance exceções a partir de construtores estáticos

## Campos

- Não crie campos publicos ou protected (defina propriedades para acessar esses campos)
- usar ` const ` para campos que não serão alterados
- usar ` readonly ` para campos com valores que serão inicializados no construtor e não sofrerão modificações.

## Enum x Bool

- Considere utilizar Enum
- Prefira a utilização de bool apenas quando houver certeza absoluta de que não haverá uma terceira possibilidade de atribuição de valor

## Parâmetros
- Evite utilizar parâmetros com ` ref ` e ` out ` a menos que seja realmente necessário.
- Considere utilizar ` params ` para receber uma quantidade variável de itens, que também pode ser apenas 1 item:
```c#
public class String {  
    public static string Format(string format, params object[] parameters);  
}  
```

## Exceptions

- Não utilize exceptions para tratamento de regras de negócio ou controle de fluxo, prefira códigos de erro.
- Considere o impacto na performance ao utilizar o lançamento de exceções
- Evite lançar exceções dentro de um bloco finally
- Não gere exceptions genéricas como ` System.Exception` ou ` System.SystemException `
- Não utilize catch com exceções genéricas como: `catch(Exception ex)` para capturar exceções geradas por seu próprio código
- Evite utilizar catch com exceções genéricas de modo geral a menos que se trate de exceções de nível equivalente
- Não lance ` ApplicationException `, ` StackOverflowException `, ` OutOfMemoryException ` `COMException`, ` ExecutionEngineException` e ` SEHException `.
- Não capture ` StackOverflowException `

## Coleções

- Não utilizar Hashtabe ou Dictionary<TKey, TValue> a menos que seja realmente necessário.
- Preferir IEnumerable À List quando houver necessidade de controle das alterações dentro da coleção.
- Prefira Collections no lugar de Arrays



