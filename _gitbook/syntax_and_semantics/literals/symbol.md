# Symbol

Um símbolo ([Symbol](http://crystal-lang.org/api/Symbol.html)) é uma constante
que é identificada por um nome sem que você tenha que atribuir um valor numérico
a ela.

```crystal
:hello
:good_bye

# Símbolos com espaço
:"símbolo com espaço"

# Terminando com pontos de interrogação e exclamação
:interrogação?
:exclamação!

# Para os operadores
:+
:-
:*
:/
:==
:<
:<=
:>
:>=
:!
:!=
:=~
:!~
:&
:|
:^
:~
:**
:>>
:<<
:%
:[]
:[]?
:[]=
:<=>
:===
```

Internamente, um símbolo é representado como um `Int32`.
