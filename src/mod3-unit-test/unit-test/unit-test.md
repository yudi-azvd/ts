---
title: 'Aula 15 - Preaparação individual'
# https://stackoverflow.com/questions/24208889/how-to-specify-numbered-sections-in-pandocs-front-matter
numbersections: true
---

<!-- 

link para entrega:
https://aprender3.unb.br/mod/assign/view.php?id=682218

Realizar as seguintes atividades:

1) Leituras:

Capítulo 4 (Test-Case Design) do livro do Mayers (The Art of Software Testing), seção "White-Box Testing”.
Capítulo 5 (Module/Unit Testing) do livro do Mayers (The Art of Software Testing), todo o capítulo. Em especial, procure entender o exemplo da função BONUS que exemplifica os métodos introduzidos no capítulo 4.

2) Enviar nesta tarefa do Moodle:

Um resumo das técnicas caixa branca para a elaboração de casos de teste;
Responda: se você fosse planejar testes caixa-branca para um método complexo que você está desenvolvendo, qual (ou quais) técnica(s) escolheria e por quê? -->

**Disciplina**: Testes de Software - Turma A

**Professora**: Elaine Venson

**Matrícula**: 160140410

**Aluno**: Yudi Yamame

# Técnicas de caixa branca e testes de módulo/unidade


## Cap 4 - Testes Case design: white-box

Se chama white-box (deveria ser chamado transparent-box) porque o testador vai 
validar o fluxo do programa, em vez de comparar apenas entrada e saída como é 
feito nas técnicas de black-box.

- **cobertura de statements**: devem ser escritos casos de teste de maneira que  todo
statement deve ser executado pelo menos uma vez. Não é eficaz.

- **cobertura de decisões**: devem ser escritos casos de teste de maneira que toda 
decisão (if, do-while, switch) tenha um resultado verdadeiro e outro falso. Por
consequência, todo statement também vai ser executado pelo menos uma vez.

- **cobertura de condições**: devem ser escritos casos de teste de maneira que
cada condição em uma decisão se passe por todos os resultados possíveis pelo
menos uma vez. Exemplo

```
DO K=0 to 50 WHILE (J+K<QUEST)
```

As condições são

1. `K <= 50`
1. `K > 50`
1. `J + K < QUEST`
1. `J + K >= QUEST`

- **cobertura de condições/decições**: devem ser escritos casos de teste de maneira
que cada condição em uma decisão tome todas os resultados possíveis ao menos
uma vez, que cada decisão tome todos os resultados possíveis ao menos uma vez e 
que todos os pontos de entrada sejam invocados ao menos uma vez.

- **cobertura por condições múltiplas**: devem ser escritos casos de teste de maneira
que todas as combinações possíveis de resultados de condições em cada decisão,
e todos os pontos de entrada sejam invocados pelo menos uma vez. 


## Cap 5 - Module/Unit testing

- em vez de testar o programa inteiro, é melhor testar blocos menores do programa,
módulos, classes, métodos ou funções.

- razões:
    - permite que módulos sejam testados em paralelo na fase de testes, que
    pode ser mais rápido
    - facilita a tarefa de depurar porque diminui o escopo de um bug ou erro
    para o módulo em teste 

- requisitos para testes de módulo:
    1. specificação do módulo
    1. código fonte do módulo

- geralmente é aplicado técnicas de caixa branca porque o escopo é suficientemente
pequeno para analisar o seu fluxo lógico. Técnicas de caixa branca vão ficando
onerosas quanto maiores forem as entidades sob teste.


### Testes de módulo
- procedimento para o teste de módulo:

> Analizar a lógica do módulo usando uma ou mais técnicas de caixa branca e, então
> suplementar esses testes aplicando técnicas de caixa preta.

- o primeiro passo é listar todas as decisões condicionais do programa.

<!-- ### Testes incrementais

### Testes Top-down vs bottom-up -->

## Técnicas caixa branca que eu escolheria

Provavelmente escolheria cobertura por condições múltiplas por ser o mais
completo. Se a preguiça batesse usaria apenas o cobertura por condição.