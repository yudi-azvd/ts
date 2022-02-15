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
- são determinadas as input conditions e, a partir delas, as classes de equivalência, 
identificando cada classe com um número único.
    - então escreve-se um teste cobrindo uma ou mais classes de equivalência.
    - usando o exemplo do livro (The Art of Software Testing), o teste para a entrada `DIMENSION A(2)` cobre as
    classes 1, 4, 7, 10, 12, 15, 24, 28, 29, and 43.
    - com uma entrada da forma

```
DIMENSION A 12345 (I,9,J4XXXX,65535,1,KLM,
X,1000, BBB(-65534:100,0:1000,10:10, I:65535)
```

cobre as classes de equivalência válidas restantes. Então pode-se escrever um caso de teste
para cada classe de equivalência inválida. 

```
 (3): DIMENSION
 (5): DIMENSION (10)
 (6): DIMENSION A234567(2)
 (9): DIMENSION A.1(2)
(11): DIMENSION 1A(10)
... outras casos de teste para as classes de equivalência ... 
(37): DIMENSION D(A(2):4)
(38): D(.:4)
(43): DIMENSION D(0)
```

Ao todo, temos 17 casos de teste que cobrem as 43 classes de equivalências, válidas
e inválidas.

- exemplos:
    - se uma entrada de programa é esperada no intervalo 0 \< x \< 99, então
    esse intervalo é representa uma classe de equivalência válida.
    Se a entrada = 5 é testada, a entrada = 89 não precisa ser testada.
    Por outro lado os intervalos x \< 0 e 99 \< x são classes de equivalência inválidas.
    - entrada do programa esperado é uma letra: classe de equivalência válida. 
    Se a entrada do programa não é uma letra: classe de equivalência inválida.

### Análise de valor limite

- de modo geral, casos de teste que exploram condições limite tem resultado melhor
do que casos de testes que o fazem.
- são casos em que a entrada estão ligeiramente acima ou abaixo do valor limite.
- cada "aresta" de uma classe de equivalência é um objeto de teste
- além de prestar atenção apenas aos valores de entrada, essa análise também
explora o espaço do _resultado_
- regras gerais:
    1. se a **entrada** vai estar em um intervalo, \[1, 100\], escrever casos de teste
    para entrada = 0, 1, 100, 101.
    1. se a **entrada** é um conjunto de valores limitados, testes os casos
        - nenhum valor
        - um valor a mais que o limite máximo
        - um valor a menos que o limite mínimo
        - um valor além do limite máximo + 1
    1. usar as regras 1 e 2 para condições **saída** também.
    1. se a entrada é um conjunto de valores ordenados, teste o primeiro
    e último elementos.
    1. explore outras condições limite com sua ingenuidade.

### Grafos de causa e efeito

- testa a combinação de condições de entrada, onde análise de valor limite
e particionamento de equivalência têm pouca eficácia.
- usa a linguagem formal grafo de causa-efeito. 

### Chute/advinhação de erro

- Vai do domínio que o testador tem sobre o domínio do problema, de sua criatividade
e experiência chutar casos de teste que simplesmente encontram falhas.
- casos como entrada = 0 ou entrada = None | \[1\] são tendenciosos a ter erros,
por isso escreve-se testes para esse casos.


## Exemplos: pesquise na internet e apresente exemplos de aplicação das técnicas caixa-preta “Particionamento de Equivalência” e “Análise de Valor Limite”

### Particionamento de Equivalência

Classes de equivalência para ano (year):

- Y1 = {century years divisible by 400} i.e., century leap years
- Y2 = {century years not divisible by 400} i.e., century
common years
- Y3 = {non-century years divisible by 4} i.e., ordinary leap
years
- Y4 = {non-century years not divisible by 4} i.e., ordinary
common years 

Referência: [slide](https://people.eecs.ku.edu/~hossein/Teaching/Fa14/814/Lectures/Jorgensen/06.pdf), página 24.

### Análise de valor limite

Exemplo de um montador de assembly hipotético.

```cpp
// isvalidsymbol.ut.cpp
TEST_CASE("should not accept symbols longer than 50 characters") {
  Scanner scanner;
  std::string veryLongSymbol = "sal_dfjlskjfksljflksjdlfkjsljf"
    "ad_askd_lkas_da_sdk_lasdk";

  INFO("veryLongSymbol length:", veryLongSymbol.size());
  CHECK_FALSE(scanner.isValidSymbol(veryLongSymbol));
}
```

Além desse teste, também deveria ter os testes

- símbolo com nenhum caractere
- símbolo com 1 caractere
- símbolo com 51 caracteres

[Repositório](https://github.com/yudi-azvd/hassembler) (não tá na `main`. Tá em outra
branch `integrate-hasm-data-to-assembler` que provavelmente vai sumir no futuro)


### Análise de Valor Limite