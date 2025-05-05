---
title: Adobe Journey Optimizer - Pushmeldingen instellen en gebruiken voor iOS
description: Pushmeldingen instellen en gebruiken voor iOS
kt: 5342
doc-type: tutorial
exl-id: 25b3c194-9acb-4085-b3e0-2932afaa04cb
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '1846'
ht-degree: 0%

---

# 3.4.4 Pushmeldingen instellen en gebruiken voor iOS

Als u pushmeldingen wilt gebruiken met Adobe Journey Optimizer, moet u een aantal instellingen controleren en weten wat deze zijn.

Hier zijn alle instellingen die moeten worden gecontroleerd:

- Datasets en schema&#39;s in Adobe Experience Platform
- DataStream voor mobiele apparaten
- Eigenschappen voor gegevensverzameling voor mobiele apparaten
- App-oppervlak voor push-certificaten
- Test uw pushinstellingen met AEP Assurance

Laten we deze een voor een herzien.

Login aan Adobe Journey Optimizer door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ ACOP ](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

U zult aan de **1&rbrace; mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. U zult dan in de **1} mening van het Huis &lbrace;van uw zandbak `--aepSandboxName--` zijn.**

![ ACOP ](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

## 3.4.4.1 Gegevensset met pushgegevens

Adobe Journey Optimizer gebruikt datasets om dingen zoals de pushtokens van mobiele apparaten of interactie met pushberichten (zoals: bericht verzonden, bericht geopend, enz.) op te slaan in een dataset in Adobe Journey Optimizer.

U kunt deze datasets vinden door naar **[!UICONTROL Datasets]** in het menu op de linkerkant van het scherm te gaan. Om systeemdatasets te tonen, klik het filterpictogram.

Laat de optie **toe tonen systeemdatasets** en onderzoek naar **AJO**. U zult dan de datasets zien die voor dupberichten worden gebruikt.

![ Ingestie van Gegevens ](./images/menudsjo1.png)

## 3.4.4.2 Gegevensstroom voor mobiele apparaten

Ga naar [ https://experience.adobe.com/#/data-collection/ ](https://experience.adobe.com/#/data-collection/).

In het linkermenu, ga naar **[!UICONTROL Datastream]** en onderzoek naar uw gegevensstroom die u in [ het Begonnen worden ](./../../../../modules/getting-started/gettingstarted/ex2.md) creeerde, die `--aepUserLdap-- - Demo System Datastream (Mobile)` wordt genoemd. Klik om het te openen.

![ klik het pictogram DataStream in de linkernavigatie ](./images/edgeconfig1a.png)

Klik **uitgeven** op de **Adobe Experience Platform** dienst.

![ klik het pictogram DataStream in de linkernavigatie ](./images/edgeconfig1.png)

U zult dan de gegevensstroommontages zien die werden bepaald, en waarin datasets gebeurtenissen en profielattributen zullen worden opgeslagen.

U zou ook de volgende opties moeten toelaten als zij nog niet worden toegelaten:

- **Offer Decisioning**
- **de Doelen van Personalization**
- **Adobe Journey Optimizer**

Klik **sparen**.

![ noem DataStream en bewaar ](./images/edgeconfig2.png)

## 3.4.4.3 Herzie uw bezit van de Inzameling van Gegevens voor Mobiel

Ga naar [ https://experience.adobe.com/#/data-collection/ ](https://experience.adobe.com/#/data-collection/). Als deel van [ Aan de slag ](./../../../../modules/getting-started/gettingstarted/ex1.md), werden 2 eigenschappen van de Inzameling van Gegevens gecreeerd.
U hebt deze eigenschappen van de Cliënt van de Inzameling van Gegevens reeds als deel van vorige modules gebruikt.

Klik om de eigenschap Gegevensverzameling voor mobiel te openen.

![ DSN ](./images/launchprop.png)

In uw bezit van de Inzameling van Gegevens, ga naar **Uitbreidingen**. Vervolgens ziet u de verschillende extensies die nodig zijn voor de mobiele app. Klik om de uitbreiding **Adobe Experience Platform Edge Network** te openen.

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/launchprop1.png)

U zult dan zien dat uw gegevensstroom voor mobiel hier verbonden is. Daarna, annuleert de klik **&#x200B;**&#x200B;om terug naar uw uitbreidingsoverzicht te gaan.

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/launchprop2.png)

Dan ben je weer terug hier. U zult de uitbreiding voor **AEP Assurance** zien. Met AEP Assurance kunt u controleren, testen, simuleren en valideren hoe u gegevens verzamelt of ervaringen opdoet in uw mobiele app. U kunt meer over AEP Assurance en Project Griffon hier lezen [ https://aep-sdks.gitbook.io/docs/beta/project-griffon ](https://aep-sdks.gitbook.io/docs/beta/project-griffon).

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/launchprop8.png)

Daarna, vormt de klik **&#x200B;**&#x200B;om de uitbreiding **Adobe Journey Optimizer** te openen.

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/launchprop9.png)

U zult dan zien dat dit is waar de dataset voor het volgen van dupgebeurtenissen verbonden is.

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/launchprop10.png)

U hoeft geen wijzigingen aan te brengen in de eigenschap Gegevensverzameling.

## 3.4.4.4 Controleer de installatie van uw toepassingsoppervlak

Ga naar [ https://experience.adobe.com/#/data-collection/ ](https://experience.adobe.com/#/data-collection/). In het linkermenu, ga naar **de Oppervlakken van de App** en open de Oppervlakte van de App voor **DX Demo App APNS**.

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/appsf.png)

U zult dan de gevormde Oppervlakte van de App voor iOS en Android zien.

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/appsf1.png)

## 3.4.4.5 Test push notification setup using AEP Assurance.

Nadat de app is geïnstalleerd, vindt u deze op het beginscherm van uw apparaat. Klik op het pictogram om de app te openen.

![ DSN ](./../../../../modules/getting-started/gettingstarted/images/mobileappn1.png)

Wanneer u de app de eerste keer gebruikt, wordt u gevraagd u aan te melden met uw Adobe ID. Voltooi het aanmeldingsproces.

![ DSN ](./../../../modules/../getting-started/gettingstarted/images/mobileappn2.png)

Nadat u zich hebt aangemeld, wordt er een melding weergegeven waarin u wordt gevraagd om toestemming voor het verzenden van meldingen. Wij zullen berichten als deel van het leerprogramma verzenden, zo klik **toestaan**.

![ DSN ](./../../../modules/../getting-started/gettingstarted/images/mobileappn3.png)

Vervolgens ziet u de startpagina van de app. Ga naar **Montages**.

![ DSN ](./../../../modules/../getting-started/gettingstarted/images/mobileappn4.png)

In montages, zult u zien dat momenteel a **Openbaar Project** in app wordt geladen. Klik **Project van de Douane**.

![ DSN ](./../../../modules/../getting-started/gettingstarted/images/mobileappn5.png)

U kunt nu een aangepast project laden. Klik de code QR om uw project gemakkelijk te laden.

![ DSN ](./../../../modules/../getting-started/gettingstarted/images/mobileappn6.png)

Na het gaan door de **Begonnen** sectie, had u dit resultaat. Klik om het **Mobiele Retail project** te openen dat voor u werd gecreeerd.

![ DSN ](./../../../modules/../getting-started/gettingstarted/images/dsn5b.png)

Voor het geval u per ongeluk uw browser venster, of voor toekomstige demo of enablement zittingen had gesloten, kunt u tot uw websiteproject ook toegang hebben door [ https://dsn.adobe.com/projects ](https://dsn.adobe.com/projects) te gaan. Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik op uw mobiele-toepassingsproject om het te openen.

![ DSN ](./../../../modules/../getting-started/gettingstarted/images/web8a.png)

Daarna, klik **Looppas**.

![ DSN ](./images/web8b.png)

U zult dan deze popup zien, die een QR code bevat. Scan deze QR-code vanuit de mobiele app.

![ DSN ](./../../../modules/../getting-started/gettingstarted/images/web8c.png)

U zult dan uw projectidentiteitskaart tonen in app zien, waarna u **kunt klikken sparen**.

![ DSN ](./../../../modules/../getting-started/gettingstarted/images/mobileappn7.png)

Nu, ga terug naar **Huis** in app. Uw app is nu klaar om te worden gebruikt.

![ DSN ](./../../../modules/../getting-started/gettingstarted/images/mobileappn8.png)

U moet nu een QR-code scannen om uw mobiele apparaat aan te sluiten op uw AEP Assurance-sessie.

Om een zitting van AEP Assurance te beginnen, ga naar [ https://experience.adobe.com/#/data-collection/ ](https://experience.adobe.com/#/data-collection/). Klik **Assurance** in het linkermenu. Dan, klik **creeer Zitting**.

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/griffon3.png)

Klik **Begin**.

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/griffon5.png)

Vul de waarden in:

- Naam van sessie: gebruik `--aepUserLdap-- - push debugging` en vervang LDAP door uw LDAP
- Basis-URL: gebruik `dxdemo://default`

Klik **daarna**.

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/griffon4.png)

Vervolgens ziet u een QR-code op uw scherm, die u moet scannen met uw iOS-apparaat.

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/griffon6.png)

Open de camera-app op uw mobiele apparaat en scan de QR-code die wordt weergegeven door AEP Assurance.

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/ipadPushTest8a.png)

U zult dan een popup scherm zien, vragend u om de SPELD-code in te gaan. Kopieer de SPELD-code van uw scherm van AEP Assurance en klik **verbinden**.

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/ipadPushTest9.png)

Dan zie je dit.

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/ipadPushTest11.png)

In Assurance zie je nu dat een apparaat naar de Assurance-sessie gaat. Klik **Gedaan**.

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/griffon7.png)

Ga naar **Push zuivert**.

>[!NOTE]
>
>In het geval dat u **Push niet kunt vinden zuivert** in het linkermenu, **&#x200B;**&#x200B;vormt &lbrace;in de bodem linkerhoek van uw scherm en voegt **Push toe zuivert** aan het menu.

Je ziet iets dergelijks.

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/griffon10.png)

Enkele uitleg:

- De eerste kolom, **Cliënt**, toont de beschikbare herkenningstekens op uw apparaat van iOS. U ziet een ECID en een pushtoken.
- De tweede kolom toont de **Credentials &amp; Configuratie van App Store**, die opstelling als deel van oefening **3.4.5.4 creeert de Configuratie van de Toepassing in Lancering**
- De tweede kolom toont **informatie van het Profiel**, met extra informatie over welk platform de Duw Symbolische levens in (APNS of APNSSandbox). Als u de **knoop van het Profiel van de Inspectie** klikt, zult u aan Adobe Experience Platform worden genomen en u zult het volledige Profiel van de Klant in real time zien.

Om uw opstelling van de Push configuratie te testen, ga **verzenden de knoop van de Opstelling van de Druk van de Test**. Klik **verzenden het Bericht van de Duw van de Test**

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/griffon11.png)

U moet ervoor zorgen dat **DX demo** app niet open is op het ogenblik van het klikken van **verzendt het Duwbericht** knoop. Als de app geopend is, wordt het pushbericht mogelijk op de achtergrond ontvangen en is het niet zichtbaar.

Vervolgens verschijnt er een pushmelding zoals deze op uw mobiele apparaat.

![ de Inzameling van Gegevens van Adobe Experience Platform ](./images/ipadPush2.png)

Als u de pushmelding hebt ontvangen, betekent dit dat uw setup correct is en goed werkt en dat u nu een echte reis kunt maken die zal leiden tot het verzenden van een pushbericht vanuit Journey Optimizer.

## 3.4.4.6 Een nieuwe gebeurtenis maken

Ga naar **Journey Optimizer**. In het linkermenu, ga naar **Configuraties** en klik **leiden** onder **Gebeurtenissen**.

![ ACOP ](./images/acopmenu.png)

Op het **scherm van Gebeurtenissen**, zult u een mening gelijkend op dit zien. Klik **creëren Gebeurtenis**.

![ ACOP ](./images/add.png)

U ziet dan een lege gebeurtenisconfiguratie.
Geef uw gebeurtenis eerst een naam zoals deze: `--aepUserLdap--StoreEntryEvent` en stel een beschrijving in op `Store Entry Event` .
Daarna is het **Type van Gebeurtenis** selectie. Selecteer **Eenheids**.
Daarna is het **selecteren van het Type van identiteitskaart van de Gebeurtenis 0&rbrace;.** Selecteer **Gegenereerd Systeem**.

![ ACOP ](./images/eventname.png)

Nu de selectie van het schema. Hiervoor is een schema opgesteld. Gebruik het schema `Demo System - Event Schema for Mobile App (Global v1.1) v.1` .

Na het selecteren van het Schema, zult u een aantal gebieden zien die in de **sectie van de Lading** worden geselecteerd. Uw gebeurtenis is nu volledig geconfigureerd.

Klik **sparen**.

![ ACOP ](./images/eventschema.png)

Uw gebeurtenis is nu geconfigureerd en opgeslagen. Klik opnieuw op uw gebeurtenis om **te openen geef het 1&rbrace; scherm van de Gebeurtenis &lbrace;opnieuw uit.**

![ ACOP ](./images/eventdone.png)

Beweeg over het **gebied van de Payload** en klik op het **3&rbrace; pictogram van de Payload van de Mening &lbrace;.**

![ ACOP ](./images/hover.png)

U zult nu een voorbeeld van de verwachte nuttige lading zien.

Uw gebeurtenis heeft een unieke orchestration eventID, die u kunt vinden door neer in die lading te scrollen tot u `_experience.campaign.orchestration.eventID` ziet.

![ ACOP ](./images/payloadeventID.png)

De gebeurtenis-id is wat naar Adobe Experience Platform moet worden verzonden om de Reis te activeren die u in de volgende stap maakt. Schrijf deze eventID neer, aangezien u het in de volgende stap zult nodig hebben.
`"eventID": "89acd341ec2b7d1130c9a73535029debf2ac35f486bc99236b1a5091d6f4bc68"`

Klik **O.K.**, die door **wordt gevolgd annuleert**.

## 3.4.4.7 Een reis maken

In het menu, ga naar **Reizen** en klik **creeer Reizen**.

![ DSN ](./images/sjourney1.png)

Dan zie je dit. Geef je reis een naam. Gebruik `--aepUserLdap-- - Store Entry journey` . Klik **sparen**.

![ DSN ](./images/sjourney3.png)

Eerst, moet u uw gebeurtenis toevoegen als uitgangspunt van uw reis. Zoek de gebeurtenis `--aepUserLdap--StoreEntryEvent` en sleep deze naar het canvas. Klik **sparen**.

![ DSN ](./images/sjourney4.png)

Daarna, onder **Acties**, onderzoek naar de **Duw** actie. De belemmering en laat vallen **duw** actie op het canvas.

Plaats de **Categorie** aan **Marketing** en selecteer een drukkend oppervlak dat u toelaat om pushberichten te verzenden. In dit geval, is de e-mailoppervlakte om te selecteren **duw-iOS-Android**.

>[!NOTE]
>
>Een Kanaal in Journey Optimizer moet bestaan dat de **Oppervlakte van de App** zoals eerder herzien gebruikt.

![ ACOP ](./images/journeyactions1push.png)

De volgende stap is uw bericht te creëren. Om dat te doen, klik **geef inhoud** uit.

![ ACOP ](./images/journeyactions2push.png)

Dan zie je dit. Klik het **verpersoonlijkings** pictogram voor het **gebied van de Titel**.

![ Duw ](./images/bp5.png)

Dan zie je dit. U kunt nu elk profiel rechtstreeks selecteren in het realtime profiel van de klant.

Onderzoek naar het gebied **Voornaam**, dan klik het **+** pictogram naast het gebied **Voornaam**. Vervolgens ziet u het personalisatietoken voor Voornaam die wordt toegevoegd: **{{profile.person.name.firstName}}** .

![ Duw ](./images/bp9.png)

Voeg vervolgens de tekst **toe, welkom in onze winkel!** behind **{{profile.person.name.firstName}}** .

Klik **sparen**.

![ Duw ](./images/bp10.png)

U hebt dit nu. Klik het **verpersoonlijkings** pictogram voor het **3&rbrace; gebied van het Lichaam &lbrace;.**

![ Duw ](./images/bp11.png)

Ga deze tekst **in Klik hier om een 10% korting te krijgen wanneer u vandaag koopt!** en klik **sparen**.

![ Duw ](./images/bp12.png)

Dan heb je dit. Klik op de pijl in de linkerbovenhoek om terug te gaan naar uw reis.

![ Journey Optimizer ](./images/bp12a.png)

Klik **sparen** om uw duwactie te sluiten.

![ DSN ](./images/sjourney8.png)

Klik **publiceren**.

![ DSN ](./images/sjourney10.png)

Klik **publiceren** opnieuw.

![ DSN ](./images/sjourney10a.png)

Uw reis is nu gepubliceerd.

![ DSN ](./images/sjourney11.png)

## 3.4.4.8 Test uw reis en uw pushbericht

In uw DX demo 2.0 mobiele toepassing, ga naar het **scherm van Montages**. Klik de **knoop van de Ingang van de Opslag**.

>[!NOTE]
>
>De **knoop van de Ingang van de Opslag** wordt momenteel uitgevoerd. U vindt deze nog niet in de app.

![ DSN ](./images/demo1b.png)

Zorg ervoor om app onmiddellijk te sluiten na het klikken van het **pictogram van de Ingang van de Opslag**, anders zal het duwbericht niet worden getoond.

Na een paar seconden, zult u het bericht zien verschijnen.

![ DSN ](./images/demo2.png)

U hebt deze oefening voltooid.

## Volgende stappen

Ga naar [ Samenvatting en voordelen ](./summary.md){target="_blank"}

Ga terug naar [ Adobe Journey Optimizer ](journeyoptimizer.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}
