# until

Um `until` executa seu corpo até que sua condição seja *verdadeira*. Um `until` é apenas açúcar sintático para um `while` com a condição negada:

```crystal
until alguma_condicao
  faz_isso
end

# O código acima é o mesmo que:
while !alguma_condicao
  faz_isso
end
```

`break` e `next` também podem ser usados dentro de um `until`.
