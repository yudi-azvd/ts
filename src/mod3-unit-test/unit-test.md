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


## Cap 4 - Testes Case design: white box

- **cobertura de statements**: devem ser escritos casos de teste de maneira que  todo
statement deve ser executado pelo menos uma vez.
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


## Cap 5 - Module/Unit testing
