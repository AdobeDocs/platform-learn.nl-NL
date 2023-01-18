---
title: Bootamp - Journey Optimizer Uw gebeurtenis maken
description: Bootamp - Journey Optimizer Uw gebeurtenis maken
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
exl-id: 89db40ab-d4c5-4310-aca6-cb64828e7bc9
source-git-commit: ead28f5631fc430c41e8c756b23dc69ffe19510e
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# 2.2 Uw gebeurtenis maken

Aanmelden bij Adobe Journey Optimizer door naar [Adobe Experience Cloud](https://experience.adobe.com). Klikken **Journey Optimizer**.

![ACOP](./images/acophome.png)

U wordt omgeleid naar de **Home**  in Journey Optimizer. Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `Bootcamp`. Als u van de ene naar de andere sandbox wilt gaan, klikt u op **Prod** en selecteert u de sandbox in de lijst. In dit voorbeeld krijgt de sandbox een naam **Bootkamp**. Dan ben je in de **Home** weergave van de sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

Blader in het linkermenu omlaag en klik op **Configuraties**. Klik op de knop **Beheren** knop onder **Gebeurtenissen**.

![ACOP](./images/acopmenu.png)

Vervolgens ziet u een overzicht van alle beschikbare gebeurtenissen. Klikken **Gebeurtenis maken** om uw eigen gebeurtenis te maken.

![ACOP](./images/emptyevent.png)

Er verschijnt dan een nieuw, leeg gebeurtenisvenster.

![ACOP](./images/emptyevent1.png)

Geef uw gebeurtenis als volgt een naam: `yourLastNameAccountCreationEvent` en voeg een dergelijke beschrijving toe `Account Creation Event`.

![ACOP](./images/eventdescription.png)

Controleer vervolgens of de **Type** is ingesteld op **Unitair** en voor de **Type gebeurtenis-id** selectie, selecteren **Door systeem gegenereerd**.

![ACOP](./images/eventidtype.png)

Nu de selectie van het schema. Hiervoor is een schema opgesteld. Gebruik het schema `Demo System - Event Schema for Website (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

Nadat u het schema hebt geselecteerd, ziet u een aantal velden die worden geselecteerd in het dialoogvenster **Velden** sectie. U moet nu de muisaanwijzer op de knop **Velden** en u ziet 3 pictogrammen verschijnen. Klik op de knop **Bewerken** pictogram.

![ACOP](./images/eventpayload.png)

Je ziet een **Velden** venster popup, waarin u enkele gebieden moet selecteren die wij e-mail moeten personaliseren.  We kiezen later andere profielkenmerken met de gegevens die al in Adobe Experience Platform staan.

![ACOP](./images/eventfields.png)

In het object `_experienceplatform.demoEnvironment`, selecteer de velden **brandLogo** en **brandName**.

![ACOP](./images/eventpayloadbr.png)

In het object `_experienceplatform.identification.core`, zorg dat u het veld selecteert **email**.

![ACOP](./images/eventpayloadbrid.png)

Klikken **OK** om uw wijzigingen op te slaan.

![ACOP](./images/saveok.png)

Dan moet je dit zien. Klikken **Opslaan** nogmaals om uw wijzigingen op te slaan.

![ACOP](./images/eventsave.png)

Uw gebeurtenis is nu geconfigureerd en opgeslagen.

![ACOP](./images/eventdone.png)

Klik nogmaals op uw gebeurtenis om het dialoogvenster **Gebeurtenis bewerken** opnieuw. Overslaan **Velden** nogmaals om de 3 pictogrammen weer te zien. Klik op de knop **Payload weergeven** pictogram.

![ACOP](./images/viewevent.png)

U zult nu een voorbeeld van de verwachte nuttige lading zien.
Uw gebeurtenis heeft een unieke orchestration eventID, die u kunt vinden door neer in die lading te scrollen tot u ziet `_experience.campaign.orchestration.eventID`.

![ACOP](./images/payloadeventID.png)

De gebeurtenis-id is wat naar Adobe Experience Platform moet worden verzonden om de reis te activeren die u in een van de volgende oefeningen gaat maken. Onthoud deze eventID, aangezien u deze later nodig kunt hebben.
`"eventID": "19cab7852cdef99d25b6d5f1b6503da39d1f486b1d585743f97ed2d1e6b6c74f"`

Klikken **OK**, gevolgd door klikken **Annuleren**.

Je hebt deze oefening nu afgerond.

Volgende stap: [2.3 Uw e-mailbericht maken](./ex3.md)

[Ga terug naar Gebruikersstroom 2](./uc2.md)

[Terug naar alle modules](../../overview.md)
