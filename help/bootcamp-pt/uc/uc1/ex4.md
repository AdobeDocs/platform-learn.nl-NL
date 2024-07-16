---
title: Bootkamp - Real-time CDP - Bouw een segment en neem actie - verzend uw segment naar Adobe Target - Brazilië
description: Bootkamp - Real-time CDP - Bouw een segment en neem actie - verzend uw segment naar Adobe Target - Brazilië
jira: KT-5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
solution: Experience Platform, Target
feature: Segments, Integrations
exl-id: 862afd4c-1b6c-48fe-bc1f-967c065642e0
source-git-commit: ee5c0af17c12f1d90774a3a4150c9788e2368e39
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---

# 1.4 Ação: envie seu segmento para o Adobe Target

Toegang tot [ Adobe Experience Platform ](https://experience.adobe.com/platform). Depois de fazer login, você irá acessar a página inicial da Adobe Experience Platform.

![ Ingestie van Gegevens ](./images/home.png)

Antes de continuar, você nauwkeurige um **zandbak**. O nome do sandbox a ser selecionado é Bootkamp. É bezível fazer isso clicando no texto **[!UICONTROL Production Prod]** na linha azul na parte superior da tela. Depois de selecionar o sandbox apropriado, você verá a tela mudando e agora você está em seu [!UICONTROL sandbox] oormerk.

![ Ingestie van Gegevens ](./images/sb1.png)

## 1.4.1 Ative seu segmento para o destination do Adobe Target

O Adobe Target está disponível como um destino do CDP em tempo real. Para configurar sua integração com aan Adobe Target, toegang tot **Doelen** e **Catalogus**.

Clique em **Personalization** geen menu **Categorieën**. Você verá o cartão de destino doet **Adobe Target**. De klemem **activeert Segmenten**.

![ AT ](./images/atdest1.png)

Selecione aan doel ``Bootcamp Target`` e kliek **daarna**.

![ AT ](./images/atdest3.png)

Na lista de segmentos disponíveis, selecione o segmento que você criou em [ 1.3 Crie um segmento ](./ex3.md), com o nome `yourLastName - Interest in Real-Time CDP`. Em seguida, klique em **Volgende**.

![ AT ](./images/atdest8.png)

Na próxima página, klique em **daarna**.

![ AT ](./images/atdest9.png)

De klikem **beëindigt**.

![ AT ](./images/atdest10.png)

Seu segmento agora está ativado para o Adobe Target.

![ AT ](./images/atdest11.png)

>[!IMPORTANT]
>
>Imediatamente após criar seu destino do Adobe Target no Real-Time CDP, pode levar até uma hora para que o destino seja ativado. Este é um tempo de espera único devido à definição da configuração de back-end. Depois que o tempo de espera inicial de 1 hora e a configuração do back-end forem concluídos, os segmentos de borda recém-adicionados que são enviados ao destino do Adobe Target estarão disponíveis para segmentação em tempo real.

## 1.4.2 Sua atividade configureren op Adobe Target

Agora que seu segmento Real-Time CDP está configurado para ser enviado ao Adobe Target, é bezível configurar sua atividade de Segmentação por experience ência no Adobe Target. Neste oefício, você irá configurar uma atividade baseada no Visual Experience Composer.

Heb toegang tot een página inicial da Adobe Experience Cloud acessando [ https://experiencecloud.adobe.com/ ](https://experiencecloud.adobe.com/). Clique em **het Doel** para abrir van het Doel.

![ RTCDP ](./images/excl.png)

Na página inicial doet **Adobe Target**, você verá todas als atividades bestaan.
Clique em **+ Create Activity** para criar uma nova atividade.

![ RTCDP ](./images/exclatov.png)

Selecione **Ervaring richtend**.

![ RTCDP ](./images/exclatcrxt.png)

Selecione **Visuele** e bepaalt a **Activiteit URL** como `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpantXX.html`, mas, antes disso, substitua XX por um número ingang 01 e 60.

>[!IMPORTANT]
>
>Cada participante da condensitação deve usar uma página da Web separada para evitar a colisão de várias experience ências do Adobe Target. É bezível escolher uma página da Web e contrasteert een URL acessando: [ https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html ](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html).
>
>Todas as páginas compartilham a mesma URL base e terminam com o número do participante.
>
>Por voorbeo, o participante 1 deve usar a URL `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant01.html` , or participation 30 deve usar a URL `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant30.html` .

Selecione aan werkruimte **BIJ Bootkamp**.

Clique em **daarna**.

![ RTCDP ](./images/exclatcrxtdtlform.png)

Agora você está no Visual Experience Composer. Pode levar de 20 a 30 segundos até que o site esteja completamente carregado.

![ RTCDP ](./images/atform1.png)

Atualmente, o público padrão são **Alle Bezoekers**. Clique nos **3 dots** ao lado de **Alle bezoekers** e clique em **het Publiek van de Verandering**.

![ RTCDP ](./images/atform3.png)

Agora você está vendo a lista de públicos disponíveis, e o segmento da Adobe Experience Platform que você criou anteriormente e enviou ao Adobe Target agora faz parte dessa lista. Selecione o segmento que você criou anteriormente na Adobe Experience Platform. De Clique em **wijst Publiek** toe.

![ RTCDP ](./images/exclatvecchaud.png)

Seu segmento da Adobe Experience Platform agora faz parte dessa Atividade de segmentação por experience ência.

![ RTCDP ](./images/atform4.png)

Antes de alternar een imagem principal, você deve klikken em **toestaat allen** geen banner de cookies.

Para isso, vá para **doorbladert**

![ RTCDP ](./images/cook1.png)

Em seguida, kliek em **allen** toestaat.

![ RTCDP ](./images/cook2.png)

Em seguida, retorne para **samenstellen**.

![ RTCDP ](./images/cook3.png)

Agora vamos mudar a imagem principal na página inicial do site. De klem na imagem belangrijkste padrão geen plaats, klikem **vervangt Inhoud** e selecione **Beeld**.

![ RTCDP ](./images/atform5.png)

Pesquise aan arquivo de imagem **rtcdp.png**. Selecione e clique em **sparen**.

![ RTCDP ](./images/atform6.png)

Você verá a nova experience ência com a nova imagem para o seu Público selecionado

![ RTCDP ](./images/atform7.png)

Clique no título da sua atividade no canto superior esquerdo para renomeá-la.

![ RTCDP ](./images/exclatvecname.png)

Para o nome, gebruik:

- `seuSobrenome - RTCDP - XT (VEC)`

Clique em **daarna**.

![ RTCDP ](./images/atform8.png)

Clique em **daarna**.

![ RTCDP ](./images/atform8a.png)

Na página **Doelen &amp; Montages**, toegang tot **Goal Metrics**.

![ RTCDP ](./images/atform9.png)

Definieer a Meta belangrijkste como **Betrokkenheid** - **Tijd op Plaats**. De klikem **sparen &amp; sluit**.

![ RTCDP ](./images/vec3.png)

Agora você está na página **Overzicht van de Activiteit**. Você ainda preca ativar sua Atividade.

![ RTCDP ](./images/atform10.png)

De klem op campo **Inactieve** e selecione **activeert**.

![ RTCDP ](./images/atform11.png)

Você receberá uma confirmação visual de que sua atividade agora está ativa.

![ RTCDP ](./images/atform12.png)

Agora sua atividade está ativa e pode ser testada no site do bootkamp.

Se agora você voltar ao seu site de demonstração e bezoekar a página do produto para **Real-Time CDP**, você se kwalificará instantaneamente para o segmento que criou e verá a atividade do Adobe Target exibida na página inicial em tempo real.

>[!IMPORTANT]
>
>Cada participante da condensitação deve usar uma página da Web separada para evitar a colisão de várias experience ências do Adobe Target. É bezível escolher uma página da Web e contrasteert een verbinding URL acessando ao: [ https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html ](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html).
>
>Todas as páginas compartilham a mesma URL base e terminam com o número do participante.
>
>Por exemplo, of participante 1 deve usar a `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant01.html`, of participante 30 deve usar een URL `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant30.html`.

![ RTCDP ](./images/atform12a.png)

Próxima etapa: [ 1.5 Ação: envie seu segmento para o Facebook ](./ex5.md)

[Retornar para Fluxo de Usuário 1](./uc1.md)

[Retornar para Todos os Módulos](../../overview.md)
