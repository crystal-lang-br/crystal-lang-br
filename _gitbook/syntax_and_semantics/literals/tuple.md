# Tuple

Um [Tuple](http://crystal-lang.org/api/Tuple.html) geralmente é criado com um literal de tuplas:

```crystal
tuple = {1, "hello", 'x'} # Tuple(Int32, String, Char)
tuple[0]                  #=> 1       (Int32)
tuple[1]                  #=> "hello" (String)
tuple[2]                  #=> 'x'     (Char)
```

Para criar uma tupla vazia, use [Tuple.new](http://crystal-lang.org/api/Tuple.html#new%28%2Aargs%29-class-method).

Para denotar o tipo tupla você pode escrever:

```crystal
# Onde o tipo denota uma tupla de Int32, String e Char
Tuple(Int32, String, Char)
```

Nas restrições de tipos, argumentos de tipo genérico e outros lugares onde espera-se um tipo, você pode usar uma sintaxe mais curta, conforme explicado no capítulo sobre [tipos](../type_grammar.md):

```crystal
# Um array de tuplas de Int32, String e Char
Array({Int32, String, Char})
```
