# Char

Um [Char](http://crystal-lang.org/api/Char.html) representa um [ponto de código](http://pt.wikipedia.org/wiki/Ponto_de_código) [Unicode](http://pt.wikipedia.org/wiki/Unicode).
Ele ocupa 32 bits.

Ele é criado envolvendo um caractere UTF-8 em aspas simples.

```crystal
'a'
'z'
'0'
'_'
'あ'
```

Você pode usar uma contra-barra para denotar alguns caracteres:

```crystal
'\'' # aspa simples
'\\' # contra-barra
'\e' # escape
'\f' # form feed
'\n' # nova linha
'\r' # carriage return
'\t' # tabulação
'\v' # tabulação vertical
```

Você pod eusar uma contrabarra seguida por até três dígitos para denotar um ponto de código escrito em octal:

```crystal
'\101' # == 'A'
'\123' # == 'S'
'\12'  # == '\n'
'\1'   # code point 1
```

Você pode usar uma contrabarra seguida por um *u* e quatro caracteres hexadecimais para denotar um ponto de código unicode:

```crystal
'\u0041' # == 'A'
```

Ou você pode usar chaves e especificar até seis números hexadecimais (de 0 a 10FFFF):

```crystal
'\u{41}'    # == 'A'
'\u{1F52E}' # == '🔮'
```
