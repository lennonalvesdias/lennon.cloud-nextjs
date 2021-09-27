---
title: Grafos, teoria e aplicações
excerpt: >-
    A teoria dos grafos é um assunto antigo, introduzida no século XVIII, porém com várias aplicações em nosso dia-a-dia.
date: '2019-11-18'
thumb_img_path: https://miro.medium.com/max/1400/1*LYcQBFLsdXbaHc4N_k-g3w.png
thumb_img_alt: Grafos, teoria e aplicações
content_img_path: https://miro.medium.com/max/1400/1*LYcQBFLsdXbaHc4N_k-g3w.png
content_img_alt: Grafos, teoria e aplicações
seo:
    title: Grafos, teoria e aplicações
    description: >-
        A teoria dos grafos é um assunto antigo, introduzida no século XVIII, porém com várias aplicações em nosso dia-a-dia.
    extra:
        - name: 'og:type'
          value: article
          keyName: property
        - name: 'og:title'
          value: Grafos, teoria e aplicações
          keyName: property
        - name: 'og:description'
          value: >-
              A teoria dos grafos é um assunto antigo, introduzida no século XVIII, porém com várias aplicações em nosso dia-a-dia.
          keyName: property
        - name: 'og:image'
          value: https://miro.medium.com/max/1400/1*LYcQBFLsdXbaHc4N_k-g3w.png
          keyName: property
          relativeUrl: true
        - name: 'twitter:card'
          value: summary_large_image
        - name: 'twitter:title'
          value: Grafos, teoria e aplicações
        - name: 'twitter:description'
          value: >-
              A teoria dos grafos é um assunto antigo, introduzida no século XVIII, porém com várias aplicações em nosso dia-a-dia.
        - name: 'twitter:image'
          value: https://miro.medium.com/max/1400/1*LYcQBFLsdXbaHc4N_k-g3w.png
          relativeUrl: true
layout: post
---

A teoria dos grafos\* é um assunto antigo, porém com várias aplicações em nosso dia-a-dia. Foi introduzida no século XVIII pelo matemático suiço Leonhard Euler, que utilizou grafos para resolver o problema que conhecemos como [**As sete pontes de Königsberg**](https://pt.wikipedia.org/wiki/Sete_pontes_de_K%C3%B6nigsberg).

> \* Ramo da matemática que estuda as relações entre os objetos de um determinado conjunto.

# 🤔 Afinal, o que são grafos?

É uma estrutura composta por um conjunto (não vazio) de pontos **(vértices)** e um conjunto de linhas que ligam esses pontos **(arestas)**.

<img alt="" class="t u v jf aj" src="https://miro.medium.com/max/664/1*mdRR7l3MtuFUiR4Ak5NUJQ.png"/>

Grafo com 3 vértices {0, 1, 2} e 3 arestas {a, b, c}

> Definição formal: Um grafo **G = (V(G), E(G))** é uma estrutura matemática composta por dois conjuntos:  
> **V(G)**, um conjunto de elementos que são chamados de **vértices**,  
> **E(G)**, um conjunto de pares de elementos de V(G), cada par é chamado de **aresta**

Está na hora de descomplicar! Mas não, sem antes, algumas definições sobre grafos:

-   Dois vértices ligados por uma aresta dizem-se **adjacentes**.

<img alt="" class="t u v jf aj" src="https://miro.medium.com/max/668/1*2uBt1vSzJrien90dvjB4tg.png"/>

Os vértices 0 e 1 são adjacentes

-   Uma aresta que ligue dois vértices diz-se **incidente** de cada um dos vértices.

<img alt="" class="t u v jf aj" src="https://miro.medium.com/max/664/1*SO1tKJ32rAf3G0VRZRiDFg.png"/>

A aresta ‘a’ é incidente de 0 e 1

-   O número de arestas incidentes num vértice diz-se o **grau** **desse vértice**. O **grau máximo** do grafo é o maior dos graus dos vértices (∆(G)), consequentemente o **grau mínimo** (δ(G)) é o menor dos graus dos vértices.

<img alt="" class="t u v jf aj" src="https://miro.medium.com/max/664/1*VZA-0GJv8n7JgKMkUzH7Nw.png"/>

O vértice 0 tem duas arestas incidentes, portanto grau 2. Os vértices 1 e 2 tem uma aresta incidente, sendo assim, ambos são grau 1. Dessa forma, o grau máximo do grafo é 2 e o grau mínimo é 1

-   O subconjunto de arestas e vértices a elas associados diz-se **sub-grafo** do grafo original.

<img alt="" class="t u v jf aj" src="hhttps://miro.medium.com/max/664/1*y96hrBuvfYrn5Zjzpk42gw.png"/>

O conjunto V(G) = {0, 1} E(G) = {a} encontrado em G2 é subconjunto de V(G) = {0, 1, 2} E(G) = {a, b} encontrado em G1, portanto, pode-se dizer que G2 é subgrafo de G1

-   Uma sequência de vértices na qual os vértices sucessivos estão ligados por arestas do grafo diz-se um **caminho**.

<img alt="" class="t u v jf aj" src="https://miro.medium.com/max/664/1*Tocc_Nh0f_S2dIvhdrv2zA.png"/>

Os vértices 0–2–3–4 representados (figura à direita) formam um caminho encontrado no grafo G (à esquerda)

Além das definições acima, outros conceitos de grafos são de que: O conjunto dos vértices pode ser infinito, onde nesse caso, chama-se de **grafo infinito**. Quando existe mais de uma aresta entre o mesmo par de vértices, temos **arestas múltiplas** e, quando temos uma aresta definida por um par de vértices não distintos (ou seja, uma aresta que conecta no mesmo nó), diz-se um **laço**.

Existem também os grafos que possuem orientação nas arestas, conhecidos como **grafo orientado** ou **digrafo** ou **grafo direcionado**.

<img alt="" class="t u v jf aj" src="https://miro.medium.com/max/640/1*S4b80YZAQ71d6YwDSw1zgg.png"/>

Grafo com orientação nas arestas. G = (V(G),E(G)), V(G) = {0, 1, 2, 3, 4}, E(G) = {(0, 1), (1, 3), (2, 0), (2, 3), (3, 0), (3, 4), (4, 0)}

Para grafos orientados, o grau de entrada de um vértice é o número de arestas que chegam nele e denota-se por `d-(v)`. O grau de saída é o número de arestas que partem do vértice em direção à outros, onde a denotação é `d+(v)`.

Quando o grau de entrada é igual a zero, o vértice é chamado de **fonte** e, quando o grau de saída é igual a zero é chamado de **semidouro** ou **sorvedouro**.

Ao remover a orientação das arestas de um grafo, resulta-se um **grafo subjacente**.

Além da orientação, é possível atribuir custo para o vértice, para a aresta ou para ambos. O grafo que recebe esses valores são os **grafos ponderados**.

<img alt="" class="t u v jf aj" src="https://miro.medium.com/max/640/1*abvGQ8mJhDONj_vocIaVfg.png"/>

Grafo com custo em suas arestas

Para representação de grafos, as formas mais comuns são: **matriz de adjacências** (M|V (G)|×|V (G)|), onde `**m**_ij_ = 1` se existe aresta entre `**v**_i_**v**_j_` e caso contrário, e a **matriz de incidência** ( M|V (G)|×|E(G)|), onde `**m**_ij_ = 1` se `**v**_i_` é um dos vértices da aresta `**e**_j_`.

<img alt="" class="t u v jf aj" src="https://miro.medium.com/max/700/1*A1ANUxSJ1p8FWREFB1qmkg.png"/>

Grafo com matriz de adjacências e matriz de incidência

Os conceitos apresentados são as definições **básicas** de grafos, onde introduzimos a teoria afim de explicar alguns problemas que podemos modelar utilizando esta técnica. À partir deste momento, convido à explorar a vasta literatura com conceitos e definições adicionais.

# 🤸‍♂ Bora descomplicar? ✍ Deixa que eu desenho!

Grafos possui uma representação gráfica de fácil entendimento, podendo traduzir problemas mais complexos em visualizações triviais. Para exemplicar os conceitos apresentados neste artigo, utilizaremos exemplos que podem ser enxergados em nosso dia-a-dia.

# 👩‍🏫Exemplos de grafos

**_(objeto = nós, relacionamento = arestas)_**

-   **Transporte aéreo** (_Objeto_: cidades, _Relacionamento_: vôo comercial entre duas cidades)
-   **Atores e filmes** (_Objeto_: atores, _Relacionamento_: atores atuaram em um mesmo filme)
-   **Web** (_Objeto_: páginas da web, _Relacionamento_: link de uma página para outra)
-   **Grade escolar** (_Objeto_: professores e disciplinas, _Relacionamento_: disciplina lecionada pelo professor)
-   **Pares em um relacionamento** (_Objeto_: rapazes e moças, _Relacionamento_: interesse mútuo em sair)
-   **Robustez da malha elétrica** (_Objeto_: torres de transmissão, _Relacionamento_: linhas entre torres)

# 👥 Rede de Relacionamentos

Uma empresa decide realizar um evento com objetivo de apresentar e vender o seu novo portfólio, com diversas palestras, mesas redondas e stands com as maiores referências de especialistas no mercado. Além disso, o evento também busca conectar pessoas dessa área, visto que existem ramificações bem específicas tais como: exatas, biológicas e humanas.

Cada pessoa preenche seu nome, data de nascimento, email, cidade, estado e cargo que ocupa no momento. As empresas são registradas com nome, cidade, estado e área de atuação. As universidades possuem o registro do nome, estado e cidade.

![](https://miro.medium.com/max/2244/1*iTPtw2Kmev1IrRoAPlkOnA.png)Representação com participantes (laranja), universidades (vermelho) e empresas (azul)

Rita atua na área de humanas, porém, possui bastante curiosidade em exatas e ficou sabendo que Fabiana é uma grande especialista na área. Com esse interesse, Rita quer saber como ela poderia ser apresentada à Fabiana para poderem bater um papo.

**Problema:** Qual é o menor caminho entre Rita e Fabiana?

![](https://miro.medium.com/max/1400/1*LYcQBFLsdXbaHc4N_k-g3w.png)Representação do caminho entre Rita e Fabiana

A resposta para esse problema poderia ser bem custosa de acordo com a modelagem do mesmo, porém nota-se que com a utilização de grafos passa a ser um problema trivial. No exemplo utilizamos poucos objetos, porém a mesma resolução é escalável para **N pessoas, N empresas** e **N universidades**.

**Resolução:** Rita trabalha na mesma empresa que Nelson, que estuda na mesma universidade que Fabiana.

# 📃 Referências

-   Introdução à Teoria dos Grafos, Profª Sheila Almeida e Mayara Omai (UTFPR/PG)
-   Grafos e suas aplicações, Fabiana Nascimento Santos Cavalcante e Severino Domingos da Silva (PUC/RS)
-   Aplicações da Matemática: Redes Sociais, Jogos, Engenharia, Profº Fábio Protti (IC-UFF/RJ)
