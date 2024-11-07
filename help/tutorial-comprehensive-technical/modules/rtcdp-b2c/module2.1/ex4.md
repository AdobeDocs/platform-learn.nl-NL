---
title: Foundation - Real-time klantprofiel - Een segment maken - UI
description: Foundation - Real-time klantprofiel - Een segment maken - UI
kt: 5342
doc-type: tutorial
source-git-commit: 6962a0d37d375e751a05ae99b4f433b0283835d0
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 2%

---

# 2.1.4 Een segment maken - UI

In deze oefening, zult u een segment tot stand brengen door gebruik van de Bouwer van het Segment van Adobe Experience Platform te maken.

## Artikel

Ga naar [ Adobe Experience Platform ](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxName--`` . U kunt dit doen door op de tekst **[!UICONTROL Production Prod]** in de blauwe lijn boven op het scherm te klikken. Nadat u de juiste [!UICONTROL sandbox] hebt geselecteerd, ziet u de schermwijziging en nu bevindt u zich in uw toegewezen [!UICONTROL sandbox] .

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/sb1.png)

In het menu op de linkerkant, ga naar **Segmenten**. Op deze pagina ziet u een overzicht van alle bestaande segmenten. Klik op de knop **+ Segment maken** om een nieuw segment te maken.

![Segmentatie](./images/menuseg.png)

Zodra u in de nieuwe segmentbouwer bent, merkt u onmiddellijk de **het menuoptie van Attributen** en de **Individuele verwijzing van het Profiel XDM**.

![Segmentatie](./images/segmentationui.png)

Aangezien XDM de taal is die de ervaringszaken macht, is XDM ook de stichting voor de segmentbouwer. Alle gegevens die in Platform worden opgenomen, moeten tegen XDM worden toegewezen en als zodanig, worden alle gegevens deel van het zelfde gegevensmodel ongeacht waar die gegevens uit komen. Dit geeft u een groot voordeel wanneer het bouwen van segmenten, zoals van deze één segment bouwer UI, kunt u gegevens van om het even welke oorsprong in het zelfde werkschema combineren. Segmenten die in Segment Builder zijn gemaakt, kunnen voor activering naar oplossingen als Adobe Target, Adobe Campaign en Adobe Audience Manager worden verzonden.

Laten wij een segment bouwen dat alle **mannelijke** klanten omvat.

Om aan het genderattribuut te krijgen, moet u XDM begrijpen en kennen.

Gender is een kenmerk van Person, dat te vinden is onder Kenmerken. Zo om daar te krijgen, zult u beginnen door op **te klikken individueel Profiel XDM**. Dan zie je dit. Van het **individuele venster van het Profiel XDM**, uitgezochte **Persoon**.

![Segmentatie](./images/person.png)

Dan zie je dit. In **Persoon**, kunt u het **3} attribuut van het Geslacht {vinden.** Sleep het attribuut Gender op de segmentbouwer.

![Segmentatie](./images/gender.png)

Nu kunt u het specifieke geslacht kiezen uit de vooraf ingevulde opties. In dit geval, laten wij **Mannelijke** kiezen.

![Segmentatie](./images/genderselection.png)

Na het selecteren van **Mannelijke**, kunt u een schatting van de bevolking van het segment krijgen door **te duwen verfrissen Schatting** knoop. Dit is zeer nuttig voor een bedrijfsgebruiker, zodat zij het effect van bepaalde attributen op de resulterende segmentgrootte kunnen zien.

![Segmentatie](./images/segmentpreview.png)

Hieronder ziet u een schatting:

![Segmentatie](./images/segmentpreviewest.png)

Daarna, zou u uw segment een beetje moeten verfijnen. U moet een segment van alle mannelijke klanten opbouwen die het product **(Oranje) jasje van de Fitness van de Proteus** hebben bekeken.

Om dit segment te bouwen, moet u een Gebeurtenis van de Ervaring toevoegen. U kunt alle Gebeurtenissen van de Ervaring vinden door op het **pictogram van Gebeurtenissen** in de **Gebieden** menubar te klikken.

![Segmentatie](./images/findee.png)

Daarna, zult u de top-level, **XDM ExperienceEvents** knoop zien. Klik op **XDM ExperienceEvent**.

![Segmentatie](./images/see.png)

Ga naar **Punten van de Lijst van het Product**.

![Segmentatie](./images/plitems.png)

Selecteer **Naam** en belemmering en laat vallen het **voorwerp van de Naam** van het linkermenu op het canvas van de segmentbouwer in de **** sectie van Gebeurtenissen.

![Segmentatie](./images/eeweb.png)

U zult dan dit zien:

![Segmentatie](./images/eewebpdtlname.png)

De vergelijkingsparameter zou **gelijken** moeten zijn en op het inputgebied, gaat **MONTANA WINT JACKET** in.

![Segmentatie](./images/pv.png)

Telkens als u een element aan de segmentbouwer toevoegt, kunt u **klikken verfrist schatten** knoop om een nieuwe schatting van de bevolking in uw segment te krijgen.

Tot dusver, hebt u slechts UI gebruikt om uw segment te bouwen, maar er is ook een code-optie om een segment te bouwen.

Wanneer u een segment maakt, stelt u een Profile Query Language-query (PQL) samen. Om de code van PQL te visualiseren, kunt u op de **schakelaar van de Mening van de Code** in de hogere juiste hoek van de segmentbouwer klikken.

![Segmentatie](./images/codeview.png)

Nu kunt u de volledige PQL-verklaring zien:

```sql
person.gender in ["male"] and CHAIN(xEvent, timestamp, [C0: WHAT(productListItems.exists(name.equals("MONTANA WIND JACKET", false)))])
```

U kunt een steekproef van de klantenprofielen ook voorproef die deel van dit segment uitmaken, door op **Profielen van de Mening** te klikken.

![Segmentatie](./images/previewprofiles.png)

![Segmentatie](./images/previewprofilesdtl.png)

Tot slot geven wij uw segment een naam en bewaren het.

Gebruik als naamgevingsconventie:

- `--aepUserLdap-- - Male customers with interest in Montana Wind Jacket`

![Segmentatie](./images/segmentname.png)

Dan, klik **sparen en sluit** knoop om uw segment te bewaren, waarna u terug naar de het overzichtspagina van het Segment zult worden genomen.

![Segmentatie](./images/savedsegment.png)

U kunt nu doorgaan met de volgende oefening en een segment maken via de API.

Volgende Stap: [ 2.1.5 leidt tot een segment - API ](./ex5.md)

[Terug naar module 2.1](./real-time-customer-profile.md)

[Terug naar alle modules](../../../overview.md)
