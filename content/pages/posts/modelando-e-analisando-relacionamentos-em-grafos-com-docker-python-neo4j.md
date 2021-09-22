---
title: Modelando e analisando relacionamentos em grafos com Docker + Python + Neo4J
excerpt: >-
    A modelagem e análise de relacionamentos, tema tratado neste artigo, é um dos cases mais aplicados no mercado.
date: '2019-11-25'
thumb_img_path: https://miro.medium.com/max/2746/1*_li2QFQdrB29imigc3hD2Q.png
thumb_img_alt: Modelando e analisando relacionamentos em grafos com Docker + Python + Neo4J
content_img_path: https://miro.medium.com/max/2746/1*_li2QFQdrB29imigc3hD2Q.png
content_img_alt: Modelando e analisando relacionamentos em grafos com Docker + Python + Neo4J
seo:
    title: Modelando e analisando relacionamentos em grafos com Docker + Python + Neo4J
    description: >-
        A modelagem e análise de relacionamentos, tema tratado neste artigo, é um dos cases mais aplicados no mercado.
    extra:
        - name: 'og:type'
          value: article
          keyName: property
        - name: 'og:title'
          value: Modelando e analisando relacionamentos em grafos com Docker + Python + Neo4J
          keyName: property
        - name: 'og:description'
          value: >-
              A modelagem e análise de relacionamentos, tema tratado neste artigo, é um dos cases mais aplicados no mercado.
          keyName: property
        - name: 'og:image'
          value: https://miro.medium.com/max/2746/1*_li2QFQdrB29imigc3hD2Q.png
          keyName: property
          relativeUrl: true
        - name: 'twitter:card'
          value: summary_large_image
        - name: 'twitter:title'
          value: Modelando e analisando relacionamentos em grafos com Docker + Python + Neo4J
        - name: 'twitter:description'
          value: >-
              A modelagem e análise de relacionamentos, tema tratado neste artigo, é um dos cases mais aplicados no mercado.
        - name: 'twitter:image'
          value: https://miro.medium.com/max/2746/1*_li2QFQdrB29imigc3hD2Q.png
          relativeUrl: true
layout: post
---

A **modelagem e análise de relacionamentos** é um dos [_cases_](https://neo4j.com/use-cases/) mais aplicados no mercado. A escolha de [qual produto recomendar](https://neo4j.com/use-cases/real-time-recommendation-engine/) ao cliente, definir [qual filme ou série sugerir](https://neo4j.com/use-cases/real-time-recommendation-engine/) ou [modelar a sua rede de contato](https://neo4j.com/use-cases/social-network/) com a proximidade das pessoas em relação ao seu perfil são exemplos que podemos encontrar nos principais serviços da internet.

Sobre este último, será a abordagem utilizada para este artigo. Para isso, será demonstrada a modelagem utilizando grafos e [_Neo4J_](https://neo4j.com/) (sistema de gerenciamento de banco de dados gráficos), a _API em_ [_Python_](https://www.python.org/) que irá gerar as entidades de formas aleatórias e a utilização de [_Docker_](https://www.docker.com/) para padronizar os ambientes.

# 👩‍🏫 O problema

Atualmente, uma rede de contatos de um profissional é muito relevante, principalmente em eventos corporativos. A importância de ter conexões no mesmo ramo de conhecimento traz benefícios, tais como: comunicação com pessoas que entendem do assunto e possíveis dúvidas podem ser esclarecidas, indicações de trabalhos disponíveis, entre outros.

Uma empresa de tecnologia decide realizar um evento com objetivo de apresentar e vender o seu novo portfólio, com diversas palestras, mesas redondas e stands com as maiores referências de especialistas no mercado. Além disso, o evento também busca conectar pessoas dessa área, visto que existem ramificações bem específicas tais como: exatas, biológicas e humanas.

Cada pessoa preenche seu nome, data de nascimento, email, cidade, estado e cargo que ocupa no momento. As empresas são registradas com nome, cidade, estado e área de atuação. As universidades possuem o registro do nome, estado e cidade.

# 😰 Mas o que são grafos?

Para entender melhor a teoria de grafos ou até mesmo relembrar seus principais conceitos, visite a breve introdução que preparamos no artigo [Grafos, teoria e aplicações](https://medium.com/@lennonalvesdias/grafos-teoria-e-aplicações-2a87444df855).

[

## Grafos, teoria e aplicações

### A teoria dos grafos é um assunto antigo, introduzida no século XVIII, porém com várias aplicações em nosso dia-a-dia.

medium.com

](https://medium.com/@lennonalvesdias/grafos-teoria-e-aplicações-2a87444df855)

# 🌍 Modelando com Neo4J

O banco de dados de grafos é um dos tipos de bancos de dados [NoSQL](https://pt.wikipedia.org/wiki/NoSQL). Ele é diretamente relacionado a um modelo (_grafos_) de dados estabelecido, eles foram criado para possibilitar o armazenamento de relacionamentos e navegação por eles. As entidades são armazenadas como nós e os relacionamentos entre elas são as arestas, nas quais possuem direcionamento.

Dentre as opções de bancos de dados gráficos, destaca-se o Neo4J. Ele é um banco confiável, escalável e de alto desempenho, suas características adequadas de ACID são a base da confiabilidade dos dados. O banco garante que as operações que envolvem a modificação de dados ocorram dentro de uma transação para garantir dados consistentes.

> [**ACID** (**A**tomicidade, **C**onsistência, **I**solamento e **D**urabilidade)](https://pt.wikipedia.org/wiki/ACID) é um conjunto de propriedades que garante que as transações do banco de dados sejam processadas com confiabilidade, sendo a transação uma operação lógica única no banco de dados.

## 👨‍💻 Show Me the Code!

Antes de utilizar a _API_ para desenhar toda a complexidade do sistema, é importante passar pelos comandos básicos do banco, como criar os nós e os relacionamentos. Esses comandos podem ser executados diretamente na interface gráfica da ferramenta. Para este artigo, foi utilizada a [imagem Docker oficial do Neo4J, disponível no Docker Hub](https://hub.docker.com/_/neo4j).

![](https://miro.medium.com/max/2000/1*TbgQNCvagPUkNM7YqiO0dA.png)Interface do Neo4J acessada pelo endereço localhost:7474

Para interagir com os comandos, iremos modelas a mesma aplicação, porém com uma quantidade menor de objetos, depois apagamos tudo e deixamos que a _API_ faça todo o _‘trabalho grosso’_.

-   Criando pessoas

```
CREATE (p1:Pessoa {Nome: 'Cintia'})
CREATE (p2:Pessoa {Nome: 'Lennon'})
CREATE (p3:Pessoa {Nome: 'Mateus'})
```

-   Criando universidade

```
CREATE (u1:Universidade {Nome: 'FIAP'})
```

-   Criando empresas

```
CREATE (e1:Empresa {Nome: 'FICO'})
CREATE (e2:Empresa {Nome: 'XP Inc'})
CREATE (e3:Empresa {Nome: 'Lumini'})
```

Após criar os nós, podemos visualizar graficamente as operações.  
Para isso executamos

```
MATCH(m1) WHERE id(m1) >= 0 RETURN m1
```

<img alt="" class="t u v lz aj" src="https://miro.medium.com/max/1400/1\*5sIpMqx7XSDt2TjTyn8VVA.png" width="700" height="269" srcSet="https://miro.medium.com/max/552/1\*5sIpMqx7XSDt2TjTyn8VVA.png 276w, https://miro.medium.com/max/1104/1\*5sIpMqx7XSDt2TjTyn8VVA.png 552w, https://miro.medium.com/max/1280/1\*5sIpMqx7XSDt2TjTyn8VVA.png 640w, https://miro.medium.com/max/1400/1\*5sIpMqx7XSDt2TjTyn8VVA.png 700w" sizes="700px" role="presentation"/>

Visualização gráfica de pessoa(s), universidade(s) e empresa(s)

-   Criando relacionamentos entre pessoas e universidade

```
MATCH(p1),(u1) WHERE p1.Nome='Cintia' AND u1.Nome='FIAP'
CREATE (p1)-\[r:ESTUDA\]->(u1)

MATCH(p2),(u1) WHERE p2.Nome='Lennon' AND u1.Nome='FIAP'
CREATE (p2)-\[r:ESTUDA\]->(u1)

MATCH(p3),(u1) WHERE p3.Nome='Mateus' AND u1.Nome='FIAP'
CREATE (p3)-\[r:ESTUDA\]->(u1)
```

-   Criando relacionamentos entre pessoas e empresas

```
MATCH(p1),(e1) WHERE p1.Nome='Cintia' AND e1.Nome='FICO'
CREATE (p1)-\[r:TRABALHA\]->(e1)

MATCH(p2),(e2) WHERE p2.Nome='Lennon' AND e2.Nome='XP Inc'
CREATE (p2)-\[r:TRABALHA\]->(e2)

MATCH(p3),(e3) WHERE p3.Nome='Mateus' AND e3.Nome='Lumini'
CREATE (p3)-\[r:TRABALHA\]->(e3)
```

É possível visualizar de maneira gráfica as ligações entre os nós, formadas pelos relacionamentos cadastrados.

<img alt="" class="t u v lz aj" src="https://miro.medium.com/max/1400/1\*i7poxdhDSous0u5uIeg0zA.png" width="700" height="288" srcSet="https://miro.medium.com/max/552/1\*i7poxdhDSous0u5uIeg0zA.png 276w, https://miro.medium.com/max/1104/1\*i7poxdhDSous0u5uIeg0zA.png 552w, https://miro.medium.com/max/1280/1\*i7poxdhDSous0u5uIeg0zA.png 640w, https://miro.medium.com/max/1400/1\*i7poxdhDSous0u5uIeg0zA.png 700w" sizes="700px" role="presentation"/>

Visualização gráfica dos objetos com os relacionamentos

-   Criando/alterando atributos

```
MATCH(p1) WHERE p1.Nome='Lennon'
SET p1.Cidade = 'São Paulo'MATCH(u1) WHERE u1.Nome='FIAP'
SET u1.Cidade = 'São Paulo'
```

Com poucos nós cadastrados, já é possível realizar algumas consultas, como: “_Quais pessoas trabalham na empresa XP Inc?”_

<img alt="" class="t u v lz aj" src="https://miro.medium.com/max/1060/1\*6sLbl2-VXT9aU1MVNafqDA.png" width="530" height="181" srcSet="https://miro.medium.com/max/552/1\*6sLbl2-VXT9aU1MVNafqDA.png 276w, https://miro.medium.com/max/1060/1\*6sLbl2-VXT9aU1MVNafqDA.png 530w" sizes="530px" role="presentation"/>

Visualização gráfica da consulta realizada pelo banco

Hora de usar a _API_ para gerar os dados, mas antes, utilizaremos alguns comandos para deletar a estrutura criada.

> Você pode encontrar uma introdução mais completa acessando a página de [treinamento online do Neo4J](https://neo4j.com/graphacademy/online-training/).

-   Deletando relacionamento entre nós

```
MATCH (p1 {Nome: 'Lennon'})-\[r:ESTUDA\]->(u1 {Nome: 'FIAP'}) DELETE rMATCH (p1 {Nome: 'Lennon'})-\[r:TRABALHA\]->(u1 {Nome: 'XP Inc'}) DELETE r
```

-   Deletando nós

```
MATCH (p1 {Nome: 'Lennon'}) DELETE p1MATCH (e1 {Nome: 'XP Inc'}) DELETE e1
```

Os comandos acima foram para exemplificar como deletar nós e/ou relacionamentos, sendo possível agrupá-los e deletar ambos de uma só vez. Para economizar tempo, podemos excluir todos os cadastros do banco com o seguinte comando:

```
MATCH (n) DETACH DELETE n
```

O restante do artigo utilizará a aplicação desenvolvida para gerar todos os registros. Entenderemos então como parametrizar a _API_ e como padronizamos os ambientes para que você possa executar em qualquer máquina que contenha _Docker_ e _Docker Compose_.

# 🚀 Escalando com Python API

Para simular os objetos e criar um ambiente mais próximo ao que costumamos encontrar em eventos, foi construida uma _API_ utilizando a linguagem _Python_. A função dessa API é receber parâmetros quantitativos e gerar aleatoriamente **n** pessoas, **n** empresas e **n** universidades. Com esses objetos gerados, a _API_ utiliza uma distribuição randômica para gerar os relacionamentos entre eles.

Com essa aplicação, é possível escalar a complexidade do modelo de acordo com os parâmetros informados no arquivo `app.py`.

# 🐋 Padronizando com Docker

Foi utilizado o _Docker_ (plataforma de código aberto para criação e administração de ambientes isolados) para manter a padronização do ambiente, das instalações e dos versionamentos das ferramentas e tecnologias utilizadas no projeto.

Para que os serviços mapeados no `docker-compose.yml` sejam _startados_, basta executar o comando após o clone do repositório da aplicação.

```
$ docker-compose up --build
```

> Para a execução do comando é necessário que o Docker e o Docker Compose estejam instalados e corretamente configurados em sua máquina.

# 💪 O poder das nossas buscas

Após a execução da _API_, temos o seguinte resultado ao consultar toda a nossa base de relacionamentos:

![](https://miro.medium.com/max/2746/1*_li2QFQdrB29imigc3hD2Q.png)Visualização gráfica dos objetos com os relacionamentos

É notável que a complexidade aumentou um pouco e que a _API_ se tornou bem útil ao não precisarmos realizar todas as operações de inserção na mão. Ao total temos 134 nós, sendo 60 pessoas, 44 empresas e 30 universidades e 120 relacionamentos, sendo 60 do tipo _‘ESTUDA’_ e 60 do tipo _‘TRABALHA’_.

Chegou a hora de ver o que podemos fazer: “_Quantos alunos cada universidade tem, em ordem decrescente e que sejam Top 5?”_

````
MATCH (p:Pessoa)-\[:ESTUDA\]->(u:Universidade)
RETURN u.Nome, count(\*) AS alunos
ORDER BY pessoas DESC
LIMIT 5
```![](https://miro.medium.com/max/2000/1*rhho8GtkFONNGAnnI-JTUQ.png)Resultado da consulta de universidades com mais alunos

E que tal _“Quais pessoas estudam ou trabalham com Thiago Hugo Paulo da Mota?”_

````

MATCH (p1:Pessoa)-\[:TRABALHA\]->(e:Empresa),  
 (p1)-\[:ESTUDA\]->(u:Universidade),  
 (p2:Pessoa)-\[:TRABALHA\]->(e),  
 (p3:Pessoa)-\[:ESTUDA\]->(u)  
WHERE p1.Nome = 'Thiago Hugo Paulo da Mota'  
RETURN \*

```![](https://miro.medium.com/max/1400/1*XzOzXgZsZP0DBGc5Us9atw.png)Resultado da consulta de pessoas próximas ao Thiago

A utilização de um banco de dados gráfico resolve problemas mais complexos de relacionamento com facilidade e alta performance.

Por fim, o exemplo clássico da utilização de grafos, encontrar o caminho mais curto. _“Os alunos da Universidade Mackenzie gostariam de compartilhar conhecimento com os alunos da Universidade do Amazonas, qual é o caminho mais curto para que esse encontro seja possível?”_

```

MATCH p = shortestPath((u1:Universidade)-\[\*\]-(u2:Universidade))  
WHERE u1.Nome = 'Universidade Mackenzie' AND  
 u2.Nome = 'Universidade do Amazonas'  
RETURN p

```

<img alt="" class="t u v lz aj" src="https://miro.medium.com/max/1400/1\*uQeIjFZ9x8g7HO9GOmmJHg.png" width="700" height="353" srcSet="https://miro.medium.com/max/552/1\*uQeIjFZ9x8g7HO9GOmmJHg.png 276w, https://miro.medium.com/max/1104/1\*uQeIjFZ9x8g7HO9GOmmJHg.png 552w, https://miro.medium.com/max/1280/1\*uQeIjFZ9x8g7HO9GOmmJHg.png 640w, https://miro.medium.com/max/1400/1\*uQeIjFZ9x8g7HO9GOmmJHg.png 700w" sizes="700px" role="presentation"/>

Resultado da consulta de menor caminho entre um aluno da Universidade Mackenzie e um aluno da Universidade do Amazonas

É possível explorar o poder da performance de um banco de dados de grafos, alterando e incrementando os exemplos citados. Nos links disponíveis existem também treinamentos para extrair o máximo poder da ferramenta.

O projeto completo você pode encontrar no [repositório do GitHub](https://github.com/lennonalvesdias/fiap-8ia-arquitetura-de-dados).

[

lennonalvesdias/fiap-8ia-arquitetura-de-dados
---------------------------------------------

### Cintia Akie Nakano . RM 333603 // Lennon V. Alves Dias . RM 334415 // Mateus Aguiar Florentino . RM 334444 ☕ Code and…

github.com

](https://github.com/lennonalvesdias/fiap-8ia-arquitetura-de-dados)
```
