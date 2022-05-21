# EP2 - Tabela De Símbolos
*Implementação de uma tabela de símbolos usando **vetor ordenado**, **árvore de busca binária**, **treap**, **árvore 2-3** e **árvore rubro-negra**.*

Para cada implementação da tabela de símbolos ordenada foram implementadas as seguintes operações:
~~~cpp
void add (Key key, Item val);
Item value (Key key);
int rank (Key key);
Key select (int k);
~~~
Para testar o tempo de execução de cada implementação, as quatro operações acima serão testadas com diferentes tipos de texto, sendo eles:
* O livro **The Southern Literary Messenger, Vol. II., No. 3, February, 1836 by Various** disponível no [Projeto Gutenberg](https://www.gutenberg.org/ebooks/68141).
* Código muito grande que ainda vou escolher
* Alguma coisa desse site https://mussumipsum.com

## Livro do Projeto Gutenberg
O livro [The Southern Literary Messenger](https://www.gutenberg.org/ebooks/68141) escolhido do Projeto Gutenberg possui cerca de 84240 palavras.
As seguintes instruções foram feitas:
* 1 82691
* 2 at
* 3 in
* 4 780

### Vetor Ordenado
Para a operação `void add (Key key, Item val);` com a instrução **1 82691**
>Tempo de execucao para a instrucao 1: 1.06 segundos.
>
>A palavra at apareceu no texto 399 vez(es) ate o momento.

Para a operação `Item value (Key key);` com a instrução **2 at**
