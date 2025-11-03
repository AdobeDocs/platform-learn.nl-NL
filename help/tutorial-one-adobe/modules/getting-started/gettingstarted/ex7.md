---
title: Aan de slag - Postman instellen
description: Aan de slag - Postman instellen
kt: 5342
doc-type: tutorial
exl-id: c2a28819-5877-4f53-96c0-e4e5095d8cec
source-git-commit: 899cb9b17702929105926f216382afcde667a1b6
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# Optie 1: Postman gebruiken

>[!IMPORTANT]
>
>Als u een werknemer van Adobe bent, volg de instructies aan [&#x200B; installeer PostBuster &#x200B;](./ex8.md){target="_blank"}!

## Video

In deze video krijgt u een uitleg en demonstratie van alle stappen die bij deze oefening betrokken zijn.

>[!VIDEO](https://video.tv.adobe.com/v/3476495?quality=12&learn=on)

## Postman-omgeving downloaden

Ga naar [&#x200B; https://developer.adobe.com/console/home &#x200B;](https://developer.adobe.com/console/home){target="_blank"} en open uw project.

![&#x200B; de Nieuwe Integratie van Adobe I/O &#x200B;](./images/iopr.png)

Klik **Firefly - Firefly Services** API. Dan, klik **Download voor Postman** en kies **Server-aan-Server** om een milieu van Postman te downloaden.

![&#x200B; de Nieuwe Integratie van Adobe I/O &#x200B;](./images/iopm.png)

## Postman-verificatie naar Adobe I/O

De download en installeert de relevante versie van Postman voor uw OS bij [&#x200B; Downloads van Postman &#x200B;](https://www.postman.com/downloads/){target="_blank"}.

![&#x200B; de Nieuwe Integratie van Adobe I/O &#x200B;](./images/getstarted.png)

Start de toepassing.

In Postman zijn er twee concepten: omgevingen en verzamelingen.

Het omgevingsbestand bevat al uw omgevingsvariabelen die min of meer consistent zijn. In het milieu, zult u dingen zoals IMSOrg van uw milieu van Adobe, naast veiligheidsgeloofsbrieven zoals uw identiteitskaart van de Cliënt en anderen vinden. U hebt het omgevingsbestand tijdens de Adobe I/O-installatie eerder gedownload en de naam is **`oauth_server_to_server.postman_environment.json`** .

De verzameling bevat een aantal API-aanvragen die u kunt gebruiken. U gebruikt de onderstaande verzamelingen:

- 1 Verzameling voor verificatie naar Adobe I/O
- 1 Verzameling voor de oefeningen van de Diensten van Adobe Firefly in deze module
- 1 Inzameling voor de oefeningen van Adobe Frame.io V4 in deze module

Download [&#x200B; postman-ff.zip &#x200B;](./../../../assets/postman/postman-ff.zip){target="_blank"} aan uw lokale Desktop.

![&#x200B; de Nieuwe Integratie van Adobe I/O &#x200B;](./images/pmfolder.png)

In **postman-ff.zip** dossier zijn de volgende dossiers:

- `Adobe IO - OAuth.postman_collection.json`
- `FF - Firefly Services Tech Insiders.postman_collection.json`
- `Frame.io V4 - Tech Insiders.postman_collection.json`

Unzip **postman-ff.zip** en sla de volgende dossiers in een omslag op uw Desktop op:

- `Adobe IO - OAuth.postman_collection.json`
- `FF - Firefly Services Tech Insiders.postman_collection.json`
- `Frame.io V4 - Tech Insiders.postman_collection.json`
- `oauth_server_to_server.postman_environment.json`

![&#x200B; de Nieuwe Integratie van Adobe I/O &#x200B;](./images/pmfolder1.png)

In Postman, uitgezochte **Invoer**.

![&#x200B; de Nieuwe Integratie van Adobe I/O &#x200B;](./images/postmanui.png)

Selecteer **Dossiers**.

![&#x200B; de Nieuwe Integratie van Adobe I/O &#x200B;](./images/choosefiles.png)

Kies alle dossiers van de omslag, dan selecteren **Open** en **Invoer**.

![&#x200B; de Nieuwe Integratie van Adobe I/O &#x200B;](./images/selectfiles.png)

Klik **Invoer**.

![&#x200B; de Nieuwe Integratie van Adobe I/O &#x200B;](./images/impconfirm.png)

Nu hebt u alles wat u nodig hebt in Postman om te beginnen met Firefly Services via de API&#39;s.

## Een toegangstoken aanvragen

Daarna, om ervoor te zorgen u behoorlijk voor authentiek wordt verklaard, moet u om een toegangstoken verzoeken.

Zorg ervoor dat u het juiste milieu hebt geselecteerd alvorens om het even welk verzoek uit te voeren door milieu-dropdown lijst in de hoogste juiste hoek te verifiëren. De geselecteerde omgeving moet een naam hebben die vergelijkbaar is met deze, `--aepUserLdap-- One Adobe OAuth Credential` .

![&#x200B; Postman &#x200B;](./images/envselemea1.png)

De geselecteerde omgeving moet een naam hebben die vergelijkbaar is met deze, `--aepUserLdap-- One Adobe OAuth Credential` .

![&#x200B; Postman &#x200B;](./images/envselemea.png)

Nu uw Postman-omgeving en -verzamelingen zijn geconfigureerd en werken, kunt u verificatie uitvoeren van Postman naar Adobe I/O.

In **Adobe IO - OAuth** inzameling, selecteer het verzoek genoemd **POST - krijg het Token van de Toegang** en selecteer **verzend**.

Bericht onder **de Params van de Vraag**, worden twee variabelen van verwijzingen voorzien, `API_KEY` en `CLIENT_SECRET`. Deze variabelen zijn afkomstig uit de geselecteerde omgeving, `--aepUserLdap-- One Adobe OAuth Credential` .

![&#x200B; Postman &#x200B;](./images/ioauth.png)

Als succesvol, een reactie die een dragerteken, een toegangstoken, en een vervalsingsvenster bevat verschijnt in de **sectie van het Lichaam** &lbrace;van Postman.

![&#x200B; Postman &#x200B;](./images/ioauthresp.png)

U zou een gelijkaardige reactie moeten zien die de volgende informatie bevat:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| token_type | **drager** |
| access_token | **eyJhbGciOiJSUz...** |
| verloopt_in | **86399** |

Adobe I/O **drager-teken** heeft een specifieke waarde (zeer lange access_token) en een vervalvenster en is nu geldig voor 24 uren. Dit betekent dat als u Postman na 24 uur wilt gebruiken voor interactie met Adobe API&#39;s, u een nieuw token moet genereren door dit verzoek opnieuw uit te voeren.

Uw Postman-omgeving is nu geconfigureerd en werkt.

## Volgende stappen

Ga naar [&#x200B; Toepassingen om &#x200B;](./ex9.md){target="_blank"} te installeren

Ga terug naar [&#x200B; Begonnen het worden &#x200B;](./getting-started.md){target="_blank"}

Ga terug naar [&#x200B; Alle modules &#x200B;](./../../../overview.md){target="_blank"}
