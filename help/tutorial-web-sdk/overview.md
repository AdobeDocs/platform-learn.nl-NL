---
title: Zelfstudie Adobe Experience Cloud implementeren met Web SDK
description: Leer hoe te om de toepassingen van Experience Cloud uit te voeren gebruikend het Web SDK van Adobe Experience Platform.
recommendations: catalog, noDisplay
exl-id: cf0ff74b-e81e-4f6d-ab7d-6c70e9b52d78
source-git-commit: cf0193e3aae4d6536c868f078f4773ee14e90408
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 1%

---

# Zelfstudie Adobe Experience Cloud implementeren met Web SDK

Leer hoe te om de toepassingen van Experience Cloud uit te voeren gebruikend het Web SDK van Adobe Experience Platform.

Experience Platform Web SDK is een client-side JavaScript-bibliotheek waarmee klanten van Adobe Experience Cloud kunnen communiceren met zowel Adobe-toepassingen als services van derden via het Adobe Experience Platform Edge Network. Zie [Adobe Experience Platform Web SDK - Overzicht](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) voor meer gedetailleerde informatie.

Deze zelfstudie begeleidt u door de implementatie van de SDK van het Web Platform op een website in de detailhandel met de naam Luma. De [Luminantiesite](https://luma.enablementadobe.com/content/luma/us/en.html) heeft een rijke gegevenslaag en functionaliteit die u een realistische implementatie laat bouwen. Nadat u deze zelfstudie hebt voltooid, kunt u al uw marketingoplossingen implementeren via Platform Web SDK op uw eigen website.

[![Luma-website](assets/old-overview-luma.png)](https://luma.enablementadobe.com/content/luma/us/en.html)


## Leerdoelstellingen

Nadat u de zelfstudie hebt voltooid, kunt u het volgende doen:

* Gegevensstromen configureren

* XDM-schema&#39;s maken

* Voeg de volgende Adobe Experience Cloud-toepassingen toe:
   * **[Adobe Experience Platform](setup-experience-platform.md)** (en toepassingen die zijn gebaseerd op Platform zoals Adobe Real-time Customer Data Platform, Adobe Journey Optimizer en Adobe Customer Journey Analytics)
   * **[Adobe Analytics](setup-analytics.md)**
   * **[Adobe Audience Manager](setup-audience-manager.md)**
   * **[Adobe Target](setup-target.md)**

* Tagregels maken en XDM-objectgegevenselementen maken om gegevens naar Adobe-toepassingen te verzenden

* De implementatie valideren met de Adobe Experience Platform Debugger

* Gebruikersgoedkeuring vastleggen

* Gegevens doorsturen naar derden met het doorsturen van gebeurtenissen

>[!NOTE]
>
>Een vergelijkbare zelfstudie met meerdere oplossingen is beschikbaar voor [Mobile SDK](../tutorial-mobile-sdk/overview.md).

## Vereisten

Alle klanten van Experience Cloud kunnen SDK van het Web van het Platform gebruiken. Het is geen vereiste om een op Platform-gebaseerde toepassing zoals Real-time Customer Data Platform of Journey Optimizer vergunning te geven om Web SDK te gebruiken.

In deze lessen wordt aangenomen dat u een Adobe-account en de [vereiste machtigingen](configure-permissions.md) om de lessen te voltooien. Als niet, moet u uw Beheerder van Experience Cloud bereiken om toegang te verzoeken.

Ook wordt aangenomen dat u bekend bent met de ontwikkelingstalen aan de voorzijde, zoals HTML en JavaScript. U hoeft geen expert in deze talen te zijn, maar u kunt meer uit deze zelfstudie halen als u code kunt lezen en begrijpen.

Laten we beginnen!

[Volgende: ](configure-permissions.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over Adobe Experience Platform Web SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
