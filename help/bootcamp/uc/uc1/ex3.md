---
title: Bootkamp - Real-time klantprofiel - Een publiek maken - UI
description: Bootkamp - Real-time klantprofiel - Een publiek maken - UI
jira: KT-5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
feature: Audiences
exl-id: 37d4a5e8-e2bc-4c8c-a74f-09f74ea79962
source-git-commit: 5876de5015e4c8c337c235c24cc28b0a32e274dd
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 2%

---

# 1.3 Een publiek maken - UI

In deze oefening, zult u een publiek creëren door gebruik van de Bouwer van het Publiek van Adobe Experience Platform te maken.

## Artikel

Ga naar [&#x200B; Adobe Experience Platform &#x200B;](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![&#x200B; Ingestie van Gegevens &#x200B;](./images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``Bootcamp`` . U kunt dit doen door op de tekst **[!UICONTROL Production Prod]** in de blauwe lijn boven op het scherm te klikken. Nadat u de juiste [!UICONTROL sandbox] hebt geselecteerd, ziet u de schermwijziging en nu bevindt u zich in uw toegewezen [!UICONTROL sandbox] .

![&#x200B; Ingestie van Gegevens &#x200B;](./images/sb1.png)

In het menu op de linkerkant, ga naar **Soorten publiek**. Op deze pagina, zult u dashboards met essentiële informatie over **publiek** prestaties zien.

![Segmentatie](./images/menuseg.png)

Klik op **doorbladeren** om een overzicht van alle bestaande soorten publiek te zien. Klik op **+ creeer publiek** knoop om een nieuw publiek te beginnen creëren.


![Segmentatie](./images/segmentationui.png)

Pop-IP zal verschijnen dat u zal vragen of u **&quot;publiek&quot;wilt samenstellen** of **&quot;regel van de Bouwstijl&quot;**. Kies **&quot;bouwt regel&quot;** om verder te gaan en **te klikken creeert**.

![Segmentatie][def]

Zodra u in de publieksbouwer bent, merkt u onmiddellijk de **het menuoptie van Attributen** en de **Individuele verwijzing van het Profiel XDM**.


Aangezien XDM de taal is die de ervaringszaken macht, is XDM ook de stichting voor de publieksbouwer. Alle gegevens die in Platform worden opgenomen, moeten tegen XDM worden toegewezen en als zodanig, worden alle gegevens deel van het zelfde gegevensmodel ongeacht waar die gegevens uit komen. Dit geeft u een groot voordeel wanneer het bouwen van publiek, zoals van deze één kijkbouwer UI, kunt u gegevens van om het even welke oorsprong in het zelfde werkschema combineren. Soorten publiek dat is gemaakt in de Audience Builder kunnen worden verzonden naar oplossingen zoals Adobe Target, Adobe Campaign of een ander activeringskanaal.

U moet nu een publiek van alle klanten tot stand brengen die het product **Real-Time CDP** hebben bekeken.

U moet een Experience Event toevoegen om dit publiek op te bouwen. U kunt alle Gebeurtenissen van de Ervaring vinden door op het **pictogram van Gebeurtenissen** in de **Gebieden** menubar te klikken.

![Segmentatie](./images/findee.png)

Daarna, zult u de top-level, **XDM ExperienceEvents** knoop zien. Klik op **XDM ExperienceEvent**.

![Segmentatie](./images/see.png)

Ga naar **Punten van de Lijst van het Product**.

![Segmentatie](./images/plitems.png)

Selecteer **Naam** en sleep en laat vallen het **voorwerp van de Naam** van het linkermenu op het canvas van de publieksbouwer in de **&#x200B;**&#x200B;sectie van Gebeurtenissen. U zult dan dit zien:

![Segmentatie](./images/eewebpdtlname.png)

De vergelijkingsparameter zou **gelijken** moeten zijn en op het inputgebied, ga **in real time CDP**.

![Segmentatie](./images/pv.png)

Telkens als u een element aan de publieksbouwer toevoegt, kunt u **klikken verfrist Schatting** knoop om een nieuwe schatting van de bevolking in uw publiek te krijgen.

![Segmentatie](./images/refreshest.png)

Als **Methode van de Evaluatie**, uitgezochte **Edge**.

![Segmentatie](./images/evedge.png)

Tot slot geven wij uw publiek een naam en bewaren het.

Gebruik als naamgevingsconventie:

- `yourLastName - Interest in Real-Time CDP`

Dan, klik **sparen en sluit** knoop om uw publiek te bewaren.

![Segmentatie](./images/segmentname.png)

U gaat nu terug naar de overzichtspagina van het publiek, waar u een voorbeeldvoorproef van klantenprofielen zult zien die voor uw publiek kwalificeren.

![Segmentatie](./images/savedsegment.png)

U kunt nu doorgaan met de volgende oefening en uw publiek gebruiken met Adobe Target.

Volgende Stap: [&#x200B; 1.4 Actie nemen: verzend uw publiek naar Adobe Target &#x200B;](./ex4.md)

[Ga terug naar gebruikersstroom 1](./uc1.md)

[Terug naar alle modules](../../overview.md)


[def]: ./images/segmentationpopup.png
