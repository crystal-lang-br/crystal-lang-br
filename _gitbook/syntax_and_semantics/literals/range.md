# Range

Um [Range](http://crystal-lang.org/api/Range.html) geralmente é construído com um literal de range:

```crystal
x..y  # um range inclusivo, representado na matemática como [x, y]
x...y # um range exclusivo, representado na matemática como [x, y)
```

Um jeito fácil de se lembrar qual é inclusivo e qual é exclusivo é pensar no ponto extra adicional como se ele empurrasse o *y* para fora, assim deixando-o fora do range.
