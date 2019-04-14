# Convenções de Nomenclatura

## Gerais
- Não utilizar notação húngara
- Frases com palavra inicial com 2 caracteres pode utilizar ambas como maiúsculas, ex: ` UIControl` no lugar de ` UiControl `
- Nome de classes e interfaces devem refletir o nome do arquivo físico
- Declaração de campos/variáveis/constantes que sejam inicializadas no construtor devem receber a palavra reservada ` readonly `.
- Na declaração de tuplas, prefira sempre tipar fortemente o retorno, ex: ` (string name, int age) = GetCustomer(); ` 
- Não utilizar abreviações como por exemplo ` GetWin ` no lugar de ` GetWindow `
- Ao versionar Apis ou classes utilizar o indicador da versão como sufixo e não prefixo:

```c#
// do
public class UserServiceV2 {}

// do not
public class V2UserService {}
```
## Namespaces

- Utilizar PascalCase
- Não utilizar um nome de tipo(classe,interface, struct etc) como nome de namespace

## Classes

- Devem seguir o padrão PascalCase
- Deve-se sempre se atentar aos modificadores (public, private, protected)
- Deve-se utilizar substantivos e frases nominais no singular para nomear as classes
- Construtores devem ficar ao final da classe

```c#
// Nome em Pascal Case
public class UserDetailsModel
{    
    public string Name { get; set; }
    
    // Construtor no final da classe
    public UserDetailsModel()
    {
        
    }
}
```


## Interfaces

- Devem começar com a letra I Maiúscula
- A segunda letra também deve ser maiúscula, seguindo o PascalCase
- Deve-se utilizar como nome substantivos ou adjetivos
```c#
 public class IUserRepository { }
```

## Parâmetros de tipo genérico

- Utilizar ` T ` como prefixo

```c#
public interface ISessionChannel<TSession> where TSession : ISession 
{  
    TSession Session { get; }  
}
```

## Métodos

- Utilizar PascalCase
- Quando for métodos simples, apenas com uma linha, utilizar bodyExpressions
- Se atentar aos modificadores
- Nomes de métodos devem ser verbos
- parâmetros enviados para um método devem ser declarados no padrão camelCase
```c#
 public string GetFullName(string name, string lastName) => name + lastName;
```


## Propriedades
- Deve utilizar o padrão PascalCase
- Nomes devem ser substantivos ou adjetivos
```c#
public string EmailAddress {  get;  set; } 
```

- Utilizar bodyExpressions quando houver necessidade de se utilizar de campos privados:
```c#
public string Email {  get => _email;  set => _email = value; } 
```

- Considere nomear uma propriedade com o mesmo nome de seu tipo:
```c#
public enum Color {...}
public class Control 
{
    public Color Color { get; set; }
}
```

## Campos de classe

- Devem seguir o camelCase
```c#
public class Test
{
    public string clientName;
}
```

- Caso seja utilizado por uma propriedade deve começar com underscore:
```c#
public class User 
{
    private string _email;
    public string Email {  get => _email;  set => _email = value; } 
}
```


## Variáveis
- Por padrão devem seguir o padrão camelCase
- Apenas variáveis estáticas devem se utilizar de _ no início da declaração
- Considere utilizar "var" para declaração de variáveis apenas para variáveis locais e que não sejam de tipos primitivos 
     - `(int teste = 100; var = File.Create(path))`
- 

## Tipos
- Preferir a utilização dos alias do C# no lugar dos System names:
```
string no lugar de String
int no lugar de Int16
etc
```

## Enumeradores
- Declare apenas com o nome do enum, sem especificar numeração:
```c#
public enum Color
{
    Red,
    Green
}
```
- Utilizar numeração apenas quando houver o uso de flags:
```c#
[Flags]
public enum Dockings
{
    None = 0,
    Top = 1, 
    Right = 2, 
    Bottom = 4,
    Left = 8
}
```

## Constants
- Utilizar PasscalCase para declaração

