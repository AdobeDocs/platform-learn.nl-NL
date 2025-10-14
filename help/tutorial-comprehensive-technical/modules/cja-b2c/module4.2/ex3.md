---
title: Gegevens van Googles Analytics verzamelen en analyseren in Adobe Experience Platform met de BigQuery Source-connector - GCP en BigQuery aansluiten op Adobe Experience Platform
description: Gegevens van Googles Analytics verzamelen en analyseren in Adobe Experience Platform met de BigQuery Source-connector - GCP en BigQuery aansluiten op Adobe Experience Platform
kt: 5342
doc-type: tutorial
exl-id: 86b04b4e-0439-4491-b700-5b0591c493b7
source-git-commit: d6f6423adbc8f0ce8e20e686ea9ffd9e80ebb147
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 0%

---

# 4.2.3 GCP en BigQuery aansluiten op Adobe Experience Platform

## Doelstellingen

- De API en services verkennen in het Google Cloud Platform
- Ben vertrouwd met OAuth Playground voor het testen van Google APIs
- Uw eerste BigQuery-verbinding maken in Adobe Experience Platform

## Context

Adobe Experience Platform verstrekt een schakelaar binnen **Bronnen** die u zal helpen datasets BigQuery in Adobe Experience Platform brengen. Deze gegevensconnector is gebaseerd op de Google BigQuery API. Daarom is het belangrijk om uw Google Cloud Platform en uw BigQuery-omgeving goed voor te bereiden voor het ontvangen van API-aanroepen van Adobe Experience Platform.

Voor het configureren van de BigQuery Source-connector in Adobe Experience Platform hebt u de volgende vier waarden nodig:

- project
- clientId
- clientSecret
- refreshToken

Tot dusverre hebt u slechts eerste, **identiteitskaart van het Project**. Deze **waarde van identiteitskaart van 0&rbrace; Project is een willekeurige identiteitskaart die door Google werd geproduceerd toen u uw project BigQuery tijdens oefening 12.1 creeerde.**

Kopieer de project-id in een gescheiden tekstbestand.

| Credentials | Naamgeving | Voorbeeld |
| ----------------- |-------------| -------------|
| Project-id | random | mogelijk-bijen-447102-h3 |

U kunt uw identiteitskaart van het Project op elk ogenblik controleren door op uw **Naam van het Project** in de hoogste menubar te klikken:

![&#x200B; demo &#x200B;](./images/ex1projectMenu.png)

U ziet uw project-id aan de rechterkant:

![&#x200B; demo &#x200B;](./images/ex1projetcselection.png)

In deze oefening zult u leren hoe te om de andere 3 vereiste gebieden te krijgen:

- clientId
- clientSecret
- refreshToken

## 4.2.3.1 Google Auth Platform

Ga om te beginnen terug naar de startpagina van het Google Cloud Platform. Klik hiertoe in de linkerbovenhoek van het scherm op het logo.

![&#x200B; demo &#x200B;](./images/ex25.png)

Zodra u op de homepage bent, onderzoek naar **Platform van de Auth van Google** in de onderzoeksbar. Klik op het eerste resultaat om het te openen.

![&#x200B; demo &#x200B;](./images/ex24.png)

U zult nu de **homepage van het Platform van de Auth van 0&rbrace; Google &lbrace;zien.** Klik **BEGONNEN** GET.

![&#x200B; demo &#x200B;](./images/ex26.png)

Voor de **naam van de App**, gebruik dit:

| Naamgeving | Voorbeeld |
| ----------------- |-------------| 
| `--aepUserLdap-- - AEP BigQuery Connector` | vangeluw - AEP BigQuery Connector |

Selecteer uw e-mailadres voor het gebied **e-mail van de de steunensteun van de Gebruiker**.

Klik **VOLGENDE**.

![&#x200B; demo &#x200B;](./images/go1.png)

Selecteer **Extern** en klik **VOLGENDE**.

![&#x200B; demo &#x200B;](./images/go2.png)

Ga uw e-mailadres in en klik **VOLGENDE**.

![&#x200B; demo &#x200B;](./images/go3.png)

Controleer checkbox en klik **DOORGAAN**. Dan, klik **CREËREN**.

![&#x200B; demo &#x200B;](./images/go4.png)

## 4.2.3.2 OAuth-client maken

Klik **CREEER OAUTH CLIENT**.

![&#x200B; demo &#x200B;](./images/ex261.png)

Dan zie je dit.

![&#x200B; demo &#x200B;](./images/ex2611.png)

Selecteer **toepassing van het Web**.

![&#x200B; demo &#x200B;](./images/ex212.png)

Er verschijnen meerdere nieuwe velden. U moet nu de **Naam** van identiteitskaart OAuth van de Cliënt ingaan en ook ingaan **Gemachtigde redirect URIs**.

Voor het gebied **Naam**, gebruik dit:

| Veld | Waarde | Voorbeeld |
| ----------------- |-------------| -------------| 
| Naam | ldap - AEP BigQuery Connector | vangeluw - Platform BigQuery Connector |

![&#x200B; demo &#x200B;](./images/ex2122.png)


Klik **+ voeg URI** toe onder **Gemachtigde opnieuw richt URIs**. Voeg de onderstaande nieuwe URI toe.

| Veld | Waarde |
| ----------------- |-------------| 
| Toegestane omleiding van URI&#39;s | https://developers.google.com/oauthplayground |

Het **Gemachtigde opnieuw richten URIs** gebied is een zeer belangrijk gebied omdat u het later zult nodig hebben om RefreshToken te krijgen u de opstelling van de Schakelaar van BigQuery Source in Adobe Experience Platform moet beëindigen.

Klik **creëren**.

![&#x200B; demo &#x200B;](./images/ex2121.png)

Uw OAuth-client-id is nu gemaakt. Klik erop om nu uw client-id en uw clientgeheim te zien.

![&#x200B; demo &#x200B;](./images/ex220.png)

U zult dan de waarden voor identiteitskaart van de Cliënt en Geheime cliënt zien.

Kopieer deze twee velden en plak ze in een tekstbestand op uw bureaublad. U kunt deze geloofsbrieven altijd tot een later stadium toegang hebben, maar het is gemakkelijker als u hen in een tekstdossier naast uw identiteitskaart van het Project BigQuery opslaat.

Als recap voor de configuratie van de BigQuery Source Connector in Adobe Experience Platform, hebt u nu al de volgende waarden beschikbaar:

| Credentials voor BigQuery Connector | Waarde |
| ----------------- |-------------| 
| Project-id | uw eigen project-id (bijvoorbeeld: maximum-bijen-447102-h3) |
| clientid | uzelf |
| kindergeheim | uw clientgeheim |

![&#x200B; demo &#x200B;](./images/ex2200.png)

Vervolgens moet u uw OAuth-app publiceren. Ga naar **Publiek** en klik **APP van PUBLISH**.

![&#x200B; demo &#x200B;](./images/ex2pub1.png)

Klik **BEVESTIGEN**.

![&#x200B; demo &#x200B;](./images/ex2pub2.png)

U mist nog **refreshToken**. refreshToken is een vereiste wegens veiligheidsredenen. In de wereld van APIs, verlopen de tekenen typisch om de 24 uur. Zo **refreshToken** is nodig om het veiligheidstoken om de 24 uur te verfrissen, zodat uw opstelling van de Verbinding van Source het verbinden met het Platform van de Wolk van Google en BigQuery kan houden.

## 4.2.3.3 BigQuery API en refreshToken

Er zijn verschillende manieren om een refreshToken te verkrijgen voor toegang tot API&#39;s van het Google Cloud-platform. Een van deze opties is bijvoorbeeld het gebruik van Postman.
Nochtans, heeft Google iets gemakkelijker gebouwd om met hun APIs te testen en te spelen, een hulpmiddel genoemd **OAuth 2.0 Playground**.

Om tot **OAuth 2.0 Playground** toegang te hebben, ga [&#x200B; https://developers.google.com/oauthplayground &#x200B;](https://developers.google.com/oauthplayground).

U zult dan **OAuth 2.0 de homepage van de Playground** zien.

![&#x200B; demo &#x200B;](./images/ex222.png)

Klik op het **versnelling** pictogram in de hoogste juiste kant van uw scherm. Zorg ervoor dat de instellingen overeenkomen met de instellingen in de bovenstaande afbeelding.

Controle checkbox: **gebruik uw eigen geloofsbrieven OAuth**

![&#x200B; demo &#x200B;](./images/ex2221.png)

Er worden twee velden weergegeven.

Vul de velden volgende op deze tabel in:

| API-instellingen voor afspelen | Uw Google API-gebruikersgegevens |
| ----------------- |-------------| 
| OAuth-client-id | uw eigen client-id (in het tekstbestand op uw bureaublad) |
| OAuth Client Secret | uw eigen clientgeheim (in het tekstbestand op uw bureaublad) |

Zodra u uw geloofsbrieven hebt ingevuld, te klikken gelieve **dicht**.

![&#x200B; demo &#x200B;](./images/ex223a.png)

In het linkermenu ziet u alle beschikbare Google API&#39;s. Onderzoek naar **BigQuery API v2** en klik het om het te openen.

![&#x200B; demo &#x200B;](./images/ex227.png)

Selecteer vervolgens het bereik dat wordt aangegeven in de onderstaande afbeelding. U moet op elk van de beschikbare API&#39;s klikken en voor elke geselecteerde API wordt een vinkje weergegeven.

Daarna, klik **autoriseer APIs**.

![&#x200B; demo &#x200B;](./images/ex226.png)

Klik op het e-mailadres dat u hebt gebruikt voor het instellen van GCP en BigQuery.

![&#x200B; demo &#x200B;](./images/ex2266.png)

U zult dan een grote waarschuwing zien: **Deze app wordt niet geverifieerd**. Dit gebeurt omdat uw Platform BigQuery Connector nog niet formeel is gecontroleerd, zodat Google niet weet of het een authentieke app is of niet.

Klik **Geavanceerd**.

![&#x200B; demo &#x200B;](./images/ex232.png)

Daarna, klik op **gaan naar —aepUserLoad— - de Schakelaar van AEP BigQuery (onveilig)**.

![&#x200B; demo &#x200B;](./images/ex233.png)

U zult dan een veiligheidsherinnering voor toegang zien. Klik **Uitgezocht allen**.

![&#x200B; demo &#x200B;](./images/ex229.png)

De rol neer en klikt **gaat** verder.

![&#x200B; demo &#x200B;](./images/ex230.png)

U wordt nu teruggestuurd naar OAuth 2.0 Playground en u zult dit zien. Klik **de vergunningscode van de Uitwisseling voor tokens**.

![&#x200B; demo &#x200B;](./images/ex236.png)

Na een paar seconden, zal de **Stap 2 - de vergunningscode van de Uitwisseling voor tokens** mening automatisch sluiten, en u zult **Stap 3 zien - verzoek aan API** vormen.

U moet terug naar **Stap 2 de vergunningscode van de Uitwisseling voor tokens** gaan, zodat klik op **Stap 2 de vergunningscode van de Uitwisseling voor tokens** opnieuw om **te visualiseren verfrissen teken**.

![&#x200B; demo &#x200B;](./images/ex237.png)

U zult nu **het verfrissen teken** zien.

![&#x200B; demo &#x200B;](./images/ex238.png)

Kopieer het **verfrissen teken** en kleef het in het tekstdossier op uw Desktop samen met andere Referenties van de Verbinding van BigQuery Source:

| Credentials voor BigQuery Source Connector | Waarde |
| ----------------- |-------------| 
| Project-id | uw eigen willekeurige project-id (bijvoorbeeld: apt-zomer-273608) |
| clientid | uzelf |
| kindergeheim | uw clientgeheim |
| vernieuwingstoken | uzelf vernieuwen |

Stel vervolgens uw Source-connector in Adobe Experience Platform in.

## 4.2.3.5 - Verbind Platform met uw eigen Lijst BigQuery

Login aan Adobe Experience Platform door naar dit URL te gaan: [&#x200B; https://experience.adobe.com/platform &#x200B;](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![&#x200B; Ingestie van Gegevens &#x200B;](./../../../modules/datacollection/module1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxName--`` . Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![&#x200B; Ingestie van Gegevens &#x200B;](./../../../modules/datacollection/module1.2/images/sb1.png)

Ga in het linkermenu naar Bronnen. U zult dan de **Bronnen** homepage zien. In het **Bronnen** menu, klik op **Gegevensbestanden**. Klik de **kaart van Google BigQuery**. Daarna, klik **Opstelling**.

![&#x200B; demo &#x200B;](./images/s1.png)

Maak nu een nieuwe verbinding.

Klik **Nieuwe rekening**. U moet nu alle hieronder gebieden invullen, die op de opstelling worden gebaseerd u in GCP en BigQuery deed.

![&#x200B; demo &#x200B;](./images/s3.png)

Laten we beginnen met de naam van de verbinding:

Gebruik deze naamgevingsconventie:

| Credentials voor BigQuery Connector | Waarde | Voorbeeld |
| ----------------- |-------------| -------------| 
| Accountnaam | `--aepUserLdap-- - BigQuery Connection` | vangeluw - BigQuery Connection |
| Beschrijving | `--aepUserLdap-- - BigQuery Connection` | vangeluw - BigQuery Connection |

Dan heb je het volgende:

![&#x200B; demo &#x200B;](./images/ex239a.png)

Daarna, vul GCP en BigQuery API **de Authentificatie van de Rekening** - details in die u in een tekst-dossier op uw Desktop opsloeg:

| Credentials voor BigQuery Connector | Waarde |
| ----------------- |-------------| 
| Project-id | uw eigen willekeurige project-id (bijvoorbeeld: maximum-bijen-447102-h3) |
| clientId | ... |
| clientSecret | ... |
| refreshToken | ... |

Uw **Authentificatie van de Rekening** - details zouden nu als dit moeten kijken. Klik **verbinden met bron**.

![&#x200B; demo &#x200B;](./images/ex239xx.png)

Als uw **details van de Authentificatie van de 0&rbrace; Rekening correct werden ingevuld, zou u nu een visuele bevestiging moeten zien dat de verbinding behoorlijk werkt, door de** Verbonden **bevestiging te zien.** Klik **daarna**.

![&#x200B; demo &#x200B;](./images/ex2projectid.png)

U zult nu de dataset zien BigQuery u in de vorige oefening creeerde.

![&#x200B; demo &#x200B;](./images/datasets.png)

Goed gedaan! In de volgende oefening, zult u gegevens van die lijst laden en het tegen een schema en dataset in Adobe Experience Platform in kaart brengen.

Volgende Stap: [&#x200B; 4.2.4 de gegevens van de Lading van BigQuery in Adobe Experience Platform &#x200B;](./ex4.md)

[Terug naar module 4.2](./customer-journey-analytics-bigquery-gcp.md)

[Terug naar alle modules](./../../../overview.md)
