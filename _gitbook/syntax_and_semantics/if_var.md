# if var

Se uma variável for a condição de um `if`, dentro do bloco `then` a variável será considerada como não tendo o tipo `Nil`:

```crystal
a = alguma_condicao ? nil : 3
# a é Int32 ou Nil

if a
  # Já que o único jeito de cair aqui é se "a" for verdadeiro,
  # "a" não pode ser nil. Então aqui "a" é Int32.
  a.abs
end
```

Isso também se aplica quando uma variável é atribuída em uma condição `if`:

```crystal
if a = alguma_expressao
  # aqui "a" não é nil
end
```

Essa lógica também se aplica se houver _ands_ (`&&`) na condição:

```crystal
if a && b
  # garante-se que aqui tanto "a" quanto "b" não são Nil
end
```

Aqui, no lado direito da expressão `&&`, também é garantido que `a` não tem o valor `Nil`.

É claro, se o for atribuído novamente o valor da variável dentro do bloco `then`, essa variável terá um novo tipo baseado na expressão atribuída.

A lógica acima **não funciona** com variáveis de instância, variáveis de classe ou variáveis globais:

```crystal
if @a
  # aqui @a pode ser nil
end
```

Isso acontece porque qualquer chamada de método pode potencialmente afetar essa variável de instância, tornando ela `nil`. Outro motivo é que outra _thread_ poderia mudar essa variável de instância após checá-la na condição.

Para fazer algo com `@a` somente se ele não for `nil`, você tem duas opções:

```crystal
# Primeira opção: atribua ele a uma variável
if a = @a
  # aqui "a" não pode ser nil
end

# Segunda opção: use `Object#try`, encontrado na biblioteca padrão
@a.try do |a|
  # aqui "a" não pode ser nil
end
```

Essa lógica também não funciona com procs e chamadas de métodos, inclusive getters e propriedades, porque não se pode garantir que procs e métodos que podem ser `nil` (ou, mais genericamente, procs e métodos do tipo união) retornem o mesmo tipo específico em duas chamadas sucessivas.

```crystal
if method # primeira chamada ao método que pode retornar Int32 ou Nil
          # aqui sabemos que a primeira chamada não retornou Nil
  method  # a segunda chamada também ainda pode retornar Int32 ou Nil
end
```

A técnica descrita acima para variáveis de instância também funcionará com procs e chamadas de métodos.
