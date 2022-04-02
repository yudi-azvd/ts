---
title: 'Testes de Software - TDD - Atividade 4' 
numbersections: true
---

<!--
Link da entrega:
https://aprender3.unb.br/mod/assign/view.php?id=691625

-->

**Disciplina**: Testes de Software

**Professor**: Elaine Venson

**Matrícula**: 160140410

**Aluno**: Yudi Yamame


# TDD - Atividade 4 - parcial 1

## Issue escolhida

Issue [#8539](https://github.com/JabRef/jabref/issues/8539) - Add 
www.biodiversitylibrary.org to the websearch options

### Especificação da issue

"A literatura mais antiga não é facilmente recuperada pelas bases de dados 
disponíveis (especialmente livros). Descreva a solução que você deseja. Adicione
https://www.biodiversitylibrary.org/bibliography aos bancos de dados disponíveis
para auxiliar na busca de material (neste caso, biologia)."

### Descrição da funcionalidade a ser desenvolvida

A nova funcionalidade deve adicionar a possibilidade de usar a Biodiversity Heritage 
Library (BHL) como banco de dados para pesquisa. A classe a ser desenvolvida
deve implementar a interface `SearchBasedFetcher` ou alguma de suas extensões:
`SearchBasedFetcher`, `SearchBasedParserFetcher`, `PagedSearchBasedFetcher` ou
`PagedSearchBasedParserFetcher`. Segundo um dos comentários da issue, a interface
provável é a `SearchBasedParserFetcher`.

A orientação geral para desenvolvedores pode ser encontrada 
[aqui](https://about.biodiversitylibrary.org/tools-and-services/developer-and-data-tools/#APIs)
e a documentação da API [aqui](https://www.biodiversitylibrary.org/docs/api3.html#top).

A API do BHL fornece apenas o que foi pedido na pesquisa para devolver informações
desnecessárias ao usuário. O usuário da API deve realizar chamadas em sucessão para
obter toda a informação que precisa.

## Requisitos

Nome provável da classe: `BHLFetcher`

### Autenticação

- Deve ser fornecida a chave de API como parâmetro de query para fazer a pesquisa.
- Deve lançar uma exceção se a chave de API for inválida.
- Deve lançar uma exceção se a chave de API tiver permissão o suficiente para o 
método.

## Pesquisa

- Deve lançar uma exceção se o método escolhido não existir.
- Deve retornar os BibEntries para uma determinada pesquisa de publicações
com o método `PublicationSearch` da API através de `searchterm`s.
- Deve retornar BibEntry para dado o ID de uma publicação.

### Observações

Até a próxima entrega serão adicionados mais requisitos. Vai ser possível 
entender melhor como funciona a API e seus mecanismos de pesquisa.