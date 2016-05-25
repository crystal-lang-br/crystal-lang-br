# Array

Um [Array](http://crystal-lang.org/api/Array.html) é um tipo genérico contendo elementos de um tipo `T`. Ele geralmente é criado com um literal de array:

```crystal
[1, 2, 3]         # Array(Int32)
[1, "hello", 'x'] # Array(Int32 | String | Char)
```

Um Array pode ter tipos misturados, significando que `T` será uma união de tipos, mas estes são determinados quando o array é criado, seja especificando T ou usando um literal de array. No segundo caso, T será definido como a união dos elementos literais do array.

Ao criar um array vazio, você sempre precisa especificar T:

```crystal
[] of Int32 # o mesmo que Array(Int32).new
[]          # syntax error
```

## Array de Strings

Arrays de strings podem ser criados com uma sintaxe especial:

```crystal
%w(one two three) # ["one", "two", "three"]
```

## Array de Símbolos

Arrays de símbolos podem ser criados com uma sintaxe especial:

```crystal
%i(one two three) # [:one, :two, :three]
```

## Tipos Semelhantes a Array

Você pode usar uma sintaxe de literal de array especial também com outros tipos, desde que eles implementem um método `new` sem argumentos e um método `<<`:

```crystal
MeuTipo{1, 2, 3}
```

Se `MeuTipo` não for genérico, o código acima é equivalente a este:

```crystal
tmp = MeuTipo.new
tmp << 1
tmp << 2
tmp << 3
tmp
```

Se `MeuTipo` for genérico, o código acima é equivalente a este:

```crystal
tmp = MeuTipo(typeof(1, 2, 3)).new
tmp << 1
tmp << 2
tmp << 3
tmp
```

No caso de um tipo genérico, os argumentos de tipos também podem ser especificados:

```crystal
MeuTipo(Int32 | String) {1, 2, "foo"}
```
