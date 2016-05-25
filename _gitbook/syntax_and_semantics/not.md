# if !

O operador `!` retorna um `Bool` que resulta da negação da [veracidade](truthy_and_falsey_values.html) de um valor.

Quando utilizado em um `if` em conjunto com uma variável, `is_a?`, `responds_to?` ou `nil?`, o compilador restringirá os tipos de acordo:

```crystal
a = alguma_condicao ? nil : 3
if !a
  # aqui a é Nil porque a é falso nesse bloco
else
  # aqui a é Int32, porque a é verdadeiro nesse bloco
end
```

```crystal
b = alguma_condicao ? 1 : "x"
if !b.is_a?(Int32)
  # aqui b é String porque ela não é um Int32
end
```
