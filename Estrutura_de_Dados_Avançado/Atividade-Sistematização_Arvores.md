# ATIVIDADE ÁRVORES


**Nome:** Liz Cristina Ferreira

**Turma:** 2D

**Disciplina:** Estrutura de Dados II

**Professora:** Profa. Kadidja Valéria


---


# Etapa 1 — Revisão bibliográfica


## Conceitos básicos de árvore


```text
        A
     /  |  \
    B   C   D
   / \       \
  E   F       G
```

- **Nó:** qualquer elemento presente na árvore.
- **Raiz:** é o primeiro elemento da árvore, que não possui pai.  

  Na árvore citada, esse elemento é **A**.
- **Pai e filho:** indicam a hierarquia/relação entre os nós da árvore.  

  B, C e D são filhos de A e, portanto, A é pai de B, C e D.
- **Folha:** é um nó que não possui filhos.  

  C, E, F e G são folhas nessa árvore.
- **Altura:** é o comprimento do caminho mais longo entre determinado nó e uma folha descendente dele.  

  Ex.: `A → B → E` ou `A → D → G`.

  Medindo por arestas, a altura da árvore seria correspondente a 2:
  - `A → B` = 1 aresta
  - `B → E` = 1 aresta
- **Caminho:** sequência de nós conectados, como `A → D → G`.
- **Percurso:** significa percorrer os nós de uma árvore seguindo uma ordem específica determinada por critérios.  

  Ex.: um percurso que visita primeiro o nó e depois seus descendentes poderia resultar em:

  **A → B → E → F → C → D → G**
- **Subárvore:** árvore formada dentro de uma árvore maior por um nó e seus descendentes.  

  Ex.: a partir do nó B:

```text
    B
   / \
  E   F
```


---


## Árvore Geral


**Definição:** É uma estrutura hierárquica onde cada nó pode possuir uma quantidade variável de filhos; não existe limite fixo de filhos ou uma regra de ordenação definida pela estrutura.

```text
        A
     /  |  \
    B   C   D
  / | \     |
 E  F  G    H
```

No exemplo acima:

- `A` possui 3 filhos;
- `B` também possui 3 filhos;
- `D` possui 1 filho;
- `C`, `E`, `F`, `G` e `H` não possuem filhos.

**Como organiza os dados:** organiza os nós de forma hierárquica, usando as relações de pai e filho.

**Exemplo:** uma estrutura de pastas no armazenamento de um sistema operacional.

```text
Documentos
├── Faculdade
│   ├── ED II
│   ├── Banco de Dados
│   └── Python
├── Imagens
│   └── Desenhos
└── Projetos Pessoais
    ├── Projeto 1 - Novel
    └── Projeto 2 - CNU
```

*Documentos* é a raiz, e cada pasta pode conter uma quantidade variável de subpastas, de acordo com a necessidade.

**Propriedade:** cada nó, exceto a raiz, possui exatamente um pai e uma quantidade variável de filhos.

**Busca:** não existe uma regra de ordenação que determine diretamente onde procurar um valor, então pode ser necessário percorrer os nós até encontrar o desejado.

**Inserção:** normalmente, é determinado sob qual nó o novo elemento será inserido. Como a quantidade de filhos pode variar, novos nós podem ser adicionados conforme a necessidade.

**Ajustes e alterações:** podem envolver a adição ou remoção de nós e a atualização das relações de pai e filho. Não há mecanismo obrigatório de balanceamento.

**Aplicações práticas:**

- sistemas de pastas;
- organogramas empresariais;
- categorias e subcategorias;
- hierarquias organizacionais;
- situações em que um elemento pode possuir múltiplos filhos.


---


## Árvore Binária


**Definição:** É uma estrutura de árvore onde cada nó possui no máximo dois filhos. Esses filhos são denominados **filho esquerdo** e **filho direito**.

```text
       A
      / \
     B   C
    / \   \
   D   E   F
```

No exemplo acima:

- `A` possui 2 filhos;
- `B` possui 2 filhos;
- `C` possui 1 filho;
- `D`, `E` e `F` possuem 0 filhos.

**Como organiza os dados:** assim como a Árvore Geral, também utiliza uma estrutura hierárquica, porém com uma restrição: cada nó possui uma subárvore esquerda e uma subárvore direita, que podem também ser vazias.

No caso, uma folha pode ser vista como:

```text
    D
   / \
vazia vazia
```

**Propriedade:** cada nó possui zero, um ou dois filhos, nunca além disso. Entretanto, na árvore binária comum não existe uma regra de ordenação baseada nos valores dos nós.

**Busca:** não existe uma regra de ordenação que indique em qual lado determinado valor está. Por isso, pode ser necessário percorrer os nós até encontrar o valor específico.

**Inserção:** na árvore binária comum não há uma regra de inserção definida com base nos valores. A posição depende da aplicação ou do método utilizado, respeitando o limite de dois filhos por nó.

**Ajustes e alterações:** a árvore binária comum não possui um mecanismo obrigatório de balanceamento.

Exemplo:

```text
A
 \
  B
   \
    C
     \
      D
```

A estrutura acima continua sendo uma árvore binária válida.

**Aplicações práticas:** serve de base para estruturas mais específicas e outras formas de representação de dados, como:

- árvores binárias de busca;
- árvores AVL;
- árvores rubro-negras;
- heaps binários;
- árvores de expressão;
- representação de decisões binárias.


---


## Árvore Binária de Busca (ABB)


**Definição:** É uma árvore binária que possui uma regra de ordenação entre as chaves de seus nós.

```text
        50
       /  \
     30    70
    / \    / \
   20 40  60 80
```

Para cada nó:

- os valores menores ficam na **subárvore esquerda**;
- os valores maiores ficam na **subárvore direita**;
- essa ordenação também é válida para os nós filhos e seus descendentes.

**Como organiza os dados:** os valores são organizados de forma hierárquica e ordenada, usando a comparação entre as chaves dos nós.

**Propriedade:** para cada nó, os valores menores ficam na subárvore esquerda e os maiores na subárvore direita. Essa regra vale recursivamente para todos os descendentes.

**Busca:** o mecanismo de ordenação por valores permite direcionar a busca para uma das subárvores, evitando percorrer caminhos desnecessários. A eficiência depende diretamente da altura da árvore.

Exemplo: na árvore acima, para encontrar 60, partindo do 50:

- `60 > 50`, então seguimos para a direita;
- chegando em 70, `60 < 70`, então seguimos para a esquerda;
- percurso: `50 → 70 → 60`.

**Inserção:** utiliza a mesma comparação da busca.

Exemplo: para inserir 40 no seguinte cenário:

```text
      50
     /  \
   30    70
```

- `40 < 50`, então seguimos para a esquerda, chegando em 30;
- `40 > 30`, então seguimos para a direita;
- como essa posição está vazia, 40 é inserido nela.

```text
      50
     /  \
   30    70
     \
      40
```

Uma ABB pode ficar desbalanceada. Quanto maior a altura da árvore, maior pode ser o caminho percorrido durante as operações e, em casos extremos, sua estrutura pode ficar semelhante a uma lista.

**Ajustes e alterações:** a ABB comum não possui um mecanismo automático ou obrigatório de balanceamento. Ela precisa preservar a propriedade de ordenação após as alterações, mas pode ficar inclinada.

**Remoção:** dependendo de o nó possuir zero, um ou dois filhos, pode ser necessário removê-lo diretamente, ligar seu filho à árvore ou substituí-lo por outro nó adequado, sempre preservando a propriedade de ordenação.

**Aplicações práticas:** é utilizada quando precisamos manter elementos ordenados e realizar operações como:

- busca;
- inserção;
- remoção;
- obtenção de valores mínimos e máximos;
- percurso dos elementos em ordem.

Se for realizado um percurso em ordem em uma ABB, os valores aparecem ordenados.

No primeiro exemplo:

`20 → 30 → 40 → 50 → 60 → 70 → 80`


---


## Árvore AVL


**Definição:** é uma Árvore Binária de Busca autobalanceada, que controla a diferença de altura entre as subárvores de cada nó.

**Como organiza os dados:** mantém a mesma organização de uma ABB, com valores menores na subárvore esquerda e maiores na direita, mas acrescenta o controle da altura das subárvores para manter a árvore balanceada.


### Propriedades


**Fator de balanceamento:** uma AVL está balanceada quando, para cada nó, a diferença entre a altura da subárvore esquerda e a altura da subárvore direita resulta em -1, 0 ou +1.

`FB = altura(esquerda) - altura(direita)`

Exemplo balanceado:

```text
      30
     /  \
   20    40
```

Está equilibrada, com `FB = 0`.

Exemplo desbalanceado:

```text
      30
     /
   20
   /
 10
```

O nó 30 apresenta fator de balanceamento 2, portanto está fora do intervalo permitido em uma AVL.


### Rotações


Podem ocorrer quatro tipos de desbalanceamento em uma AVL. Para cada caso, são aplicadas rotações específicas para reorganizar a estrutura e restaurar o balanceamento, sem perder a propriedade de ordenação da ABB.

**LL:** o desequilíbrio ocorreu no lado esquerdo do filho esquerdo, então é necessária uma rotação para a direita.

```text
      30
     /
   20
   /
 10
```

**RR:** o desequilíbrio ocorreu no lado direito do filho direito, então é necessária uma rotação para a esquerda.

```text
10
  \
   20
     \
      30
```

**LR:** o desequilíbrio começa pela esquerda, mas o novo nó foi para a direita daquele filho. São necessárias duas rotações: uma para a esquerda em 10 e uma para a direita em 30.

```text
      30
     /
   10
     \
      20
```

**RL:** é o espelho de LR. O desequilíbrio começa pela direita, mas o novo nó está à esquerda desse filho. São necessárias duas rotações: uma rotação à direita em 30 e, depois, uma rotação à esquerda em 10.

```text
10
  \
   30
   /
  20
```

**Busca:** funciona da mesma forma que em uma ABB, utilizando a comparação entre as chaves. Porém, o balanceamento da AVL procura manter a altura controlada, evitando caminhos excessivamente longos.

**Inserção:** segue a lógica de uma ABB, utilizando comparações para encontrar a posição adequada. Depois da inserção, os fatores de balanceamento são verificados e, caso exista desequilíbrio, aplica-se a rotação correspondente.

**Ajustes e alterações:** após inserções ou remoções, as alturas das subárvores podem mudar. Por isso, os fatores de balanceamento são verificados novamente. Se algum nó apresentar fator fora de -1, 0 ou +1, são aplicadas as rotações adequadas para restaurar o balanceamento.

**Remoção:** inicialmente segue as regras de remoção de uma ABB. Depois, verifica-se o balanceamento dos nós afetados e podem ser necessárias rotações para restaurar a propriedade da AVL.

**Aplicações práticas:** a AVL é útil quando queremos:

- manter elementos ordenados;
- realizar buscas frequentes;
- evitar uma ABB excessivamente inclinada;
- manter a altura controlada mesmo após inserções e remoções.


---


## Árvore Rubro-Negra


**Definição:** é uma Árvore Binária de Busca autobalanceada que utiliza cores, vermelho e preto, associadas aos nós para controlar o balanceamento da estrutura.

```text
       20(P)
       /   \
   10(V)   30(V)
```

**Como organiza os dados:** mantém a organização de uma ABB, com valores menores na subárvore esquerda e maiores na direita. Além das chaves, cada nó possui uma cor, vermelha ou preta, usada como informação de controle para o balanceamento.


### Propriedades


A cor é uma informação de controle utilizada para manter a árvore aproximadamente balanceada.

1. Cada nó é vermelho ou preto.
2. A raiz é preta.
3. As folhas NIL (vazias) são consideradas pretas.
4. Se um nó é vermelho, seus filhos são pretos. Dois nós vermelhos não podem aparecer consecutivamente numa relação pai-filho.
5. Todo caminho de um nó até suas folhas NIL descendentes contém a mesma quantidade de nós pretos. Essa quantidade é chamada de **altura negra (black-height)**.

Apesar de ser autobalanceada, a Rubro-Negra permite maior diferença entre as alturas dos caminhos do que uma AVL. Suas propriedades garantem que a altura permaneça proporcional a `log n`, evitando que a estrutura se degrade como uma ABB completamente inclinada.

**Busca:** funciona da mesma forma que em uma ABB, comparando os valores para decidir entre a subárvore esquerda ou direita. As cores não determinam o caminho da busca; sua função é auxiliar no controle do balanceamento.

**Inserção:** assim como em uma ABB, utilizamos a comparação de valores para definir onde o novo nó será inserido. A diferença está nos ajustes realizados após a inserção para preservar as propriedades rubro-negras.

Normalmente, um novo nó é inserido como vermelho, pois inseri-lo como preto poderia alterar a quantidade de nós pretos em apenas alguns caminhos. Após a inserção, as propriedades rubro-negras são verificadas e podem ocorrer recolorações e/ou rotações.


### Recoloração e rotações


A recoloração altera a informação de controle, sem mudar o valor do nó:

`V → P` ou `P → V`

As rotações reorganizam a estrutura, como na AVL. Na Rubro-Negra, a decisão depende não apenas da posição dos nós, mas também das cores do pai, do avô e do tio.

```text
        avô
       /   \
     pai   tio
      |
   novo nó
```

Se pai e tio forem vermelhos, muitas vezes o ajuste envolve **recoloração**. Se o tio for preto e houver uma configuração estrutural inadequada, podem ser necessárias **rotações e recolorações**.

**Remoção:** como a remoção de um nó preto pode alterar a quantidade de nós pretos existente nos caminhos, ela pode exigir:

- recolorações;
- rotações;
- propagação de ajustes pela árvore.

**Ajustes e alterações:** após inserções ou remoções, as propriedades de cor podem ser violadas. Para restaurá-las, a árvore pode realizar recolorações e rotações, mantendo simultaneamente a ordenação de uma ABB e o balanceamento da estrutura.

**Aplicações práticas:** é útil quando queremos:

- manter valores ordenados;
- realizar busca, inserção e remoção eficientemente;
- impedir que uma ABB fique excessivamente inclinada;
- trabalhar com estruturas que sofrem alterações frequentes.


---


## Árvore B


**Definição:** uma estrutura de árvore de busca multivias, onde um único nó pode armazenar várias chaves. Assim, um nó pode direcionar a busca para vários caminhos e também pode ter mais de dois filhos.

```text
       [20 | 40 | 60]
        /    |    |    \
```

**Como os dados são organizados:** várias chaves ordenadas podem ser armazenadas em um mesmo nó. Essas chaves dividem os valores em intervalos, e cada intervalo corresponde a um dos filhos do nó.

No exemplo acima, as três chaves dividem os valores em quatro regiões:

- filho 1 → valores `< 20`;
- filho 2 → valores entre `20` e `40`;
- filho 3 → valores entre `40` e `60`;
- filho 4 → valores `> 60`.

A lógica de busca continua sendo baseada em ordenação, mas agora existe mais de uma chave dentro do mesmo nó.

A Árvore B foi projetada para situações em que acessar um novo bloco ou página de armazenamento possui custo. Em vez de armazenar apenas uma chave por nó, permite armazenar várias chaves em um mesmo nó, aumentando o número de caminhos possíveis e contribuindo para uma menor altura da estrutura.


### Propriedades


Uma Árvore B possui uma ordem ou um limite de capacidade que determina quantas chaves e filhos cada nó pode possuir.

- um nó pode armazenar várias chaves;
- as chaves dentro do nó ficam ordenadas;
- um nó pode ter vários filhos;
- os filhos correspondem aos intervalos definidos pelas chaves;
- a árvore permanece balanceada;
- todas as folhas ficam no mesmo nível.

```text
          [40]
        /      \
 [10 | 20]   [60 | 80]
```

**Busca:** acontece em duas etapas. Primeiro, procura-se entre as chaves do nó e, depois, escolhe-se o filho correspondente ao intervalo.

Exemplo:

```text
[20 | 40 | 60]
```

Se queremos 50:

- `50 > 20`;
- `50 > 40`;
- `50 < 60`.

Então sabemos que o valor procurado pertence ao intervalo `40 < valor < 60` e seguimos pelo filho correspondente.

Isso continua até:

- encontrar a chave; ou
- chegar a uma folha sem encontrá-la.

**Inserção:** primeiramente, utiliza-se a ordenação da Árvore B para localizar a folha adequada para inserir a nova chave. A chave é adicionada mantendo a ordem dos valores. Caso o nó ainda possua espaço disponível, nenhuma outra alteração é necessária. Porém, se o nó ultrapassar sua capacidade, ocorre uma divisão (*split*): o nó é dividido e uma das chaves é promovida para o nó pai. Caso o pai também fique cheio, o processo pode se propagar até a raiz. Se a própria raiz for dividida, uma nova raiz é criada, aumentando a altura da árvore.

Exemplo, supondo que o nó possa armazenar no máximo 3 chaves:

```text
[10 | 20 | 30]
```

Queremos inserir 40:

```text
[10 | 20 | 30 | 40]
```

A capacidade foi ultrapassada, então ocorre uma divisão. De forma simplificada:

```text
       [20]
      /    \
   [10]   [30 | 40]
```

**Remoção:** após remover uma chave, caso um nó fique abaixo da ocupação mínima permitida, pode ser necessário redistribuir chaves com um nó irmão ou realizar a fusão de nós, preservando as propriedades da Árvore B.

**Ajustes e alterações:** após inserções ou remoções, podem ocorrer divisões, redistribuições ou fusões de nós para manter os limites de capacidade e o balanceamento da árvore.

**Aplicações práticas:** a Árvore B é especialmente útil quando queremos:

- armazenar grandes quantidades de dados;
- reduzir o número de acessos a disco;
- construir índices;
- trabalhar com bancos de dados;
- trabalhar com sistemas de arquivos.


---


## Árvore B+


**Definição:** é uma árvore de busca multivias derivada da Árvore B, na qual os nós internos funcionam como índices para orientar a busca, enquanto os registros ou referências aos registros ficam nas folhas, que são ligadas sequencialmente.

```text
                  [30 | 60]
                 /    |    \
                /     |     \
[10 | 20] → [30 | 40 | 50] → [60 | 70 | 80]
```

As folhas formam a parte inferior e ficam ligadas entre si.

**Como os dados são organizados:** na Árvore B+, as chaves dos nós internos servem como índices para determinar qual caminho seguir, enquanto as folhas armazenam os registros ou referências aos dados.

**Propriedade:** é uma estrutura multivias e balanceada, com todas as folhas no mesmo nível. Os nós internos armazenam chaves de separação para orientar a busca, enquanto os registros ou referências aos registros ficam nas folhas, que são ligadas sequencialmente.

```text
[10 | 20] → [30 | 40] → [50 | 60] → [70 | 80]
```

Essa ligação permite percorrer os valores em ordem sem precisar voltar para os níveis internos da árvore durante um percurso sequencial.

**Busca:** utiliza os nós internos para escolher o caminho até a folha adequada. Na B+, a busca por um registro chega até uma folha, pois é nela que estão armazenadas as entradas correspondentes.

```text
                  [30 | 60]
                 /    |    \
       [10 | 20]   [30 | 40 | 50]   [60 | 70 | 80]
```

Se queremos 40, começando no nó interno `[30 | 60]`:

Como `30 ≤ 40 < 60`, seguimos para a folha `[30 | 40 | 50]` e encontramos 40.

A ligação entre as folhas facilita principalmente consultas por intervalo, pois, depois de localizar o primeiro valor, é possível continuar percorrendo as folhas sequencialmente.

**Inserção:** a lógica é parecida com a Árvore B, mas a nova entrada é colocada na folha apropriada.

1. usamos os nós internos para encontrar a folha correta;
2. inserimos a chave mantendo a ordenação;
3. se houver espaço, termina;
4. se a folha ficar cheia, ela é dividida;
5. uma chave separadora é inserida no nó pai;
6. se o pai também ultrapassar sua capacidade, a divisão pode se propagar para cima.

**Remoção:** ocorre inicialmente nas folhas. Caso um nó fique abaixo da ocupação mínima, pode ser necessário redistribuir entradas entre nós irmãos ou fundir nós, além de atualizar as chaves dos índices internos.

**Ajustes e alterações:** após inserções ou remoções, podem ocorrer divisões, redistribuições ou fusões de nós. As chaves dos nós internos também podem precisar ser atualizadas para continuar direcionando corretamente as buscas, mantendo a árvore balanceada.

**Aplicações práticas:** a B+ é especialmente utilizada em:

- índices de bancos de dados;
- armazenamento de grandes volumes de dados;
- consultas por intervalo;
- acesso ordenado/sequencial aos registros;
- sistemas em que é importante reduzir acessos ao armazenamento.


---


# Etapa 2 — Quadro comparativo


| **Estrutura** | **Organização dos dados** | **Regra ou propriedade** | **Operação ou ajuste** | **Aplicação** | **Referência** |
|---|---|---|---|---|---|
| **Árvore Geral** | Nós organizados hierarquicamente em relações de pai e filho. | Cada nó, exceto a raiz, possui um pai e pode possuir quantidade variável de filhos. | Inserção/remoção de nós e atualização das relações; não possui balanceamento obrigatório. | Sistemas de pastas, organogramas e hierarquias. | Goodrich et al., cap. 8 — *Trees* |
| **Árvore Binária** | Estrutura hierárquica com posições de filho esquerdo e direito. | Cada nó possui no máximo dois filhos; não exige ordenação por valor. | Inserção, remoção e percursos; não possui balanceamento obrigatório. | Base para ABB, AVL, rubro-negra, heap e árvores de expressão. | Goodrich et al., cap. 8 — *Trees* |
| **ABB** | Chaves organizadas hierarquicamente e em ordem. | Valores menores ficam na subárvore esquerda e maiores na direita, recursivamente. | Busca e inserção por comparação; remoção preserva a ordenação; não há balanceamento automático. | Manutenção de elementos ordenados, busca, mínimo/máximo e percursos em ordem. | Cormen et al., cap. 12 — *Binary Search Trees* |
| **AVL** | Mesma organização de uma ABB, acrescentando controle de altura. | Para cada nó, `FB = altura(esq.) − altura(dir.)` deve ser −1, 0 ou +1. | Rotações LL, RR, LR e RL após inserções ou remoções quando necessário. | Estruturas ordenadas com buscas frequentes e altura controlada. | Goodrich et al., seção 11.3 — *AVL Trees* |
| **Rubro-Negra** | ABB em que cada nó possui também uma cor vermelha ou preta. | Respeita propriedades de cor e altura negra que mantêm a altura controlada. | Recolorações e rotações após inserções ou remoções. | Estruturas ordenadas com inserções, remoções e buscas frequentes. | Cormen et al., cap. 13 — *Red-Black Trees* |
| **Árvore B** | Várias chaves ordenadas podem existir no mesmo nó, criando vários caminhos. | Estrutura multivias balanceada; todas as folhas ficam no mesmo nível e os nós têm limites de ocupação. | *Split* e promoção de chave na inserção; redistribuição ou fusão na remoção. | Índices, bancos de dados e sistemas de arquivos. | Cormen et al., cap. 18 — *B-Trees* |
| **Árvore B+** | Nós internos funcionam como índice; registros/referências ficam nas folhas, que são ligadas. | Multivias, balanceada, folhas no mesmo nível e conectadas sequencialmente. | Divisão, redistribuição, fusão e atualização das chaves separadoras. | Índices de bancos de dados, consultas por intervalo e acesso sequencial. | Silberschatz et al., cap. 14, seção 14.3 — *B+-Tree Index Files* |
| **Heap** | Normalmente organizado como uma árvore binária completa. | Em max-heap, o pai tem prioridade ≥ filhos; em min-heap, prioridade ≤ filhos. | Inserção/remoção seguida de reajuste para cima ou para baixo para recuperar a propriedade do heap. | Filas de prioridade e Heapsort. | Goodrich et al., seção 9.3 — *Heaps*; Cormen et al., cap. 6 |
| **Trie** | Chaves são representadas por caminhos formados por caracteres/partes; prefixos iguais compartilham caminhos. | A posição depende da sequência de símbolos da chave, não de comparações entre palavras inteiras. | Inserção e busca percorrem os símbolos sucessivamente; podem ser criados/removidos ramos. | Dicionários, autocompletar e busca por prefixos. | Goodrich et al., seção 13.3 — *Tries* |


---


# Etapa 3 — Identificação por analogias


## 1. Uma estante de números é reorganizada por rotações quando um lado fica alto demais em relação ao outro.


**Estrutura:** Árvore AVL.

**Justificativa:** A AVL controla a diferença de altura entre suas subárvores por meio do fator de balanceamento. Quando ocorre um desequilíbrio, podem ser realizadas rotações simples ou duplas para restaurar o balanceamento.

**Limite da analogia:** Uma estante comum não calcula alturas ou fatores de balanceamento e também não possui relações formais entre nós e subárvores.


---


## 2. Um catálogo guarda várias chaves por página; quando uma página fica cheia, ela é dividida.


**Estrutura:** Árvore B.

**Justificativa:** Uma Árvore B pode armazenar várias chaves em um mesmo nó. Quando um nó ultrapassa sua capacidade, ocorre uma divisão (*split*), e uma chave pode ser promovida para o nó pai.

**Limite da analogia:** Uma página de catálogo físico não realiza automaticamente divisões, promoção de chaves ou manutenção das regras de ocupação e balanceamento da Árvore B.


---


## 3. Uma fila mantém a tarefa de maior prioridade no topo para retirá-la primeiro.


**Estrutura:** Heap, especificamente um max-heap.

**Justificativa:** No max-heap, cada nó possui prioridade ou valor maior ou igual ao de seus filhos, fazendo com que o elemento de maior prioridade permaneça na raiz e possa ser removido primeiro.

**Limite da analogia:** Uma fila comum costuma possuir uma organização linear, enquanto o heap utiliza uma estrutura em árvore. Além disso, o heap não mantém todos os elementos completamente ordenados, apenas preserva sua propriedade de prioridade.


---


## 4. Um índice percorre letras sucessivas e compartilha o início das palavras de mesmo prefixo.


**Estrutura:** Trie.

**Justificativa:** Em uma Trie, as chaves são representadas por caminhos formados pelos caracteres da palavra. Palavras que possuem o mesmo prefixo compartilham os mesmos nós iniciais.

Exemplo: `casa`, `casaco`, `casal`

Compartilham:

`c → a → s → a`

**Limite da analogia:** Um índice comum não necessariamente representa cada caractere por meio de nós nem registra formalmente onde uma palavra termina, como ocorre em uma Trie.


---


## 5. Uma estrutura usa cores, recolorações e rotações para manter controlada a altura dos caminhos de busca.


**Estrutura:** Árvore Rubro-Negra.

**Justificativa:** Cada nó recebe uma cor vermelha ou preta e a estrutura possui regras relacionadas a essas cores. Após inserções ou remoções, podem ocorrer recolorações e rotações para preservar suas propriedades e manter a altura controlada.

**Limite da analogia:** As cores não representam características dos dados armazenados; são apenas informações de controle. A analogia também não representa todas as regras, como a altura negra dos caminhos e as folhas NIL pretas.


---


## 6. Um índice conduz às folhas que contêm os registros, ligadas entre si para facilitar consultas por intervalo.


**Estrutura:** Árvore B+.

**Justificativa:** Na Árvore B+, os nós internos funcionam como índices para direcionar a busca, enquanto os registros ou referências aos registros ficam nas folhas. Essas folhas são ligadas sequencialmente, facilitando consultas por intervalo.

**Limite da analogia:** A comparação com um índice não demonstra todos os mecanismos da B+, como divisão, redistribuição e fusão de nós ou os limites de ocupação de cada nó.


---


## 7. Numa coleção de números, cada nó direciona valores menores para a esquerda e maiores para a direita.


**Estrutura:** Árvore Binária de Busca — ABB.

**Justificativa:** Em uma ABB, para cada nó, os valores menores são direcionados para a subárvore esquerda e os maiores para a subárvore direita. Essa propriedade vale recursivamente para os demais nós.

**Limite da analogia:** A analogia representa a ordenação dos valores, mas não mostra que uma ABB pode ficar desbalanceada nem os procedimentos necessários para inserção e remoção.


---


# Referências bibliográficas


GOODRICH, Michael T.; TAMASSIA, Roberto; GOLDWASSER, Michael H. *Data Structures and Algorithms in Java*. 6. ed. Hoboken: Wiley, 2014.

CORMEN, Thomas H.; LEISERSON, Charles E.; RIVEST, Ronald L.; STEIN, Clifford. *Introduction to Algorithms*. 4. ed. Cambridge: MIT Press, 2022.

SILBERSCHATZ, Abraham; KORTH, Henry F.; SUDARSHAN, S. *Database System Concepts*. 7. ed. New York: McGraw-Hill, 2019.

---

## Observação sobre o uso de IA

As referências bibliográficas acima foram utilizadas com auxílio do **ChatGPT (OpenAI)** para localização, síntese e compreensão dos conteúdos.

A ferramenta também foi utilizada como apoio para explicação dos conceitos, organização da atividade e revisão da redação.

O conteúdo final foi revisado e organizado pela estudante com base nesse processo de consulta e estudo.
