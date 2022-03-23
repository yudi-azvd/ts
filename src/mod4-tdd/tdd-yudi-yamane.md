---
title: 'Testes de Software - TDD' 
numbersections: true

---

<!--
Link da entrega:
https://aprender3.unb.br/mod/assign/view.php?id=689081

-->

**Disciplina**: Testes de Software

**Professor**: Elaine Venson

**Matrícula**: 160140410

**Aluno**: Yudi Yamame

<!-- 

3) Enviar nesta tarefa do Moodle:

- Um resumo dos passos realizados no vídeo para a construção da calculadora de imposto de renda;
- Um resumo da técnica TDD;
- Um resumo sobre os tipos de Mock (dublês de teste). 

-->

# Test Driven Development 

## Calculadora de imposto de renda

Sobre o vídeo do professor Llana:

1. entender as especificações do problema, ou seja, enteder como funciona o 
cálculo do imposto de renda.
    - nessa etapa é interessante fazer uma lista de requisitos ou funcionalidades
    para ser consultada durante o desenvolvimento.
1. começar com testes falhando
    - método pode começar retornando simplesmente um valor _hard coded_ (ténica de 
    falsificação)
1. acrescentar um caso de teste que introduz uma falha
1. corrigir código
1. testes devem estar passando
1. repetir passos 3 a 5 até o módulo estar com todas as funcionalidades 
funcionando e testes passando

## TDD

Livro: Test-Driven Java Development

- Abraçar e aceitar **falha** como parte do desenvolvimento

- Testes são como uma documentação executável

- Sessões de depuração são menos necessárias

- Deixa a refatoração mais fácil porque existe um conjunto de testes
que garante que o código continua funcionando como esperado

- Ajuda a criar um _design_ melhor de código porque incentiva a 
projetar classes e métodos do ponto de vista de quem os usa deixando
o casos de teste curtos e fáceis de entender.

- Incentiva baixo acoplamento

- Documentação atualizada

### Ciclo _red-green-refactor_

1. Escreva um teste
2. Execute todos os testes
3. Escreva o código de implementação
4. Execute todos os testes
5. Refatore
6. Execute todos os testes

- O primeiro teste deve ser um teste que **falha**

- "If a fix is not done in a matter of minutes, the best thing to do is to revert the changes. After all, everything worked not long ago. Implementation that broke something is obviously wrong, so why not go back to where we started and think again about the correct way to implement the test?"

- Não faça a implementação do testes final a implementação definitiva, 
nem tente escrever o código perfeito. Apenas escrever código o suficiente para o teste passar

- O importante é agilidade, o ciclo deve ser muito curto. Pode se 
preocupar com organização do código na fase refatoração


### Mocks