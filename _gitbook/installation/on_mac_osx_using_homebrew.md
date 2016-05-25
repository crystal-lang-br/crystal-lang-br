# No Mac OSX Usando Homebrew

Para instalar facilmente o Crystal no seu Mac, você pode usar o [Homebrew](http://brew.sh/).

```
brew update
brew install crystal-lang
```

Se você planeja contribuir com o projeto, você pode achar útil também instalar o LLVM, então substitua a última linha por:

```
brew install crystal-lang --with-llvm
```

## Resolvendo Problemas no OSX 10.11 (El Capitan)

Se você encontrar um erro do tipo:

```
ld: library not found for -levent
```

você precisa reinstalar as ferramentas de linha de comando e então selecionar a _toolchain_ ativa padrão:

```
$ xcode-select --install
$ xcode-select --switch /Library/Developer/CommandLineTools
```
