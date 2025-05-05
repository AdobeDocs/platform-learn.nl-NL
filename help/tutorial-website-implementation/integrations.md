---
title: Integratie van Experiencen Cloud met tags implementeren
description: Leer hoe u de integratie van Soorten publiek, A4T en Klantkenmerken in uw Adobe Experience Cloud-implementatie kunt valideren. Deze les maakt deel uit van de zelfstudie Experience Cloud implementeren in websites.
exl-id: 1d02efce-a50a-4f4d-a0cf-eb8275cf0faa
source-git-commit: 2182441d992aec0602d0955d78aa85407bd770c9
workflow-type: tm+mt
source-wordcount: '1191'
ht-degree: 0%

---

# Integratie van Experience Cloud

In deze les, zult u de belangrijkste integraties tussen de oplossingen herzien u enkel uitvoerde. Het goede nieuws is dat u de codesaspecten van de integratie al hebt geïmplementeerd door de eerdere lessen te voltooien! U hoeft geen extra werk in deze les te doen behalve het lezen en valideren.

## Leerdoelen

Aan het eind van deze les, zult u kunnen:

1. Verklaar de basisgebruiksgevallen voor Audience Sharing, Analytics voor Doel (A4T) en de Integraties van de Attributen van de Klant
1. Bevestig de basiscliënt-zijimplementatieaspecten van deze integratie

## Vereisten

U zou alle vorige lessen in deze zelfstudie moeten voltooien alvorens de instructies in deze les te volgen.

>[!NOTE]
>
>Er zijn vele gebruiker-toestemmingsvereisten, rekeningsconfiguraties, en leveringsstappen die worden vereist om deze integratie volledig te gebruiken en die buiten het werkingsgebied van dit leerprogramma zijn. Als u deze integratie nog niet gebruikt in uw huidige implementatie van het Experience Cloud, moet u het volgende overwegen:
>
>* Herzie de volledige vereisten van de [ Integraties van de Diensten van de Kern ](https://experienceleague.adobe.com/en/docs/core-services/interface/services/getting-started)
>* Herzie de volledige vereisten van [ Analytics voor de integratie van het Doel ](https://experienceleague.adobe.com/en/docs/target/using/integrate/a4t/before-implement)

## Doelgroepen

[ Soorten publiek ](https://experienceleague.adobe.com/en/docs/core-services/interface/services/audiences/overview) maakt deel uit van de Dienst van de Kern van Mensen en staat u toe om publiek tussen oplossingen te delen. U kunt bijvoorbeeld een publiek in de Audience Manager maken en dit gebruiken om gepersonaliseerde inhoud met Target te leveren.

De belangrijkste vereisten om A4T uit te voeren-die u reeds hebt gedaan-zijn:

1. De Adobe Experience Platform Identity Service implementeren
1. Audience Manager implementeren
1. Voer andere oplossingen uit die u zou willen ontvangen of publiek, zoals Doel en Analytics tot stand brengen

### De integratie van soorten publiek valideren

De beste manier om de integratie van het publiek te bevestigen is een publiek te bouwen, het te delen aan een andere oplossing, en dan het volledig te gebruiken in de andere oplossing (b.v. te bevestigen dat een bezoeker die voor een AAM segment in aanmerking komt voor een activiteit van het Doel die aan dat segment wordt gericht). Dit valt echter buiten het bereik van deze zelfstudie.

Deze validatiestappen zijn gericht op het kritieke onderdeel dat zichtbaar is in de implementatie op de client, namelijk de bezoeker-id.

1. Open de [ plaats van de Luma ](https://luma.enablementadobe.com/content/luma/us/en.html)

1. Zorg ervoor debugger het markeringsbezit aan *in kaart brengt uw* milieu van de Ontwikkeling, zoals die in de [ vroegere les ](switch-environments.md) wordt beschreven

   ![ Uw milieu van de tagontwikkeling dat in Debugger wordt getoond ](images/switchEnvironments-debuggerOnWeRetail.png)

1. Ga naar het tabblad Netwerk van Foutopsporing

1. Klik **[!UICONTROL Clear All Requests]** alleen om de zaken op te schonen

1. Laad de pagina Luma opnieuw, waarbij u ervoor zorgt dat zowel de aanvraag voor Doel als de aanvraag voor Analytics in Foutopsporing wordt weergegeven

1. De pagina Luma opnieuw laden

1. U zou vier verzoeken op het lusje van het Netwerk van debugger-twee voor Doel en twee voor Analyse nu moeten zien

1. Kijk in de rij met het label &quot;Bezoeker-id Experience Cloud&quot;. Ids in elk verzoek door elke oplossing zou altijd het zelfde moeten zijn.

   ![ Bevestig passende SDIDs ](images/integrations-matchingECIDs.png)

1. De id&#39;s zijn uniek per bezoeker. U kunt dit bevestigen door een collega te vragen deze stappen te herhalen.

## Analyses voor doel (A4T)

De [ Analytics voor de integratie van het Doel (A4T) ](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t.html) staat u toe om uw gegevens van Analytics als bron voor het melden van metriek in Doel te hefboomwerking.

De belangrijkste vereisten om A4T uit te voeren-die u reeds hebt gedaan-zijn:

1. De Adobe Experience Platform Identity Service implementeren
1. Vuur het verzoek van de de paginadading van het Doel vóór het de paginameningsbaken van de Analyse in brand

A4T werkt door een server-zijverzoek van Doel aan Analytics met het Beacon van de de paginamening van Analytics te stitching, die wij &quot;hit-stitching&quot;noemen.  Hit-stitching vereist dat het verzoek van het Doel dat de activiteit (of toename een op doel gebaseerd doel metrisch) levert een parameter heeft die een parameter in de het meningsbaken van de pagina van de Analyse aanpast. Deze parameter wordt de aanvullende gegevens-id (SDID&#39;s) genoemd.

### De A4T-implementatie valideren

De beste manier om de integratie te bevestigen A4T is een activiteit van het Doel te bouwen gebruikend A4T en de rapporteringsgegevens te bevestigen, nochtans is dit voorbij het werkingsgebied van dit leerprogramma. Dit leerprogramma zal u tonen hoe te om te bevestigen dat de supplementaire gegevens ids tussen de oplossingsvraag aanpassen.

**om SDIDs** te bevestigen

1. Open de [ plaats van de Luma ](https://luma.enablementadobe.com/content/luma/us/en.html)

1. Zorg ervoor debugger het markeringsbezit aan *in kaart brengt uw* milieu van de Ontwikkeling, zoals die in de [ vroegere les ](switch-environments.md) wordt beschreven

   ![ Uw milieu van de tagontwikkeling dat in Debugger wordt getoond ](images/switchEnvironments-debuggerOnWeRetail.png)

1. Ga naar het tabblad Netwerk van Foutopsporing

1. Klik **[!UICONTROL Clear All Requests]** alleen om de zaken op te schonen

1. Laad de pagina Luma opnieuw, waarbij u ervoor zorgt dat zowel de aanvraag voor Doel als de aanvraag voor Analytics in Foutopsporing wordt weergegeven

1. De pagina Luma opnieuw laden

1. U zou vier verzoeken op het lusje van het Netwerk van debugger-twee voor Doel en twee voor Analyse nu moeten zien

1. Zoek in de rij met het label &quot;Aanvullende gegevens-id&quot;. De id&#39;s van de eerste pagina die wordt geladen, moeten overeenkomen met die van Target en Analytics. De id&#39;s van het laden van de tweede pagina moeten ook overeenkomen, maar moeten verschillen van het laden van de eerste pagina.

   ![ Bevestig passende SDIDs ](images/integrations-matchingSDIDs.png)

Als u extra verzoeken van het Doel in het werkingsgebied van een paginading (exclusief single-page apps) doet die deel van A4T activiteiten uitmaken, is het goed om hen unieke namen (niet doel-globaal-mbox) te geven zodat zij zelfde SDIDs van het aanvankelijke Doel en de verzoeken van de Analyse zullen blijven hebben.

## Klantkenmerken

[ de Attributen van de Klant ](https://experienceleague.adobe.com/docs/core-services/interface/customer-attributes/attributes.html) is een deel van de Dienst van de Kern van Mensen die u toestaat om gegevens van uw gegevensbestand van het het beheer van de klantenverhouding (CRM) te uploaden en hefboomwerking het in Adobe Analytics en Adobe Target.

De belangrijkste vereisten om de Attributen van de Klant uit te voeren—die u reeds hebt gedaan-zijn:

1. De Adobe Experience Platform Identity Service implementeren
1. Plaats Klantidentiteitskaart via de Dienst van Id *vóór* het Doel en de Analyse in brand hun verzoeken (die u het gebruiken van de regel die eigenschap in markeringen opdracht geeft tot stand bracht)

### De implementatie van klantkenmerken valideren

U hebt al gevalideerd dat de id&#39;s van de klant worden doorgegeven aan zowel de identiteitsservice als aan Target in eerdere lessen. U kunt de klant-id ook valideren in de hit Analytics.
Op dit moment is de klant-id een van de weinige parameters die niet in het Experience Cloud Debugger worden weergegeven. U gebruikt dus de JavaScript-console van de browser om deze weer te geven.

1. De Luministsite openen
1. De ontwikkelaarsgereedschappen van uw browser openen
1. Ga naar het tabblad Netwerk
1. Typ in het filterveld `b/ss` wat wat u ziet, beperkt tot de Adobe Analytics-aanvragen

   ![ open de Hulpmiddelen van de Ontwikkelaar en filter het lusje van het Netwerk om slechts de verzoeken van Analytics te tonen ](images/aam-openTheJSConsole.png)

1. Klik op de koppeling **[!UICONTROL LOGIN]** rechtsboven in de site

   ![ klik Login op het hoogste recht ](images/idservice-loginNav.png)

1. Voer `test@adobe.com` in als gebruikersnaam
1. Voer `test` in als wachtwoord
1. Klik op de knop **[!UICONTROL LOGIN]**

   ![ ga geloofsbrieven in en klik login ](images/idservice-login.png)

1. Het zou u aan de Homepage moeten terugkeren, die ook een baken zal teweegbrengen dat u in de Hulpmiddelen van de Ontwikkelaar kunt zien. Als u naar de pagina met accountinformatie wordt gebracht, klikt u op het WE.RETAIL-logo om terug te keren naar de startpagina.
1. Klik op de aanvraag en selecteer het tabblad Koppen
1. Omlaag schuiven totdat u enkele geneste parameters ziet
   1. cid - dit is het standaardscheidingsteken voor het gedeelte van de aanvraag voor de klant-id
   1. crm_id - Dit is de code van de douaneintegratie die u in de les van de Dienst van de Identiteit specificeerde
   1. id - De waarde voor de klant-id die afkomstig is uit het gegevenselement `Email (Hashed)`
   1. as - De authentificatiestatus, met &quot;1&quot;betekent het programma geopend

   {de Bevestiging van identiteitskaart van de Klant van 0} Analytics ![&#128279;](images/integrations-analyticsCustomerIDValidation.png)

[Volgende &quot;Publish your Property&quot; >](publish.md)
