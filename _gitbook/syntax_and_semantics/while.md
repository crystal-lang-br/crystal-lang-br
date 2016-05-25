# while

Um `while` executa seu corpo enquanto sua condição for *verdadeira*.

```crystal
while alguma_condicao
  faz_isso
end
```

Primeiro a condição é testada, e se for *verdadeira*, o corpo é executado. Ou seja, pode ser que o corpo nunca seja executado.

O tipo de um `while` é sempre `Nil`.

De maneira semelhante a um `if`, se a condição de um `while` for uma variável, é garantido que a variável não é `nil` dentro do corpo. Se a condição for um teste `var.is_a?(Type)`, é garantido que `var` é do tipo Type dentro do corpo. E se a condição for `var.responds_to?(:method)`, é garantido que `var` é de um tipo que responde a aquele método.

O tipo de uma variável depois de um `while` depende do tipo que ela tinha antes do `while` e do tipo que ela tinha antes de deixar o corpo do `while`:

```crystal
a = 1
while alguma_condicao
  # a : Int32 | String
  a = "olá"
  # a : String
  a.size
end
# a : Int32 | String
```

## Checando a condição no final de um loop

Se você precisa executar o corpo pelo menos uma vez e então checar por uma condição de interrupção, você pode fazer o seguinte:

```crystal
while true
  faz_alguma_coisa
  break if alguma_condicao
end
```

Ou usar o `loop`, encontrado na biblioteca padrão:

```crystal
loop do
  faz_alguma_coisa
  break if alguma_condicao
end
```
