---
title: Aan de slag met Firefly Services
description: Aan de slag met Firefly Services
kt: 5342
doc-type: tutorial
exl-id: 52385c33-f316-4fd9-905f-72d2d346f8f5
source-git-commit: 608fc570f9aa172db3578664e793f35fb3f1bf50
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 0%

---

# 1.1.1 Aan de slag met Firefly Services

In deze oefening, zult u Postman en Adobe I/O gebruiken om de Diensten APIs van de Adobe Firefly te vragen.

## Uw Adobe I/O-project configureren

In deze oefening zult u Adobe I/O vrij intensief aan vraag tegen de Diensten APIs van de Firefly gebruiken. Volg de onderstaande stappen om Adobe I/O in te stellen.

Ga naar [ https://developer.adobe.com/console/home](https://developer.adobe.com/console/home)

![ Adobe I/O Nieuwe Integratie ](./images/iohome.png)

Selecteer de juiste instantie in de rechterbovenhoek van het scherm. Uw instantie is `--aepImsOrgName--` . Klik **creëren nieuw project**.

![ Adobe I/O Nieuwe Integratie ](./images/iocomp.png)

Selecteer **+ toevoegen aan Project** en selecteren **API**.

![ Adobe I/O Nieuwe Integratie ](./images/adobe_io_access_api.png)

U zult dan dit zien:

![ Adobe I/O Nieuwe Integratie ](./images/api1.png)

Selecteer **Creative Cloud** en klik **Firefly - de Diensten van de Firefly**. Klik **daarna**.

![ Adobe I/O Nieuwe Integratie ](./images/api3.png)

Dit zie je nu. Geef een naam op voor de referentie: `--aepUserLdap-- - Firefly Services OAuth credential` . Klik **daarna**.

![ Adobe I/O Nieuwe Integratie ](./images/api4.png)

Vervolgens moet u een productprofiel selecteren waarmee wordt gedefinieerd welke machtigingen beschikbaar zijn voor deze integratie.

Selecteer de Configuratie van de Diensten van de Firefly van het profiel **Standaard**.

Klik **sparen Vormde API**.

![ Adobe I/O Nieuwe Integratie ](./images/api9.png)

Uw Adobe I/O-integratie is nu klaar.

![ Adobe I/O Nieuwe Integratie ](./images/api11.png)

Klik de **Download voor Postman** knoop en klik dan **Server-aan-Server** om een milieu van Postman te downloaden.

![ Adobe I/O Nieuwe Integratie ](./images/iopm.png)

Uw IO-project heeft momenteel een algemene naam. Je moet je integratie een vriendelijke naam geven. Klik op **Project X** (of gelijkaardige naam) zoals vermeld

![ Adobe I/O Nieuwe Integratie ](./images/api13.png)

Klik **uitgeven Project**.

![ Adobe I/O Nieuwe Integratie ](./images/api14.png)

Voer een naam in voor uw integratie: `--aepUserLdap-- Firefly` .

Klik **sparen**.

![ Adobe I/O Nieuwe Integratie ](./images/api15.png)

De instellingen van uw Adobe I/O-integratie zijn nu voltooid.

![ Adobe I/O Nieuwe Integratie ](./images/api16.png)

## Postman-verificatie naar Adobe I/O

Ga naar [ https://www.postman.com/downloads/ ](https://www.postman.com/downloads/).

Download en installeer de relevante versie van Postman voor uw besturingssysteem.

![ Adobe I/O Nieuwe Integratie ](./images/getstarted.png)

Start de toepassing nadat u Postman hebt geïnstalleerd.

In Postman zijn er twee concepten: omgevingen en verzamelingen.

- Het omgevingsbestand bevat al uw omgevingsvariabelen die min of meer consistent zijn. In het milieu, zult u dingen zoals IMSOrg van uw milieu van de Adobe, naast veiligheidsgeloofsbrieven zoals uw identiteitskaart van de Cliënt en anderen vinden. Het omgevingsbestand is het bestand dat u tijdens de vorige Adobe I/O-installatie hebt gedownload. Het heet als volgt: **`oauth_server_to_server.postman_environment.json`** .

- De verzameling bevat een aantal API-aanvragen die u kunt gebruiken. We gebruiken twee verzamelingen
   - 1 Verzameling voor Authentificatie aan Adobe I/O
   - 1 Verzameling voor de oefeningen in deze module

Gelieve te downloaden het dossier [ postman.zip ](./../../../assets/postman/postman-ff.zip) aan uw lokale Desktop.

![ Adobe I/O Nieuwe Integratie ](./images/pmfolder.png)

In dit {**dossier 0} postman.zip, zult u de volgende dossiers vinden:**

- `Adobe IO - OAuth.postman_collection.json`
- `FF - Firefly Services Tech Insiders.postman_collection.json`

Pak het {**dossier 0} postman-ff.zip uit en sla deze 2 dossiers in een omslag op uw Desktop, samen met het gedownloade milieu van Postman van Adobe I/O op, dat het dossier `oauth_server_to_server.postman_environment.json` is.** U hebt deze 3 bestanden nodig in die map:

![ Adobe I/O Nieuwe Integratie ](./images/pmfolder1.png)

Ga terug naar Postman. Klik **Invoer**.

![ Adobe I/O Nieuwe Integratie ](./images/postmanui.png)

Klik **dossiers**.

![ Adobe I/O Nieuwe Integratie ](./images/choosefiles.png)

Navigeer naar de map op het bureaublad waarin u de twee gedownloade bestanden hebt uitgepakt. Selecteer deze 3 dossiers tezelfdertijd en klik **Open**.

![ Adobe I/O Nieuwe Integratie ](./images/selectfiles.png)

Na het klikken **Open**, zal Postman u een overzicht van het Milieu en de Inzamelingen tonen u op het punt staat in te voeren. Klik **Invoer**.

![ Adobe I/O Nieuwe Integratie ](./images/impconfirm.png)

U hebt nu alles wat u nodig hebt in Postman om te beginnen met het communiceren met Firefly Services via de API&#39;s.

Het eerste wat je moet doen, is ervoor zorgen dat je op de juiste manier geverifieerd bent. Om voor authentiek te worden verklaard, moet u om een toegangstoken verzoeken.

Zorg ervoor dat u het juiste milieu hebt geselecteerd alvorens om het even welk verzoek uit te voeren. U kunt de momenteel geselecteerde omgeving controleren door de vervolgkeuzelijst Omgeving in de rechterbovenhoek te controleren.

De geselecteerde omgeving moet een naam hebben die vergelijkbaar is met deze, `--aepUserLdap-- Firefly Services OAuth Credential` .

![ Postman ](./images/envselemea.png)

Uw Postman-omgeving en -verzamelingen zijn nu geconfigureerd en werken. U kunt nu verifiëren van Postman naar Adobe I/O.

In de **Adobe IO - OAuth** inzameling, selecteer het verzoek met de naam **POST - krijg het Token van de Toegang**. U zult dat onder **Params**, 2 variabelen worden van verwijzingen voorzien, `API_KEY` en `CLIENT_SECRET`. Deze variabelen zijn afkomstig uit de geselecteerde omgeving, `--aepUserLdap-- Firefly Services OAuth Credential` .

Klik **verzenden**.

![ Postman ](./images/ioauth.png)

Na het klikken **verzend**, zult u een reactie zien die in de **wordt getoond Hoofdtekst** sectie van Postman:

![ Postman ](./images/ioauthresp.png)

Als uw configuratie succesvol was, zou u een gelijkaardige reactie moeten zien die de volgende informatie bevat:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| token_type | **drager** |
| access_token | **eyJhbGciOiJSU...** |
| verloopt_in | **86399** |

Adobe I/O heeft u a **drager** - teken, met een specifieke waarde (zeer lange access_token) en een vervalvenster gegeven.

De token die we hebben ontvangen, is nu 24 uur geldig. Dit betekent dat na 24 uur, als u Postman wilt gebruiken om aan Adobe I/O voor authentiek te verklaren, u een nieuw teken zult moeten produceren door dit verzoek opnieuw in werking te stellen.

## Firefly Services API, Text 2 Image

Nu kunt u uw eerste verzoek naar de API&#39;s van de Firefly Services verzenden.

In de **FF - de inzameling van Tech Insiders van de Diensten van de Firefly**, selecteer het verzoek met de naam **POST - Firefly - T2I V3**. In de **sectie van het Lichaam**, zult u een standaardherinnering het zeggen `Horses in a field` zien. Klik **verzenden** om de Diensten van de Firefly te hebben die beeld produceren.

![ Firefly ](./images/ff1.png)

Vervolgens ziet u een vergelijkbaar antwoord met een URL voor de afbeelding. Kopieer de URL van de afbeelding en open deze in uw webbrowser.

![ Firefly ](./images/ff2.png)

U ziet nu een mooi beeldportretteren `horses in a field` .

![ Firefly ](./images/ff3.png)

U kunt vrij spelen met de API-aanvraag voordat u verdergaat met de volgende oefening.

Volgende Stap: [ 1.1.2 beelden van het Verzoek met specificaties ](./ex2.md)

[Terug naar module 1.1](./firefly-services.md)

[Terug naar alle modules](./../../../overview.md)
