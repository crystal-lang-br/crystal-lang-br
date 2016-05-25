# Atribuição

A atribuição é feita com o caractere de igual (`=`).

```crystal
# Atribui a uma variável local
local = 1

# Atribui a uma variável de instância
@instance = 2

# Atribui a uma variável de classe
@@class = 3

# Atribui a uma variável global
$global = 4
```

Cada um dos tipos de variáveis acima serão explicados adiante.

Está disponível um pouco de açúcar sintático com o caractere `=`:

```crystal
local += 1  # é o mesmo que: local = local + 1

# A sintaxe acima também funciona com estes operadores:
# +, -, *, /, %, |, &, ^, **, <<, >>

local ||= 1 # é o mesmo que: local || (local = 1)
local &&= 1 # é o mesmo que: local && (local = 1)
```

A invocação de um método que termina com `=` também tem açúcar sintatico:

```crystal
# Um setter
person.name=("John")

# A linha acima pode ser escrita como:
person.name = "John"

# Uma atribuição de um índice
objects.[]=(2, 3)

# A linha acima pode ser escrita como:
objects[2] = 3

# Não está relacionado a atribuição, mas também é tem açúcar sintático:
objects.[](2, 3)

# A linha acima pode ser escrita como:
objects[2, 3]
```

O açúcar sintático do operador `=` também está disponível para setters e indexadores. Perceba que `||` e `&&` usam o método `[]?` para checar a presença da chave.

```crystal
person.age += 1        # é o mesmo que: person.age = person.age + 1

person.name ||= "John" # é o mesmo que: person.name || (person.name = "John")
person.name &&= "John" # é o mesmo que: person.name && (person.name = "John")

objects[1] += 2        # é o mesmo que: objects[1] = objects[1] + 2

objects[1] ||= 2       # é o mesmo que: objects[1]? || (objects[1] = 2)
objects[1] &&= 2       # é o mesmo que: objects[1]? && (objects[1] = 2)
```
