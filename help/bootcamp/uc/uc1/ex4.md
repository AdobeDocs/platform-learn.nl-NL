---
title: Bootkamp - Real-time CDP - Bouw een publiek en neem actie - verzend uw publiek naar Adobe Target
description: Bootkamp - Real-time CDP - Bouw een publiek en neem actie - verzend uw publiek naar Adobe Target
jira: KT-5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
solution: Experience Platform, Target
feature: Audiences, Integrations
exl-id: 6a76c2ab-96b7-4626-a6d3-afd555220b1e
source-git-commit: 5876de5015e4c8c337c235c24cc28b0a32e274dd
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# 1.4 Actie nemen: stuur je publiek naar Adobe Target

Ga naar [Adobe Experience Platform](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![Gegevensinname](./images/home.png)

Voordat u verdergaat, moet u een **sandbox**. De sandbox die moet worden geselecteerd, krijgt een naam ``Bootcamp``. U kunt dit doen door op de tekst te klikken **[!UICONTROL Production Prod]** in de blauwe lijn boven op het scherm. Nadat u de juiste [!UICONTROL sandbox], ziet u de schermwijziging en nu bent u in uw eigen omgeving [!UICONTROL sandbox].

![Gegevensinname](./images/sb1.png)

## 1.4.1 Activeer je publiek naar de Adobe Target-bestemming

Adobe Target is beschikbaar als een bestemming vanuit Real-Time CDP. Ga naar **Doelen**, naar **Catalogus**.

Klikken **Personalisatie** in de **Categorieën** -menu. Dan zie je de **Adobe Target** doelkaart. Klikken **Soorten publiek activeren**.

![AT](./images/atdest1.png)

Het doel selecteren ``Bootcamp Target`` en klik op **Volgende**.

![AT](./images/atdest3.png)

Selecteer in de lijst met beschikbare doelgroepen het publiek dat u hebt gemaakt in [1.3 Een publiek maken](./ex3.md), die `yourLastName - Interest in Real-Time CDP`. Klik vervolgens op **Volgende**.

![AT](./images/atdest8.png)

Klik op de volgende pagina op **Volgende**.

![AT](./images/atdest9.png)

Klikken **Voltooien**.

![AT](./images/atdest10.png)

Uw publiek wordt nu geactiveerd voor Adobe Target.

![AT](./images/atdest11.png)

>[!IMPORTANT]
>
>Als je net je Adobe Target-bestemming hebt gemaakt in Real-Time CDP, kan het tot een uur duren voordat de bestemming live is. Dit is eenmalig wachttijd, wegens de opstelling van de backendconfiguratie. Zodra de aanvankelijke 1 uur wachttijd en de backendconfiguratie wordt gedaan, zal het onlangs toegevoegde randpubliek dat naar de bestemming van Adobe Target wordt verzonden voor richten in real time beschikbaar zijn.

## 1.4.2 Configureer uw Adobe Target-formuliergebaseerde activiteit

Nu uw Real-Time CDP-publiek is geconfigureerd om naar Adobe Target te worden verzonden, kunt u uw Experience Targeting-activiteit in Adobe Target configureren. In deze oefening zult u een Visuele op Composer-Gebaseerde activiteit van de Ervaring vormen.

Ga naar de Adobe Experience Cloud-homepage door naar [https://experiencecloud.adobe.com/](https://experiencecloud.adobe.com/). Klikken **Doel** om het te openen.

![RTCDP](./images/excl.png)

Op de **Adobe Target** homepage, zult u alle bestaande Activiteiten zien.
Klikken **+ Activiteit maken** om een nieuwe Activiteit te creëren.

![RTCDP](./images/exclatov.png)

Selecteren **Gericht op ervaring**.

![RTCDP](./images/exclatcrxt.png)

Selecteren **Zichtbaar** en stelt de **URL van activiteit** tot `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpantXX.html`Maar voordat u dat doet, vervangt u XX door een getal tussen 01 en 30.

>[!IMPORTANT]
>
>Elke deelnemer aan het activering moet een aparte webpagina gebruiken om botsing met verschillende Adobe Target-ervaringen te voorkomen. U kunt een webpagina kiezen en de URL vinden door hier te gaan: [https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html).
>
>Pagina&#39;s delen allemaal dezelfde basis-URL en eindigen op het nummer van de deelnemer.
>
>Als voorbeeld zou deelnemer 1 URL moeten gebruiken `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant01.html`, deelnemer 30 de URL moet gebruiken `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant30.html`.

De werkruimte selecteren **AT Bootkamp**.

Klik op **Next**.

![RTCDP](./images/exclatcrxtdtlform.png)

U bent nu in de Composer van de Visuele Ervaring. Het kan 20-30 seconden duren totdat de website volledig is geladen.

![RTCDP](./images/atform1.png)

Het standaardpubliek is momenteel **Alle bezoekers**. Klik op de knop **3 punten** naast **Alle bezoekers** en klik op **Publiek wijzigen**.

![RTCDP](./images/atform3.png)

U ziet nu de lijst met beschikbare soorten publiek. Het Adobe Experience Platform-publiek dat u eerder hebt gemaakt en naar Adobe Target hebt verzonden, maakt nu deel uit van deze lijst. Selecteer het publiek dat u eerder in Adobe Experience Platform hebt gemaakt. Klikken **Publiek toewijzen**.

![RTCDP](./images/exclatvecchaud.png)

Uw Adobe Experience Platform-publiek maakt nu deel uit van deze Experience Targeting Activity.

![RTCDP](./images/atform4.png)

Voordat u de hoofdafbeelding kunt wijzigen, moet u eerst op **Alles toestaan** op de cookiebanner.

Ga hiertoe naar **Bladeren**

![RTCDP](./images/cook1.png)

Klik op Volgende **Alles toestaan**.

![RTCDP](./images/cook2.png)

Ga vervolgens terug naar **Samenstellen**.

![RTCDP](./images/cook3.png)

Laten we nu de hoofdafbeelding veranderen op de homepage van de website. Klik op de standaardhoofdafbeelding op de website en klik op **Inhoud vervangen** en selecteer vervolgens **Afbeelding**.

![RTCDP](./images/atform5.png)

Zoeken naar het afbeeldingsbestand **rtcdp.png**. Selecteer het en klik vervolgens op **Opslaan**.

![RTCDP](./images/atform6.png)

U zult dan de nieuwe ervaring met het nieuwe beeld, voor uw geselecteerd Publiek zien.

![RTCDP](./images/atform7.png)

Klik op de titel van uw activiteit in de linkerbovenhoek om de naam ervan te wijzigen.

![RTCDP](./images/exclatvecname.png)

Gebruik voor de naam:

- `yourLastName - RTCDP - XT (VEC)`

Klik op **Next**.

![RTCDP](./images/atform8.png)

Klik op **Next**.

![RTCDP](./images/atform8a.png)

Op de **Doelstellingen en instellingen** - pagina, ga naar **Goederenstatistieken**.

![RTCDP](./images/atform9.png)

Het primaire doel instellen op **Betrokkenheid** - **Tijd op de site**. Klikken **Opslaan en sluiten**.

![RTCDP](./images/vec3.png)

Je bent nu op de **Overzicht van activiteiten** pagina. U moet uw activiteit nog activeren.

![RTCDP](./images/atform10.png)

Klik in het veld **Inactief** en selecteert u **Activeren**.

![RTCDP](./images/atform11.png)

Je krijgt dan een visuele bevestiging dat je activiteit nu actief is.

![RTCDP](./images/atform12.png)

Uw activiteiten zijn nu live en kunnen worden getest op de website van het bootkamp.

Als u nu teruggaat naar uw demo-website en de productpagina bezoekt voor **Real-Time CDP** U komt dan meteen in aanmerking voor het publiek dat u hebt gemaakt en u ziet dat de Adobe Target-activiteit in real-time wordt weergegeven op de homepage.

>[!IMPORTANT]
>
>Elke deelnemer aan het activering moet een aparte webpagina gebruiken om botsing met verschillende Adobe Target-ervaringen te voorkomen. U kunt een webpagina kiezen en de URL vinden door hier te gaan: [https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html](https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises.html).
>
>Pagina&#39;s delen allemaal dezelfde basis-URL en eindigen op het nummer van de deelnemer.
>
>Als voorbeeld zou deelnemer 1 URL moeten gebruiken `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant01.html`, deelnemer 30 de URL moet gebruiken `https://bootcamp.aepdemo.net/content/aep-bootcamp-experience/language-masters/en/exercises/particpant30.html`.

![RTCDP](./images/atform12a.png)

Volgende stap: [1.5 Actie nemen: stuur je publiek naar Facebook](./ex5.md)

[Ga terug naar gebruikersstroom 1](./uc1.md)

[Terug naar alle modules](../../overview.md)
