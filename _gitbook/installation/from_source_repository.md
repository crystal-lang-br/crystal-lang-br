# Do Código-fonte

Se você quer colaborar com o projeto, entao você pode querer instalar o Crystal a partir do código-fonte. Mas o Crystal é escrito no próprio Crystal! Então primeiramente você precisa usar um dos métodos descritos anteriormente para ter um compilador rodando.

Você também precisará do LLVM 3.5 ou 3.6 no path. Se você está usando um Mac e a fórmula do Homebrew, isso é configurado automaticamente se você instalar o Crystal adicionando a flag `--with-llvm`.

Então clone o repositório:

```
git clone https://github.com/crystal-lang/crystal.git
```

e você está pronto para começar a programar.

Para fazer o build de sua própria versão do compilador, rode `make`. O novo compilador estará localizado em `.build/crystal`.

Assegure-se de instalar [todas as bibliotecas necessárias](https://github.com/crystal-lang/crystal/wiki/All-required-libraries). Você também pode querer ler o [guia de colaboração](https://github.com/crystal-lang/crystal/blob/master/Contributing.md).

Dentro do repositório você também encontrará um script de wrapper em `bin/crystal`. Esse script executará o compilador instalado globalmente ou aquele que você acabou de compilar (se houver algum).
