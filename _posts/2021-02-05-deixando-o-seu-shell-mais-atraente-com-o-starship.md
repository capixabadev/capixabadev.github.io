---
layout: post
title: Deixando o seu shell mais atraente com o Starship
author: Douglas Gusson
tags: [bash, starship,terminal]
comments: true
---

Nesse post eu mostro como instalar o [starship.rs](https://starship.rs/) para deixar o seu shell mais atraente.

![Logo do Starship](/assets/img/posts/starship/logo.svg)

## Instalação

A instalação é bem simples, basta executar o seguinte comando:

```sh
curl -fsSL https://starship.rs/install.sh | bash
```

Em seguinda será necessário adicionar o script de inicialição do Starship no seu `.bashrc`:

```sh
vim ~/.bashrc
```

Adiocione a seguinte instrução no fim do arquivo:

```sh
eval "$(starship init bash)"
```

Após essa configuração, basta recarregar as configurações do `.bashrc` através do comando `source` ou simplesmente fechar o a janela do terminal e abrir novamente.

```sh
source ~/.bashrc
```

Feito isso, o prompt do seu shell ficará paracido com a imagem abaixo:

![Exemplo de terminal com o starship instalado](/assets/img/posts/starship/exemplo-terminal-com-starship.png)

Repare que ele identifica e mostra informações da linguagem de programação encontrada no diretório, apresenta também qual a `branch` do `git`, etc. 

Bacana, não é mesmo?! Mas não para por aí, ele é super customizável e simples de configurar, apesar das configurações padrões já serem bem interessantes, você pode querer deixar mais ao seu gosto. Para isso, recomendo dar uma olhada nesse link da documentação que fala de todas as configurações possíveis: [https://starship.rs/config/](https://starship.rs/config/), talvez eu faça um novo post mostrando algumas configurações.

## Mas só no bash? E o Zsh e o Fish?

Então, se você usa algum deles, não se preocupe! Funciona no Zsh e no Fish também. O passo de instalação é exatamente o mesmo, o que muda é a configuração do script de inicialização.

### Zsh

Basta adicionar o seguinte no fim do seu `~/.zshrc`:

```sh
eval "$(starship init zsh)"
```

### Fish

Basta adicionar o seguinte no fim do arquivo `~/.config/fish/config.fish`:

```sh
starship init fish | source
```

## Links

- Site oficial: [https://starship.rs/](https://starship.rs/)
- Repositório no Github: [https://github.com/starship/starship](https://github.com/starship/starship)