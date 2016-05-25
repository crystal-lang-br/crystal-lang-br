# No RedHat e CentOS

Em distribuições derivadas do RedHat, você pode usar o repositório oficial do Crystal.

## Configuração do repositório

Primeiramente, você precisa adicionar o repositório à configuração do seu YUM. Para facilitar a configuração, apenas rode em seu terminal:

```
  curl http://dist.crystal-lang.org/rpm/setup.sh | sudo bash
```

Isso adicionará a chave de assinatura e a configuração do repositório. Se você prefere fazer isso manualmente, execute:

```
rpm --import http://dist.crystal-lang.org/rpm/RPM-GPG-KEY

cat > /etc/yum.repos.d/crystal.repo <<END
[crystal]
name = Crystal
baseurl = http://dist.crystal-lang.org/rpm/
END
```

## Instalação
Depois de configurar o repositório, você está pronto para instalar o Crystal:

```
sudo yum install crystal
```

## Atualização

Quando uma nova versão do Crystal for lançada, você pode atualizar o seu sistema usando:

```
sudo yum update crystal
```
