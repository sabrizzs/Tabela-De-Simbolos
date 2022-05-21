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

### Vetor Ordenado
