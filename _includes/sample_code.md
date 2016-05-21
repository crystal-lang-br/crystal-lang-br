{% highlight ruby %}
# Um servidor HTTP bem básico
require "http/server"

server = HTTP::Server.new(8080) do |context|
  context.response.content_type = "text/plain"
  context.response.print "Hello world, got #{context.request.path}!"
end

puts "Rodando em: http://0.0.0.0:8080"
server.listen
{% endhighlight %}
