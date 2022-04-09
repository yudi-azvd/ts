---
title: 'Testes de Software - TDD - Atividade 4 - Final' 
numbersections: true
---

<!--
Link da entrega:
https://aprender3.unb.br/mod/assign/view.php?id=691622

-->

**Disciplina**: Testes de Software

**Professor**: Elaine Venson

**Matrícula**: 160140410

**Aluno**: Yudi Yamame

# Breve observação

É recomendado olhar no seu visualizador de PDF o outline do documento para navegar
facilmente entre os ciclos.

# Issue escolhida

Issue [#8539](https://github.com/JabRef/jabref/issues/8539) - Add 
www.biodiversitylibrary.org to the websearch options

## Especificação da issue

"A literatura mais antiga não é facilmente recuperada pelas bases de dados 
disponíveis (especialmente livros). Descreva a solução que você deseja. Adicione
https://www.biodiversitylibrary.org/bibliography aos bancos de dados disponíveis
para auxiliar na busca de material (neste caso, biologia)."

## Descrição da funcionalidade a ser desenvolvida

(Essa parte é igual à entrega parcial 1. Pode pular)

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

# Requisitos

- Deve retornar o nome ao ser invocado o método `.getName()` (importante para o usuário saber
qual é o banco de dados que vai ser usado para a pesquisa)
- Deve fazer o parse da resposta JSON que API devolve.
- Deve utilizar a URL correta para fazer a pesquisa.

# Usando o TDD

A prática do TDD foi semelhante à prática apresentada no capítulo 3 do livro 
_Test-Driven Java Development_. 

- Escrever a especificação da funcionalidade no código
de teste
- Executar testes pra verificar que não há falso positivo
- Implementar funcionalidade (diferente do livro, não segui muito a proposta do
implementar apenas o necessário para passar)
- Executar testes novamente para verificar o funcionamento correto.
- Refatorar código (fiz isso apenas algumas vezes)

O jogo rápido de ping pong mencionado no livro não transpareceu durante a realização
dessa atividade.  Eu tinha wue ficar alternando entre os arquivos do projeto para
entender o que eu devia fazer.

# Execução do TDD

## Ciclo 1

Requisito básico: deve retornar o nome ao ser invocado o método `.getName()`.

### Especificação do requisito em teste

Especificação do teste na figura \ref{fig:tdd-p2-c1-spec}.

![Ciclo 1, especificação do teste\label{fig:tdd-p2-c1-spec}](./tdd-p2-c1-spec.png){ width=600 }

Nesse ponto, `BHLFetcher` está assim

```java
package org.jabref.logic.importer.fetcher;
import org.jabref.logic.importer.SearchBasedParserFetcher;

public class BHLFetcher implements SearchBasedParserFetcher {

}
```

### Vermelho

Rodar os testes gera um erro de compilação, como mostrado na figura \ref{fig:tdd-p2-c1-red-1}:

![Ciclo 1, vermelho\label{fig:tdd-p2-c1-red-1}](./tdd-p2-c1-red-1.png){ width=600 }

Para compilar, `BHLFetcher` deve implementar corretamente a interface 
`SearchBasedParserFetcher`, o que resulta em:

```java
package org.jabref.logic.importer.fetcher;

import java.net.MalformedURLException;
import java.net.URISyntaxException;
import java.net.URL;
import org.jabref.logic.importer.FetcherException;
import org.jabref.logic.importer.Parser;
import org.jabref.logic.importer.SearchBasedParserFetcher;
import org.apache.lucene.queryparser.flexible.core.nodes.QueryNode;

public class BHLFetcher implements SearchBasedParserFetcher {
  @Override
  public Parser getParser() {
    return null;
  }

  @Override
  public URL getURLForQuery(QueryNode luceneQuery) throws URISyntaxException, 
    MalformedURLException, FetcherException 
  {
    return null;
  }

  @Override
  public String getName() {
    return null;
  }
}
```

Rodar os testes novamente resulta em um erro diferente, figura \ref{fig:tdd-p2-c1-red-2}.
Dessa vez está sendo dito que a string esperada é diferente da string resultante.

![Ciclo 1, ainda vermelho\label{fig:tdd-p2-c1-red-2}](./tdd-p2-c1-red-2.png){ width=600 }

### Verde

Para fazer os testes passarem, basta modificar o método `getName()`


```java
package org.jabref.logic.importer.fetcher;

// import ...

public class BHLFetcher implements SearchBasedParserFetcher {
  // ...
  @Override
  public String getName() {
    return "Biodiversity H. Library";
  }
}
```

Rodando os testes agora passamos para a fase verde. Como o código até o momento
é muito simples, não é necessária refatoração ou limpeza.

## Ciclo 2

Requisito de pesquisa

### Especificação do teste

![Ciclo 2, especificação do teste\label{fig:tdd-p2-c2-spec}](./tdd-p2-c2-spec.png){ width=600 }

### Vermelho

Rodar os testes resulta em

![Ciclo 2, vermelho\label{fig:tdd-p2-c2-red-1}](./tdd-p2-c2-red-1.png){ width=600 }

A `url` retornada na linha 35 da figura \ref{fig:tdd-p2-c2-red-1} é nula porque 
o método ainda não foi implementado.

### Verde

Para fazer os testes passarem, foi implmentado o seguinte:

```java
public class BHLFetcher implements SearchBasedParserFetcher {
  final String API_KEY = new BuildInfo().bhlAPIKey;
  private final String SEARCH_URL = "https://www.biodiversitylibrary.org/api3?";

  // ...

  @Override
  public URL getURLForQuery(QueryNode luceneQuery) throws URISyntaxException, MalformedURLException,
   FetcherException 
  {
    URIBuilder uriBuilder = new URIBuilder(SEARCH_URL);
    uriBuilder.addParameter("op", "PublicationSearch");
    uriBuilder.addParameter("searchterm", new DefaultQueryTransformer().
      btransformLuceneQuery(luceneQuery).orElse(""));
    uriBuilder.addParameter("searchtype", "C");
    uriBuilder.addParameter("page", "1");
    uriBuilder.addParameter("pageSize", "10");
    uriBuilder.addParameter("apikey", API_KEY);
    uriBuilder.addParameter("format", "json");

    return uriBuilder.build().toURL();
  }
}
```

E os testes passaram.


## Ciclo 3

Converter resposta de JSON para para Bibtex.

### Especificação do teste

![Ciclo 3, especificação do teste\label{fig:tdd-p2-c3-spec}](./tdd-p2-c3-spec.png){ width=600 }

Esse teste verifica se parser consegue converter um objeto JSON em uma entrada Bib.
Esse JSON foi retirado de uma resposta da API. A parte principal da resposta
está no vetor `"Result"` (originalmente `"Result"` vem com vários objetos, mas deixei
apenas o primeiro para o caso de teste).


### Vermelho

Executar os testes resulta em um erro de compilação: o método `parseBHLJSONToBibtex`
não existe.

![Ciclo 3, vermelho\label{fig:tdd-p2-c3-red-1}](./tdd-p2-c3-red-1.png){ width=600 }


Implementando o mínimo do método `parseBHLJSONToBibtex` em `BHLFetcher` temos o seguinte

```java
public class BHLFetcher implements SearchBasedParserFetcher {
  // ...
  public static BibEntry parseBHLJSONToBibtex(JSONObject jsonObject) {
    BibEntry bibEntry = new BibEntry();
    return bibEntry;
  }
}
```

Rodar os testes novamente resulta em um erro de asserção:

![Ciclo 3, vermelho 2\label{fig:tdd-p2-c3-red-2}](./tdd-p2-c3-red-2.png){ width=600 }

A asserção falha porque o código implementado apenas retorna uma `BiBEntry` vazia.
Para corrigir isso, vamos acrecentar o seguinte código.


```java
public static BibEntry parseBHLJSONToBibtex(JSONObject bhlJSONResult) {
  BibEntry bibEntry = new BibEntry();

  if (bhlJSONResult.has("Date")) {
    bibEntry.setField(StandardField.DATE, bhlJSONResult.getString("Date"));
  }
  return bibEntry;
}
```

Agora o método `parseBHLJSONToBibtex` itera no vetor `"Result"`. Em uma pesquisa por termos,
esse vetor pode vir preenchido com vários objetos, por isso o loop é necessário.

Executar os testes retorna outro erro:

![Ciclo 3, vermelho 3\label{fig:tdd-p2-c3-red-3}](./tdd-p2-c3-red-3.png){ width=600 }

Aparentemente, o campo da data foi extraído corretamente. Agora a próxima asserção sobre o nome
do autor é que está falhando. O método foi modificado assim:

```java
public static BibEntry parseBHLJSONToBibtex(JSONObject bhlJSONResult) {
  BibEntry bibEntry = new BibEntry();

  if (bhlJSONResult.has("Date")) {
    bibEntry.setField(StandardField.DATE, bhlJSONResult.getString("Date"));
  }
  if (bhlJSONResult.has("Authors")) {
    JSONArray authors = bhlJSONResult.getJSONArray("Authors");
    List<String> authorsList = new ArrayList<>();
    for (int j = 0; j < authors.length(); j++) {
      if (authors.getJSONObject(j).has("Name")) {
        authorsList.add(authors.getJSONObject(j).getString("Name"));
      } else {
        LOGGER.info("Empty author name.");
      }
    }
    bibEntry.setField(StandardField.AUTHOR, String.join(" and ", authorsList));
  } else {
    LOGGER.info("No author found.");
  }
  return bibEntry;
}
```

O que mudou foi a verificação por um campo `"Authors"` na 
linha `if (bhlJSONResult.has("Authors")`.

Rodar os testes novamente resulta em outro erro:

![Ciclo 3, vermelho 4\label{fig:tdd-p2-c3-red-4}](./tdd-p2-c3-red-4.png){ width=600 }

O erro agora é sobre campo título. Vamos repetir esse processo para 
todos os campos restantes. 

### Verde
O seguinte código faz os testes passarem.

```java
public static BibEntry parseBHLJSONToBibtex(JSONObject bhlJSONResult) {
  BibEntry bibEntry = new BibEntry();

  if (bhlJSONResult.has("Date")) {
    bibEntry.setField(StandardField.DATE, bhlJSONResult.getString("Date"));
  }
  if (bhlJSONResult.has("Authors")) {
    JSONArray authors = bhlJSONResult.getJSONArray("Authors");
    List<String> authorsList = new ArrayList<>();
    for (int j = 0; j < authors.length(); j++) {
      if (authors.getJSONObject(j).has("Name")) {
        authorsList.add(authors.getJSONObject(i).getString("Name"));
      } else {
        LOGGER.info("Empty author name.");
      }
    }
    bibEntry.setField(StandardField.AUTHOR, String.join(" and ", authorsList));
  } else {
    LOGGER.info("No author found.");
  }
  if (bhlJSONResult.has("Title")) {
    bibEntry.setField(StandardField.TITLE, bhlJSONResult.getString("Title"));
  }
  if (bhlJSONResult.has("PartUrl")) {
    bibEntry.setField(StandardField.URL, bhlJSONResult.getString("PartUrl"));
  }
  if (bhlJSONResult.has("Series")) {
    bibEntry.setField(StandardField.SERIES, bhlJSONResult.getString("Series"));
  }
  if (bhlJSONResult.has("Volume")) {
    bibEntry.setField(StandardField.VOLUME, bhlJSONResult.getString("Volume"));
  }
  return bibEntry;
}
```

### Refatoração

As extrações dos campos de data, URL, volume, série e título são muito similares.
Podemos colocar os campos em um mapa que mapeia de `Field` para uma `String` do
JSON.

```java
public static BibEntry parseBHLJSONToBibtex(JSONObject jsonObject) {
  BibEntry bibEntry = new BibEntry();
  Map<Field, String> fieldToBHL = new HashMap<>();
  fieldToBHL.put(StandardField.DATE, "Date");
  fieldToBHL.put(StandardField.VOLUME, "Volume");
  fieldToBHL.put(StandardField.TITLE, "Title");
  fieldToBHL.put(StandardField.SERIES, "Series");
  fieldToBHL.put(StandardField.URL, "PartUrl");

  if (bhlJSONResult.has("Authors")) {
    JSONArray authors = bhlJSONResult.getJSONArray("Authors");
    List<String> authorsList = new ArrayList<>();
    for (int j = 0; j < authors.length(); j++) {
      if (authors.getJSONObject(j).has("Name")) {
        authorsList.add(authors.getJSONObject(i).getString("Name"));
      } else {
        LOGGER.info("Empty author name.");
      }
    }
    bibEntry.setField(StandardField.AUTHOR, String.join(" and ", authorsList));
  } else {
    LOGGER.info("No author found.");
  }

  for (var entry : fieldToBHL.entrySet()) {
    Field field = entry.getKey();
    String bhlName = entry.getValue();
    if (bhlJSONResult.has(bhlName)) {
      String text = bhlJSONResult.getString(bhlName);
      if (!text.isEmpty()) {
        bibEntry.setField(field, text);
      }
    }
  }

  return bibEntry;
}
```

E os testes continuam passando. A vantagem de fazer assim é que se for necessário
extrair mais um campo do JSON só precisamos adicionar no mapa `fieldToBHL` o tipo
de campo Bib e a string que aparece no JSON.

![Ciclo 3, verde](./tdd-final-verde.png){ width=600 }

[Código de teste](https://github.com/yudi-azvd/jabref/blob/add-biodiversity-library/src/test/java/org/jabref/logic/importer/fetcher/BHLFetcherTest.java).

[Código fonte](https://github.com/yudi-azvd/jabref/blob/add-biodiversity-library/src/main/java/org/jabref/logic/importer/fetcher/BHLFetcher.java).


# Trabalhos futuros

(nas férias quem sabe)

- Deve retornar BibEntry dado o ID de uma publicação.
- Deve retornar os BibEntries para uma determinada pesquisa de publicações
com o método `PublicationSearch` da API através de `searchterm`s.
- Fazer funcionar de ponta a ponta, com interação com a interface
gráfica. Eu tentei brevemente, mas dá um erro de SSL no download 
das informações.