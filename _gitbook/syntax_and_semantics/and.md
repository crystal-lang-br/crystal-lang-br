# &&

O `&&` (_and_) avalia seu lado esquerdo. Se ele for *verdadeiro*, ele avalia o seu lado direito e recebe seu valor. Caso contrário, ele recebe o valor do lado esquerdo. Seu tipo é a união dos tipos de ambos os lados.

Você pode pensar em um `&&` como açúcar sintático para um `if`:

```crystal
alguma_expressao_1 && alguma_expressao_2

# O código acima é o mesmo que:
tmp = alguma_expressao_1
if tmp
  alguma_expressao_2
else
  tmp
end
```
