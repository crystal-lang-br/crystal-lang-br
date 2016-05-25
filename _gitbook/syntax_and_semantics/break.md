# break

Você pode usar `break` para sair de um loop de um `while`:

```crystal
a = 2
while (a += 1) < 20
  if a == 10
    # vai para 'puts a'
    break
  end
end
puts a #=> 10
```
