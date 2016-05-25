# Variáveis Globais

Variáveis globais começam com um sinal de dólar (`$`). Elas são declaradas na primeira vez em que você atribui um valor a elas.

```crystal
$year = 2014
```

Seu tipo é inferido usando o [algoritmo global de inferência de tipo](type_inference.md)

Além disso, se o seu programa ler uma variável global antes que algum valor seja atribuído a ela, ela também terá o tipo `Nil`.
