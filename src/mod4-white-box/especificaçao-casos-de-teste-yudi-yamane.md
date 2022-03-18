---
title: 'Engenharia de Requisitos - Especificação dos casos de teste' 
---

<!--
./sh/md2pdf src/mod4-white-box/especificaçao-casos-de-teste.md 

Título: Especificação dos casos de teste

Objetivo: escolher método a ser testado e iniciar especificação dos casos de teste.

Instruções:

Analisar a cobertura de testes do projeto
Selecionar um método sem testes ou com pouca cobertura ou poucos casos de teste
Construir tabela identificando as decisões e condições do método, juntamente com as situações para que cada condição de cada decisão possa resultar e True e False (a exemplo do método BONUS)
Iniciar a especificação dos casos de teste (dados de entrada e saídas esperadas) atendendo às situações identificadas na tabela (a exemplo do método BONUS)

Entregáveis:

Captura de tela com o método selecionado (apresentando a numeração das linhas)
Tabela de decisões/condições e situações para resultar em Verdadeiro/Falso
Especificação dos casos de teste, indicando o mapeamento para as condições identificadas


Link da entrega:
https://aprender3.unb.br/mod/assign/view.php?id=684636

-->

**Disciplina**: Testes de Software

**Professor**: Elaine Venson

**Matrícula**: 160140410

**Aluno**: Yudi Yamame

<!-- 
Outros métodos interessantes

- MonthChecker.java
- Edition.java 
-->

# Especificação dos casos de teste

## Método escolhido
**`PdfAnnotationImporter.isSupportedAnnotionType`** da classe da classe:

`jabref/src/main/java/org/jabref/logic/pdf/PdfAnnotationImporter.java`. O código
segue assim:
<!-- 
```java
private boolean isSupportedAnnotationType(PDAnnotation annotation) {
  if (annotation.getSubtype() == null) {
    return false;
  }
  if ("Link".equals(annotation.getSubtype()) || "Widget".equals(annotation.getSubtype())) {
    LOGGER.debug(annotation.getSubtype() + " is excluded from the supported file annotations");
    return false;
  }
  try {
    if (!Arrays.asList(FileAnnotationType.values())
      .contains(FileAnnotationType.valueOf(annotation.getSubtype()))) {
      return false;
    }
  } catch (IllegalArgumentException e) {
    LOGGER.debug(String
      .format("Could not parse the FileAnnotation %s into any known FileAnnotationType. It was %s!", 
        annotation, annotation.getSubtype()));
  }
  return true;
}
``` -->

![Código fonte do método `isSupportedAnnotionType`.](./method.png)

Possíveis valores do `enum` `FileAnnotationType`:

```java
TEXT("Text", false),
HIGHLIGHT("Highlight", true),
SQUIGGLY("Squiggly", true),
UNDERLINE("Underline", true),
STRIKEOUT("StrikeOut", true),
POLYGON("Polygon", false),
POPUP("Popup", false),
LINE("Line", false),
CIRCLE("Circle", false),
FREETEXT("FreeText", false),
INK("Ink", false),
UNKNOWN("Unknown", false),
NONE("None", false);
```

\newpage
## Tabela de Condições

A coluna de linha da tabela \ref{tab:mult-cond} usa a notação `linha:i`, onde 
`linha` é o número da linha da decisão e `i` é a  i-ésima condição dessa decisão.

Table: Mútiplas condições \label{tab:mult-cond}

| Linha | Condição                              | Situação para Verdadeiro              | Situação para Falso                   |
| ----- | ------------------------------------- | ------------------------------------- | ------------------------------------- |
| 71    | `annotation.getSubtype() == null`     | `annotation.getSubtype() == null`     | `annotation.getSubtype() != null`     |
| 74.1  | `annotation.getSubtype() == "Link"`   | `annotation.getSubtype() == "Link"`   | `annotation.getSubtype() != "Link"`   |
| 74.2  | `annotation.getSubtype() == "Widget"` | `annotation.getSubtype() == "Widget"` | `annotation.getSubtype() != "Widget"` |
| 79    | valores de FileAnnotationType **não** | valores de FileAnnotationType **não** | valores de FileAnnotationType         |
|       | contém o subtipo de `annotation`      | contém o subtipo de `annotation`      | **contém** o subtipo de `annotation`  |

## Especificação de casos de teste

A 2ª coluna da Tabela \ref{tab:tests-spec}, indica quais condições e seus devidos 
resultados são cobertos pelo caso de teste usando o seguinte formato: 
`linha:booleano`. Exemplo: 71:F indica o condição da linha 72 (tabela \ref{tab:mult-cond})
com a situação para Falso.

Vale ressaltar que a combinação das condições 74.1:V e 74.2:V é impossível de 
acontecer porque `annotation.getSubType()` não pode ser igual a `"Link"` e 
`"Widget"` ao  mesmo tempo.

Table: Especificação dos casos de teste \label{tab:tests-spec}

| Caso de teste | Condições cobertas         | Entrada                               | Saída esperada |
| ------------- | -------------------------- | ------------------------------------- | -------------- |
| 1             | 71:F                       | `annotation = null`                   | `false`        |
| 2             | 71:V, 74.1:V, 74.2:F       | `annotation.subType = "Link"`         | `false`        |
| 3             | 71:V, 74.1:F, 74.2:V       | `annotation.subType = "Widget"`       | `false`        |
| 4             | 71:V, 79:V, 71.4:F, 74.2:F | `annotation.subType = "Non-existent"` | `false`        |
| 5             | 71:V, 79:F, 71.4:F, 74.2:F | `annotation.subType = "Text"`         | `true`         |

O caso de teste 5 cobre a combinação 71.4:F, 74.2:F redundantemente.