# Git

> Git do jeito correto.

## Sumário

- [Mantendo um repositório](#mantendo-um-reposit%C3%B3rio)
- [Commits](#commits)
- [Fluxo](#fluxo)
- [Dicas de leitura](#dicas-de-leitura)
- [Referências](#refer%C3%AAncias)

[[⬅ Voltar para Boas Práticas]](../boas-praticas)

## Mantendo um repositório

- Evite versionar arquivos específicos do seu computador ou processo de desenvolvimento.
- Trabalhe sempre em uma *feature branch*.
- Exclua branches locais de features que já foram mescladas à brach `master`.
- Baixe atualizações dos remotes frequentemente. Prefira `git pull --rebase`, para evitar merges desnecessários.

[[⬆ Topo]](#sum%C3%A1rio)

## Commits

- Use mensagens em português.

- Escreva uma boa mensagem de commit. Título com até 50 caracteres iniciando com letra maiúscula no [presente do indicativo](https://www.conjugacao.com.br/presente-do-indicativo/) e sem ponto final. [(?)](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)
    - Formato de exemplo:

        ```
        Resumo no presente com menos de 50 caracteres

        Se necessário, escreva mais texto explicativo para documentar
        as suas mudanças.

        * Mais informações sobre o commit (até 72 caracteres).
        * Etc...

        Ref.: http://project.management-system.com/ticket/123
        ```

- Evite utilizar `git commit -m ""`. Este comando impede que você escreva mensagens com múltiplas linhas com facilidade. Sem o `-m`, você escreverá suas mensagens num editor de textos.

- Prefira `git commit --verbose`. Este comando fará com que você veja o diff dos arquivos a serem commitados. É uma grande facilidade.

- Procure responder as seguintes perguntas na sua mensagem de commit: [(?)](http://robots.thoughtbot.com/5-useful-tips-for-a-better-commit-message)
    1. Por que essa alteração é necessária?
    2. Como essa alteração resolve o problema?
    3. Quais os efeitos colaterais desta alteração?

[[⬆ Topo]](#sum%C3%A1rio)

## Fluxo de trabalho

1. Atualize seu repositório local ou clone um remoto.
    - Clonando repositório remoto:

        ```
        git clone <git-url>
        cd <project-name>
        ```

    - Atualizando repositório local:

        ```
        git checkout master
        git pull --rebase
        ```

2. Crie uma *feature branch* local.

    ```
    git checkout -b <branch-name>
    ```

3. Realize um *rebase* frequentemente para incorporar mudanças.

    ```
    git fetch origin
    git rebase origin/master
    ```

4. Adicione suas alterações.

    ```
    git add .
    ```

5. Escreva uma [boa mensagem de commit](#commits).

6. Compartilhe a sua branch.

    ```
    git push origin <branch-name>
    ```

7. Após o merge da feature com a branch master, remova sua branch local.

    ```
    git branch -D <branch-name>
    ```

[[⬆ Topo]](#sum%C3%A1rio)

## Dicas de leitura

- [git-useful](https://github.com/hugobessaa/git-useful), lista com comandos úteis para usar o git no CLI.
- [Every line of code is always documented](http://mislav.uniqpath.com/2014/02/hidden-documentation/)

[[⬆ Topo]](#sum%C3%A1rio)

## Referências

- [Guides por Toughtbot](https://github.com/thoughtbot/guides/tree/master/protocol/git): Este guia também é uma adaptação do Guides da Thoughtbot.
- [git-useful](https://github.com/hugobessaa/git-useful): Uma lista de comandos úteis para utilizar git no Terminal.

[[⬆ Topo]](#sum%C3%A1rio)
