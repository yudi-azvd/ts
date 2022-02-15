---
title: 'Caixa Preta: 14/02 Preparação Individual assíncrona'
# https://stackoverflow.com/questions/24208889/how-to-specify-numbered-sections-in-pandocs-front-matter
numbersections: true
---

**Disciplina**: Testes de Software

**Professora**: Elaine Venson

**Matrícula**: 160140410

**Aluno**: Yudi Yamame

# Testes de Caixa Preta

<!-- 
Link de entrega
https://aprender3.unb.br/mod/assign/view.php?id=672369 

Capítulo 4 (Test-Case Design) do livro do Mayers (The Art of Software Testing), seções:
Introdução (texto inicial)
Black-Box Testing 

Capítulo 6 (Higher-Order Testing) do livro do Mayers (The Art of Software Testing), seções:
Introdução (texto inicial)
Function Testing

-->


## Um resumo das técnicas caixa preta para a elaboração de casos de teste
<!-- De modo geral, é interessante usar técnicas de teste de
caixa preta e complementar com técnicas de testes caixa branca -->
Caixa preta/entrada e saída/dirigido a dados. Se preocupa se determinada
entrada gera a saída correta.

Apresentadas pelo livro são 4 técnicas:

- Particionamento de equivalência
- Análise de valor limite
- Grafos de causa e efeito
- Chute/advinhação de erro


### Particionamento de equivalência

- reduz a quatidade de testes, dividindo o domínio do programa em um número finito classes de equivalência (de preferência com o
mínimo de sobreposição possível), em que o teste de um valor de uma classe é equivalente ao teste do valor da mesma classe.
- se um teste detectou um erro em um caso, podemos assumir com razoável certeza que o mesmo erro seria detectado 
testando outro caso da mesma classe de equivalência.

### Análise de valor limite

### Grafos de causa e efeito

### Chute/advinhação de erro


## Exemplos: pesquise na internet e apresente exemplos de aplicação das técnicas caixa-preta “Particionamento de Equivalência” e “Análise de Valor Limite”

### Particionamento de Equivalência

- Y1 = {century years divisible by 400} i.e., century leap years
- Y2 = {century years not divisible by 400} i.e., century
common years
- Y3 = {non-century years divisible by 4} i.e., ordinary leap
years
- Y4 = {non-century years not divisible by 4} i.e., ordinary
common years 

Referência: [slide](https://people.eecs.ku.edu/~hossein/Teaching/Fa14/814/Lectures/Jorgensen/06.pdf), página 24.

### Análise de Valor Limite