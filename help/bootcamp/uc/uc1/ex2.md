---
title: Bootkamp - Real-time klantprofiel - visualiseer uw eigen Real-time profiel van de Klant - UI
description: Bootkamp - Real-time klantprofiel - visualiseer uw eigen Real-time profiel van de Klant - UI
jira: KT-5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
feature: Profiles
exl-id: 4c810767-00ab-4cae-baa9-97b0cb9bf2df
source-git-commit: 5876de5015e4c8c337c235c24cc28b0a32e274dd
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 0%

---

# 1.2 Visualiseer uw eigen Real-time profiel van de Klant - UI

In deze oefening, zult u login aan Adobe Experience Platform en uw eigen Profiel van de Klant in real time in UI bekijken.

## Artikel

In het profiel van de Klant in real time, worden alle profielgegevens getoond naast gebeurtenisgegevens, evenals bestaande publiekslidmaatschappen. De getoonde gegevens kunnen van overal, van de toepassingen van de Adobe en externe oplossingen komen. Dit is de krachtigste weergave in Adobe Experience Platform, het echte ervaringssysteem van record.

## 1.2.1 De weergave Klantprofiel in Adobe Experience Platform gebruiken

Ga naar [ Adobe Experience Platform ](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](./images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``Bootcamp`` . U kunt dit doen door op de tekst **[!UICONTROL Production Prod]** in de blauwe lijn boven op het scherm te klikken. Nadat u de juiste [!UICONTROL sandbox] hebt geselecteerd, ziet u de schermwijziging en nu bevindt u zich in uw toegewezen [!UICONTROL sandbox] .



In het linkermenu, ga naar **Profielen** en **doorbladeren**.

![ Profiel van de Klant ](./images/homemenu.png)

In het deelvenster Profielviewer op uw website vindt u het identiteitsoverzicht. Elke identiteit is gekoppeld aan een naamruimte.

![ Profiel van de Klant ](./images/identities.png)




In Adobe Experience Platform zijn alle id&#39;s even belangrijk. Eerder was de ECID de belangrijkste id in de context van de Adobe en alle andere id&#39;s waren hiërarchisch gekoppeld aan de ECID. In Adobe Experience Platform is dit niet langer het geval en kan elke id als een primaire id worden beschouwd.

De primaire id is doorgaans afhankelijk van de context. Als u uw Centrum van de Vraag vraagt, **wat belangrijkste identiteitskaart is?** zij zullen waarschijnlijk antwoorden, **het telefoonaantal!** Maar als u uw team van CRM vraagt, zullen zij, **het e-mailadres beantwoorden!** Adobe Experience Platform begrijpt deze complexiteit en beheert deze voor u. Elke toepassing, of een toepassing van de Adobe of niet-Adobe, zal met Adobe Experience Platform spreken door te verwijzen naar identiteitskaart zij primair beschouwen. Het werkt gewoon.

Voor het gebied **Identiteitsnaamruimte**, uitgezochte **ECID** en voor de waarde van de 4} Identiteit van het gebied **gaat ECID in u op het paneel van de Kijker van het Profiel van de bootcampings website kunt vinden.** Klik **Mening**. Vervolgens ziet u uw profiel in de lijst. Klik **identiteitskaart van het Profiel** om uw profiel te openen.

![ Profiel van de Klant ](./images/popupecid.png)

U ziet nu een overzicht van een paar belangrijke **Attributen van het Profiel** van uw klantenprofiel.

![ Profiel van de Klant ](./images/profile.png)

Ga naar **Gebeurtenissen**, waar u ingangen voor elke ervaringsgebeurtenis kunt zien die met uw Profiel wordt verbonden.

![ Profiel van de Klant ](./images/profileee.png)

Tot slot ga naar het lidmaatschap van het Publiek van de menuoptie ****. U ziet nu alle soorten publiek die in aanmerking komen voor dit profiel.

![ Profiel van de Klant ](./images/profileseg.png)

Laten wij nu een nieuw publiek creëren dat u zal toestaan om de klantenervaring voor een anonieme of bekende klant te personaliseren.

Volgende Stap: [ 1.3 leidt tot een publiek - UI ](./ex3.md)

[Ga terug naar gebruikersstroom 1](./uc1.md)

[Terug naar alle modules](../../overview.md)
