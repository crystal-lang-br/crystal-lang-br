# NamedTuple

Uma [NamedTuple](http://crystal-lang.org/api/NamedTuple.html) geralmente é criada com o literal de tupla nomeada:

```crystal
tuple = {name: "Crystal", year: 2011} # NamedTuple(name: String, year: Int32)
tuple[:name] # => "Crystal" (String)
tuple[:year] # => 2011      (Int32)
```

Para denotar o tipo de uma tupla nomeada, você pode escrever:

```crystal
# O tipo denotando uma tupla nomeada de x: Int32, y: String
NamedTuple(x: Int32, y: String)
```

Nas restrições de tipos, argumentos de tipo genérico e outros lugares onde se espera um tipo, você pode usar uma sintaxe mais curta, conforme explicado no capítulo sobre [tipos](../type_grammar.md):

```crystal
# Um array de tuplas nomeadas de x: Int32, y: String
Array({x: Int32, y: String})
```
