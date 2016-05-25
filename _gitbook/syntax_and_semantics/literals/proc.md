# Proc

Uma [Proc](http://crystal-lang.org/api/Proc.html) representa o ponteiro de uma função com um contexto opcional (os dados do ambiente). Geralmente é criado com um literal de proc:

```crystal
# Uma proc sem argumentos:
->{ 1 } # Proc(Int32)

# Uma proc com um argumento:
->(x : Int32) { x.to_s } # Proc(Int32, String)

# Uma proc com dois argumentos:
->(x : Int32, y : Int32) { x + y } # Proc(Int32, Int32, Int32)
```

Os tipos dos argumentos são obrigatórios, exceto ao enviar diretamente um literal de proc a uma `fun` de uma lib em bindings para C.

O tipo do retorno é inferido do corpo da proc.

Também é disponibilizado um método `new` especial:

```crystal
Proc(Int32, String).new { |x| x.to_s } # Proc(Int32, String)
```

Esta forma permite que você especifique o tipo de retorno e verifique-o em relação ao corpo da proc.

## O tipo Proc

Para denotar o tipo Proc, você pode escrever:

```crystal
# Uma Proc aceitando um único argumento Int32 e retornando uma String
Proc(Int32, String)

# Uma proc que não aceita nenhum argumento e retorna Void
Proc(Void)

# Uma proc que aceita dois argumentos (um Int32 e uma String) e retorna um Char
Proc(Int32, String, Char)
```

Nas restrições de tipos, argumentos de tipo genérico e outros lugares onde espera-se um tipo, você pode usar uma sintaxe mais curta, conforme explicado no capítulo sobre [tipos](../type_grammar.md):

```crystal
# Um array de Proc(Int32, String, Char)
Array(Int32, String -> Char)
```

## Invocando

Para invocar uma Proc, você chama o método `call` dela. O número de argumentos deve coincidir com o tipo da proc:

```crystal
proc = ->(x : Int32, y : Int32) { x + y }
proc.call(1, 2) #=> 3
```

## A Partir de Métodos

Uma Proc pode ser criada a partir de um método existente:

```crystal
def one
  1
end

proc = ->one
proc.call #=> 1
```

Se o método tiver argumentos, você precisa especificar seus tipos:

```crystal
def plus_one(x)
  x + 1
end

proc = ->plus_one(Int32)
proc.call(41) #=> 42
```

Uma proc pode opcionalmente especificar um receptáculo:

```crystal
str = "hello"
proc = ->str.count(Char)
proc.call('e') #=> 1
proc.call('l') #=> 2
```
