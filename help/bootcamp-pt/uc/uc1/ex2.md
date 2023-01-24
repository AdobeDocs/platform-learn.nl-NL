---
title: Bootamp - Real-time klantprofiel - Visualiseer uw eigen Real-time klantprofiel - UI - Brazilië
description: Bootamp - Real-time klantprofiel - Visualiseer uw eigen Real-time klantprofiel - UI - Brazilië
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
source-git-commit: 75a878ba596078e6d013b65062606931402302dd
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# 1.2 Visualiseer uw eigen Real-time profiel van de Klant - UI

In deze oefening, zult u login aan Adobe Experience Platform en uw eigen Profiel van de Klant in real time in UI bekijken.

## Artikel

In het profiel van de Klant in real time, worden alle profielgegevens getoond naast gebeurtenisgegevens, evenals bestaande segmentlidmaatschap. De getoonde gegevens kunnen van overal, van de toepassingen van Adobe en externe oplossingen komen. Dit is de krachtigste weergave in Adobe Experience Platform, het echte ervaringssysteem van record.

## 1.2.1 De weergave Klantprofiel in Adobe Experience Platform gebruiken

Ga naar [Adobe Experience Platform](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![Gegevensinname](./images/home.png)

Voordat u verdergaat, moet u een **sandbox**. De sandbox die moet worden geselecteerd, krijgt een naam ``Bootcamp``. U kunt dit doen door op de tekst te klikken **[!UICONTROL Productieproduct]** in de blauwe lijn boven op het scherm. Nadat u de juiste [!UICONTROL sandbox], ziet u de schermwijziging en nu bent u in uw eigen omgeving [!UICONTROL sandbox].

![Gegevensinname](./images/sb1.png)

Ga in het linkermenu naar **Profielen** en **Bladeren**.

![Klantprofiel](./images/homemenu.png)

In het deelvenster Profielviewer op uw website vindt u het identiteitsoverzicht. Elke identiteit is gekoppeld aan een naamruimte.

![Klantprofiel](./images/identities.png)

In het deelvenster Profielviewer kunt u deze identiteit momenteel zien:

| Naamruimte | Identiteit |
|:-------------:| :---------------:|
| Experience Cloud ID (ECID) | 19428085896177382402834560825640259081 |

In Adobe Experience Platform zijn alle id&#39;s even belangrijk. Voorheen was de ECID de belangrijkste id in de context van Adobe en alle andere id&#39;s waren hiërarchisch gekoppeld aan de ECID. In Adobe Experience Platform is dit niet langer het geval en kan elke id als een primaire id worden beschouwd.

Doorgaans is de primaire id afhankelijk van de context. Als u uw Centrum van de Vraag vraagt, **Wat is de belangrijkste ID?** zij zullen waarschijnlijk antwoorden , **het telefoonnummer!** Maar als u uw team van CRM vraagt, zullen zij antwoorden, **Het e-mailadres!**  Adobe Experience Platform begrijpt deze complexiteit en beheert deze voor u. Elke toepassing, of een toepassing van de Adobe of niet-Adobe, zal met Adobe Experience Platform spreken door te verwijzen naar identiteitskaart zij primair beschouwen. Het werkt gewoon.

Voor het veld **Naamruimte identiteit**, selecteert u **ECID** en voor het veld **Identiteitswaarde** Voer de ECID in die u kunt vinden in het deelvenster Profielviewer van de bootcampingwebsite. Klikken **Weergave**. Vervolgens ziet u uw profiel in de lijst. Klik op de knop **Profiel-id** om uw profiel te openen.

![Klantprofiel](./images/popupecid.png)

U ziet nu een overzicht van een paar belangrijke **Profielkenmerken** van uw klantprofiel.

![Klantprofiel](./images/profile.png)

Ga naar **Gebeurtenissen**, waar u ingangen voor elke ervaringsgebeurtenis kunt zien die met uw Profiel wordt verbonden.

![Klantprofiel](./images/profileee.png)

Tot slot ga naar de menuoptie **Segmentlidmaatschap**. U ziet nu alle segmenten die in aanmerking komen voor dit profiel.

![Klantprofiel](./images/profileseg.png)

Laten wij nu een nieuw segment tot stand brengen dat u zal toestaan om de klantenervaring voor een anonieme of bekende klant te personaliseren.

Volgende stap: [1.3 Een segment maken - UI](./ex3.md)

[Ga terug naar gebruikersstroom 1](./uc1.md)

[Terug naar alle modules](../../overview.md)
