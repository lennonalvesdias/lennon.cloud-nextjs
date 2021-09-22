---
title: Criando um projeto VanillaJS com VJSCLI
excerpt: >-
    O 🍦 Vanilla JavaScript CLI é um projeto que tem como intuíto disponibilizar uma CLI para projetos em ES6 utilizando WebPack e Babel.
date: '2019-11-07'
thumb_img_path:
thumb_img_alt: Criando um projeto VanillaJS com VJSCLI
content_img_path:
content_img_alt: Criando um projeto VanillaJS com VJSCLI
seo:
    title: Criando um projeto VanillaJS com VJSCLI
    description: >-
        O 🍦 Vanilla JavaScript CLI é um projeto que tem como intuíto disponibilizar uma CLI para projetos em ES6 utilizando WebPack e Babel.
    extra:
        - name: 'og:type'
          value: article
          keyName: property
        - name: 'og:title'
          value: Criando um projeto VanillaJS com VJSCLI
          keyName: property
        - name: 'og:description'
          value: >-
              O 🍦 Vanilla JavaScript CLI é um projeto que tem como intuíto disponibilizar uma CLI para projetos em ES6 utilizando WebPack e Babel.
          keyName: property
        - name: 'og:image'
          value:
          keyName: property
          relativeUrl: true
        - name: 'twitter:card'
          value: summary_large_image
        - name: 'twitter:title'
          value: Criando um projeto VanillaJS com VJSCLI
        - name: 'twitter:description'
          value: >-
              O 🍦 Vanilla JavaScript CLI é um projeto que tem como intuíto disponibilizar uma CLI para projetos em ES6 utilizando WebPack e Babel.
        - name: 'twitter:image'
          value:
          relativeUrl: true
layout: post
---

# 🤔 O que é o VJSCLI ?

O Vanilla JavaScript CLI é um projeto que tem como intuito disponibilizar uma CLI para projetos em ES6 utilizando WebPack e Babel. Foi utilizado sass no projeto, para testes unitários Jasmine + Karma. Para a documentação foi utilizado o docjs com template do docdash.

# 👨‍🏫 Introdução ao VJSCLI

O primeiro passo para a utilização do pacote é realizar a instalação através do gerenciador de pacotes [NPM](https://www.npmjs.com/package/vjscli), utilizando o comando abaixo

```
npm install -g vjscli
```

Para validar se a instalação ocorreu corretamente, basta utilizar um dos comandos abaixo

```
vjs -V
vjs --version
```

Uma imagem como essa deve aparecer após a execução

<img alt="" class="" src="https://miro.medium.com/max/700/1*ZVy-3XjWyLCSOWA_l-iZkg.png">

Versão do VJSCLI instalado na máquina

É possível também consultar o helper do pacote, onde você pode encontrar os comandos necessários para criação de um novo projeto ou um novo componente:

```
vjs -h
vjs --helper
```

<img alt="" class="" src="https://miro.medium.com/max/700/1*VVfWbXQRfO7jF1T4lsuhCw.png">

Helper do VJSCLI com a lista de funcionalidades e seus comandos

# 👨‍💻 Show Me the Command!

Com os comandos para visualizar a versão e identificar se estamos com a instalação do pacote atualizada e para visualizar as funcionalidades disponíveis no pacote, podemos iniciar a criação de um novo projeto

```
vjs -n projetovjs -a "Lennon Dias" -d "Projeto Exemplo VJS"
```

Em alguns instantes o projeto estará criado à partir da pasta onde você executou o comando acima:

<img alt="" class="" src="https://miro.medium.com/max/700/1*0rBDZLe8CwY3b_mG_ThJHQ.gif">

Criação de um novo projeto utilizando VJSCLI

<img alt="" class="" src="https://miro.medium.com/max/229/1*bZVSqf6E6s-Y1-TvYJfWKA.png">

Estrutura de pastas e arquivos gerada pelo VJSCLI

É possível também, gerar novos componentes dentro do projeto criado:

```
vjs -g login
```

<img alt="" class="" src="https://miro.medium.com/max/700/1*jroXxtngYAjPoLfyJE0xQQ.png">

<img alt="" class="" src="https://miro.medium.com/max/221/1*mINPy9VU7cW2ny1x0RHOSw.png">

Estrutura de pastas da criação do componente

# 🚀 Executando o projeto

Após gerar o projeto e os componentes conforme sua necessidade, você pode executar utilizando o comando:

```
npm run local
```

Após a execução, seu projeto estará disponível acessando o endereço [http://localhost:8080/](http://localhost:8080/)

<img alt="" class="" src="https://miro.medium.com/max/700/1*MJzuq4vQFTGKWqHtxgHE8A.png">

Visualização da tela default do projeto

Outros comandos úteis para o seu novo projeto são: o **_build_** (valida o seu projeto e gera os arquivos finais para utilização em ambiente de produção) e o **_docs_** (gera documentação do seu desenvolvimento).

```
npm run build
npm run docs
```

# 📝 Últimas considerações

O projeto foi disponibilizado dia 01/11/2019 e conta com seus mantenedores e a ajuda da comunidade para novas atualizações.

Para contribuir ou entender melhor sobre o VJSCLI você pode acessar a página oficial do projeto no GitHub através do link: [https://bit.ly/34Dv1zr](https://bit.ly/34Dv1zr) e a página NPM do projeto através do link: [https://bit.ly/2Nqomml](https://bit.ly/2Nqomml).
