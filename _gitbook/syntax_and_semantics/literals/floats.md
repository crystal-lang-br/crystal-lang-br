# Floats

Exixtem dois tipos de pontos flutuantes, [Float32](http://crystal-lang.org/api/Float32.html) e [Float64](http://crystal-lang.org/api/Float64.html),
que correspondem aos tipos [binary32](http://en.wikipedia.org/wiki/Single_precision_floating-point_format)
e [binary64](http://en.wikipedia.org/wiki/Double_precision_floating-point_format)
definidos pelo IEEE.

Um literal de ponto flutuante é um sinal de `+` ou `-` opcional, seguido por uma
sequência de número ou underscores, seguidos por um ponto, seguido por números
ou underscores, seguidos por sufixo opcional de expoente, seguidos por um sufixo
opcional de tipo. Se nenhum sufixo estiver presente, o tipo do literal será
`Float64`.

```crystal
1.0      # Float64
1.0_f32  # Float32
1_f32    # Float32

1e10     # Float64
1.5e10   # Float64
1.5e-7   # Float64

+1.3     # Float64
-0.5     # Float64
```

O underscore `_` antes do sufixo é opcional.

Underscores podem ser utilizados para tornar alguns números mais legíveis:

```crystal
1_000_000.111_111 # é melhor do que 1000000.111111
```
