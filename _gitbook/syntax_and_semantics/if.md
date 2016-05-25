# if

Um `if` executa o bloco do `then` se a sua condição for *verdadeira*, caso contrário, executa o bloco do `else`, se houver um.

```crystal
a = 1
if a > 0
  a = 10
end
a #=> 10

b = 1
if b > 2
  b = 10
else
  b = 20
end
b #=> 20
```

Para escrever uma corrente de if-else-if, você utiliza o `elsif`:

```crystal
if alguma_condicao
  faz_alguma_coisa
elsif alguma_outra_condicao
  faz_outra_coisa
else
  faz_aquilo
end
```

Após um `if`, o tipo de uma variável depende do tipo das expressões usadas em ambos os blocos.

```crystal
a = 1
if alguma_condicao
  a = "olá"
else
  a = true
end
# a : String | Bool

b = 1
if alguma_condicao
  b = "hello"
end
# b : Int32 | String

if alguma_condicao
  c = 1
else
  c = "olá"
end
# c : Int32 | String

if alguma_condicao
  d = 1
end
# d : Int32 | Nil
```

Perceba que se uma variável é declarada dentro de um dos blocos, mas não no outro, no final do `if` ela também conterá o tipo `Nil`.

Dentro do bloco de um `if`, o tipo de uma variável é aquele que foi atribuído naquele bloco, ou aquele que ela tinha antes do bloco se ela não foi reatribuída:

```crystal
a = 1
if alguma_condicao
  a = "olá"
  # a : String
  a.size
end
# a : String | Int32
```

Ou seja, o tipo de uma variável é o tipo da(s) última(s) expressão(ões) atribuídas a ela.

Se um dos blocos nunca chega até depois do final de um `if`, como no caso de um `return`, `next`, `break` ou `raise`, esse tipo não é considerado no final do `if`:

```crystal
if alguma_condicao
  e = 1
else
  e = "olá"
  # e : String
  return
end
# e : Int32
```
