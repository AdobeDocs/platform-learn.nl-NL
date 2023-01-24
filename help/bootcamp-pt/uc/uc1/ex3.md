---
title: Bootkamp - Real-time klantprofiel - Een segment maken - UI - Brazilië
description: Bootkamp - Real-time klantprofiel - Een segment maken - UI - Brazilië
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
source-git-commit: 75a878ba596078e6d013b65062606931402302dd
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 2%

---

# 1.3 Een segment maken - UI

In deze oefening, zult u een segment tot stand brengen door gebruik van de Bouwer van het Segment van Adobe Experience Platform te maken.

## Artikel

Ga naar [Adobe Experience Platform](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![Gegevensinname](./images/home.png)

Voordat u verdergaat, moet u een **sandbox**. De sandbox die moet worden geselecteerd, krijgt een naam ``Bootcamp``. U kunt dit doen door op de tekst te klikken **[!UICONTROL Productieproduct]** in de blauwe lijn boven op het scherm. Nadat u de juiste [!UICONTROL sandbox], ziet u de schermwijziging en nu bent u in uw eigen omgeving [!UICONTROL sandbox].

![Gegevensinname](./images/sb1.png)

Ga in het menu aan de linkerkant naar **Segmenten**. Op deze pagina ziet u een overzicht van alle bestaande segmenten. Klik op de knop **+ Segment maken** om een nieuw segment te maken.

![Segmentering](./images/menuseg.png)

Zodra u in de nieuwe segmentbouwer bent, merkt u onmiddellijk **Attributen** en de **Afzonderlijk XDM-profiel** referentie.

![Segmentering](./images/segmentationui.png)

Aangezien XDM de taal is die de ervaringszaken macht, is XDM ook de stichting voor de segmentbouwer. Alle gegevens die in Platform worden opgenomen, moeten tegen XDM worden toegewezen en als zodanig, worden alle gegevens deel van het zelfde gegevensmodel ongeacht waar die gegevens uit komen. Dit geeft u een groot voordeel wanneer het bouwen van segmenten, zoals van deze één segment bouwer UI, kunt u gegevens van om het even welke oorsprong in het zelfde werkschema combineren. Segmenten die in Segment Builder zijn gemaakt, kunnen voor activering naar oplossingen als Adobe Target, Adobe Campaign en Adobe Audience Manager worden verzonden.

U moet nu een segment tot stand brengen van alle klanten die het product hebben bekeken **Real-Time CDP**.

Om dit segment te bouwen, moet u een Gebeurtenis van de Ervaring toevoegen. U kunt alle Experience Events vinden door op **Gebeurtenissen** in het deelvenster **Velden** menubalk.

![Segmentering](./images/findee.png)

Vervolgens ziet u het hoogste niveau, **XDM ExperienceEvents** knooppunt. Klikken op **XDM ExperienceEvent**.

![Segmentering](./images/see.png)

Ga naar **Objecten in de productlijst**.

![Segmentering](./images/plitems.png)

Selecteren **Naam** en sleep de **Naam** object van het linkermenu naar het gesegmenteerde buildercanvas **Gebeurtenissen** sectie. U zult dan dit zien:

![Segmentering](./images/eewebpdtlname.png)

De vergelijkingsparameter moet **equals** en in het invoerveld typt u **Real-time CDP**.

![Segmentering](./images/pv.png)

Telkens als u een element aan de segmentbouwer toevoegt, kunt u klikken **Offerte vernieuwen** om een nieuwe schatting van de bevolking in uw segment te krijgen.

![Segmentering](./images/refreshest.png)

Als **Evaluatiemethode**, selecteert u **Rand**.

![Segmentering](./images/evedge.png)

Tot slot geven wij uw segment een naam en bewaren het.

Gebruik als naamgevingsconventie:

- `yourLastName - Interest in Real-Time CDP`

Klik vervolgens op de knop **Opslaan en sluiten** om uw segment op te slaan.

![Segmentering](./images/segmentname.png)

U zult nu aan de pagina van het segmentoverzicht worden teruggenomen, waar u een steekproefvoorproef van klantenprofielen zult zien die voor uw segment kwalificeren.

![Segmentering](./images/savedsegment.png)

U kunt nu doorgaan met de volgende oefening en uw segment gebruiken met Adobe Target.

Volgende stap: [1.4 Actie ondernemen: Uw segment verzenden naar Adobe Target](./ex4.md)

[Ga terug naar gebruikersstroom 1](./uc1.md)

[Terug naar alle modules](../../overview.md)
