---
title: XGBoost e LigthGBM no modelo de decisão de crédito
excerpt: >-
    Na primeira versão utilizamos os algoritmos RandomForest e GradientBoosting, mas será que eles são mesmo a melhor opção?
date: '2020-05-15'
thumb_img_path: https://miro.medium.com/max/1400/1*6eUtcNtT4fJUrlmlcUlN0w.png
thumb_img_alt: XGBoost e LigthGBM no modelo de decisão de crédito
content_img_path: https://miro.medium.com/max/1400/1*6eUtcNtT4fJUrlmlcUlN0w.png
content_img_alt: XGBoost e LigthGBM no modelo de decisão de crédito
seo:
    title: XGBoost e LigthGBM no modelo de decisão de crédito
    description: >-
        Na primeira versão utilizamos os algoritmos RandomForest e GradientBoosting, mas será que eles são mesmo a melhor opção?
    extra:
        - name: 'og:type'
          value: article
          keyName: property
        - name: 'og:title'
          value: XGBoost e LigthGBM no modelo de decisão de crédito
          keyName: property
        - name: 'og:description'
          value: >-
              Na primeira versão utilizamos os algoritmos RandomForest e GradientBoosting, mas será que eles são mesmo a melhor opção?
          keyName: property
        - name: 'og:image'
          value: https://miro.medium.com/max/1400/1*6eUtcNtT4fJUrlmlcUlN0w.png
          keyName: property
          relativeUrl: true
        - name: 'twitter:card'
          value: summary_large_image
        - name: 'twitter:title'
          value: XGBoost e LigthGBM no modelo de decisão de crédito
        - name: 'twitter:description'
          value: >-
              Na primeira versão utilizamos os algoritmos RandomForest e GradientBoosting, mas será que eles são mesmo a melhor opção?
        - name: 'twitter:image'
          value: https://miro.medium.com/max/1400/1*6eUtcNtT4fJUrlmlcUlN0w.png
          relativeUrl: true
layout: post
---

No artigo [“Decisão de crédito utilizando machine learning e visão computacional”](https://medium.com/@lennonalvesdias/decisão-de-crédito-utilizando-machine-learning-e-visão-computacional-d0a1e785ca80) foi demonstrada a utilização de técnicas de inteligência artificial para um sistema modelo de análise e decisão de crédito.

O artigo demonstra a utilização de APIs e bibliotecas para reconhecer uma pessoa à partir de uma foto, extrair idade e gênero e realizar marcações como os pontos fiduciais.

[

Decisão de crédito utilizando machine learning e visão computacional
--------------------------------------------------------------------

### Utilização de APIs e bibliotecas de visão computacional e aprendizado de máquina para criação de um motor de decisão de…

medium.comC

](https://medium.com/@lennonalvesdias/decisão-de-crédito-utilizando-machine-learning-e-visão-computacional-d0a1e785ca80)

Um dos pontos do artigo citado, no qual iremos abordar com mais detalhes, é a criação e treinamento de modelos de predição de score para tomada de decisão. Na primeira versão utilizamos os algoritmos _RandomForest_ e _GradientBoosting_, mas será que eles são mesmo a melhor opção? 🤔

![](https://miro.medium.com/max/2524/1*j4fXcaziurkVXNeS9l9hFw.png)

Nesta nova versão, novos algoritmos foram testados e o score de cada um deles foi comparado, tanto para classificação quanto para regressão.

> Uma lista com vários algoritmos implementados na biblioteca sklearn você pode encontrar pelo link: [https://scikit-learn.org/stable/modules/classes.html#module-sklearn.ensemble](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.ensemble)

_RandomForest_ e _GradientBoosting_ são “figurinhas carimbadas” nas disciplinas de _Machine Learning_, que resolvem grande parte dos problemas de mercado, entregando uma acurácia aceitável pelo seu tempo de treinamento.

Com base na indicação do professor [Me. Felipe Teodoro](https://www.linkedin.com/in/felipe-teodoro-87b25217/) e, nos recentes resultados destas bibliotecas em competições de aprendizado de máquina, os dois outros algoritmos são: [_XGBoost_](https://github.com/dmlc/xgboost/blob/master/demo/README.md)  e [_Light GBM_](https://github.com/microsoft/LightGBM/blob/master/README.md).

> É possível encontrar mais sobre as competições e os resultados nos links de cada um dos algoritmos acima.

Como explicado no [artigo anterior](https://medium.com/@lennonalvesdias/decisão-de-crédito-utilizando-machine-learning-e-visão-computacional-d0a1e785ca80) sobre o tema, com a atualização do modelo o GitHub Action se encarrega de realizar o _Build_ e o _Deploy_ da aplicação. Um dos passos deste processo é o treinamento do modelo, [disponível clicando aqui](https://github.com/lennonalvesdias/credit-decisor/runs/676849494?check_suite_focus=true), em que temos o seguinte resultado:

```
model\_1\_randomforest\_classifier accuracy: 0.8600333333333333  
model\_1\_xgboost\_classifier accuracy: 0.8746  
model\_1\_lightgbm\_classifier accuracy: 0.8762666666666666  
model\_1\_gradientboosting\_classifier accuracy: 0.8768333333333334  
model\_1\_randomforest\_regressor accuracy: 0.5901592249304006  
model\_1\_xgboost\_regressor accuracy: 0.6371604287220034  
model\_1\_lightgbm\_regressor accuracy: 0.6450610561426381  
model\_1\_gradientboosting\_regressor accuracy: 0.6329410198786587  
model\_2\_randomforest\_classifier accuracy: 0.8464333333333334  
model\_2\_xgboost\_classifier accuracy: 0.8633333333333333  
model\_2\_lightgbm\_classifier accuracy: 0.8649666666666667  
model\_2\_gradientboosting\_classifier accuracy: 0.8657666666666667  
model\_2\_randomforest\_regressor accuracy: 0.5519534871968672  
model\_2\_xgboost\_regressor accuracy: 0.6072325295143952  
model\_2\_lightgbm\_regressor accuracy: 0.6134725152532305  
model\_2\_gradientboosting\_regressor accuracy: 0.6069039918997955
```

Código completo: