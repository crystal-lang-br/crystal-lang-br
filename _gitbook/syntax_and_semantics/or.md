# ||

Um `||` (_or_) avalia seu lado esquerdo. Se ele for *falso*, ele avalia seu lado direito e recebe seu valor. Caso contrário, ele recebe o valor do lado esquerdo. Seu tipo é a união dos tipos de ambos os lados.

Você pode pensar em um `||` como açúcar sintático de um `if`:

```crystal
alguma_expressao_1 || alguma_expressao_2

# O código acima é o mesmo que:
tmp = alguma_expressao_1
if tmp
  tmp
else
  alguma_expressao_2
end
```
