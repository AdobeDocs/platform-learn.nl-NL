---
title: Aan de slag met Firefly Services
description: Leer hoe u Postman en Adobe I/O kunt gebruiken om query's uit te voeren op Adobe Firefly Services-API's
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 52385c33-f316-4fd9-905f-72d2d346f8f5
source-git-commit: 219945c74c620b9a4b93cb2b7462137118d42d33
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 0%

---

# 1.1.1 Aan de slag met Firefly Services

Leer hoe u Postman en Adobe I/O kunt gebruiken om query&#39;s uit te voeren op Adobe Firefly Services-API&#39;s.

## 1.1.1.1 Uw Adobe I/O-project configureren

In deze oefening, wordt Adobe I/O gebruikt om tegen de Diensten APIs van Firefly te vragen. Voer de volgende stappen uit om Adobe I/O in te stellen.

1. Ga naar [ https://developer.adobe.com/console/home ](https://developer.adobe.com/console/home) {target="_blank"}.

![ de Nieuwe Integratie van Adobe I/O ](./images/iohome.png){zoomable="yes"}

1. Selecteer de juiste instantie in de rechterbovenhoek van het scherm. Uw instantie is `--aepImsOrgName--` . Daarna, uitgezochte **creeer nieuw project**.

![ de Nieuwe Integratie van Adobe I/O ](./images/iocomp.png){zoomable="yes"}

1. Selecteer **+ toevoegen aan Project** en kies **API**.

![ de Nieuwe Integratie van Adobe I/O ](./images/adobe_io_access_api.png){zoomable="yes"}

Het scherm moet er zo uitzien.

![ de Nieuwe Integratie van Adobe I/O ](./images/api1.png){zoomable="yes"}

1. Selecteer **Creative Cloud** en kies **Firefly - de Diensten van Firefly**, dan selecteren **daarna**.

![ de Nieuwe Integratie van Adobe I/O ](./images/api3.png){zoomable="yes"}

1. Verstrek een naam voor uw referentie: `--aepUserLdap-- - Firefly Services OAuth credential` en selecteer **daarna**.

![ de Nieuwe Integratie van Adobe I/O ](./images/api4.png){zoomable="yes"}

1. Selecteer de standaardprofiel **StandaardConfiguratie van de Diensten van Firefly** en selecteer **sparen Gevormde API**.

![ de Nieuwe Integratie van Adobe I/O ](./images/api9.png){zoomable="yes"}

Uw Adobe I/O-integratie is nu gereed.

![ de Nieuwe Integratie van Adobe I/O ](./images/api11.png){zoomable="yes"}

## 1.1.1.2 Download de Postman-omgeving

1. Selecteer **Download voor Postman**, dan kies **Server-aan-Server** om een milieu van Postman te downloaden.

![ de Nieuwe Integratie van Adobe I/O ](./images/iopm.png){zoomable="yes"}

1. Selecteer de projectnaam.

![ de Nieuwe Integratie van Adobe I/O ](./images/api13.png){zoomable="yes"}

1. Selecteer **uitgeven Project**.

![ de Nieuwe Integratie van Adobe I/O ](./images/api14.png){zoomable="yes"}

1. Ga een vriendschappelijke naam voor uw integratie in: `--aepUserLdap-- Firefly` en selecteer **sparen**.

![ de Nieuwe Integratie van Adobe I/O ](./images/api15.png){zoomable="yes"}

De installatie van uw Adobe I/O-integratie is nu voltooid.

![ de Nieuwe Integratie van Adobe I/O ](./images/api16.png){zoomable="yes"}

## 1.1.1.3 Postman-verificatie naar Adobe I/O

1. De download en installeert de relevante versie van Postman voor uw OS bij [ Downloads van Postman ](https://www.postman.com/downloads/) {target="_blank"}.

![ de Nieuwe Integratie van Adobe I/O ](./images/getstarted.png){zoomable="yes"}

1. Start de toepassing.

In Postman zijn er twee concepten: omgevingen en verzamelingen.

- Het omgevingsbestand bevat al uw omgevingsvariabelen die min of meer consistent zijn. In het milieu, zult u dingen zoals IMSOrg van uw milieu van Adobe, naast veiligheidsgeloofsbrieven zoals uw identiteitskaart van de Cliënt en anderen vinden. U hebt het omgevingsbestand tijdens de Adobe I/O-installatie eerder gedownload en de naam is **`oauth_server_to_server.postman_environment.json`** .

- De verzameling bevat een aantal API-aanvragen die u kunt gebruiken. We gebruiken twee verzamelingen
   - 1 Verzameling voor verificatie naar Adobe I/O
   - 1 Verzameling voor de oefeningen in deze module

1. Download [ postman-ff.zip ](./../../../assets/postman/postman-ff.zip) aan uw lokale Desktop.

![ de Nieuwe Integratie van Adobe I/O ](./images/pmfolder.png){zoomable="yes"}

In **postman.zip** dossier zijn de volgende dossiers:

     - ` Adobe IO - OAuth.postman_collection.json ` 
     - ` FF - Firefly Services Tech Insiders.postman_collection.json ` 

1. Unzip **postman-ff.zip** en sla de volgende 2 dossiers in een omslag op uw Desktop op:
- Adobe IO - OAuth.postman_collection.json
- FF - Firefly Services Tech Insiders.postman_collection.json
- oauth_server_to_server.postman_environment.json

![ de Nieuwe Integratie van Adobe I/O ](./images/pmfolder1.png){zoomable="yes"}

1. In Postman, uitgezochte **Invoer**.

![ de Nieuwe Integratie van Adobe I/O ](./images/postmanui.png){zoomable="yes"}

1. Selecteer **Dossiers**.

![ de Nieuwe Integratie van Adobe I/O ](./images/choosefiles.png){zoomable="yes"}

1. Kies de drie dossiers van de omslag, dan selecteren **Open** en **Invoer**.

![ de Nieuwe Integratie van Adobe I/O ](./images/selectfiles.png){zoomable="yes"}

![ de Nieuwe Integratie van Adobe I/O ](./images/impconfirm.png){zoomable="yes"}

U hebt niet alles wat u nodig hebt in Postman om te beginnen met het communiceren met Firefly Services via de API&#39;s.

## 1.1.1.4 Verzoek om een toegangstoken

Daarna, om ervoor te zorgen u behoorlijk voor authentiek wordt verklaard, moet u om een toegangstoken verzoeken.

1. Zorg ervoor dat u het juiste milieu hebt geselecteerd alvorens om het even welk verzoek uit te voeren door milieu-dropdown lijst in de hoogste juiste hoek te verifiëren. De geselecteerde omgeving moet een naam hebben die vergelijkbaar is met deze, `--aepUserLdap-- Firefly Services OAuth Credential` .

![ Postman ](./images/envselemea1.png){zoomable="yes"}

De geselecteerde omgeving moet een naam hebben die vergelijkbaar is met deze, `--aepUserLdap-- Firefly Services OAuth Credential` .

![ Postman ](./images/envselemea.png){zoomable="yes"}

Nu uw Postman-omgeving en -verzamelingen zijn geconfigureerd en werken, kunt u verificatie uitvoeren van Postman naar Adobe I/O.

1. In **Adobe IO - OAuth** inzameling, selecteer het verzoek genoemd **POST - krijg het Token van de Toegang** en selecteer **verzend**.

Bericht onder **de Params van de Vraag**, worden twee variabelen van verwijzingen voorzien, `API_KEY` en `CLIENT_SECRET`. Deze variabelen zijn afkomstig uit de geselecteerde omgeving, `--aepUserLdap-- Firefly Services OAuth Credential` .

![ Postman ](./images/ioauth.png){zoomable="yes"}

Als succesvol, een reactie die een dragerteken, een toegangstoken, en een vervalsingsvenster bevat verschijnt in de **sectie van het Lichaam** {van Postman.

![ Postman ](./images/ioauthresp.png){zoomable="yes"}


U zou een gelijkaardige reactie moeten zien die de volgende informatie bevat:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| token_type | **drager** |
| access_token | **eyJhbGciOiJSU...** |
| verloopt_in | **86399** |

Adobe I/O **drager-teken** heeft een specifieke waarde (zeer lange access_token) en een vervalvenster en is nu geldig voor 24 uren. Dit betekent dat als u Postman na 24 uur wilt gebruiken voor verificatie voor Adobe I/O, u een nieuwe token moet genereren door dit verzoek opnieuw uit te voeren.

## 1.1.1.5 Firefly Services API, Text 2 Image

Nu bent u klaar om uw eerste verzoek naar de API&#39;s van Firefly Services te verzenden.

1. Selecteer het verzoek genoemd **POST - Firefly - T2I V3** van de **FF - de Ingenieurs van de Technologie van de Diensten van Firefly** inzameling.

![ Firefly ](./images/ff1.png){zoomable="yes"}

1. Kopieer de URL van de afbeelding uit het antwoord en open deze in uw webbrowser om de afbeelding weer te geven.

![ Firefly ](./images/ff2.png){zoomable="yes"}

Er moet een mooie afbeelding worden afgebeeld `horses in a field` .

![ Firefly ](./images/ff3.png){zoomable="yes"}

U kunt vrij spelen met de API-aanvraag voordat u verdergaat met de volgende oefening.

## Volgende stappen

Ga naar [ optimaliseer uw proces van Firefly gebruikend Microsoft Azure en presigned URLs ](./ex2.md){target="_blank"}

Ga terug naar [ Overzicht van de Diensten van Adobe Firefly ](./firefly-services.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../overview.md){target="_blank"}
