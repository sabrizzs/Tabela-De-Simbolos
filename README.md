# EP2 - Tabela De Símbolos
### MAC0323 – Algoritmos e Estruturas de Dados II
### Sabrina Araújo da Silva
*Implementação de uma tabela de símbolos usando **vetor ordenado**, **árvore de busca binária**, **treap**, **árvore 2-3** e **árvore rubro-negra**. (ordered vector, binary search tree, treap, 2-3 tree, red–black tree)*

Para cada implementação da tabela de símbolos ordenada foram implementadas as seguintes operações:
~~~cpp
void add (Key key, Item val);
Item value (Key key);
int rank (Key key);
Key select (int k);
~~~

Para testar o tempo de execução de cada implementação, as quatro operações acima serão testadas com diferentes tipos de texto, sendo eles:
* O livro **The Southern Literary Messenger, Vol. II., No. 3, February, 1836 by Various** disponível no Projeto Gutenberg.
* Texto gerado aleatoriamente com 50 parágrafos, no estilo loren ipsum.

### Descrição da entrada para os teste
A primeira linha indica a estrutura a ser testada (VO, ABB, TR, A23, ARN). Em seguida, na segunda temos um inteiro N com o número de palavras do texto. Então, temos N palavras que constituem o texto, que poderão ocupar diversas
linhas do input. Logo após o texto, temos um inteiro Q, que representa o número de operações
a serem realizadas na tabela de símbolos. Em sequência, temos Q linhas, cada uma com uma
instrução do tipo:
* 1 x - Adicione as próximas x palavras do texto a tabela de símbolos
* 2 s - Quantas vezes a palavra s apareceu no texto até o momento - operação `value(s)`.
* 3 s - Quantas palavras são menores que s - operação `rank(s)`.
* 4 k - Qual a k-ésima chave da tabela - operação `select(k)`;

### Descrição da implementação
#### class Item
A `class Item` cria um item (célula) para o vetor ordenado que recebe uma key e um value.
<li> string chave() : retorna a key do Item</li>
<li> int valor() : retorna o value do Item</li>
<li> attChave() : atualiza a chave do Item</li>
<li> attVal() : atualiza o value do Item</li>

#### class No
A `class No` cria um nó para a árvore binária que recebe uma key e um value, além de ter ponteiros para o nó esquerdo e direito.

#### class NoTR
A `class NoTR` cria um nó para a treap que recebe uma key e um value, além de ter um valor para prioridade e ponteiros para o nó esquerdo e direito. 

#### class NoDT
A `class NoDT` cria um nó para a árvore 2-3 que recebe uma key e um value, além de ter um valor booleano para marcar se o nó é dois nó ou não e ponteiros para o nó esquerdo, meio, direito e o pai do nó. 
<li> setFilho() : coloca o nó filho de um nó na posição passada como argumento.</li>
<li> rstFilho() : reseta a posição do nó filho para NULL.</li>

#### class NoRB
A `class NoRB` cria um nó para a árvore rubro-negra que recebe uma key e um value, além de ter a cor RED e ponteiros para o nó esquerdo, direito e o nó pai.
<li> naEsquerda() : retorna se há um nó na esquerda do nó (tio).</li>
<li> *tio() : retorna o tio do nó.</li>
<li> paraBaixo() : posiciona o nó para baixo.</li>

#### class VO
A classe `class VO` determina as funções para o vetor ordenado.

#### class ABB
A classe `class ABB` determina as funções para a árvore binária.
<li> put() : função auxiliar para a função select().</li>
<li> getValue(), getRank(), getSelect() : funções auxiliares para as funções value, rank e select respectivamente.</li>

#### class TR
A classe `class TR` determina as funções para a treap.
<li> *rotacaoDir() : rotaciona para a direita.</li>
<li> *rotacaoEsq() : rotaciona para a esquerda.</li>
<li> put() : função auxiliar para a função select().</li>
<li> getValue(), getRank(), getSelect() : funções auxiliares para as funções value, rank e select respectivamente.</li>

#### class DT
A classe `class DT` determina as funções para a árvore 2-3.
<li> put() : função auxiliar para a função select().</li>
<li> procura() : procura se a chave já existe ou um lugar disponível para inserir um novo nó.</li>
<li> addDoisNo() : adiciona o nó em um dois nó.</li>
<li> separa() : separa nós quando um nó é adicionado em um três nó.</li>
<li> getValue(), getRank(), getSelect() : funções auxiliares para as funções value, rank e select respectivamente.</li>

#### class RB
A classe `class RB` determina as funções para a árvore rubro-negra.
<li> rotacaoDir() : rotaciona para a direita.</li>
<li> rotacaoEsq() : rotaciona para a esquerda.</li>
<li> mudaCor() : alterna a cor de um nó.</li>
<li> redRed() : arruma a árvore quando o pai de um nó vermelho também é vermelho.</li>
<li> procura() : procura se a chave já existe ou um lugar disponível para inserir um novo nó.</li>
<li> getValue(), getRank(), getSelect() : funções auxiliares para as funções value, rank e select respectivamente.</li>

#### função converte()
Converte string para int para auxiliar no recebimento das funções.

#### funções fVO, fABB, fTR, fADT, fARN
As funções fVO, fABB, fTR, fADT e fARN recebem as instruções e as executam.

#### arrayChar()
Separa as palavras do texto em um vetor e retira as pontuações.

## Livro do Projeto Gutenberg
O livro The Southern Literary Messenger (disponível em https://www.gutenberg.org/ebooks/68141) escolhido do Projeto Gutenberg possui cerca de 82691 palavras.
As seguintes instruções foram feitas para cada uma das 5 implementações:
<li>1 82691</li>
<li>2 at</li>
<li>3 in</li>
<li>4 780</li>

*observação 1: o **tempo total** se refere ao tempo total da execução da implementação e não da soma dos tempos das operações. O tempo de **0 segundos** se refere à um tempo muito pequeno em relação aos outros tempos.*

*observação 2: para fazer os testes, a saída do programa foi alterada para ter comentários e assim facilitar o entendimento. Exemplo: "A palavra at apareceu no texto 399 vez(es) ate o momento." ao invés de "399". Porém no programa enviado, as saídas estão como no PDF do EP.*

### Vetor Ordenado
#### Saídas:

Para a operação `void add (Key key, Item val);` com a instrução **1 82691**
>Tempo de execucao para a instrucao 1: 0.947 segundos.

Para a operação `Item value (Key key);` com a instrução **2 at**
>A palavra at apareceu no texto 399 vez(es) ate o momento.
>
>Tempo de execucao para a instrucao 2: 0.001 segundos.

Para a operação `int rank (Key key);` com a instrução **3 in**
>8003 palavra(s) sao/eh menor(es) que in.
>
>Tempo de execucao para a instrucao 3: 0 segundos.

Para a operação `Key select (int k);` com a instrução **4 780**
>A 780-esima chave da tabela eh Archelais.
>
>Tempo de execucao para a instrucao 4: 0 segundos.

Tempo total
>Tempo de execucao para a estrutura VO: 0.962 segundos.

### Árvore de Busca Binária
#### Saídas:

Para a operação `void add (Key key, Item val);` com a instrução **1 82691**
>Tempo de execucao para a instrucao 1: 0.157 segundos.

Para a operação `Item value (Key key);` com a instrução **2 at**
>A palavra at apareceu no texto 399 vez(es) ate o momento.
>
>Tempo de execucao para a instrucao 2: 0 segundos.

Para a operação `int rank (Key key);` com a instrução **3 in**
>8003 palavra(s) sao/eh menor(es) que in.
>
>Tempo de execucao para a instrucao 3: 0.003 segundos.

Para a operação `Key select (int k);` com a instrução **4 780**
>A 780-esima chave da tabela eh Archelais.
>
>Tempo de execucao para a instrucao 4: 0.001 segundos.

Tempo total
>Tempo de execucao para a estrutura ABB: 0.175 segundos.

### Treap
#### Saídas:

Para a operação `void add (Key key, Item val);` com a instrução **1 82691**
>Tempo de execucao para a instrucao 1: 0.185 segundos.

Para a operação `Item value (Key key);` com a instrução **2 at**
>A palavra at apareceu no texto 399 vez(es) ate o momento.
>
>Tempo de execucao para a instrucao 2: 0.001 segundos.

Para a operação `int rank (Key key);` com a instrução **3 in**
>8003 palavra(s) sao/eh menor(es) que in.
>
>Tempo de execucao para a instrucao 3: 0.003 segundos.

Para a operação `Key select (int k);` com a instrução **4 780**
>A 780-esima chave da tabela eh Archelais.
>
>Tempo de execucao para a instrucao 4: 0.001 segundos.

Tempo total
>Tempo de execucao para a estrutura TR: 0.201 segundos.

### Árvore 2-3
#### Saídas:

Para a operação `void add (Key key, Item val);` com a instrução **1 82691**
>Tempo de execucao para a instrucao 1: 0.06 segundos.

Para a operação `Item value (Key key);` com a instrução **2 at**
>A palavra at apareceu no texto 399 vez(es) ate o momento.
>
>Tempo de execucao para a instrucao 2: 0.001 segundos.

Para a operação `int rank (Key key);` com a instrução **3 in**
>8003 palavra(s) sao/eh menor(es) que in.
>
>Tempo de execucao para a instrucao 3: 0.001 segundos.

Para a operação `Key select (int k);` com a instrução **4 780**
>A 780-esima chave da tabela eh Archelais.
>
>Tempo de execucao para a instrucao 4: 0.001 segundos.

Tempo total
>Tempo de execucao para a estrutura ADT: 0.098 segundos.

### Árvore rubro-negra
#### Saídas:

Para a operação `void add (Key key, Item val);` com a instrução **1 82691**
>Tempo de execucao para a instrucao 1: 0.056 segundos.

Para a operação `Item value (Key key);` com a instrução **2 at**
>A palavra at apareceu no texto 399 vez(es) ate o momento.
>
>Tempo de execucao para a instrucao 2: 0 segundos.

Para a operação `int rank (Key key);` com a instrução **3 in**
>8003 palavra(s) sao/eh menor(es) que in.
>
>Tempo de execucao para a instrucao 3: 0.003 segundos.

Para a operação `Key select (int k);` com a instrução **4 780**
>A 780-esima chave da tabela eh Archelais.
>
>Tempo de execucao para a instrucao 4: 0.001 segundos.

Tempo total
>Tempo de execucao para a estrutura ARN: 0.073 segundos.

## Texto no estilo loren ipsum
O texto foi gerado aleatoriamente pelo site https://mussumipsum.com e possui 30 parágrafos com cerca de 1100 palavras.
As seguintes instruções foram feitas para cada uma das 5 implementações:
<li>1 1100</li>
<li>2 um</li>
<li>3 num</li>
<li>4 0</li>

### Vetor Ordenado
#### Saídas:

Para a operação `void add (Key key, Item val);` com a instrução **1 1100**
>Tempo de execucao para a instrucao 1: 0.001 segundos.

Para a operação `Item value (Key key);` com a instrução **2 um**
>A palavra um apareceu no texto 11 vez(es) ate o momento.
>
>Tempo de execucao para a instrucao 2: 0 segundos.

Para a operação `int rank (Key key);` com a instrução **3 num**
>180 palavra(s) sao/eh menor(es) que num.
>
>Tempo de execucao para a instrucao 3: 0.001 segundos.

Para a operação `Key select (int k);` com a instrução **4 0**
>A 0-esima chave da tabela eh A.
>
>Tempo de execucao para a instrucao 4: 0.001 segundos.

Tempo total
>Tempo de execucao para a estrutura VO: 0.003 segundos.

### Árvore de busca binária
#### Saídas:

Para a operação `void add (Key key, Item val);` com a instrução **1 1100**
>Tempo de execucao para a instrucao 1: 0.002 segundos.

Para a operação `Item value (Key key);` com a instrução **2 um**
>A palavra um apareceu no texto 11 vez(es) ate o momento.
>
>Tempo de execucao para a instrucao 2: 0 segundos.

Para a operação `int rank (Key key);` com a instrução **3 num**
>180 palavra(s) sao/eh menor(es) que num.
>
>Tempo de execucao para a instrucao 3: 0 segundos.

Para a operação `Key select (int k);` com a instrução **4 0**
>A 0-esima chave da tabela eh A.
>
>Tempo de execucao para a instrucao 4: 0 segundos.

Tempo total
>Tempo de execucao para a estrutura ABB: 0.006 segundos.

### Treap
#### Saídas:

Para a operação `void add (Key key, Item val);` com a instrução **1 1100**
>Tempo de execucao para a instrucao 1: 0.002 segundos.

Para a operação `Item value (Key key);` com a instrução **2 um**
>A palavra um apareceu no texto 11 vez(es) ate o momento.
>
>Tempo de execucao para a instrucao 2: 0.001 segundos.

Para a operação `int rank (Key key);` com a instrução **3 num**
>180 palavra(s) sao/eh menor(es) que num.
>
>Tempo de execucao para a instrucao 3: 0 segundos.

Para a operação `Key select (int k);` com a instrução **4 0**
>A 0-esima chave da tabela eh A.
>
>Tempo de execucao para a instrucao 4: 0.001 segundos.

Tempo total
>Tempo de execucao para a estrutura TR: 0.005 segundos

### Árvore 2-3
#### Saídas:

Para a operação `void add (Key key, Item val);` com a instrução **1 1100**
>Tempo de execucao para a instrucao 1: 0.001 segundos.

Para a operação `Item value (Key key);` com a instrução **2 um**
>A palavra um apareceu no texto 11 vez(es) ate o momento.
>
>Tempo de execucao para a instrucao 2: 0 segundos.

Para a operação `int rank (Key key);` com a instrução **3 num**
>180 palavra(s) sao/eh menor(es) que num.
>
>Tempo de execucao para a instrucao 3: 0 segundos.

Para a operação `Key select (int k);` com a instrução **4 0**
>A 0-esima chave da tabela eh A.
>
>Tempo de execucao para a instrucao 4: 0.001 segundos.

Tempo total
>Tempo de execucao para a estrutura ADT: 0.004 segundos.

### Árvore rubro-negra
#### Saídas:

Para a operação `void add (Key key, Item val);` com a instrução **1 1100**
>Tempo de execucao para a instrucao 1: 0.001 segundos.

Para a operação `Item value (Key key);` com a instrução **2 um**
>A palavra um apareceu no texto 11 vez(es) ate o momento.
>
>Tempo de execucao para a instrucao 2: 0.001 segundos.

Para a operação `int rank (Key key);` com a instrução **3 num**
>180 palavra(s) sao/eh menor(es) que num.
>
>Tempo de execucao para a instrucao 3: 0 segundos.

Para a operação `Key select (int k);` com a instrução **4 0**
>A 0-esima chave da tabela eh A.
>
>Tempo de execucao para a instrucao 4: 0.001 segundos.

Tempo total
>Tempo de execucao para a estrutura ARN: 0.003 segundos.

## Desempenho no total de cada implementação

### Texto do Projeto Gutenberg
Operação | VO | ABB | TR | A23 | ARN
:----:|:--:|:---:|:--:|:---:|:---:
add | 0.947s | 0.157s | 0.185s | 0.06s | 0.056s
value | 0.001s | 0s | 0.001s | 0.001s | 0s
rank | 0s | 0.003s | 0.003s | 0.001s | 0.003s
select | 0s | 0.001s | 0.001s | 0.001s | 0.001s
total | 0.962s | 0.175s | 0.201s | 0.087s | 0.073s

Em ordem de execução mais rápida, temos:
<ol>
<li>ARN</li>
<li>A23</li>
<li>ABB</li>
<li>TR</li>
<li>VO</li>
</ol>

### Texto no estilo loren ipsum
Operação | VO | ABB | TR | A23 | ARN
:----:|:--:|:---:|:--:|:---:|:---:
add | 0.001 | 0.002s | 0.002s | 0.001s | 0.001s
value | 0s | 0s | 0.001s | 0s | 0.001s
rank | 0.001s | 0s | 0s | 0s | 0s
select | 0.001s | 0s | 0.001s | 0.001s | 0.001s
total | 0.003s | 0.006s | 0.005s | 0.004s | 0.003s

Em ordem de execução mais rápida, temos:
<ol>
<li>ARN</li>
<li>VO</li>
<li>A23</li>
<li>TR</li>
<li>ABB</li>
</ol>

