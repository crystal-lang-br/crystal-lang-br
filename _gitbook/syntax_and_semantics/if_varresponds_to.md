# if var.responds_to?(...)

Se a condição de um `if` é um teste `responds_to?`, é garantido que no bloco do `then` o tipo da variável está restrito aos tipos que respondem a aquele método:

```crystal
if a.responds_to?(:abs)
  # aqui o tipo de "a" será reduzido a aqueles que respondem ao método "abs"
end
```

Além disso, no bloco `else`, é garantido que o tipo da variável está restrito aos tipos que não respondem a aquele método:

```crystal
a = alguma_condicao ? 1 : "olá"
# a : Int32 | String

if a.responds_to?(:abs)
  # aqui "a" será Int32, já que Int32#abs existe, mas String#abs não
else
  # aqui "a" será String
end
```

O código acima **não funciona** com variáveis de instância, de classe ou globais. Para trabalhar com elas, primeiro atributa a uma variável:

```crystal
if @a.responds_to?(:abs)
  # aqui não garante-se que @a responda a `abs`
end

a = @a
if a.responds_to?(:abs)
  # aqui é garantido que "a" responde a `abs`
end

# Versão um pouco mais curta:
if (a = @a).responds_to?(:abs)
  # aqui é garantido que "a" responde a `abs`
end
```
