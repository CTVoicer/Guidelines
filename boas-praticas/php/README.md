# PHP

> Boas práticas domando o elePHPante 🐘

## Sumário

- [Visão Geral](#Vis%C3%A3o-Geral)
- [Namespaces e Classes](#Namespaces-e-Classes)
- [Classes, Constantes e Métodos](#Classes%2C-Constantes-e-M%C3%A9todos)
- [Estrutura de controle](#Estrutura-de-controle)

[[⬅ Voltar para Boas Práticas]](../boas-praticas)

## Visão Geral

- Nunca utilize a versão curta das tags do PHP: `<?` e `<?=`.
- Salve todos os seus arquivos PHP com a codificação UTF-8 sem BOM.
- Nunca utilize `tab` para indentar o código. Utilize 4 espaços ao invés disso.

[[⬆ Topo]](#sum%C3%A1rio)

## Namespaces e Classes

- Os nomes de classe devem ser declaradas em `PascalCase`.

```php
<?php

namespace Vendor\Model;

class FooBar
{
}
```

[[⬆ Topo]](#sum%C3%A1rio)

## Classes, Constantes e Métodos

- Defina as propriedades constantes sempre em caracteres maiúsculos:

```php
<?php
namespace Vendor\Model;

class Foo
{
    const VERSION = '1.0';
    const DATE_APPROVED = '2012-06-01';
}
```

- Não utilize a *keyword* `var`.
- Sempre declare a visibilidade de uma propriedade.

```php
<?php

namespace Vendor\Package;

class ClassName
{
    // ruim
    var $foo = null;
    var $foo=null;
    var $foo=NULL;
    var $foo_bar = null;
    var $FooBar = null;

    // bom
    public $foo = null;
    public $fooBar = null;
}
```

- O nome dos métodos deve ser sempre declarado em `camelCase()`.

```php
<?php

namespace Vendor\Package;

class FooBar
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // ...
    }
}
```

- Qualquer *keyword* do PHP [(?)](http://php.net/manual/en/reserved.keywords.php) deve ser escrita em letras minúsculas, assim como os valores `true`, `false`, e `null`.

[[⬆ Topo]](#sum%C3%A1rio)

## Estrutura de controle

As regras gerais são as seguintes:

- Deve haver um espaço após a palavra-chave da estrutura de controle.
- Não deve haver um espaço após o parêntese de abertura.
- Não deve haver um espaço antes do parêntese de fechamento.
- A chave de fechamento deve estar na linha seguinte após o corpo.

Exemplo `if`, `elseif`, `else`

```php
<?php

// ruim
if($exp) $var=2;

// bom
if ($exp) {
    $var = 2;
}
```

Exemplo `foreach`

```php
<?php

// ruim
foreach($iterable as $key=>$value){
    // ...
}

// ruim
foreach($iterable as $key => $value)
{
    // ...
}

// bom
foreach ($iterable as $key => $value) {
    // ...
}
```

[[⬆ Topo]](#sum%C3%A1rio)
