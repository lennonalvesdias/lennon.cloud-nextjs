---
title: Publicando meu site em Angular 8 no GitHub Pages com domínio customizado
excerpt: >-
    Utilizando a biblioteca angular-cli-ghpages para realizar o deploy da minha aplicação Angular no GitHub Pages diretamente do terminal.
date: '2020-01-22'
thumb_img_path: https://miro.medium.com/max/1280/1*HGShqAPMdgsntCcNZDD-pg.jpeg
thumb_img_alt: Publicando meu site em Angular 8 no GitHub Pages com domínio customizado
content_img_path: https://miro.medium.com/max/1280/1*HGShqAPMdgsntCcNZDD-pg.jpeg
content_img_alt: Publicando meu site em Angular 8 no GitHub Pages com domínio customizado
seo:
    title: Publicando meu site em Angular 8 no GitHub Pages com domínio customizado
    description: >-
        Utilizando a biblioteca angular-cli-ghpages para realizar o deploy da minha aplicação Angular no GitHub Pages diretamente do terminal.
    extra:
        - name: 'og:type'
          value: article
          keyName: property
        - name: 'og:title'
          value: Publicando meu site em Angular 8 no GitHub Pages com domínio customizado
          keyName: property
        - name: 'og:description'
          value: >-
              Utilizando a biblioteca angular-cli-ghpages para realizar o deploy da minha aplicação Angular no GitHub Pages diretamente do terminal.
          keyName: property
        - name: 'og:image'
          value: https://miro.medium.com/max/1280/1*HGShqAPMdgsntCcNZDD-pg.jpeg
          keyName: property
          relativeUrl: true
        - name: 'twitter:card'
          value: summary_large_image
        - name: 'twitter:title'
          value: Publicando meu site em Angular 8 no GitHub Pages com domínio customizado
        - name: 'twitter:description'
          value: >-
              Utilizando a biblioteca angular-cli-ghpages para realizar o deploy da minha aplicação Angular no GitHub Pages diretamente do terminal.
        - name: 'twitter:image'
          value: https://miro.medium.com/max/1280/1*HGShqAPMdgsntCcNZDD-pg.jpeg
          relativeUrl: true
layout: post
---

Utilizando a biblioteca [_angular-cli-ghpages_](https://www.npmjs.com/package/angular-cli-ghpages) para realizar o _deploy_ da minha aplicação Angular no [_GitHub Pages_](https://pages.github.com/) diretamente do terminal.

![](https://miro.medium.com/max/1280/1*HGShqAPMdgsntCcNZDD-pg.jpeg)

# 💁‍♂ Considerações iniciais

Neste artigo será abordada a instalação e configuração dos pacotes necessários assim como demonstrado o passo à passo do _build_ e _deploy_ da aplicação. Não será abordada a construção e/ou o desenvolvimento da mesma.

Para que o _GitHub_ entenda seu projeto como padrão do _GitHub Pages_, é necessário que ele respeite o formato **_O_QUE_VOCE_QUISER.github.io_**.

# 👣 Primeiros passos

O artigo utiliza como base para o processo de _deploy o angular-cli-ghpages_ e, como tarefa inicial, iremos realizar a instação global desta biblioteca.

```
npm install -g angular-cli-ghpages
```

## 📃 Anotações (dicas) úteis

Este artigo tem como base a utilização do [repositório do meu site pessoal](https://github.com/lennonalvesdias/lennonalvesdias.github.io), nele algumas estruturações de _branchs_ foram realizadas para facilitar a implementação e o desenvolvimento. Para que as alterações sejam aplicadas automaticamente na [página do site](https://lennonalves.com.br/#/user-profile), a _branch master_ foi reservada para os arquivos gerados pelo _deploy_ e, uma _branch_ de desenvolvimento chamada _develop_ foi criada (nela todas as alterações são realizadas).

No decorrer do artigo, algumas linhas de comandos são citadas. Para um uso mais simplificado no dia à dia, esses comandos foram mapeados no arquivo [_package.json_](https://github.com/lennonalvesdias/lennonalvesdias.github.io/blob/develop/package.json).

Dentro das configurações do [_angular.json_](https://github.com/lennonalvesdias/lennonalvesdias.github.io/blob/develop/angular.json) é possível configurar o _outputPath_ para que o conteúdo da sua aplicação seja distribuída na pasta raiz.

[lennonalvesdias/lennonalvesdias.github.io](https://github.com/lennonalvesdias/lennonalvesdias.github.io)

# ⚙ Build

Com a instalação realizada com sucesso, o próximo passo é a realização do _build_ do projeto. Caso a _URL_ do projeto seja a do _GitHub Pages_, o comando deverá ser parecido com:

```
ng build --prod --base-href [https://lennonalvesdias.github.io/](https://lennonalvesdias.github.io/)
```

Caso você opte por utilizar domínio personalizado para o seu site, o comando será apenas:

```
ng build --prod
```

## 🌎 Habilitando domínio personalizado no _GitHub_

O GitHub Pages permite que você utilize o domínio _O_QUE_VOCE_QUISER.github.io_ de forma gratuita, porém você ainda pode configurar um domínio próprio para exibição do seu site.

Para isso, na página do seu repositório clique na opção _Settings_. Nesta aba, rolando para baixo, estará visível a sessão _GitHub Pages_, onde você encontrará a opção _Custom Domain_. Nesta opção você deve informar o domínio que deseja utilizar e clicar na opção _Save_.

<img alt="" class="t u v lg aj" src="https://miro.medium.com/max/700/1*S5gR-N7lGxwIi0F67pWBpg.png"/>

<img alt="" class="t u v lg aj" src="https://miro.medium.com/max/700/1*-R6cq8RXKZf1D-umWliYoA.png"/>

É importante ressaltar que você deve ser proprietário deste domínio e configurar a Zona _DNS_ do mesmo. Caso você tenha segurança em alterar a Zona, basta criar registro do tipo `A` apontando para os seguintes endereços IP ([conforme página de ajuda do _GitHub_](https://help.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site)):

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

# 🚀 Deploy

Com a biblioteca _angular-cli-ghpages_ instalada de forma global e as _branchs_ configuradas conforme demonstrado acima, o comando de _deploy_ sem a utilização do domínio personalizado será:

```
ngh --branch=master
```

Caso opte por utilizar o domínio personalizado no site, o comando de _deploy_ será parecido com:

```
ngh --branch=master --cname=lennonalves.com.br
```

A biblioteca permite ainda a configuração da mensagem de implantação com o parâmetro `--message`, a utilização do parâmetro `--dry-run`para obter a saída antes de publicar a mudança além de outras opções que podem ser encontradas em sua [página no _NPM_](https://www.npmjs.com/package/angular-cli-ghpages).
