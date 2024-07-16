---
title: Bootkamp - Real-time CDP - Bouw een segment en neem actie - verzend uw segment naar DV360 - Brazilië
description: Bootkamp - Real-time CDP - Bouw een segment en neem actie - verzend uw segment naar DV360 - Brazilië
jira: KT-5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
feature: Destinations
exl-id: acb32859-6f82-44e0-8948-a045a9fe2afe
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# 1.5 Ação: envie seu segmento para o Facebook

Toegang tot [ Adobe Experience Platform ](https://experience.adobe.com/platform). Depois de fazer login, você irá acessar a página inicial da Adobe Experience Platform.

![ Ingestie van Gegevens ](./images/home.png)

Antes de continuar, você nauwkeurige um **zandbak**. O nome do sandbox a ser selecionado é Bootkamp. É bezível fazer isso clicando no texto **[!UICONTROL Production Prod]** na linha azul na parte superior da tela. Depois de selecionar o sandbox apropriado, você verá a tela mudando e agora você está em seu [!UICONTROL sandbox] oormerk.

![ Ingestie van Gegevens ](./images/sb1.png)

Geen menu à esquerda, vá para **Doelen** e, em seguida, vá para **Catalogus**. Você verá o **Catalogus van Doelen**. Em **Doelen**, klikem **activeert Segmenten** geen cartão **de Aangepaste Publiek van Facebook**.

![ RTCDP ](./images/rtcdpgoogleseg.png)

Selecione aan **bootkamp-facebook** e clique em **daarna**.

![ RTCDP ](./images/rtcdpcreatedest2.png)

Na lista de segmentos disponíveis, selecione o segmento que você criou no uitoefício anterior. Clique em **daarna**.

![ RTCDP ](./images/rtcdpcreatedest3.png)

Na página **Afbeelding**, verifieert gebruik a caixa de seleção **past Transformatie** está marcada toe. Clique em **daarna**.

![ RTCDP ](./images/rtcdpcreatedest4a.png)

Na página **Plan van het Segment**, verkies a **Oorsprong van uw publiek** e defina como **direct van klanten**. Clique em **daarna**.

![ RTCDP ](./images/rtcdpcreatedest4.png)

Por fim, na página **Overzicht**, kliek em **Afwerking**.

![ RTCDP ](./images/rtcdpcreatedest5.png)

Seu segmento agora está vinculado aos Públicos Personalizados do Facebook. Sempre que um cliente se quality para esse segmento, um sinal será enviado ao lado do servidor (server-side) do Facebook para incluir esse cliente no Público Personalizado no lado do Facebook.

Geen Facebook, você encontrará seu segmento da Adobe Experience Platform em Públicos Personalizados:

![ RTCDP ](./images/rtcdpcreatedest5b.png)

Agora você pode ver seu público personalizado aparecer no Facebook:

![ RTCDP ](./images/rtcdpcreatedest5a.png)

[Retornar para Fluxo de Usuário 1](./uc1.md)

[Retornar para Todos os Módulos](../../overview.md)
