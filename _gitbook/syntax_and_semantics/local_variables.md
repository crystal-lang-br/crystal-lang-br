# Variáveis Locais

Variáveis locais começam com letras minúsculas. Elas são criadas na primeira vez em que você atribui um valor a elas.

```crystal
name = "Crystal"
age = 1
```

Seu tipo é inferido a partir de seu uso, não apenas de seu inicializador. Em geral, elas só são recipientes de valores associados com o tipo que o programador espera que elas tenham de acordo com sua localização e uso no programa.

Por exemplo, atribuir outra expressão a uma variável faz com que ela tenha o tipo dessa expressão:

```crystal
flower = "Tulip"
# Neste momento 'flower' é uma String

flower = 1
# Neste momento 'flower' é um Int32
```

Underscores podem ser usados no começo de uma variável, mas esses nomes são reservados para o compilador, portanto o seu uso não é recomendado (e isso também torna o código mais feio de ler).
