---
layout: post
title: Preparando o ambiente no Fedora para trabalhar com o Jekyll usando o asdf
author: Douglas Gusson
tags: [asdf, ruby, jekyll, ambiente, fedora]
comments: true
---

Pra quem ainda não conhece, o **Jekyll** é uma ferramenta escrita em [Ruby](https://www.ruby-lang.org/pt/) para geração de sites e blogs estáticos. Ele faz o *build* do `HTML` basedo em templates do [Liquid](https://shopify.github.io/liquid/) e em arquivos *markdown*. Nesse post, veremos como preparar o ambiente na distribução Linux [Fedora](https://getfedora.org/) para começar trabalhar com Jekyll.

## Primeiro passo

Será necessário instalar algumas dependências de ferramentas de desenvolvimento. O gerenciador de pacotes do Fedora (DNF) possui um recurso que agrupa diversas dependências comuns de desenvolvimento, para instalar basta rodar o seguinte comando: 

```sh
sudo dnf groupinstall "Development Tools"
```

Pelo fato do Jekyll ter sido desenvolvido com a linguagem Ruby, precisaremos instalar o Ruby na máquina para conseguirmos executar o Jekyll e desenvolver nossos sites. Para que a instalação do Ruby ocorra com sucesso precisamos de mais duas dependẽncias de desenvolvimento:

```sh
sudo dnf install openssl-devel readline-devel
```

## asdf

**asdf** é uma ferramenta de linha de comando que permite o gerenciamento de várias versões de *runtime* de diversas linguagens de programação. Essa ferramenta irá nos ajudar instalar e gerenciar as versões do Ruby.

### Instalação

A instalação é bem simples, basicamente um `git clone`: 

```sh
git clone https://github.com/asdf-vm/asdf.git ~/.asdf
cd ~/.asdf
git checkout "$(git describe --abbrev=0 --tags)"
```

Em seguida precisamos adicionar duas instruções no nosso `~/.bashrc` para que o asdf seja carregado na inicialização do nosso shell:

```
. $HOME/.asdf/asdf.sh
. $HOME/.asdf/completions/asdf.bash
```

## Ruby

Feito tudo isso, partimos para uma das últimas etapas da preparação do nosso ambiente, que é a instalação do Ruby e finalmente a instalação do Jekyll.

Para gerenciarmos as versões do Ruby através do asdf, precisamos adicionar um plugin no asdf que ficará responsável pela linguagem.

Instalando o plugin do `ruby` no `asdf`:

```sh
asdf plugin-add ruby
```

Agora, podemos instalar uma versão do Ruby utilizando o asdf, executando o seguinte comando:

```sh
asdf install ruby 2.7.2
```

*Obs.: como dito anteriormente, com o asdf é possível gerenciar diversas versões de runtime, nesse exemplo foi instalada a versão `2.7.2` do Ruby. O Jekyll tem como requisito uma versão maior ou igual a versão 2.4.0 do Ruby.*

Tendo uma versão do Ruby instalada, precisamos "setar" ela no ambiente para começar usar. É possivel também definir em qual escopo ela será setada, no exemplo abaixo configuramos de forma global:

```sh
asdf global ruby 2.7.2
```

Nesse momento, já podemos verificar a versão do Ruby:

```sh
ruby -v
```

## Jekyll

E, finalmente, instalar o **Jekyll** e também o **Bundler**: 

```sh
gem install jekyll bundler
```

### Extra

Para validar as nossas instalações, vamos criar um novo projeto usando o Jekyll e executar.

Crie um novo projeto com o comando `jekyll new <NOME_DO_PROJETO>`, pro exemplo:

```sh
jekyll new meusite
```

Acesse o diretório do projeto:

```sh
cd meusite
```

Execute o servidor de desenvolvimento:

```sh
bundle exec jekyll serve
```
Esse comando executará um servidor de desenvolvimento que ficará acessível em: [http://localhost:4000](http://localhost:4000)

Espero que esse tutorial tenha sido útil para facilitar a sua preparação do ambiente para trabalhar com o Jekyll. Obrigado e até a próxima. 

## Links

- Site oficial do Jekyll: [https://jekyllrb.com/](https://jekyllrb.com/)
- Site oficial do asdf: [https://asdf-vm.com/](https://asdf-vm.com/)
- Repositório do asdf no Github: [https://github.com/asdf-vm/asdf](https://github.com/asdf-vm/asdf)
- Site oficial do Fedora: [https://getfedora.org/](https://getfedora.org/)