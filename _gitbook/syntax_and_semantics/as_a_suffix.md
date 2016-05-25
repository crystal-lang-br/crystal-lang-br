# Como um sufixo

Um `if` pode ser escrito como um sufixo de uma expressão:

```crystal
a = 2 if alguma_condicao

# O código acima é o mesmo que:
if alguma_condicao
  a = 2
end
```

Às vezes isso leva a código que pode ser lido mais naturalmente.
