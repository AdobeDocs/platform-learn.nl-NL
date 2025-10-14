---
title: Een reis configureren met pushberichten
description: Een reis configureren met pushberichten
kt: 5342
doc-type: tutorial
exl-id: 63d7ee24-b6b5-4503-b104-a345c2b26960
source-git-commit: fb14ba45333bdd5834ff0c6c2dc48dda35cfe85f
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 0%

---

# 3.3.2 Vorm een reis met dupberichten

Login aan Adobe Journey Optimizer door naar [&#x200B; Adobe Experience Cloud &#x200B;](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![&#x200B; ACOP &#x200B;](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

U zult aan de **1&rbrace; mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. U zult dan in de **1} mening van het Huis &lbrace;van uw zandbak** zijn.`--aepSandboxName--`

![&#x200B; ACOP &#x200B;](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

## 3.3.2.1 Een nieuwe gebeurtenis maken

In het linkermenu, ga naar **Configuraties** en klik **leiden** onder **Gebeurtenissen**.

![&#x200B; ACOP &#x200B;](./images/acopmenu.png)

Op het **scherm van Gebeurtenissen**, zult u een mening gelijkend op dit zien. Klik **creëren Gebeurtenis**.

![&#x200B; ACOP &#x200B;](./images/add.png)

U ziet dan een lege gebeurtenisconfiguratie.
Geef uw gebeurtenis eerst een naam zoals deze: `--aepUserLdap--StoreEntryEvent` en stel een beschrijving in op `Store Entry Event` .
Daarna is het **Type van Gebeurtenis** selectie. Selecteer **Eenheids**.
Daarna is het **selecteren van het Type van identiteitskaart van de Gebeurtenis 0&rbrace;.** Selecteer **Gegenereerd Systeem**.

![&#x200B; ACOP &#x200B;](./images/eventname.png)

Nu de selectie van het schema. Hiervoor is een schema opgesteld. Gebruik het schema `Demo System - Event Schema for Mobile App (Global v1.1) v.1` .

Na het selecteren van het Schema, zult u een aantal gebieden zien die in de **sectie van de Lading** worden geselecteerd. Verifieer dat het gebied **Namespace** aan **ECID** wordt geplaatst. Uw gebeurtenis is nu volledig geconfigureerd.

Klik **sparen**.

![&#x200B; ACOP &#x200B;](./images/eventschema.png)

Uw gebeurtenis is nu geconfigureerd en opgeslagen. Klik opnieuw op uw gebeurtenis om **te openen geef het 1&rbrace; scherm van de Gebeurtenis &lbrace;opnieuw uit.**

![&#x200B; ACOP &#x200B;](./images/eventdone.png)

Beweeg over het **gebied van de Payload** en klik op het **3&rbrace; pictogram van de Payload van de Mening &lbrace;.**

![&#x200B; ACOP &#x200B;](./images/hover.png)

U zult nu een voorbeeld van de verwachte nuttige lading zien.

Uw gebeurtenis heeft een unieke orchestration eventID, die u kunt vinden door neer in die lading te scrollen tot u `_experience.campaign.orchestration.eventID` ziet.

De gebeurtenis-id is wat naar Adobe Experience Platform moet worden verzonden om de Reis te activeren die u in de volgende stap maakt. Schrijf deze eventID neer, aangezien u het in de volgende stap zult nodig hebben.
`"eventID": "aa895251f76831e6440f169f1bb9d2a4388f0696d8e2782cfab192a275817dfa"`

Klik **OK**.

![&#x200B; ACOP &#x200B;](./images/payloadeventID.png)

Klik **annuleren**.

![&#x200B; ACOP &#x200B;](./images/payloadeventIDa.png)

## 3.3.2.2 Een reis maken

In het linkermenu, ga naar **Reizen** en klik **creeer Weg**.

![&#x200B; DSN &#x200B;](./images/sjourney1.png)

Dan zie je dit. Geef uw reis een naam: `--aepUserLdap-- - Store Entry journey`. Klik **sparen**.

![&#x200B; DSN &#x200B;](./images/sjourney3.png)

Eerst, moet u uw gebeurtenis toevoegen als uitgangspunt van uw reis. Zoek de gebeurtenis `--aepUserLdap--StoreEntryEvent` en sleep deze naar het canvas. Klik **sparen**.

![&#x200B; DSN &#x200B;](./images/sjourney4.png)

Daarna, onder **Acties**, onderzoek naar de **Duw** actie. De belemmering en laat vallen **duw** actie op het canvas.

Plaats de **Categorie** aan **Marketing** en selecteer een drukkend oppervlak dat u toelaat om pushberichten te verzenden. In dit geval, is de e-mailoppervlakte om te selecteren **duw-iOS-Android**.

>[!NOTE]
>
>Een Kanaal in Journey Optimizer moet bestaan dat de **Oppervlakte van de App** zoals eerder herzien gebruikt.

![&#x200B; ACOP &#x200B;](./images/journeyactions1push.png)

De volgende stap is uw bericht te creëren. Om dat te doen, klik **geef inhoud** uit.

![&#x200B; ACOP &#x200B;](./images/journeyactions2push.png)

Dan zie je dit. Klik het **verpersoonlijkings** pictogram voor het **gebied van de Titel**.

![&#x200B; Duw &#x200B;](./images/bp5.png)

Dan zie je dit. U kunt nu om het even welk profielattribuut van het Profiel van de Klant in real time direct selecteren.

Onderzoek naar het gebied **Voornaam**, dan klik het **+** pictogram naast het gebied **Voornaam**. Vervolgens ziet u het personalisatietoken voor Voornaam die wordt toegevoegd: **{{profile.person.name.firstName}}** .

![&#x200B; Duw &#x200B;](./images/bp9.png)

Voeg vervolgens de tekst **toe, welkom in onze winkel!** behind **{{profile.person.name.firstName}}** .

Klik **sparen**.

![&#x200B; Duw &#x200B;](./images/bp10.png)

U hebt dit nu. Klik het **verpersoonlijkings** pictogram voor het **3&rbrace; gebied van het Lichaam &lbrace;.**

![&#x200B; Duw &#x200B;](./images/bp11.png)

Ga deze tekst **in Klik hier om een 10% korting te krijgen wanneer u vandaag koopt!** en klik **sparen**.

![&#x200B; Duw &#x200B;](./images/bp12.png)

Dan heb je dit. Klik op de pijl in de linkerbovenhoek om terug te gaan naar uw reis.

![&#x200B; Journey Optimizer &#x200B;](./images/bp12a.png)

Klik **sparen** om uw duwactie te sluiten.

![&#x200B; DSN &#x200B;](./images/sjourney8.png)

Klik **publiceren**.

![&#x200B; DSN &#x200B;](./images/sjourney10.png)

Klik **publiceren** opnieuw.

![&#x200B; DSN &#x200B;](./images/sjourney10a.png)

Uw reis is nu gepubliceerd.

![&#x200B; DSN &#x200B;](./images/sjourney11.png)

## 3.3.2.3 De eigenschap voor gegevensverzameling bijwerken voor mobiele apparaten

In **Aan de slag**, leidde het Systeem van de Demo daarna tot de eigenschappen van Markeringen voor u: voor de website en voor mobiele app. Vind hen door `--aepUserLdap--` in het **vakje van het Onderzoek** te zoeken. Klik om het **Mobiele** bezit te openen.

![&#x200B; DSN &#x200B;](./images/pushpoi1.png)

Dan moet je dit zien.

![&#x200B; DSN &#x200B;](./images/pushpoi2.png)

In het linkermenu, ga naar **Regels** en klik om de ingang van de regel **Plaats** te openen.

![&#x200B; DSN &#x200B;](./images/pushpoi3.png)

Dan moet je dit zien. Klik de actie **Mobiele Kern - Verbind Gegevens**.

![&#x200B; DSN &#x200B;](./images/pushpoi4.png)

Dan moet je dit zien.

![&#x200B; DSN &#x200B;](./images/pushpoi5.png)

Plak eventID van uw gebeurtenis `--aepUserLdap--StoreEntryEvent` in het **JSON 2&rbrace; venster van de Payload.** Klik **houden Veranderingen**.

![&#x200B; DSN &#x200B;](./images/pushpoi6.png)

Klik **sparen** of **sparen aan Bibliotheek**.

![&#x200B; DSN &#x200B;](./images/pushpoi7.png)

Ga naar **het Publiceren Stroom** en klik om de bibliotheek **Hoofd** te openen.

![&#x200B; DSN &#x200B;](./images/pushpoi8.png)

Klik **toevoegen Alle Gewijzigde Middelen** en klik dan **sparen &amp; bouwen aan Ontwikkeling**.

![&#x200B; DSN &#x200B;](./images/pushpoi9.png)

## 3.3.2.4 Test uw reis en pushbericht

Open de **mobiele DSN** toepassing.

![&#x200B; DSN &#x200B;](./images/dxdemo1.png)

Ga naar de **pagina van het Merkteken van de Opslag 0&rbrace;.**

![&#x200B; DSN &#x200B;](./images/dxdemo2.png)

Klik **de Ingang van POI simuleren**.

![&#x200B; DSN &#x200B;](./images/dxdemo3.png)

Na een paar seconden ziet u de pushmelding verschijnen.

![&#x200B; DSN &#x200B;](./images/dxdemo4.png)

## Volgende stappen

Ga naar [&#x200B; 3.3.3 vormen een campagne met in-app berichten &#x200B;](./ex3.md){target="_blank"}

Ga terug naar [&#x200B; Adobe Journey Optimizer: Duw en In-app Berichten &#x200B;](ajopushinapp.md){target="_blank"}

Ga terug naar [&#x200B; Alle modules &#x200B;](./../../../../overview.md){target="_blank"}