---
title: Criando componentes customizados (Custom Activity) no Marketing Cloud
excerpt: >-
    Com os componente customizados você pode integrar todo tipo de serviço nas jornadas do cliente.
date: '2019-12-02'
thumb_img_path: https://miro.medium.com/max/700/1*eG0HBdKYFmygQfZ7jxJszg.png
thumb_img_alt: Criando componentes customizados (Custom Activity) no Marketing Cloud
content_img_path: https://miro.medium.com/max/700/1*eG0HBdKYFmygQfZ7jxJszg.png
content_img_alt: Criando componentes customizados (Custom Activity) no Marketing Cloud
seo:
    title: Criando componentes customizados (Custom Activity) no Marketing Cloud
    description: >-
        Com os componente customizados você pode integrar todo tipo de serviço nas jornadas do cliente.
    extra:
        - name: 'og:type'
          value: article
          keyName: property
        - name: 'og:title'
          value: Criando componentes customizados (Custom Activity) no Marketing Cloud
          keyName: property
        - name: 'og:description'
          value: >-
              Com os componente customizados você pode integrar todo tipo de serviço nas jornadas do cliente.
          keyName: property
        - name: 'og:image'
          value: https://miro.medium.com/max/700/1*eG0HBdKYFmygQfZ7jxJszg.png
          keyName: property
          relativeUrl: true
        - name: 'twitter:card'
          value: summary_large_image
        - name: 'twitter:title'
          value: Criando componentes customizados (Custom Activity) no Marketing Cloud
        - name: 'twitter:description'
          value: >-
              Com os componente customizados você pode integrar todo tipo de serviço nas jornadas do cliente.
        - name: 'twitter:image'
          value: https://miro.medium.com/max/700/1*eG0HBdKYFmygQfZ7jxJszg.png
          relativeUrl: true
layout: post
---

Com os componente customizados você pode integrar todo tipo de serviço nas jornadas do cliente.

# ☁ Salesforce Marketing Cloud

Junte-se aos seus clientes em uma jornada personalizada com sua marca. Com o Salesforce Marketing Cloud é possível personalizar experiências por e-mail, dispositivos móveis, redes sociais, publicidade e Web. Crie uma experiência unificada, conectando toda a sua empresa em todos os departamentos e disciplinas. [Clique aqui](https://www.salesforce.com/br/products/marketing-cloud/why-salesforce/#) e saiba o por que Salesforce Marketing Cloud.

## 🚀 O que vamos utilizar?

-   [Salesforce Marketing Cloud](https://www.salesforce.com/products/marketing-cloud/overview/)
-   [Heroku](https://www.heroku.com/)
-   [NodeJS](https://nodejs.org/en/)

Para este artigo será demonstrada a criação de um componente customizado à ser embutido dentro de uma jornada. A configuração e execução desta jornada pode envolver particularidades e dados sensíveis, que podem ser tratados em um futuro artigo.

# 👨‍💻 Mão na massa!

Para este artigo, utilizaremos um template adaptado à partir do template da [Devs United](https://github.com/devsutd).

[

## lennonalvesdias/journey-builder-custom-activity

### ☕ Code and coffee Projeto | Funcionalidades | Como usar | Como contribuir | Licença Com o Salesforce MarketCloud Custom…

github.com

](https://github.com/lennonalvesdias/journey-builder-custom-activity)

Para que possamos realizar o deploy automático de acordo com o versionamento das nossas atualizações, é importante [fazer um _fork_](https://help.github.com/en/github/getting-started-with-github/fork-a-repo) do repositório acima.

## 📌 Configurando o web service

Após o _fork_, vamos criar uma nova aplicação no Heroku. Caso você ainda não tenha conta, é possível [criar uma de forma gratuita](https://signup.heroku.com/), caso contráro, basta realizarmos o [_login_](https://id.heroku.com/login) ao _dashboard_ da plataforma.

No [dashboard da plataforma](https://dashboard.heroku.com/apps), navegaremos em `New > Create new app`, nomearemos a nova aplicação e finalizaremos clicando em `Create app`.

<img alt="" class="t u v iz aj" src="https://miro.medium.com/max/1400/1\*SRoCMebroxY2ki1yKs\_5nQ.png" width="700" height="74" srcSet="https://miro.medium.com/max/552/1\*SRoCMebroxY2ki1yKs\_5nQ.png 276w, https://miro.medium.com/max/1104/1\*SRoCMebroxY2ki1yKs\_5nQ.png 552w, https://miro.medium.com/max/1280/1\*SRoCMebroxY2ki1yKs\_5nQ.png 640w, https://miro.medium.com/max/1400/1\*SRoCMebroxY2ki1yKs\_5nQ.png 700w" sizes="700px" role="presentation"/>

Print da criação de uma nova aplicação (parte 1).

<img alt="" class="t u v iz aj" src="https://miro.medium.com/max/1090/1\*\_xR-iMlkui8dCsL8C3pqNQ.png" width="545" height="319" srcSet="https://miro.medium.com/max/552/1\*\_xR-iMlkui8dCsL8C3pqNQ.png 276w, https://miro.medium.com/max/1090/1\*\_xR-iMlkui8dCsL8C3pqNQ.png 545w" sizes="545px" role="presentation"/>

Criação de uma nova aplicação.

Com a aplicação criada, podemos escolher o método de _deploy_ que utilizaremos na aplicação. Para este artigo, utilizarei o GitHub, porém você pode escolher o seu preferido.

Ao selecionar o método de _deploy_, será necessário realizar a conexão com a minha conta e então procurar pelo repositório que eu queria conectar. Para este exemplo, escolhi conectar com o `journey-builder-custom-activity`, que refere-se ao link encontrado logo no começo desta sessão.

<img alt="" class="t u v iz aj" src="https://miro.medium.com/max/1400/1\*zLf098OcTE4vC0qjCzbz5g.png" width="700" height="581" srcSet="https://miro.medium.com/max/552/1\*zLf098OcTE4vC0qjCzbz5g.png 276w, https://miro.medium.com/max/1104/1\*zLf098OcTE4vC0qjCzbz5g.png 552w, https://miro.medium.com/max/1280/1\*zLf098OcTE4vC0qjCzbz5g.png 640w, https://miro.medium.com/max/1400/1\*zLf098OcTE4vC0qjCzbz5g.png 700w" sizes="700px" role="presentation"/>

Configuração do deploy.

Com o repositório configurado, é possível realizar algumas outras configurações alternativas, como habilitar o _deploy_ automático, para que o conteúdo do servidor seja atualizado assim que for realizado uma atualização ([git _push_](https://git-scm.com/docs/git-push)) no controlador de versão. Caso prefira manter as atualizações automáticas desligadas, é possível utilizar o botão `Deploy Branch` para realizar a modificação de forma manual.

> Além da opção de deploy automático, é possível também configurar a branch que irá ser publicada (`Choose a branch to deploy`).

Com as configurações ajustadas, e realiado o seu concluído o seu primeiro deploy, é possível clicar no botão `Open App` para visualizar a sua aplicação no endereço provisinado pelo Heroku.

<img alt="" class="t u v iz aj" src="https://miro.medium.com/max/1400/1\*Uiy65R-TpJ47XEX9kiKacA.png" width="700" height="51" srcSet="https://miro.medium.com/max/552/1\*Uiy65R-TpJ47XEX9kiKacA.png 276w, https://miro.medium.com/max/1104/1\*Uiy65R-TpJ47XEX9kiKacA.png 552w, https://miro.medium.com/max/1280/1\*Uiy65R-TpJ47XEX9kiKacA.png 640w, https://miro.medium.com/max/1400/1\*Uiy65R-TpJ47XEX9kiKacA.png 700w" sizes="700px" role="presentation"/>

Botão disponível para navegar ao endereço da aplicação.

## 📌 Configurando o Marketing Cloud

Com o _Heroku_ configurado, o próximo passo é criar um novo _package_ no ambiente do _Marketing Cloud_. Para isso, é necessário navegar em `Perfil > Setup` no menu superior direito e, após isso, em `Apps > Installed Packages` no menu à esquerda.

<img alt="" class="t u v iz aj" src="https://miro.medium.com/max/876/1\*ahDbkA8GvmqT57Da2GJERg.png" width="438" height="199" srcSet="https://miro.medium.com/max/552/1\*ahDbkA8GvmqT57Da2GJERg.png 276w, https://miro.medium.com/max/876/1\*ahDbkA8GvmqT57Da2GJERg.png 438w" sizes="438px" role="presentation"/>

Configurações de Setup.

<img alt="" class="t u v iz aj" src="https://miro.medium.com/max/394/1\*SFQTO3Zi-Rw-Objb5FGG-w.png" width="197" height="488" role="presentation"/>

Navegação de pacotes instalados.

Estará visível a lista com o nome de todos os pacotes criados, assim como sua descrição e a data de instalação. Nesse passo, criaremos um novo pacote clicando no botão `New`.

<img alt="" class="t u v iz aj" src="https://miro.medium.com/max/1400/1\*WuRMZ8WXIUuTq-9dwPfEXw.png" width="700" height="54" srcSet="https://miro.medium.com/max/552/1\*WuRMZ8WXIUuTq-9dwPfEXw.png 276w, https://miro.medium.com/max/1104/1\*WuRMZ8WXIUuTq-9dwPfEXw.png 552w, https://miro.medium.com/max/1280/1\*WuRMZ8WXIUuTq-9dwPfEXw.png 640w, https://miro.medium.com/max/1400/1\*WuRMZ8WXIUuTq-9dwPfEXw.png 700w" sizes="700px" role="presentation"/>

Criação de um novo pacote.

Será então solicitado o nome e a descrição do novo pacote, após o preenchimento basta clicar no botão `Save` e ele estará criado.

A tela com as configurações do pacote estará disponível com o _status_, a _conta de serviço_, o _id do pacote_ e a _chave jwt_. É recomendado **salvar a _chave jwt_** em um outro arquivo, essa chave será utilizada na configuração do ambiente.

<img alt="" class="t u v iz aj" src="https://miro.medium.com/max/1400/1\*BuSI7V3UlKbrwa6LeqPgHA.png" width="700" height="534" srcSet="https://miro.medium.com/max/552/1\*BuSI7V3UlKbrwa6LeqPgHA.png 276w, https://miro.medium.com/max/1104/1\*BuSI7V3UlKbrwa6LeqPgHA.png 552w, https://miro.medium.com/max/1280/1\*BuSI7V3UlKbrwa6LeqPgHA.png 640w, https://miro.medium.com/max/1400/1\*BuSI7V3UlKbrwa6LeqPgHA.png 700w" sizes="700px" role="presentation"/>

Painel de configurações do novo pacote.

O próximo passo é clicar no botão `Add Component` e iniciar a configuração do `Journey Builder Activity`.

<img alt="" class="t u v iz aj" src="https://miro.medium.com/max/1018/1\*NnuFAvvUgRBFTrZE3TytIA.png" width="509" height="291" srcSet="https://miro.medium.com/max/552/1\*NnuFAvvUgRBFTrZE3TytIA.png 276w, https://miro.medium.com/max/1018/1\*NnuFAvvUgRBFTrZE3TytIA.png 509w" sizes="509px" role="presentation"/>

Criação de um componente (parte 1).

<img alt="" class="t u v iz aj" src="https://miro.medium.com/max/1018/1\*6D6tjQBRhhBIK\_JdgryxWw.png" width="509" height="424" srcSet="https://miro.medium.com/max/552/1\*6D6tjQBRhhBIK\_JdgryxWw.png 276w, https://miro.medium.com/max/1018/1\*6D6tjQBRhhBIK\_JdgryxWw.png 509w" sizes="509px" role="presentation"/>

Criação de um componente (parte 2).

Após a criação do componente, será exibida novamente a tela do painel com as informações do nova criação. Nesse painel estará visível a _Unique Key_, recomenda-se também **salvar esta chave**.

Com isso, a finalização do novo pacote dentro do _Marketing Cloud_ está finalizada. O próximo passo é configurar a _activity_, onde utilizaremos esta última chave salva.

## 📌 Configurando a Activity

Para a configuração da _activity_, é necessário alterar no `/public/config.json`a _applicationExtensionKey_ com o valor da _Unique Key_ salva, além de atualizar com o _url_ com o _endpoint_ da aplicação criada no _Heroku_.

Modelo do arquivo .config

Com essas alterações e eventuais personalizações do componente, é possível realizar o _deploy_ para que as configurações sejam aplicadas em produção. Este _deploy_ pode variar de acordo com as configurações demonstradas acima.

## 📌 Configurando o ambiente no Heroku

Para os ajustes finais, precisamos inserir a chave _jwt_ nas variáveis de ambiente da nossa aplicação no _Heroku_. As configurações destas variáveis são encontradas em `Settings`, no menu superior da aplicação.

```
[https://dashboard.heroku.com/apps/\[ID\_DA\_SUA\_APLICAÇÃO\]/settings](https://dashboard.heroku.com/apps/nova-atividade-customizada/settings)
```

O passo de inserir, deletar ou modificar uma variável de ambiente é à partir do botão `Reveal Config Vars`, onde serão listadas as variáveis cadastradas e exibidas as opções de manipulação entre elas.

<img alt="" class="t u v iz aj" src="https://miro.medium.com/max/1400/1\*ez6H9dFCwD4QlfiHjqTfVQ.png" width="700" height="113" srcSet="https://miro.medium.com/max/552/1\*ez6H9dFCwD4QlfiHjqTfVQ.png 276w, https://miro.medium.com/max/1104/1\*ez6H9dFCwD4QlfiHjqTfVQ.png 552w, https://miro.medium.com/max/1280/1\*ez6H9dFCwD4QlfiHjqTfVQ.png 640w, https://miro.medium.com/max/1400/1\*ez6H9dFCwD4QlfiHjqTfVQ.png 700w" sizes="700px" role="presentation"/>

Configuração das variáveis de ambiente (passo 01).

<img alt="" class="t u v iz aj" src="https://miro.medium.com/max/1400/1\*pZqAXP-KkdcXUjnE5pptbg.png" width="700" height="154" srcSet="https://miro.medium.com/max/552/1\*pZqAXP-KkdcXUjnE5pptbg.png 276w, https://miro.medium.com/max/1104/1\*pZqAXP-KkdcXUjnE5pptbg.png 552w, https://miro.medium.com/max/1280/1\*pZqAXP-KkdcXUjnE5pptbg.png 640w, https://miro.medium.com/max/1400/1\*pZqAXP-KkdcXUjnE5pptbg.png 700w" sizes="700px" role="presentation"/>

Configuração das variáveis de ambiente (passo 02).

Após inserir o código _jwt_ com a chave _jwtSecret_, é necessário clicar no botão `Add` para confirmar a inclusão da nova variável. Com a configuração aplicada, já será possível testar seu novo componente em uma jornada do _Marketing Cloud_.

## 📌 Executando a jornada

As jornadas podem ser acessadas pelo menu _Journey Builder_, onde existe o submenu _Automation Studio_(rotina de automação para execução da jornada) e _Journey Builder_ (configuração da jornada).

<img alt="" class="t u v iz aj" src="https://miro.medium.com/max/1400/1\*JzTwTuN61hOddoe86Bstbw.png" width="700" height="170" srcSet="https://miro.medium.com/max/552/1\*JzTwTuN61hOddoe86Bstbw.png 276w, https://miro.medium.com/max/1104/1\*JzTwTuN61hOddoe86Bstbw.png 552w, https://miro.medium.com/max/1280/1\*JzTwTuN61hOddoe86Bstbw.png 640w, https://miro.medium.com/max/1400/1\*JzTwTuN61hOddoe86Bstbw.png 700w" sizes="700px" role="presentation"/>

Menu principal do Salesforce Marketing Cloud.

Ao acessar o _Journey Builder_, será possível configurar a sua jornada ou então criar uma nova. No exemplo abaixo é possível encontrar o novo componente, nomeado de ‘_Atividade Customizada_’, nas opções à esquerda. Ao clicar e arrastar, o componente fará parte da jornada desenhada.

<img alt="" class="t u v iz aj" src="https://miro.medium.com/max/1400/1\*tpKzmYKtvgie--fHKH18rQ.png" width="700" height="377" srcSet="https://miro.medium.com/max/552/1\*tpKzmYKtvgie--fHKH18rQ.png 276w, https://miro.medium.com/max/1104/1\*tpKzmYKtvgie--fHKH18rQ.png 552w, https://miro.medium.com/max/1280/1\*tpKzmYKtvgie--fHKH18rQ.png 640w, https://miro.medium.com/max/1400/1\*tpKzmYKtvgie--fHKH18rQ.png 700w" sizes="700px" role="presentation"/>

Configuração da jornada incluindo componente customizado.

Após concluir o mapeamento da jornada, é possível salvar, validar e ativar. Assim que ativa, a jornada está pronta para ser executada de acordo com o [_schedule_](https://pt.wikipedia.org/wiki/Escalonamento_de_processos) configurado.

É possível encontrar um exemplo prático de uma atividade que realiza o disparo de templates _HSM_ do _Whatsapp_ acessando o repositório:

[

## lennonalvesdias/journey-builder-custom-activity

### ☕ Code and coffee Projeto | Funcionalidades | Como usar | Como contribuir | Licença Com o Salesforce MarketCloud Custom…

github.com

](https://github.com/lennonalvesdias/journey-builder-custom-activity/tree/whatsapp-hsm)

# 📃 Referências

-   [Salesforce](https://developer.salesforce.com/docs/atlas.en-us.noversion.mc-apis.meta/mc-apis/getting-started-spec.htm?search_text=custom%20activity)
