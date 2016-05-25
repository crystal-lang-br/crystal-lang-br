# No Debian e Ubuntu

Nas distribuições derivadas de Debian, você pode utilizar o repositório oficial do Crystal.

## Configuração do repositório

Primeiramente você precisa adicionar o repositório à configuração do APT. Para facilitar a configuração, apenas execute isso no seu terminal:

```
  curl http://dist.crystal-lang.org/apt/setup.sh | sudo bash
```

Isso adicionará a chave de assinatura e a configuração do repositório. Se você prefere fazer isso manualmente, execute os seguintes comandos como *root*:

```
apt-key adv --keyserver keys.gnupg.net --recv-keys 09617FD37CC06B54
echo "deb http://dist.crystal-lang.org/apt crystal main" > /etc/apt/sources.list.d/crystal.list
apt-get update
```

## Instalação
Depois de configurar o repositório, você está pronto para instalar o Crystal:

```
sudo apt-get install crystal
```

## Atualização

Quando uma nova versão do Crystal for lançada, você pode atualizar o seu sistema usando:

```
sudo apt-get update
sudo apt-get install crystal
```
