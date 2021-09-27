---
title: Rapidinhas - Evitando armadilhas comuns com .NetCore Async
excerpt: >-
    Nessa primeira #rapidinha abordaremos armadilhas (algumas bem comuns) que devemos evitar na implementações de códigos assíncronos
date: '2020-07-09'
thumb_img_path: https://miro.medium.com/max/1400/1*wZb4MppIKgUSWw1QMKpqUQ.jpeg
thumb_img_alt: Rapidinhas - Evitando armadilhas comuns com .NetCore Async
content_img_path: https://miro.medium.com/max/1400/1*wZb4MppIKgUSWw1QMKpqUQ.jpeg
content_img_alt: Rapidinhas - Evitando armadilhas comuns com .NetCore Async
seo:
    title: Rapidinhas - Evitando armadilhas comuns com .NetCore Async
    description: >-
        Nessa primeira #rapidinha abordaremos armadilhas (algumas bem comuns) que devemos evitar na implementações de códigos assíncronos
    extra:
        - name: 'og:type'
          value: article
          keyName: property
        - name: 'og:title'
          value: Rapidinhas - Evitando armadilhas comuns com .NetCore Async
          keyName: property
        - name: 'og:description'
          value: >-
              Nessa primeira #rapidinha abordaremos armadilhas (algumas bem comuns) que devemos evitar na implementações de códigos assíncronos
          keyName: property
        - name: 'og:image'
          value: https://miro.medium.com/max/1400/1*wZb4MppIKgUSWw1QMKpqUQ.jpeg
          keyName: property
          relativeUrl: true
        - name: 'twitter:card'
          value: summary_large_image
        - name: 'twitter:title'
          value: Rapidinhas - Evitando armadilhas comuns com .NetCore Async
        - name: 'twitter:description'
          value: >-
              Nessa primeira #rapidinha abordaremos armadilhas (algumas bem comuns) que devemos evitar na implementações de códigos assíncronos
        - name: 'twitter:image'
          value: https://miro.medium.com/max/1400/1*wZb4MppIKgUSWw1QMKpqUQ.jpeg
          relativeUrl: true
layout: post
---

Nessa primeira #rapidinha abordaremos armadilhas (algumas bem comuns) que devemos evitar na implementações de códigos assíncronos utilizando .NET Core.

## 1\. Usar `Task.Run()`na aplicação.

Cria uma thread não otimizada.  
Causa sobrecarga.  
Diminui a escalabilidade.

## 2\. `Task.Wait()` e `Task.Result()`bloqueiam o seguimento da chamada.

O encademanto não é retornado ao conjunto de encadeamento.  
Bloquear código assíncrono prejudica a escalabilidade.-  
O ASP.NET Core não possui um contexto de sincronização.

## 3\. Modificando o estado compartilhado.

Threads diferentes podem manipular o mesmo estado ao mesmo tempo.  
A correção não pode ser garantida.

Conhece alguma outra armadilha que não devemos cair? Já utilizou alguns desses recursos acima e não sabia disso? Compartilhe suas experiências e vamos trocar uma idéia.

Quer aprender mais sobre como montar uma API assincrona garantindo segurança, performance e escalabilidade? Confira esse curso:

[Building an Async API with ASP.NET Core](https://www.pluralsight.com/courses/building-async-api-aspdotnet-core)
