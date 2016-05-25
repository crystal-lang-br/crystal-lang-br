# Como uma expressão

O valor de um `if` é o valor da última expressão encontrada em cada um de seus blocos:

```crystal
a = if 2 > 1
      3
    else
      4
    end
a #=> 3
```

Se um bloco do `if` estiver vazio ou ausente, considera-se como se houvesse `nil` nele:

```crystal
if 1 > 2
  3
end

# O código acima é o mesmo que:
if 1 > 2
  3
else
  nil
end

# Outro exemplo:
if 1 > 2
else
  3
end

# O código acima é o mesmo que:
if 1 > 2
  nil
else
  3
end
```
