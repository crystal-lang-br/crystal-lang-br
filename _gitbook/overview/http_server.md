# Servidor HTTP

Um exemplo ligeiramente mais interessando é o de um servidor HTTP:

```crystal
require "http/server"

server = HTTP::Server.new(8080) do |context|
  context.response.content_type = "text/plain"
  context.response.print "Hello world! The time is #{Time.now}"
end

puts "Listening on http://0.0.0.0:8080"
server.listen
```

O código acima fará sendio depois que você ler a documentação completa, mas já podemos aprender algumas coisas.

* Você pode [incluir](../syntax_and_semantics/requiring_files.html) código definido em outros arquivos:

    ```ruby
    require "http/server"
    ```
* Você pode definir [variáveis locais](../syntax_and_semantics/local_variables.html) sem a necessidade de especificar o seu tipo:

    ```ruby
    server = HTTP::Server.new ...
    ```

* Você programa invocando [métodos](../syntax_and_semantics/classes_and_methods.html) (ou enviando mensagens) em objetos.

    ```ruby
    HTTP::Server.new(8000) ...
    ...
    Time.now
    ...
    puts "Listening on http://0.0.0.0:8080"
    ...
    server.listen
    ```

* Você pode usar blocos de código, ou simplesmente [blocos](../syntax_and_semantics/blocks_and_procs.html), que são um modo muito conveniente de reaproveitar código e usar algumas características do mundo funcional:

    ```ruby
    HTTP::Server.new(8080) do |context|
      ...
    end
    ```

* Você pode criar strings facilmente com conteúdo embutido, também chamado de interpolação de strings. A linguagem também vem com outras [sintaxes](../syntax_and_semantics/literals.html) para criar arrays, hashes, ranges, tuplas e mais:

    ```ruby
    "Hello world! The time is #{Time.now}"
    ```
