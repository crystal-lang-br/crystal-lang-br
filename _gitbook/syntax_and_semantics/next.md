# next

Você pode usar `next` para tentar executar a próxima iteração do loop de um `while`. Após executar `next`, a condição do `while` é checada e, se for *verdadeira*, o corpo será executado.

```crystal
a = 1
while a < 5
  a += 1
  if a == 3
    next
  end
  puts a
end
# O código acima imprime os números 2, 4 e 5
```
