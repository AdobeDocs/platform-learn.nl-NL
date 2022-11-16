---
title: Journey Optimizer Create your event
description: Journey Optimizer Create your event
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
exl-id: e35d2357-21f9-4566-b2a1-cc0cf0c64956
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# 7.1 Uw gebeurtenis maken

Aanmelden bij Adobe Journey Optimizer door naar [Adobe Experience Cloud](https://experience.adobe.com). Klikken **Journey Optimizer**.

![ACOP](./images/acophome.png)

U wordt omgeleid naar de **Home**  in Journey Optimizer. Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxId--`. Als u van de ene naar de andere sandbox wilt gaan, klikt u op **PRODUCTIEVOORRAAD (VA7)** en selecteert u de sandbox in de lijst. In dit voorbeeld krijgt de sandbox een naam **AEP-activering FY22**. Dan ben je in de **Home** weergave van de sandbox `--aepSandboxId--`.

![ACOP](./images/acoptriglp.png)

Blader in het linkermenu omlaag en klik op **Configuraties**. Klik op de knop **Beheren** knop onder **Gebeurtenissen**.

![ACOP](./images/acopmenu.png)

Vervolgens ziet u een overzicht van alle beschikbare gebeurtenissen. Klikken **Gebeurtenis maken** om uw eigen gebeurtenis te maken.

![ACOP](./images/emptyevent.png)

Er verschijnt dan een nieuw, leeg gebeurtenisvenster.

![ACOP](./images/emptyevent1.png)

Geef uw gebeurtenis als volgt een naam: `--demoProfileLdap--AccountCreationEvent`.

![ACOP](./images/eventname.png)

Voeg vervolgens een beschrijving als deze toe `Account Creation Event`.

![ACOP](./images/eventdescription.png)

Controleer vervolgens of de **Type** is ingesteld op **Unitair** en voor de **Type gebeurtenis-id** selectie, selecteren **Door systeem gegenereerd**.

![ACOP](./images/eventidtype.png)

Nu de selectie van het schema. Hiervoor is een schema opgesteld. Gebruik het schema `Demo System - Event Schema for Website (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

Nadat u het schema hebt geselecteerd, ziet u een aantal velden die worden geselecteerd in het dialoogvenster **Payload** sectie. U moet nu de muisaanwijzer op de knop **Payload** en u ziet 3 pictogrammen verschijnen. Klik op de knop **Bewerken** pictogram.

![ACOP](./images/eventpayload.png)

Je ziet een **Velden** venster popup, waarin u enkele gebieden moet selecteren die wij e-mail moeten personaliseren.  We kiezen later andere profielkenmerken met de gegevens die al in Adobe Experience Platform staan.

![ACOP](./images/eventfields.png)

In het object `--aepTenantId--.demoEnvironment`, selecteer de velden **brandLogo** en **brandName**.

![ACOP](./images/eventpayloadbr.png)

In het object `--aepTenantId--.identification.core`, zorg dat u het veld selecteert **email**.

![ACOP](./images/eventpayloadbrid.png)

Klikken **OK** om uw wijzigingen op te slaan.

![ACOP](./images/saveok.png)

U zou dan dit moeten zien:

![ACOP](./images/eventsave.png)

Klikken **Opslaan** nogmaals om uw wijzigingen op te slaan.

![ACOP](./images/save1.png)

Uw gebeurtenis is nu geconfigureerd en opgeslagen.

![ACOP](./images/eventdone.png)

Klik nogmaals op uw gebeurtenis om het dialoogvenster **Gebeurtenis bewerken** opnieuw. Houd de aanwijzer boven de **Payload** nogmaals in om de 3 pictogrammen weer te zien. Klik op de knop **Payload weergeven** pictogram.

![ACOP](./images/viewevent.png)

U zult nu een voorbeeld van de verwachte nuttige lading zien.

![ACOP](./images/fullpayload.png)

Uw gebeurtenis heeft een unieke orchestration eventID, die u kunt vinden door neer in die lading te scrollen tot u ziet `_experience.campaign.orchestration.eventID`.

![ACOP](./images/payloadeventID.png)

De gebeurtenis-id is wat naar Adobe Experience Platform moet worden verzonden om de Reis te activeren die u maakt in Oefening 7.2. Herinner deze eventID, aangezien u het in Oefening 7.3 zult nodig hebben.
`"eventID": "227402c540eb8f8855c6b2333adf6d54d7153d9d7d56fa475a6866081c574736"`

Klikken **OK**, gevolgd door klikken **Annuleren**.

Je hebt deze oefening nu afgerond.

Volgende stap: [7.2 Journey Optimizer: Uw reis- en e-mailbericht maken](./ex2.md)

[Ga terug naar module 7](./journey-orchestration-create-account.md)

[Terug naar alle modules](../../overview.md)
