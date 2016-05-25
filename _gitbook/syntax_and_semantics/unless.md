# unless

Um `unless` avalia o bloco `then` somente se a sua condição é *falsa*, ou doutra forma avalia o bloco `else`, se houver algum. Em outras palavras, ele funciona de maneira oposta ao `if`:

```crystal
unless alguma_condicao
  expressao_then
else
  expressao_else
end

# O código acima é o mesmo que:
if alguma_condicao
  expressao_else
else
  expressao_then
end

# Também pode ser escrito como um sufixo
fechar_porta unless porta_fechada?
```
