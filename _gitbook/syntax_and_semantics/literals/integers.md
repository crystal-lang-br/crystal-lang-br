# Integers

Existem quatro tipos de inteiros com sinal: [Int8](http://crystal-lang.org/api/Int8.html), [Int16](http://crystal-lang.org/api/Int16.html), [Int32](http://crystal-lang.org/api/Int32.html) e [Int64](http://crystal-lang.org/api/Int64.html), que permitem representar números de 8, 16, 32 e 64 bits, respectivamente.

Existem quatro tipos de inteiros sem sinal: [UInt8](http://crystal-lang.org/api/UInt8.html), [UInt16](http://crystal-lang.org/api/UInt16.html), [UInt32](http://crystal-lang.org/api/UInt32.html) e [UInt64](http://crystal-lang.org/api/UInt64.html).

Um literal de inteiro é um sinal de `+` ou `-` opcional, seguido por uma
sequêcia de dígitos e underscores, opcionalmente seguidos por um sufixo. Se
nenhum sufixo estiver presente, o tipo do literal será o menor em que o número
couber dentr `Int32`, `Int64` e `UInt64`:

```crystal
1      # Int32

1_i8   # Int8
1_i16  # Int16
1_i32  # Int32
1_i64  # Int64

1_u8   # UInt8
1_u16  # UInt16
1_u32  # UInt32
1_u64  # UInt64

+10    # Int32
-20    # Int32

2147483648          # Int64
9223372036854775808 # UInt64
```

O underscore `_` antes do sufixo é opcional.

Underscores podem ser usados para tornar alguns números mais legíveis:

```crystal
1_000_000 # é melhor do que 1000000
```

Números binários começam com `0b`:

```crystal
0b1101 # == 13
```

Números octais começam com um `0o`:

```crystal
0o123 # == 83
```

Números hexadecimais começam com `0x`:

```crystal
0xFE012D # == 16646445
0xfe012d # == 16646445
```
