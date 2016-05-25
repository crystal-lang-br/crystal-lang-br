# if var.nil?

Se a condição de um `if` for `var.nil?`, então para o compilador o tipo de `var` no bloco `then` será tido como `Nil` e no bloco `else` como não-`Nil`:

```crystal
a = alguma_condicao ? nil : 3
if a.nil?
  # aqui a é Nil
else
  # aqui a é Int32
end
```
