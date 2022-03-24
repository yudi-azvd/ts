---
title: 'Testes de Software - TDD' 
numbersections: true

---

<!--
Link da entrega:
https://aprender3.unb.br/mod/assign/view.php?id=689081

Livro:
file:///home/yudi/Documents/3-recursos/livros/programming/Test-Driven%20Java%20Development%20Invoke%20TDD%20principles%20for%20end-to-end%20application%20development%20with%20Java%20Viktor%20Farcic,%20Alex%20Garcia%20.pdf

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

Livro: Test-Driven Java Development, capítulos 1, 3 e 6.

Os testes do livro foram implementados e estão no repositório
[yudi-azvd/tdd-java](https://github.com/yudi-azvd/tdd-java)

- Abraçar e aceitar **falha** como parte do desenvolvimento

- Testes são como uma documentação executável. Cada funcionalidade idealmente
possui um conjunto de testes que garantem o seu funcionamento e detalham o seu
funcionamento em certos casos teste

- Sessões de depuração são menos necessárias

- Deixa a refatoração mais fácil porque existe um conjunto de testes
que garante que o código continua funcionando como esperado

- Ajuda a criar um _design_ melhor de código porque incentiva a 
projetar classes e métodos do ponto de vista de quem os usa deixando
o casos de teste curtos e fáceis de entender.

- Incentiva baixo acoplamento

- Documentação atualizada

- Código teste realizado _depois_ da implementação tende a ser enviesado a 
confirmar o que a implementação faz, não necessariamente tentando encontrar erros

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

- Todos os testes devem passar antes antes de seguir para o próximo 
teste

- O importante é agilidade, o ciclo deve ser muito curto. Passar da fase de teste
para a fase de implementação deve levar alguns minutos ou segundos. Pode-se 
preocupar com organização do código na fase refatoração

    - ping (escrever um teste e rodar testes)
    - pong (implementar código)
    - ping (escrever mais um teste e rodar testes)
    - pong (implementar código)
    - ping (escrever mais um teste e rodar testes)
    - ponto (refatorar código e confirmar que testes continuam passando)
    - jogo rápido que nem tênis de mesa

- O objetivo principal do TDD é design de código testável com testes
como resultado secundário que garantem que um alerta vai tocar quando alguém
quebrar uma parte do código no futuro


### Mocks

- permite o design do código de forma que as dependências sejam facilmente
substituíveis porque é encorajado que fatores externos sejam removidos (conexão
com banco de dados, APIs, outros servidores e serviços)
- desenvolvimento e execução dos testes é mais rápido. Regra geral,
em TDD os testes devem executar em 10 a 15 segundos para manter a
sanidade e o engajamento dos desenvolvedores.
- se o teste for bem feito, o que é testado é apenas o código principal e não
as conexões com banco de dados ou outros servidores externos. O código é
**isolado** de todas as suas dependências

Dublês de teste têm os seguintes tipos:

- Dummy object: agir como subtituto para um argumento real de um método
- Stub: fornece a entrada desejada para o system under test (SUT)
- Spy: intercepta de saída indireta de outro componente chamado pelo SUT
- Mock: substitui um _objeto_ que é dependência do SUT para que seja verificado
que está sendo corretamente usado pelo SUT
- Fake: substitui um _componente_ que é dependência do SUT com uma implementação 
mais leve.

Páginas 135, 136.
<!-- Páginas 158, 159 -->

