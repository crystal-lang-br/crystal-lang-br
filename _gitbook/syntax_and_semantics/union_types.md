# Tipos união

O tipo de uma variável ou expressão pode consistir de múltiplos tipos. Chamamos isso de tipo união. Por exemplo, quando atribuímos valores a uma mesma variável em partes diferentes de um [if](if.html):

```crystal
if 1 + 2 == 3
  a = 1
else
  a = "olá"
end

a # : Int32 | String
```

No final do if, `a` terá o tipo `Int32 | String`, ou seja, "a união de Int32 e String". Este tipo união é criado automaticamente pelo compilador. Em tempo de execução, `a` só terá um tipo, é claro. Pode-se visualizar isso invocando o método `class`:

```crystal
# O tipo em tempo de execução
a.class # => Int32
```

O tipo em tempo de compilação pode ser visto usando [typeof](typeof.html):

```crystal
# O tipo em tempo de compilação
typeof(a) # => Int32 | String
```

Uma união pode consistir de um número de tipos grande e arbitrário. Quando invocamos um método em uma expressão cujo tipo seja um tipo união, todos os tipos nessa união precisam responder ao método, doutra forma haverá um erro em tempo de compilação. O tipo da chamada do método é o tipo união de todos os tipos de retorno desses métodos.

```crystal
# to_s é definido para Int32 e String, ele retorna String
a.to_s # => String

a + 1 # Erro, porque String#+(Int32) não está definido
```

## Regras para tipos união

No caso geral, quando dois tipos `T1` e `T2` são combinados, o resultado é uma união de `T1 | T2`. No entanto, existem alguns casos específicos onde o tipo resultante é diferente.

### União de classes e structs sob a mesma hierarquia

Se `T1` e `T2` estão sob a mesma hierarquia, e seu ancestral mais próximo em comum `Parent` não for `Reference`, `Struct`, `Int`, `Float` e nem `Value`, o tipo resultante é `Parent+`. Isso é chamado de um tipo virtual, o que basicamente significa que o compilador verá esse tipo como sendo `Parent` ou qualquer um de seus sub-tipos.

Por exemplo:

```crystal
class Foo
end

class Bar < Foo
end

class Baz < Foo
end

bar = Bar.new
baz = Baz.new

# Aqui o tipo de foo será Bar | Baz,
# mas uma vez que tanto Bar quanto Baz herdam de Foo,
# o tipo resultante é Foo+
foo = rand < 0.5 ? bar : baz
typeof(foo) # => Foo+
```

### União de tuplas de mesmo tamanho

A união de duas tuplas de mesmo tamanho resultado em um tipo de tupla que possui a união dos tipos em cada posição.

Por exemplo:

```crystal
t1 = {1, "oi"}   # Tuple(Int32, String)
t2 = {true, nil} # Tuple(Bool, Nil)

t3 = rand < 0.5 ? t1 : t2
typeof(t3) # Tuple(Int32 | Bool, String | Nil)
```

### União de tuplas nomeadas com as mesmas chaves

A união de duas tuplas nomeadas com as mesmas chaves (não importa a ordem) resulta em um tipo de tupla nomeada que possui a união dos tipos em cada chave. A ordem das chaves será a mesma que a das chaves à esquerda.

Por exemplo:

```crystal
t1 = {x: 1, y: "oi"}   # Tuple(x: Int32, y: String)
t2 = {y: true, x: nil} # Tuple(y: Bool, x: Nil)

t3 = rand < 0.5 ? t1 : t2
typeof(t3) # NamedTuple(x: Int32 | Nil, y: String | Bool)
```
