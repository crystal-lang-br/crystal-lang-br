# case

Um `case` é uma expressão de controle que permite realizar uma forma de _pattern matching_. Ele permite escrever uma corrente de if-else-if com uma pequena mudança na semântica e alguns construtores mais poderosos.

Em sua forma mai básica, ele permite comparar um valor com outros:

```crystal
case exp
when valor1, valor2
  faz_alguma_coisa
when valor3
  faz_outra_coisa
else
  faz_mais_uma_coisa
end

# O código acima é o mesmo que:
tmp = exp
if valor1 === tmp || valor2 === tmp
  faz_alguma_coisa
elsif valor3 === tmp
  faz_outra_coisa
else
  faz_mais_uma_coisa
end
```

Perceba que é usado o `===` para comparar uma expressão no valor do `case`.

Se a expressão do `when` for um tipo, é usado o `is_a?`. Além disso, se a expressão do `case` for uma variável ou a atribuição de um variável, o tipo dela será restringido:

```crystal
case var
when String
  # var : String
  faz_alguma_coisa
when Int32
  # var : Int32
  faz_outra_coisa
else
  # aqui "var" não é nem String e nem Int32
  faz_mais_uma_coisa
end

# O código acima é o mesmo que:
if var.is_a?(String)
  faz_alguma_coisa
elsif var.is_a?(Int32)
  faz_outra_coisa
else
  faz_mais_uma_coisa
end
```

Você pode invocar um método na expressão do `case` em um `when`, utilizando a sintaxe de objeto implícito:

```crystal
case num
when .even?
  faz_alguma_coisa
when .odd?
  faz_outra_coisa
end

# O código acima é o mesmo que:
tmp = num
if tmp.even?
  faz_alguma_coisa
elsif tmp.odd?
  faz_outra_coisa
end
```

Por fim, você pode omitir o valor do `case`:

```crystal
case
when cond1, cond2
  faz_alguma_coisa
when cond3
  faz_outra_coisa
end

# O código acima é o mesmo que:
if cond1 || cond2
  faz_alguma_coisa
elsif cond3
  faz_outra_coisa
end
```

Isso as vezes leva a um código que é mais natural de ler.


## Literal de tupla

Quando uma expressão case for um literal de tupla, existem algumas diferenças semânticas se uma condição when também for um literal de tupla.

### O tamanho das tuplas deve ser igual

```crystal
case {value1, value2}
when {0, 0} # OK, 2 elementos
  # ...
when {1, 2, 3} # Erro do compilador, porque nunca vai bater
  # ...
end
```

### Underscores são permitidos

```crystal
case {value1, value2}
when {0, _}
  # Executa se 0 === value1, nenhum teste é feito com value2
when {_, 0}
  # Executa se 0 === value2, nenhum teste é feito com value1
end
```

### Objetos implícitos são permitidos

```crystal
case {value1, value2}
when {.even?, .odd?}
  # Executa se value1.even? && value2.odd?
end
```

### Comparar com um tipo realizará uma checagem com is_a?

```crystal
case {value1, value2}
when {String, Int32}
  # Executa se value1.is_a?(String) && value2.is_a?(Int32)
  # O compilador entende que o tipo de value1 é uma String,
  # e que o tipo de value2 é um Int32
end
```
