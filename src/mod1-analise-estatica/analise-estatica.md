<!-- Realizar as seguintes atividades:

## 1) Ler o Capítulo 3 (Program Inspections, Walkthroughs, and Reviews) do livro do Mayers (The Art of Software Testing).

## 2) Ler a seção 3.3 (Static Analysis by Tools) do livro do Homes (Fundamentals of Software Testing). -->

<!-- Não gostei muito de **peer rating**, ainda mais se for um ritual muito recorrente
como retrospectiva de sprint. Parece um desvio consideralmente longo do processo
de _desenvolvimento_ de software. -->

**Explique com suas palavras porque as técnicas estáticas de V&V (inspeções/walkthroughs) e 
técnicas dinâmicas de V&V (teste) são complementares**

Segundo Mayers, inspeções/walktroughs são mais eficazes pra detectar certos tipos
de erros, enquanto outros passam despercebidos. Por outro lado, testes baseados
em computador são mais eficientes para outros tipos de erros. Assim, técinas
dinâmicas e estáticas se complementam.

(minha opinião: enquanto aparentemente muito úteis na identificação precoce de erros, 
inspeções/walkthoughs em grupo em sessões de 2 a 4 horas parecem técnicas desnecessariamente
custosas e um pouco ultrapassadas. Com que frequências essas sessões seriam feitas? 
A cada PR? Feature? Como essas técnicas se  encaixam no mercado atual? Ainda mais com outras 
técnicas mais populares como programação pareada, TDD, code review, CI, refatoração e
ferramentas como ferramentas de análise estática automáticas (sonarlint e similares), 
language servers, linters, formatadores etc)

Que técnica estática de V&V você recomendaria para o seu grupo de MDS para 
melhorar a qualidade do produto gerado na disciplina? Justifique a escolha e 
explique como você executaria a técnica com o seu grupo.

**Inspection**: me parece a técnica mais próxima de code review. 
O item 1 do _Inspection Agenda_ me lembra uma mistura da técnica do pato de borracha
com code review. O item 2 dessa agenda me parece facilmente realizável por uma
ferramenta como sonarlint.

A execução de Inspection seria através de uma reunião de chamada em grupo, 
enquanto o programador compartilha a tela para os outros participantes da sessão.

