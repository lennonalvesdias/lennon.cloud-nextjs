---
title: Análise (Classificador) de sentimentos com Python + Pandas + scikit-learn + spaCy
excerpt: >-
    Abordagem dos principais classificadores para solucionar o problema de análise de sentimentos utilizando python.
date: '2019-12-23'
thumb_img_path: https://miro.medium.com/max/1400/1*oIxy3zkD2mNkbec27wRgpw.jpeg
thumb_img_alt: Análise (Classificador) de sentimentos com Python + Pandas + scikit-learn + spaCy
content_img_path: https://miro.medium.com/max/1400/1*oIxy3zkD2mNkbec27wRgpw.jpeg
content_img_alt: Análise (Classificador) de sentimentos com Python + Pandas + scikit-learn + spaCy
seo:
    title: Análise (Classificador) de sentimentos com Python + Pandas + scikit-learn + spaCy
    description: >-
        Abordagem dos principais classificadores para solucionar o problema de análise de sentimentos utilizando python.
    extra:
        - name: 'og:type'
          value: article
          keyName: property
        - name: 'og:title'
          value: Análise (Classificador) de sentimentos com Python + Pandas + scikit-learn + spaCy
          keyName: property
        - name: 'og:description'
          value: >-
              Abordagem dos principais classificadores para solucionar o problema de análise de sentimentos utilizando python.
          keyName: property
        - name: 'og:image'
          value: https://miro.medium.com/max/1400/1*oIxy3zkD2mNkbec27wRgpw.jpeg
          keyName: property
          relativeUrl: true
        - name: 'twitter:card'
          value: summary_large_image
        - name: 'twitter:title'
          value: Análise (Classificador) de sentimentos com Python + Pandas + scikit-learn + spaCy
        - name: 'twitter:description'
          value: >-
              Abordagem dos principais classificadores para solucionar o problema de análise de sentimentos utilizando python.
        - name: 'twitter:image'
          value: https://miro.medium.com/max/1400/1*oIxy3zkD2mNkbec27wRgpw.jpeg
          relativeUrl: true
layout: post
---

Abordagem dos principais classificadores para solucionar o problema de análise de sentimentos utilizando [python](https://www.python.org/) com [pandas](https://pandas.pydata.org/), [numpy](https://numpy.org/), [scikit-learn](https://scikit-learn.org/stable/), [nltk](https://www.nltk.org/), e [spaCy](https://spacy.io/).

Para este artigo será utilizada a base de _reviews_ (análises) de filmes do [IMDb](https://www.imdb.com/).

> IMDb, também conhecido como Internet Movie Database, é uma base de dados online de informação sobre música, cinema, filmes, programas e comerciais para televisão e jogos de computador, hoje pertencente à Amazon. [\[Wikipedia\]](https://pt.wikipedia.org/wiki/IMDb)

## 🔎 Técnicas de pré processamento utilizadas:

-   Tratamento de valores nulos
-   _Upcase_/_Downcase (str.lower)_
-   Sinais de pontuação _(unidecode)_
-   Lematização\*

> \* Processo de **deflexionar** (provocar mudança ou alteração no posicionamento normal uma palavra) para determinar o seu **lema**. (Exemplo: palavras = tiver, tenho, tinha, tem; lema = ter)

## 🚀 Técnicas de classificação utilizadas:

-   Decision Tree
-   Random Forest
-   Multinomial Naive Bayes
-   Gradient Boosting
-   Support Vector Machine (SVM)
-   Multinomial Logistic Regression

# Considerações finais

A classificação utilizando regressão logística teve a melhor acurácia, chegando à 0.89506. Além da acurácia, destaca-se também o fato deste método possuir um tempo de processamento _(minutos)_ muito menor do que outros utilizados nesta comparação, como o SVM _(dias)_.

Para obter as melhores configurações ao `LogisticRegression` nós utilizamos o `GridSearchCV`. Essa função consiste em testar variadas combinações de parâmetros ao modelo, encontrando assim o melhor resultado.

> É possível que este arquivo evolua em técnicas de pré processamento e modelos de classificação.

# 👊 Agradecimentos

-   [Cintia Akie Nakano](https://www.linkedin.com/in/cintia-akie/)
-   [Mateus Aguiar Florentino](https://www.linkedin.com/in/mateus-florentino-53993513b/)
-   [Rafael Souza](https://www.linkedin.com/in/rafael-souza-6901aa15/)
