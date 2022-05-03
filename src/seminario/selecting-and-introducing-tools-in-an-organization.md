# Suporte de ferramentas para teste

## Selecionar e introduzir ferramentas em uma organização

### Princípios

É importante ter em mente alguns pontos principais ao escolher e introduzir 
uma ferramenta de testes em uma organização.

- Custo. Não se deve pensar apenas nos custo de comprar a ferramenta, mas
também no que vem depois. A organização deve pensar na capacitação dos integrantes
da equipe, na implementação de scripts de teste e sua manutenção ao longo do tempo)
- Uma ferramenta não resolve todos os problemas. 
- Pode ser necessária mais de uma ferramenta. O JUnit, por exemplo, executa
testes unitários, realiza asserções e etc. Entretanto se o time precisa de mock,
apenas utilzar apenas o JUnit não é o suficiente.


### Processo de seleção de ferramentas

- entender como a empresa organiza os processos de teste, qual o nível 
de manturidade. quais tipos, se são automatizados etc 
  - estimar lucro e prejuízo ao usar a ferramenta
- seleção de um conjunto de ferramentas
- seleção de verdade da ferramenta

#### Pesquisa

- Fórums
- Github - (issues, PRs, SemVer, colaboradores)
- dicussões com colegas 
- blogs de desenvolvedores ou de empresas

Pesquisar na internet em inglês ou português?

```
PT -   139.000.000 de resultados
EN - 7.760.000.000 de resultados
```

critérios de seleção:

- O que o meu time precisa?
- custo
- curva de aprendizado/treinamento da equipe
- benefícios esperados
- essa ferramenta vai ajudar a gente a melhorar o no processo de testes?
- testes unitários?
- testes e2e?
- O que a ferramenta NÃO CONSEGUE fazer?


Testar as ferramentas no mesmo ambiente

Depois de uma PoC, é possível
chegar em uma conclusão baseada em dados.

PoC com um pedaço da aplicação

Numerical measurements must be taken in order to have measurable decision
elements

### Implementação da ferramenta de teste

### Construir ou comprar ferramentas?
... ou usar uma open source?

**Open source** Tem que ficar atento à licença da ferramenta. Pode ser que
ela ela force que o software (privado) sendo desenvolvido seja colocado
em público.

**Comprar** geralmente é muito caro.

**Desenvolver a própria solução** tem vantagem de ser uma ferramenta sob medida
para o seu software. 

Mas é muito mais desenvolvimento.

## Referências

- Fundamentals of Software Testing, Holmes. Capítulo 6.