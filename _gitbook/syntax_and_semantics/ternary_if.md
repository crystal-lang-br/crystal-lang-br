# if ternário

O `if` ternário permite escrever um `if` de uma maneira mais curta:

```crystal
a = 1 > 2 ? 3 : 4

# O código acima é o mesmo que:
a = if 1 > 2
      3
    else
      4
    end
```
