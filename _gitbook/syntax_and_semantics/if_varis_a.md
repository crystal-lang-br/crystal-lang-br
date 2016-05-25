# if var.is_a?(...)

Se a condição de um `if` for um teste `is_a?`, garante-se que o tipo da variável está restrito ao tipo no bloco `then`.

```crystal
if a.is_a?(String)
  # aqui "a" é uma String
end

if b.is_a?(Number)
  # aqui "b" é um Number
end
```

Além disso, no bloco `else`, garante-se que o tipo da variável não está restrito a aquele tipo:

```crystal
a = alguma_condicao ? 1 : "olá"
# a : Int32 | String

if a.is_a?(Number)
  # a : Int32
else
  # a : String
end
```

Perceba que vcê pode usar qualquer tipo como um teste `is_a?`, como por exemplo classes abstratas e módulos.

O código acima também funciona se houver _ands_ (`&&`) na condição:

```crystal
if a.is_a?(String) && b.is_a?(Number)
  # aqui "a" é uma String e "b" é um Number
end
```

O código acima **não funciona** com variáveis de instância, de classe ou globais. Para trabalhar com elas, primeiro atribua a uma variável:

```crystal
if @a.is_a?(String)
  # aqui não garante-se que @a seja uma String
end

a = @a
if a.is_a?(String)
  # aqui é garantido que "a" é uma String
end

# Versão um pouco mais curta:
if (a = @a).is_a?(String)
  # aqui é garantido que "a" é uma String
end
```
