# Hash

Um [Hash](http://crystal-lang.org/api/Hash.html) representa um mapeamento de chaves de um tipo `K` a valores de um tipo `V`. Geralmente é criado com um literal de hash:

```crystal
{1 => 2, 3 => 4}     # Hash(Int32, Int32)
{1 => 2, 'a' => 3}   # Hash(Int32 | Char, Int32)
```

Um Hash pode ter tipos misturados, tanto para as chaves quanto para os valores, significando que `K`/`V` serão tipos união, mas estes são determinados quando o hash é criado, seja especificando `K` e `V` ou através da utilização de um literal de hash. No segundo caso, `K` será definido como a união dos tipos das chaves do literal do hash, e `V` será definido como a união dos valores do literal do hash.

Ao criar um hash vazio, você sempre precisa especificar `K` e `V`:

```crystal
{} of Int32 => Int32 # é o mesmo que Hash(Int32, Int32).new
{}                   # syntax error
```

## Chaves como Strings

Uma notação especial permite criar hashes com strings como chaves:

```crystal
{"key1": 'a', "key2": 'b'} # Hash(String, Char)
```

## Tipos Semelhantes a Hashes

Você também pode usar uma sintaxe de literal de hash especial com outros tipos, desde que eles implementem um método `new` sem argumentos e um método `[]=`:

```crystal
MeuTipo{"foo": "bar"}
```

Se `MeuTipo` não for genérico, o código acima é equivalente a este:

```crystal
tmp = MeuTipo.new
tmp["foo"] = "bar"
tmp
```

Se `MeuTipo` for genérico, o código acima é equivalente a este:

```crystal
tmp = MeuTipo(typeof("foo"), typeof("bar")).new
tmp["foo"] = "bar"
tmp
```

No caso de um tipo genérico, o argumentos de tipos também pode ser especificados:

```crystal
MeuTipo(String, String) {"foo": "bar"}
```
