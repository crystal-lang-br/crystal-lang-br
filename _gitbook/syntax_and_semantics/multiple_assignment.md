# Atribuição Múltipla

Você pode declarar/atribuir múltiplas variáveis ao mesmo tempo, separando as expressões com uma vírgula (`,`):

```crystal
name, age = "Crystal", 1

# A linha acima é o mesmo que isso:
temp1 = "Crystal"
temp2 = 1
name  = temp1
age   = temp2
```

Perceba que uma vez que as expressões são atribuídas a variáveis temporárias, é possível trocar os conteúdos de variáveis em uma única linha:

```crystal
a = 1
b = 2
a, b = b, a
a #=> 2
b #=> 1
```

Se o lado da direita contém somente uma expressão, ela é considerada como um tipo indexado e o seguinte açúcar sintático se aplica:

```crystal
name, age, source = "Crystal,1,github".split(",")

# A linha acima é o mesmo que isso:
temp = "Crystal,1,github".split(",")
name   = temp[0]
age    = temp[1]
source = temp[2]
```

Se o lado da esquerda contém uma única variável, o lado da direita é considerado como um array:

```crystal
names = "John", "Peter", "Jack"

# A linha acima é o mesmo que isso:
names = ["John", "Peter", "Jack"]
```

A atribuição múltipla também está disponível para métodos que terminam com `=`:

```crystal
person.name, person.age = "John", 32

# É o mesmo que:
temp1 = "John"
temp2 = 32
person.name = temp1
person.age = temp2
```

E também está disponível para indexadores (`[]=`):

```crystal
objects[1], objects[2] = 3, 4

# É o mesmo que:
temp1 = 3
temp2 = 4
objects[1] = temp1
objects[2] = temp2
```
