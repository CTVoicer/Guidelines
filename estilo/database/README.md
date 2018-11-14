# Banco de Dados

> Banco de dados consistente.

## Sumário

- [Banco de Dados](#banco-de-dados)
    - [Sumário](#sum%C3%A1rio)
    - [Modelagem](#modelagem)
    - [Nomes de tabelas](#nomes-de-tabelas)
    - [Chaves primárias](#chaves-prim%C3%A1rias)
    - [Chaves estrangeiras e índices](#chaves-estrangeiras-e-%C3%ADndices)
        - [Nome das colunas](#nome-das-colunas)
        - [Nome das chaves](#nome-das-chaves)
        - [Tabelas pivô](#tabelas-piv%C3%B4)
    - [Referências](#refer%C3%AAncias)

[[⬅ Voltar para Estilo]](https://github.com/CTVoicer/Guidelines/tree/master/estilo)

## Modelagem

Durante a modelagem do banco de dados, as nomeclaturas deverão seguir o mesmo exemplo do código-fonte dos projetos e deverão ser sempre em inglês (com excessão dos comentários/documentação).

Exemplo:

```sql
CREATE TABLE `flights` (
  `id` int(10) NOT NULL COMMENT 'Comentário em pt-br',
  `passenger` int(10) NOT NULL,
  `plane` varchar(10) COLLATE utf8mb4_unicode_ci NOT NULL,
  `plataforma` varchar(25) COLLATE utf8mb4_unicode_ci NOT NULL,
  `boarding_hours` timestamp DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```

[[⬆ Topo]](#sum%C3%A1rio)

## Nomes de tabelas

Por convenção, os nomes das tabelas são escritos no formato *snake_case* e no plural. Tabelas que fujam a esse padrão precisam ser explicitamente documentadas.

No caso do exemplo acima, podemos inferir que a tabela `flights` faz referência à *model* `Flight`. O contrário também é válido. Se temos uma *model* chamada `Order`, esperamos encontrar no banco de dados uma tabela com o nome `orders`.

[[⬆ Topo]](#sum%C3%A1rio)

## Chaves primárias

Por padrão, todas as tabelas deverão possuir uma coluna primária chamada `id`. Além do mais, assume-se que a *primary key* é um número inteiro com auto-incremento, o que significa que, dentro da aplicação, ele poderá ser entendido como um tipo *integer* sem efeitos colaterais.

Caso seja necessário criar uma excessão a essa regra, tudo deve ser devidamente documentado.

[[⬆ Topo]](#sum%C3%A1rio)

## Chaves estrangeiras e índices

### Nome das colunas

Por padrão, o nome da coluna de um relacionamento é baseado no nome da *model* em questão.

Se temos uma tabela de usuários (`users`), uma tabela de telefones (`phones`) e queremos relacionar um número de telefone a um determinado usuário, esperamos encontrar uma coluna chamada `user_id` dentro da tabela de telefones. Onde `user` é o nome da model da tabela de usuários e `id` é o nome da chave primária desta mesma tabela.

### Nome das chaves

Os índices e chaves estrangeiras devem seguir o seguinte padrão de nomeclatura: \<NOME\_DA\_TABELA\>\_\<NOME\_DA\_COLUNA\>\_\<INDEX\_OU\_FOREIGN\>.

Por exemplo, se queremos adicionar um índice para a coluna `email` dentro da tabela `users`, o nome do nosso índice será `users_email_index`.

Se queremos criar uma referencia à coluna `id` na tabela `users` partindo da coluna `user_id` dentro da tabela `posts`, o nome da foreign key será `posts_user_id_foreign`.

### Tabelas pivô

Em relacionamentos de *muitos para muitos*, onde um objeto pode estar relacionado a vários outros e vice-versa, geralmente usamos uma tabela intermediária chamada "pivô".

Um exemplo desse tipo de relacionamento acontece quando temos um usuário com muitas permissões e uma permissão pertencente a muitos usuários. Nesses casos temos 3 tabelas: `users`, `roles` e `role_user`. A tabela `role_user` é o nosso pivô. Seu nome é derivado da forma singular e em ordem alfabética das outras duas tabelas. Nesse caso, espera-se que a tabela pivô tenha as colunas `user_id` e `role_id`.

[[⬆ Topo]](#sum%C3%A1rio)

## Referências

- [Laravel - Database Migrations](https://laravel.com/docs/migrations): As diretrizes de nomes de tabelas e colunas obrigatórias foram baseadas nesse framework.
- [Laravel - Eloquent Relationships](https://laravel.com/docs/eloquent-relationships): As diretrizes de chaves primárias, chaves estrangeiras, índices e tabelas pivô também.

[[⬆ Topo]](#sum%C3%A1rio)
