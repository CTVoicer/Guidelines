# Geral

> Diretrizes gerais para escrever código bonito.

## Sumário

- [Idioma](#idioma)
- [Formatação](#formata%C3%A7%C3%A3o)
- [Ordenação](#ordena%C3%A7%C3%A3o)

[[⬅ Voltar para Estilo]](../estilo)

## Idioma

- Escreva código em inglês.
    - Todo código deve estar em inglês, incluindo nomes de variáveis e atributos de objetos.
    - Sinta-se livre para criar traduções se for realmente importante.
- Escreva comentários e documentação em português.
    - Para facilitar a leitura para toda a equipe, conteúdo de suporte ao código (documentação, comentários, commits) devem ser escritos em português.
    - Se este conteúdo já estiver em inglês, continue escrevendo em inglês. Evite misturar idiomas dentro de um mesmo arquivo.

[[⬆ Topo]](#sum%C3%A1rio)

## Formatação

- Fique atento aos erros de ortografia.

    ```javascript
    // ruim
    var mesage;

    // bom
    var message;
    ```

- Evite linhas com mais de 80 caracteres.
    - As vezes é inevitável, mas quase sempre podemos ser mais explícitos e coesos ao dividir o código em mais linhas.

    ```javascript
    // ruim
    var message = 'this is a very long message that will probably hurt this style guide so I can explain how to properly use it';

    // bom
    var message = 'this is a very long message that was broken '+
                  'to not hurt this style guide';
    ```

- Use espaços para indentação (não `tab`). De preferência use 2 espaços de indentação para arquivos JavaScript, JSON, CSS e HTML; e 4 espaços para arquivos PHP e Markdown.

    ```javascript
    for (var i = 0, len = obj.length; i < len; i++) {
    ∙∙console.log(obj[i]);
    }
    ```

    ```php
    <?php

    for ($i = 0; $i < count($arr); $i++) {
    ∙∙∙∙echo $arr[i];
    }
    ```

- Use linhas em branco em volta de blocos com múltiplas linhas.

    ```scss
    // ruim
    .user {
        border: 1px solid $white;
        color: $red;
    }
    .post {
        border: 1px solid $red;
        color: $white;
    }

    // bom
    .user {
        border: 1px solid $white;
        color: $red;
    }

    .post {
        border: 1px solid $red;
        color: $white;
    }
    ```

- Use espaços, eles são grandes amigos para melhorar a legibilidade do seu código.

    ```javascript
    // ruim
    var i,total=10,obj=[];
    for (i=0;i<total;i++){
        obj[i]=i;
    }

    // bom
    var i, total = 10, obj = [];
    for (i = 0; i < total; i++) {
        obj[i] = i;
    }
    ```

- Contudo, não use espaços depois de `(`, `[` ou antes de `]`, `)`  
(estou olhando pra vocês, desenvolvedores do WordPress).

    ```javascript
    // ruim
    console.log( messages[ 0 ] );

    // bom
    console.log(messages[0]);
    ```

- Evite abreviações. Prefira variáveis com nomes explicativos, mesmo que fiquem grandes. O tamanho do nome de uma variável não altera a performance do código, então, não precisa economizar letra.

    ```javascript
    // ruim
    var l = [],
        u = {},
        bul = [];

    // bom
    var list = [];
    var users = {};
    var blockedUsersList = [];
    ```

[[⬆ Topo]](#sum%C3%A1rio)

## Ordenação

- Ordene os métodos para que os métodos que chamam estejam logo acima dos métodos chamados ou o mais perto possível daqueles que eles chamam no escopo de um arquivo.
- Ordene declarações e blocos para que estejam perto de outras declarações e blocos dentro do mesmo contexto.
- Não use ordenação alfabética.

[[⬆ Topo]](#sum%C3%A1rio)
