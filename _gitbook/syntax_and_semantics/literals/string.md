# String

Uma [String](http://crystal-lang.org/api/String.html) representa uma sequência imutável de caracteres UTF-8.

Uma String geralmente é criada com um literal de string, envolvendo-se caracteres UTF-8 em aspas duplas:

```crystal
"olá mundo"
```

Uma contrabarra pode ser utilizada para denotar alguns caracteres dentro de uma string:

```crystal
"\"" # aspas duplas
"\\" # contrabarra
"\e" # escape
"\f" # form feed
"\n" # nova linha
"\r" # carriage return
"\t" # tabulação
"\v" # tabulação vertical
```

Você pode usar uma contrabarra seguida por até três dígitos para denotar um ponto de código escrito em octal:

```crystal
"\101" # == "A"
"\123" # == "S"
"\12"  # == "\n"
"\1"   # string com um caractere com o código de ponto 1
```

Você pode usar uma contrabarra seguida por um *u* e quatro caracteres hexadecimais para denotar um ponto de código unicode:

```crystal
"\u0041" # == "A"
```

Ou você pode usar chaves e especiifcar até seis números hexadecimais (de 0 a 10FFFF):

```crystal
"\u{41}"    # == "A"
"\u{1F52E}" # == "🔮"
```

Uma string pode envolver múltiplas linhas:

```crystal
"hello
      world" # é o mesmo que "hello\n      world"
```

Perceba que no exemplo acima os espaços antes e depois das linhas, bem como as
quebras de linha, aparecem na string resultante. Para evitar isso, você pode
dividir uma string em múltiplas linhas juntando múltiplos literais com uma
contrabarra:

```crystal
"hello " \
"world, " \
"no newlines" # é o mesmo que "hello world, no newlines"
```

Alternativamente, uma contrabarra seguida por uma nova linha pode ser inserida
dentro do literal de string:

```crystal
"hello \
     world, \
     no newlines" # é o mesmo que "hello world, no newlines"
```

Neste caso, o espaço em branco no começo e no final não é incluso na string
resultante.


Se você precisar escrever uma string que tem muitas aspas duplas, parênteses ou
caracteres similares, você pode usar literais alternativos:

```crystal
# Suporta aspas duplas e parênteses aninhados
%(hello ("world")) # same as "hello (\"world\")"

# Suporta aspas duplas e colchetes aninhados
%[hello ["world"]] # same as "hello [\"world\"]"

# Suporta aspas duplas e chaves aninhadas
%{hello {"world"}} # same as "hello {\"world\"}"

# Suporta aspas duplas e sinais de maior que e menor que
%<hello <"world">> # same as "hello <\"world\">"
```

## Heredoc

Você também pode usar um "heredoc" para criar uma string:

```crystal
<<-XML
<parent>
  <child />
</parent>
XML
```

Um "heredoc" é escrito com `<<-IDENT`, onde `IDENT` é um identificador, uma sequência de letras e números que precisa começar com uma letra. O "heredoc" termina na linha que começa com `IDENT`, ignorando espaços em branco antes da palavra.

Os espaços em branco no começo da linha são removidos do conteúdo do heredoc de acordo com o número de espaços que este último `IDENT` tem. Por exemplo:

```crystal
# O mesmo que "Hello\n  world"
<<-STRING
  Hello
    world
  STRING

# O mesmo que "  Hello\n    world"
<<-STRING
    Hello
      world
  STRING
```

## Interpolação

Para cirar uma String com expressões embutidas, você pode usar a interpolação de strings:

```crystal
a = 1
b = 2
"soma = #{a + b}"        # "soma = 3"
```

Isso chama `Object#to_s(IO)` em cada expressão envolvida por `#{...}`.
