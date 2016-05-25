# Usando o Compilador

Depois de [instalar](../installation/README.md) o compilador, você terá um binário `crystal` à sua disposição.

Nas próximas seções, o sinal de dólar (`$`) denota o terminal.

## Compilando e rodando ao mesmo tempo

Para compilar e imediatamente rodar um programa, você pode invocar `crystal` com um único nome de arquivo:

```
$ crystal algum_programa.cr
```

Os arquivos do Crystal terminam com a extensão `.cr`.

Alternativamente, você pode usar o comando `run`:

```
$ crystal run algum_programa.cr
```

## Criando um executável

Para criar um executável, use o comando `build`:

```
$ crystal build algum_programa.cr
```

Isso criará um arquivo `algum_programa` que você pode executar:

```
$ ./algum_programa
```

**Observação:** por padrão os executáveis gerados **não estão completamente otimizados**. Para ativar as otimizações, use a flag `--release`:

```
$ crystal build algum_programa.cr --release
```

Assegure-se de sempre usar `--release` para gerar executáveis prontos para produção e para fazer benchmarks.

O motivo para isso é que a performance sem otimização ainda assim é muito boa e possibilita um tempo rápido de compilação, de modo que você pode usar o comando `crystal` quase como se fosse um interpretador.

## Criando um projeto ou biblioteca

Use o comando `init` para criar um projeto Crystal com a estrutura padrão de diretórios.

```
$ crystal init lib MinhaBibliotecaLegal
      create  MinhaBibliotecaLegal/.gitignore
      create  MinhaBibliotecaLegal/LICENSE
      create  MinhaBibliotecaLegal/README.md
      create  MinhaBibliotecaLegal/.travis.yml
      create  MinhaBibliotecaLegal/Projectfile
      create  MinhaBibliotecaLegal/src/MinhaBibliotecaLegal.cr
      create  MinhaBibliotecaLegal/src/MinhaBibliotecaLegal/version.cr
      create  MinhaBibliotecaLegal/spec/spec_helper.cr
      create  MinhaBibliotecaLegal/spec/MinhaBibliotecaLegal_spec.cr
Initialized empty Git repository in ~/MinhaBibliotecaLegal/.git/
```

## Outros comandos e opções

Para ver a lista completa de comandos, invoque `crystal` sem argumentos.

```
$ crystal
Usage: crystal [command] [switches] [program file] [--] [arguments]

Command:
    init                     generate new crystal project
    build                    compile program file
    deps                     install project dependencies
    docs                     generate documentation
    eval                     eval code from args or standard input
    run (default)            compile and run program file
    spec                     compile and run specs (in spec directory)
    tool                     run a tool
    --help, -h               show this help
    --version, -v            show version
```

Para ver todas as opções disponíveis para um comando em particular, use a flag `--help` após um comando:

```
$ crystal build --help
Usage: crystal build [options] [programfile] [--] [arguments]

Options:
    --cross-compile flags            cross-compile
    -d, --debug                      Add symbolic debug info
    -D FLAG, --define FLAG           Define a compile-time flag
    --emit [asm|llvm-bc|llvm-ir|obj] Comma separated list of types of output for the compiler to emit
    -h, --help                       Show this message
    --ll                             Dump ll to .crystal directory
    --link-flags FLAGS               Additional flags to pass to the linker
    --mcpu CPU                       Target specific cpu type
    --no-color                       Disable colored output
    --no-codegen                     Don't do code generation
    -o                               Output filename
    --prelude                        Use given file as prelude
    --release                        Compile in release mode
    -s, --stats                      Enable statistics output
    --single-module                  Generate a single LLVM module
    --threads                        Maximum number of threads to use
    --target TRIPLE                  Target triple
    --verbose                        Display executed commands
```
