---
title: 'Atividade de Aplicação - Módulo 2'
# https://stackoverflow.com/questions/24208889/how-to-specify-numbered-sections-in-pandocs-front-matter
numbersections: true
---

**Disciplina**: Testes de Software - Turma A

**Professora**: Elaine Venson

**Matrícula**: 160140410

**Aluno**: Yudi Yamame


<!-- 
Link de entrega parcial:
https://aprender3.unb.br/mod/assign/view.php?id=677989

Link da atividade:
https://aprender3.unb.br/mod/assign/view.php?id=677981

Objetivo: realizar testes funcionais na aplicação.

Instruções:

Defina o projeto OSS a ser utilizado na atividade. Preencha o nome e a URL do GitHub na planilha "Equipes - Turma A" no Teams.
Navegue pela documentação do usuário do projeto e escolha uma funcionalidade para testar. Cada membro da equipe deve escolher uma funcionalidade distinta dos demais. A funcionalidade deve ser minimamente complexa para gerar ao menos 6 casos de teste.
Leia atentamente a especificação da funcionalidade e identifique as condições de entrada e as condições de saída. Observe que a maioria dos projetos não terá uma especificação explícita. De forma geral, informações sobre o comportamento esperado das funcionalidades podem ser encontradas no manual do usuário, wiki, site de documentação ou outras ferramentas utilizadas pelo projeto. Na falta de informações claras, a equipe pode utilizar o bom senso e fazer suposições sobre as condições de entrada.
A partir das condições de entrada e de saída, identifique as classes de equivalência válidas e inválidas.
Escreva casos de teste cobrindo o máximo de classes válidas, aplicando as técnicas de particionamento de equivalência e análise de valor limite.
Escreva um caso de teste para cada classe inválida, aplicando a análise de valor limite.
Execute os casos de teste e reporte os resultados da execução.
Entrega:

Relatório contendo as seguintes informações:

Identificação da funcionalidade escolhida e especificação da funcionalidade (pode ser copiado da documentação ou escrita por você).
Tabela com as condições de entrada, identificando e numerando as classes válidas e inválidas.
Especificação dos casos de teste. Cada caso de teste deve apresentar: número do caso de teste, quais classes de equivalência está cobrindo, dados de entrada, saída esperada e procedimento para executar o teste (passo-a-passo para executar a funcionalidade com os dados de entrada).
Resultados da execução: cada caso de teste deve apresentar as seguintes informações: resultado geral (sucesso ou falha) e no caso de falha qual o resultado obtido que é diferente do esperado.
Capturas de tela mostrando a execução dos testes (telas com os dados de entrada, telas com os dados de saída e telas intermediárias se necessário).
 -->


# Projeto Open Source

O projeto escolhido pelo grupo foi o [JabRef](https://github.com/JabRef/jabref).
Os testes podem ser executados rodando

```
./gradlew test
```

# Funcionalidade

Não determinei a funcionalidade específica mas estou entre alugmas das funcionalidades
das actions como `NewEntryAction` e `ImportAction`.

# Condições de entrada

Para o caso de `NewEntryAction`, as condições de entrada são baseadas no ações do 
mouse do usuário. Usuário pode escolher gerar uma nova entrada ou cancelar a adição,
além de escolher as características da entrada.

(A escolha dessa funcionalidade ainda pode mudar)
