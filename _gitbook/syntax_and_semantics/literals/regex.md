# Regex

Expressões regulares são representadas pela classe [Regex](http://crystal-lang.org/api/Regex.html), que geralmente é criada com um literal:

```crystal
foo_or_bar = /foo|bar/
heeello    = /h(e+)llo/
integer    = /\d+/
```

Um literal de expressão regular é delimitado por `/` e usa a sintaxe [PCRE](http://pcre.org/pcre.txt).

Pode ser seguido por estes modificadores:

* i: ignorar maiúsculas e minúsculas (PCRE_CASELESS)
* m: multi-linhas (PCRE_MULTILINE)
* x: estendido (PCRE_EXTENDED)

Por exemplo:

```crystal
r = /foo/imx
```

Barras precisam ser escapadas:

```crystal
barra = /\//
```

É disponibilizada uma sintaxe alternativa:

```crystal
r = %r(regex com barra: /)
```
