---
title: Decisão de crédito utilizando machine learning e visão computacional
excerpt: >-
    Utilização de APIs e bibliotecas de visão computacional e aprendizado de máquina para criação de um motor de decisão de crédito.
date: '2020-05-10'
thumb_img_path: https://miro.medium.com/max/1400/1*6eUtcNtT4fJUrlmlcUlN0w.png
thumb_img_alt: Decisão de crédito utilizando machine learning e visão computacional
content_img_path: https://miro.medium.com/max/1400/1*6eUtcNtT4fJUrlmlcUlN0w.png
content_img_alt: Decisão de crédito utilizando machine learning e visão computacional
seo:
    title: Decisão de crédito utilizando machine learning e visão computacional
    description: >-
        Utilização de APIs e bibliotecas de visão computacional e aprendizado de máquina para criação de um motor de decisão de crédito.
    extra:
        - name: 'og:type'
          value: article
          keyName: property
        - name: 'og:title'
          value: Decisão de crédito utilizando machine learning e visão computacional
          keyName: property
        - name: 'og:description'
          value: >-
              Utilização de APIs e bibliotecas de visão computacional e aprendizado de máquina para criação de um motor de decisão de crédito.
          keyName: property
        - name: 'og:image'
          value: https://miro.medium.com/max/1400/1*6eUtcNtT4fJUrlmlcUlN0w.png
          keyName: property
          relativeUrl: true
        - name: 'twitter:card'
          value: summary_large_image
        - name: 'twitter:title'
          value: Decisão de crédito utilizando machine learning e visão computacional
        - name: 'twitter:description'
          value: >-
              Utilização de APIs e bibliotecas de visão computacional e aprendizado de máquina para criação de um motor de decisão de crédito.
        - name: 'twitter:image'
          value: https://miro.medium.com/max/1400/1*6eUtcNtT4fJUrlmlcUlN0w.png
          relativeUrl: true
layout: post
---

Neste projeto abordamos a utilização de APIs e bibliotecas de visão computacional e aprendizado de máquina para criação de um motor de decisão de crédito. As tecnologias que foram utilizadas neste projeto são: [_Python_](https://www.python.org/), [_Jupyter_](https://jupyter.org/), [_IBM Watson_](https://www.ibm.com/watson), [_Microsoft Azure Computer Vision_](https://azure.microsoft.com/en-us/services/cognitive-services/computer-vision/), [_Docker_](https://www.docker.com/) e [_GitHub Actions_](https://github.com/features/actions).

# ⚙ Setup

A instalação dos requisitos do projeto podem ser feitas utilizando o comando `python -m pip install -r requirements.txt`. Caso deseje, dentro da pasta `env`você pode acessar o [_environment (venv)_ virtual](https://docs.python.org/3/library/venv.html) com o comando `source ./env/Scripts/activate`.

Caso encontre algum problema com a instalação da biblioteca [dlib](http://dlib.net/), é possível realizar a instalação através do seguinte comando:

```
python -m pip install https://files.pythonhosted.org/packages/0e/ce/f8a3cff33ac03a8219768f0694c5d703c8e037e6aba2e865f9bae22ed63c/dlib-19.8.1-cp36-cp36m-win\_amd64.whl#sha256=794994fa2c54e7776659fddb148363a5556468a6d5d46be8dad311722d54bfcf
```

# 🧐 Visão Geral

Para a demonstração e visão geral do projeto, foi criado um vídeo apresentando o repositório e a execução do motor principal de decisão de crédito:

# 🧠 Modelo

O arquivo `[training.py](https://github.com/lennonalvesdias/credit-decisor/blob/master/model/training.py)`é responsável por criar e treinar os classificadores e regressores utilizados para os modelos 01 e 02. Nele são definidas as variáveis utilizadas para cada modelo, assim como é apresentada a acurácia atingida.

```
Modelo 01 (classificador), criado com acurácia de: \[0.99994\]
Modelo 02 (Regressor), criado com acurácia de: \[0.9378733530692113\]
```

# 🌎 API

Utilizando Flask, foi criado o arquivo `[server.py](https://github.com/lennonalvesdias/credit-decisor/blob/master/api/server.py)`para expor os _endpoints_ de predição dos modelos. Dessa forma é possível que o serviço seja utilizado em clientes web, aplicações console, …, ou até mesmo um Jupyter Notebook (como faremos neste projeto), com uma simples requisição [REST](https://pt.wikipedia.org/wiki/REST).

Exemplo de requisição utilizando [cURL](https://curl.haxx.se/):

```
curl --location --request POST '[https://creditdecisor.lennon.cloud/modelo01'](https://creditdecisor.lennon.cloud/modelo01') \\
\--header 'Content-Type: application/json' \\
\--data-raw '{
    "nome": {
        "1": "Lennon Alves Dias"
    },
    "renda": {
        "1": 1000
    },
    "idade": {
        "1": 25
    },
    "etnia": {
        "1": 0
    },
    "sexo": {
        "1": 0
    },
    "casapropria": {
        "1": 0
    },
    "outrasrendas": {
        "1": 0
    },
    "estadocivil": {
        "1": 0
    },
    "escolaridade": {
        "1": 2
    }
}'
```

# ⚖ Decisão de Crédito

O arquivo principal do projeto é o `[decisor.ipynb](https://github.com/lennonalvesdias/credit-decisor/blob/master/client/decisor.ipynb)`. Nele além de algumas funções utilitárias e definições de variáveis, são construídas as funções:

-   `validate_person`: Utiliza a API de classificação `default`de imagem da IBM, procura-se a identificação da classe `person`no retorno da chamada.
-   `validate_explicit`: Utiliza a API de classificação `explicit`de imagem da IBM, procura-se a identificação da classe `explicit`no retorno da chamada.
-   `facial_recognition`: Utiliza a API de reconhecimento facial da Azure, procura-se por faces na foto e, para cada face encontrada, é desenhado um retângulo em sua volta, assim como marcado os pontos fiduciais da foto.

> Por definição, um ponto fiducial facial (PFF) — em inglês, facial landmark, ou simplesmente landmark — é aquele localizado em uma posição específica da face humana que garanta sua existência na maioria das observações. Esses pontos normalmente marcam características salientes como: cantos e centros dos olhos, bordas da boca, centro do nariz e sobrancelhas, não se limitando a estes.
>
> KATSIKITIS, M. The human face: measurement and meaning. Kluwer Academic Publishers, 2003

-   `predict_model`: Utiliza a bilioteca `requests`para realizar a requisição que retorna a predição dos modelos.
-   `identify_face`: Utiliza a biblioteca `opencv`e o classificador `haarcascade`para reconhecimento e marcação de uma face.
-   `get_fiducial_points`e `identify_fiducial_points` : Utiliza a biblioteca `dlib`e o modelo `shape_predictor_68` para identificação e marcação dos pontos fiduciais faciais.

O último bloco do arquivo é responsável pela decisão lógica do empréstimo, baseado nas seguintes regras:

-   Validar se a imagem possui uma pessoa (se não, negar).
-   Validar se a imagem possui conteúdo explícito (se sim, negar).
-   Validar a idade da pessoa (se a imagem diferir em 5 anos da cadastrada, negar).
-   Validar o gênero da pessoa (se não for o mesmo do cadastro, negar).
-   Score de predição 01 igual à 0.
-   Score de predição 02 menor ou igual à 0.7.

# 🚀 Deploy

Foi construída uma esteira automatizada utilizando o GitHub Actions, com pouco esforço temos nossa API e/ou nosso modelo atualizado no servidor pronto para ser utilizado.

![](https://miro.medium.com/max/2000/1*sHn1A7InUwLvPTDB__kdOg.png)

Para essa esteira, temos os seguintes passos:

-   Setups do workflow.
-   Setup do Python.
-   Instalação dos requisitos necessários para execução dos scripts.
-   Execução do script de criação e treinamento do modelo.
-   Login do [Docker Registry](https://docs.docker.com/registry/) privado utilizando [secrets](https://help.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets).
-   Build do Dockerfile da API no ambiente do GitHub e criação e tagueamento da imagem para o servidor.
-   Deploy da aplicação atualizando o container no servidor.
