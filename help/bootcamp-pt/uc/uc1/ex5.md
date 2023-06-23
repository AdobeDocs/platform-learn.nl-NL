---
title: Bootkamp - Real-time CDP - Bouw een segment en neem actie - verzend uw segment naar DV360 - Brazilië
description: Bootkamp - Real-time CDP - Bouw een segment en neem actie - verzend uw segment naar DV360 - Brazilië
jira: KT-5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: acb32859-6f82-44e0-8948-a045a9fe2afe
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 1%

---

# 1.5 Ação: envie seu segmento para o Facebook

Acesse [Adobe Experience Platform](https://experience.adobe.com/platform). Depois de fazer login, você irá acessar a página inicial da Adobe Experience Platform.

![Gegevensopname](./images/home.png)

Antes de continue ar, vocêprecisa selecionar um **sandbox**. O nome do sandbox a ser selecionado é Bootkamp. É bezível fazer isso clicando no texto **[!UICONTROL Productieproduct]** Na linha azul na parte superior da tela. Depois de selecionar o sandbox apropriado, você verá a tela mudando e agora você está em seu [!UICONTROL sandbox] toewijding.

![Gegevensopname](./images/sb1.png)

Geen menu à esquerda, vá para **Doelen** e, em seguida, vá para **Catalogus**. Você verá o **Doelcatalogus**. Em **Doelen**, klikem **Segmenten activeren** geen cartão **Facebook Aangepast publiek**.

![RTCDP](./images/rtcdpgoogleseg.png)

Selectie o **bootkamp-facebook** e clique em **Volgende**.

![RTCDP](./images/rtcdpcreatedest2.png)

Na lista de segmentos disponíveis, selecione o segmento que você criou no uitoefício anterior. Clique em **Volgende**.

![RTCDP](./images/rtcdpcreatedest3.png)

Na página **Toewijzing**, controlque se a caixa de seleção **Transformatie toepassen** está marcada . Clique em **Volgende**.

![RTCDP](./images/rtcdpcreatedest4a.png)

Na página **Segmentatieschema**, selecteert u een **Oorsprong van uw publiek** e defina como **Direct van klanten**. Clique em **Volgende**.

![RTCDP](./images/rtcdpcreatedest4.png)

Por fim, na página **Controleren**, klikem **Voltooien**.

![RTCDP](./images/rtcdpcreatedest5.png)

Seu segmento agora está vinculado aos Públicos Personalizados do Facebook. Sempre que um cliente se quality para esse segmento, um sinal será enviado ao lado do servidor (server-side) do Facebook para incluir esse cliente no Público Personalizado no lado do Facebook.

Geen Facebook, você encontrará seu segmento da Adobe Experience Platform em Públicos Personalizados:

![RTCDP](./images/rtcdpcreatedest5b.png)

Agora você pode ver seu público personalizado aparecer no Facebook:

![RTCDP](./images/rtcdpcreatedest5a.png)

[Retornar para Fluxo de Usuário 1](./uc1.md)

[Retornar para Todos os Módulos](../../overview.md)
