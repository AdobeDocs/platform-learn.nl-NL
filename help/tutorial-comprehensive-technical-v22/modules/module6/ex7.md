---
title: Real-time CDP - Doelen SDK
description: Real-time CDP - Doelen SDK
kt: 5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 9585f858-569b-421e-a21d-aa623cd6c819
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '2386'
ht-degree: 0%

---

# 6.7 Doelen SDK

## 6.7.1 Uw Adobe I/O-project instellen

>[!IMPORTANT]
>
>Als u uw project van de Adobe I/O na December 2021 hebt gecreeerd, kunt u dat project hergebruiken, deze oefening overslaan en zich aan oefening 6.7.2 onmiddellijk bewegen.
>
>Als u uw Adobe I/O project vóór December 2021 creeerde, gelieve een nieuw project tot stand te brengen om het met de Authoring API van Doelen compatibel te maken.

In deze oefening zult u Adobe I/O vrij intensief aan vraag tegen Platform APIs gebruiken. Volg de onderstaande stappen om Adobe I/O in te stellen.

Ga naar [https://developer.adobe.com/console/home](https://developer.adobe.com/console/home)

![Adobe I/O Nieuwe integratie](../module3/images/iohome.png)

Selecteer de juiste Adobe Experience Platform-instantie in de rechterbovenhoek van het scherm. Uw instantie is `--envName--`.

![Adobe I/O Nieuwe integratie](../module3/images/iocomp.png)

Klikken **Nieuw project maken**.

![Adobe I/O Nieuwe integratie](../module3/images/adobe_io_new_integration.png) of
![Adobe I/O Nieuwe integratie](../module3/images/adobe_io_new_integration1.png)

Selecteren **+ Toevoegen aan project** en selecteert u **API**.

![Adobe I/O Nieuwe integratie](../module3/images/adobe_io_access_api.png)

U zult dan dit zien:

![Adobe I/O Nieuwe integratie](../module3/images/api1.png)

Klik op de knop **Adobe Experience Platform** pictogram.

![Adobe I/O Nieuwe integratie](../module3/images/api2.png)

Klikken **Experience Platform-API**.

![Adobe I/O Nieuwe integratie](../module3/images/api3.png)

Klik op **Next**.

![Adobe I/O Nieuwe integratie](../module3/images/next.png)

U kunt er nu voor kiezen om Adobe I/O uw beveiligingssleutel te laten genereren of een bestaand sleutelpaar te laten uploaden.

Kies **Optie 1 - Een sleutelpaar genereren**.

![Adobe I/O Nieuwe integratie](../module3/images/api4.png)

Klikken **Keypair genereren**.

![Adobe I/O Nieuwe integratie](../module3/images/generate.png)

Je ziet een spinner voor ongeveer 30 seconden.

![Adobe I/O Nieuwe integratie](../module3/images/spin.png)

U zult dan dit zien, en uw geproduceerd sleutelpaar zal als zip dossier worden gedownload: **config.zip**.

Het bestand uitpakken **config.zip** op uw bureaublad ziet u dat het 2 bestanden bevat:

![Adobe I/O Nieuwe integratie](../module3/images/zip.png)

- **certificate_pub.crt** is uw openbare-sleutelcertificaat. Vanuit een veiligheidsperspectief, is dit het certificaat dat vrij aan opstellingsintegratie met online toepassingen wordt gebruikt.
- **private.key** is uw persoonlijke sleutel. Dit mag nooit met iemand worden gedeeld. De persoonlijke sleutel is wat u gebruikt voor verificatie voor uw API-implementatie en moet een geheim zijn. Als u uw Privé Sleutel met iedereen deelt, kunnen zij tot uw implementatie toegang hebben en API misbruiken om kwaadwillige gegevens in Platform in te voeren en alle gegevens te halen die in Platform zitten.

![Adobe I/O Nieuwe integratie](../module3/images/config.png)

Zorg ervoor dat u de **config.zip** bestand op een veilige locatie. U hebt dit nodig voor de volgende stappen en voor toekomstige toegang tot Adobe I/O- en Adobe Experience Platform-API&#39;s.

Klik op **Next**.

![Adobe I/O Nieuwe integratie](../module3/images/next.png)

U moet nu de **Productprofiel(en)** voor uw integratie.

Selecteer de vereiste productprofielen.

**FYI**: in uw Adobe Experience Platform-exemplaar hebben de productprofielen een andere naam. U moet ten minste één productprofiel selecteren met de juiste toegangsrechten, die zijn ingesteld in de Adobe Admin Console.

![Adobe I/O Nieuwe integratie](../module3/images/api9.png)

Klikken **Configureerde API opslaan**.

![Adobe I/O Nieuwe integratie](../module3/images/saveconfig.png)

Je ziet een spinner voor een paar seconden.

![Adobe I/O Nieuwe integratie](../module3/images/api10.png)

En daarna zie je je integratie.

![Adobe I/O Nieuwe integratie](../module3/images/api11.png)

Klik op de knop **Downloaden naar Postman** en klik vervolgens op **Serviceaccount (JWT)** om een Postman-omgeving te downloaden (dit kan een paar seconden duren voordat de omgeving is gedownload).

![Adobe I/O Nieuwe integratie](../module3/images/iopm.png)

Omlaag schuiven totdat u ziet **Serviceaccount (JWT)**, waar u al uw integratiegegevens kunt vinden die worden gebruikt om de integratie met Adobe Experience Platform te configureren.

![Adobe I/O Nieuwe integratie](../module3/images/api12.png)

Uw IO-project heeft momenteel een algemene naam. Je moet je integratie een vriendelijke naam geven. Klikken op **Project 1** (of soortgelijke naam) zoals aangegeven

![Adobe I/O Nieuwe integratie](../module3/images/api13.png)

Klikken **Project bewerken**.

![Adobe I/O Nieuwe integratie](../module3/images/api14.png)

Voer een naam en beschrijving in voor uw integratie. Als naamgevingsconventie gebruiken we `AEP API --demoProfileLdap--`. Vervang ldap door uw ldap.
Als uw LDAP bijvoorbeeld vangeluw is, worden de naam en beschrijving van uw integratie gewijzigd in AEP API vangeluw.

Enter `AEP API --demoProfileLdap--` als de **Projecttitel**. Klikken **Opslaan**.

![Adobe I/O Nieuwe integratie](../module3/images/api15.png)

Uw Adobe I/O-integratie is nu voltooid.

![Adobe I/O Nieuwe integratie](../module3/images/api16.png)

## 6.7.2 Postman-verificatie naar Adobe I/O

Ga naar [https://www.getpostman.com/](https://www.getpostman.com/).

Klikken op **Aan de slag**.

![Adobe I/O Nieuwe integratie](../module3/images/getstarted.png)

Download en installeer vervolgens Postman.

![Adobe I/O Nieuwe integratie](../module3/images/downloadpostman.png)

Start de toepassing nadat u Postman hebt geïnstalleerd.

In Postman zijn er twee concepten: Omgevingen en verzamelingen.

- Het milieu bevat al uw milieuvariabelen die min of meer samenhangend zijn. In het Milieu, zult u dingen zoals IMSOrg van ons milieu van het Platform, naast veiligheidsgeloofsbrieven zoals uw Privé Sleutel en anderen vinden. Het omgevingsbestand is het bestand dat u tijdens de vorige Adobe I/O-installatie hebt gedownload. De naam ziet er als volgt uit: **service.postman_environment.json**.

- De verzameling bevat een aantal API-aanvragen die u kunt gebruiken. We gebruiken twee verzamelingen
   - 1 Verzameling voor Authentificatie aan Adobe I/0
   - 1 Verzameling voor de oefeningen in deze module
   - 1 inzameling voor de oefeningen in de module van Real-Time CDP, voor de Authoring van de Bestemming

Download het bestand [postman.zip](../../assets/postman/postman_profile.zip) naar uw lokale bureaublad.

In dit **postman.zip** , vindt u de volgende bestanden:

- `_Adobe I-O - Token.postman_collection.json`
- `_Adobe Experience Platform Enablement.postman_collection.json`
- `Destination_Authoring_API.json`

De **postman.zip** Deze 3 bestanden samen met de gedownloade Postman-omgeving van Adobe I/O opslaan en opslaan in een map op uw bureaublad. U hebt deze 4 bestanden nodig in die map:

![Adobe I/O Nieuwe integratie](../module3/images/pmfolder.png)

Ga terug naar Postman. Klikken **Importeren**.

![Adobe I/O Nieuwe integratie](../module3/images/postmanui.png)

Klikken **Bestanden uploaden**.

![Adobe I/O Nieuwe integratie](../module3/images/choosefiles.png)

Navigeer naar de map op uw bureaublad waarin u de vier gedownloade bestanden hebt uitgepakt. Selecteer deze 4 bestanden tegelijk en klik op **Openen**.

![Adobe I/O Nieuwe integratie](../module3/images/selectfiles.png)

Nadat u hebt geklikt **Openen** Postman geeft u een overzicht van de omgeving en verzamelingen die u wilt importeren. Klikken **Importeren**.

![Adobe I/O Nieuwe integratie](../module3/images/impconfirm.png)

U hebt nu alles wat u nodig hebt in Postman om te gaan communiceren met Adobe Experience Platform via de API&#39;s.

Het eerste wat je moet doen, is ervoor zorgen dat je op de juiste manier geverifieerd bent. Om voor authentiek te worden verklaard, moet u om een toegangstoken verzoeken.

Zorg ervoor dat u het juiste Milieu hebt geselecteerd alvorens om het even welk verzoek uit te voeren. U kunt de momenteel geselecteerde omgeving controleren door de vervolgkeuzelijst Omgeving in de rechterbovenhoek te controleren.

De geselecteerde omgeving moet een naam hebben die vergelijkbaar is met deze:

![Postman](../module3/images/envselemea.png)

Klik op de knop **oog** pictogram en klik vervolgens op **Bewerken** om de persoonlijke sleutel in het omgevingsbestand bij te werken.

![Postman](../module3/images/gear.png)

Dan zie je dit. Alle velden zijn vooraf ingevuld, behalve het veld **PRIVATE_KEY**.

![Postman](../module3/images/pk2.png)

De persoonlijke sleutel is gegenereerd toen u uw Adobe I/O-project hebt gemaakt. Het bestand is gedownload als een ZIP-bestand met de naam **config.zip**. Pak dat ZIP-bestand uit op uw bureaublad.

![Postman](../module3/images/pk3.png)

De map openen **config** en opent u het bestand **private.key** met de gewenste teksteditor.

![Postman](../module3/images/pk4.png)

Vervolgens ziet u iets dat hierop lijkt, en kopieert u alle tekst naar het klembord.

![Postman](../module3/images/pk5.png)

Ga terug naar Postman en plak de persoonlijke sleutel in de velden naast de variabele **PRIVATE_KEY** voor beide kolommen **EERSTE WAARDE** en **HUIDIGE WAARDE**. Klikken **Opslaan**.

![Postman](../module3/images/pk6.png)

Uw Postman-omgeving en -verzamelingen zijn nu geconfigureerd en werken. U kunt nu verifiëren van Postman naar Adobe I/O.

Hiervoor moet u een externe bibliotheek laden die zorgt voor de codering en ontsleuteling van communicatie. Als u deze bibliotheek wilt laden, moet u de aanvraag met de naam uitvoeren **INIT: Cryptobibliotheek laden voor RS256**. Selecteer deze aanvraag in het dialoogvenster **_Adobe I/O - Symbolische verzameling** en je ziet het midden op je scherm.

![Postman](../module3/images/iocoll.png)

![Postman](../module3/images/cryptolib.png)

Klik op blauw **Verzenden** knop. Na een paar seconden, zou u een reactie moeten zien die in wordt getoond **Lichaam** sectie van Postman:

![Postman](../module3/images/cryptoresponse.png)

Met de cryptobibliotheek nu geladen, kunnen wij aan Adobe I/O voor authentiek verklaren.

In de **\_Adobe I/O - Symbolische verzameling** selecteert u de aanvraag met de naam **IMS: JWT Genereren + Auth**. Ook hier ziet u de aanvraagdetails midden in het scherm.

![Postman](../module3/images/ioauth.png)

Klik op blauw **Verzenden** knop. Na een paar seconden, zou u een reactie moeten zien die in wordt getoond **Lichaam** sectie van Postman:

![Postman](../module3/images/ioauthresp.png)

Als uw configuratie succesvol was, zou u een gelijkaardige reactie moeten zien die de volgende informatie bevat:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| token_type | **drager** |
| access_token | **eyJ4NXUiOiJpbXNfbmEx...QT7mqZkumN1tdsPEioOEl4087Dg** |
| verloopt_in | **86399973** |

Adobe I/O heeft u een **drager**-token, met een specifieke waarde (dit zeer lange access_token) en een vervalvenster.

De token die we hebben ontvangen, is nu 24 uur geldig. Dit betekent dat na 24 uur, als u Postman wilt gebruiken om aan Adobe I/O voor authentiek te verklaren, u een nieuw teken zult moeten produceren door dit verzoek opnieuw in werking te stellen.

## 6.7.3 Definiëren van eindpunt en formaat

Voor deze oefening, zult u een eindpunt nodig hebben om te vormen zodat wanneer een segment kwalificeert, de kwalificatiegebeurtenis aan dat eindpunt kan worden gestroomd. In deze oefening, zult u een steekproefeindpunt gebruiken gebruikend [https://webhook.site/](https://webhook.site/). Ga naar [https://webhook.site/](https://webhook.site/)Daar zie je iets gelijkaardigs. Klikken **Kopiëren naar klembord** om de URL te kopiëren. U zult deze url in de volgende oefening moeten specificeren. De URL in dit voorbeeld is `https://webhook.site/e0eb530c-15b4-4a29-8b50-e40877d5490a`.

![Gegevensinname](./images/webhook1.png)

Wat het formaat betreft, zullen wij een standaardmalplaatje gebruiken dat segmentkwalificaties of onkwalificaties samen met meta-gegevens zoals klantenherkenningstekens stroomt. De malplaatjes kunnen worden aangepast om aan de verwachtingen van specifieke eindpunten te voldoen, maar in deze oefening zullen wij een standaardmalplaatje opnieuw gebruiken, dat in een nuttige last als dit zal resulteren die aan het eindpunt zal worden gestroomd.

```json
{
  "profiles": [
    {
      "identities": [
        {
          "type": "ecid",
          "id": "64626768309422151580190219823409897678"
        }
      ],
      "AdobeExperiencePlatformSegments": {
        "add": [
          "f58c723c-f1e5-40dd-8c79-7bb4ab47f041"
        ],
        "remove": []
      }
    }
  ]
}
```

## 6.7.4 Een server- en sjabloonconfiguratie maken

De eerste stap om uw eigen Doel in Adobe Experience Platform te creëren is een server en malplaatjeconfiguratie tot stand te brengen.

Ga om dat te doen naar **Authoring-API voor doelen**, naar **Doelservers en sjablonen** en klik om het verzoek te openen **POST - Een doelserverconfiguratie maken**. Dan zie je dit. Onder **Kopteksten** moet u de waarde voor de toets handmatig bijwerken **x-sandbox-name** en stel deze in op `--aepSandboxId--`. Selecteer de waarde **{{SANDBOX_NAME}}**.

![Gegevensinname](./images/sdkpm1.png)

Vervangen door `--aepSandboxId--`.

![Gegevensinname](./images/sdkpm2.png)

Ga vervolgens naar **Lichaam**. de tijdelijke aanduiding selecteren **{{body}}**.

![Gegevensinname](./images/sdkpm3.png)

U moet nu de tijdelijke aanduiding vervangen **{{body}}** met de onderstaande code:

```json
{
    "name": "Custom HTTP Destination",
    "destinationServerType": "URL_BASED",
    "urlBasedDestination": {
        "url": {
            "templatingStrategy": "PEBBLE_V1",
            "value": "yourURL"
        }
    },
    "httpTemplate": {
        "httpMethod": "POST",
        "requestBody": {
            "templatingStrategy": "PEBBLE_V1",
            "value": "{\n    \"profiles\": [\n    {%- for profile in input.profiles %}\n        {\n            \"identities\": [\n            {%- for idMapEntry in profile.identityMap -%}\n            {%- set namespace = idMapEntry.key -%}\n                {%- for identity in idMapEntry.value %}\n                {\n                    \"type\": \"{{ namespace }}\",\n                    \"id\": \"{{ identity.id }}\"\n                }{%- if not loop.last -%},{%- endif -%}\n                {%- endfor -%}{%- if not loop.last -%},{%- endif -%}\n            {% endfor %}\n            ],\n            \"AdobeExperiencePlatformSegments\": {\n                \"add\": [\n                {%- for segment in profile.segmentMembership.ups | added %}\n                    \"{{ segment.key }}\"{%- if not loop.last -%},{%- endif -%}\n                {% endfor %}\n                ],\n                \"remove\": [\n                {#- Alternative syntax for filtering segments by status: -#}\n                {% for segment in removedSegments(profile.segmentMembership.ups) %}\n                    \"{{ segment.key }}\"{%- if not loop.last -%},{%- endif -%}\n                {% endfor %}\n                ]\n            }\n        }{%- if not loop.last -%},{%- endif -%}\n    {% endfor %}\n    ]\n}"
        },
        "contentType": "application/json"
    }
}
```

Nadat u de bovenstaande code hebt geplakt, moet u het veld handmatig bijwerken **urlBasedDestination.url.value** en moet u deze instellen op de URL van de webhaak die u in de vorige stap hebt gemaakt, namelijk `https://webhook.site/e0eb530c-15b4-4a29-8b50-e40877d5490a` in dit voorbeeld.

![Gegevensinname](./images/sdkpm4.png)

Na het bijwerken van het veld **urlBasedDestiantion.url.value** Het moet er zo uitzien. Klikken **Verzenden**.

![Gegevensinname](./images/sdkpm5.png)

Na klikken **Verzenden**, wordt uw serversjabloon gemaakt en als onderdeel van de reactie ziet u een veld met de naam **instanceId**. Schrijf het neer, aangezien u het in de volgende stap zult nodig hebben. In dit voorbeeld wordt **instanceId** is
`eb0f436f-dcf5-4993-a82d-0fcc09a6b36c`.

![Gegevensinname](./images/sdkpm6.png)

## 6.7.5 Creeer uw bestemmingsconfiguratie

In Postman, onder **Authoring-API voor doelen**, ga naar **Doelconfiguraties** en klik om het verzoek te openen **POST - Een doelconfiguratie maken**. Dan zie je dit. Onder **Kopteksten** moet u de waarde voor de toets handmatig bijwerken **x-sandbox-name** en stel deze in op `--aepSandboxId--`. Selecteer de waarde **{{SANDBOX_NAME}}**.

![Gegevensinname](./images/sdkpm7.png)

Vervangen door `--aepSandboxId--`.

![Gegevensinname](./images/sdkpm8.png)

Ga vervolgens naar **Lichaam**. de tijdelijke aanduiding selecteren **{{body}}**.

![Gegevensinname](./images/sdkpm9.png)

U moet nu de tijdelijke aanduiding vervangen **{{body}}** met de onderstaande code:

```json
{
    "name": "--demoProfileLdap-- - Webhook",
    "description": "Exports segment qualifications and identities to a custom webhook via Destination SDK.",
    "status": "TEST",
    "customerAuthenticationConfigurations": [
        {
            "authType": "BEARER"
        }
    ],
    "customerDataFields": [
        {
            "name": "endpointsInstance",
            "type": "string",
            "title": "Select Endpoint",
            "description": "We could manage several instances across the globe for REST endpoints that our customers are provisioned for. Select your endpoint in the dropdown list.",
            "isRequired": true,
            "enum": [
                "US",
                "EU",
                "APAC",
                "NZ"
            ]
        }
    ],
    "uiAttributes": {
        "documentationLink": "https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=en",
        "category": "streaming",
        "connectionType": "Server-to-server",
        "frequency": "Streaming"
    },
    "identityNamespaces": {
        "ecid": {
            "acceptsAttributes": true,
            "acceptsCustomNamespaces": false
        }
    },
    "segmentMappingConfig": {
        "mapExperiencePlatformSegmentName": true,
        "mapExperiencePlatformSegmentId": true,
        "mapUserInput": false
    },
    "aggregation": {
        "aggregationType": "BEST_EFFORT",
        "bestEffortAggregation": {
            "maxUsersPerRequest": "1000",
            "splitUserById": false
        }
    },
    "schemaConfig": {
        "profileRequired": false,
        "segmentRequired": true,
        "identityRequired": true
    },
    "destinationDelivery": [
        {
            "authenticationRule": "NONE",
            "destinationServerId": "yourTemplateInstanceID"
        }
    ]
}
```

![Gegevensinname](./images/sdkpm11.png)

Nadat u de bovenstaande code hebt geplakt, moet u het veld handmatig bijwerken **destinationDelivery. destinationServerId** en moet u deze instellen op **instanceId** van het malplaatje van de bestemmingsserver u in de vorige stap creeerde, die `eb0f436f-dcf5-4993-a82d-0fcc09a6b36c` in dit voorbeeld. Volgende, klik **Verzenden**.

![Gegevensinname](./images/sdkpm10.png)

Dan zie je dit antwoord.

![Gegevensinname](./images/sdkpm12.png)

Je bestemming is nu gemaakt in Adobe Experience Platform. Laten we daar naartoe gaan en het controleren.

Ga naar [Adobe Experience Platform](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![Gegevensinname](../module2/images/home.png)

Voordat u verdergaat, moet u een **sandbox**. De sandbox die moet worden geselecteerd, krijgt een naam ``--aepSandboxId--``. U kunt dit doen door op de tekst te klikken **[!UICONTROL Productieproduct]** in de blauwe lijn boven op het scherm. Nadat u de juiste [!UICONTROL sandbox], ziet u de schermwijziging en nu bent u in uw eigen omgeving [!UICONTROL sandbox].

![Gegevensinname](../module2/images/sb1.png)

Ga in het linkermenu naar **Doelen**, klikt u op **Catalogus** en naar de categorie schuiven **Streaming**. Je ziet je bestemming nu beschikbaar.

![Gegevensinname](./images/destsdk1.png)

## 6.7.6 Verbinding uw segment aan uw bestemming

In **Doelen** > **Catalogus**, klikt u op **Instellen** op uw bestemming beginnen segmenten aan uw nieuwe bestemming toe te voegen.

![Gegevensinname](./images/destsdk2.png)

Voer bijvoorbeeld een dummytoken voor toonder in **1234**. Klikken **Verbinden met doel**.

![Gegevensinname](./images/destsdk3.png)

Dan zie je dit. Als naam voor uw bestemming, gebruik `--demoProfileLdap-- - Webhook`. Selecteer een eindpunt van keus, in dit voorbeeld **EU**. Klik op **Next**.

![Gegevensinname](./images/destsdk4.png)

U kunt desgewenst een beleid voor gegevensbeheer selecteren. Klik op **Next**.

![Gegevensinname](./images/destsdk5.png)

Selecteer het segment dat u eerder hebt gemaakt en dat een naam heeft `--demoProfileLdap-- - Interest in PROTEUS FITNESS JACKSHIRT`. Klik op **Next**.

![Gegevensinname](./images/destsdk6.png)

Dan zie je dit. Zorg ervoor dat u de **BRONVELD** `--aepTenantId--.identification.core.ecid` naar het veld `Identity: ecid`. Klik op **Next**.

![Gegevensinname](./images/destsdk7.png)

Klikken **Voltooien**.

![Gegevensinname](./images/destsdk8.png)

Uw bestemming is nu live. Nieuwe segmentkwalificaties worden nu gestreamd naar uw aangepaste webhaak.

![Gegevensinname](./images/destsdk9.png)

## 6.7.7 Test uw segment activeren

Ga naar [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Nadat je je hebt aangemeld bij je Adobe ID, kun je dit zien. Klik op uw websiteproject om het te openen.

![DSN](../module0/images/web8.png)

U kunt nu de onderstaande workflow volgen om toegang te krijgen tot de website. Klikken **Integraties**.

![DSN](../module0/images/web1.png)

Op de **Integraties** pagina, moet u het bezit van de Inzameling van Gegevens selecteren dat in oefening 0.1 werd gecreeerd.

![DSN](../module0/images/web2.png)

Vervolgens wordt uw demowebsite geopend. Selecteer de URL en kopieer deze naar het klembord.

![DSN](../module0/images/web3.png)

Open een nieuw Incognito-browservenster.

![DSN](../module0/images/web4.png)

Plak de URL van uw demowebsite, die u in de vorige stap hebt gekopieerd. Vervolgens wordt u gevraagd u aan te melden met uw Adobe ID.

![DSN](../module0/images/web5.png)

Selecteer uw accounttype en voltooi het aanmeldingsproces.

![DSN](../module0/images/web6.png)

Uw website wordt vervolgens geladen in een Incognito-browservenster. Voor elke demonstratie, zult u een vers, incognito browser venster moeten gebruiken om uw demowebsite URL te laden.

![DSN](../module0/images/web7.png)

Van de **Luminantie** homepage, ga naar **Mannen** en klik op het product **PROTEUS FITNESS JACKSHIRT**.

![Gegevensinname](./images/homenadia.png)

U hebt nu de productpagina bezocht voor **PROTEUS FITNESS JACKSHIRT** Dit betekent dat u nu in aanmerking komt voor het segment dat u eerder in deze oefening hebt gemaakt.

![Gegevensinname](./images/homenadiapp.png)

Wanneer u de profielviewer opent en naar **Segmenten**, ziet u dat het segment in aanmerking komt.

![Gegevensinname](./images/homenadiapppb.png)

Ga nu terug naar uw open webhaak op [https://webhook.site/](https://webhook.site/), waar u een nieuw inkomend verzoek zou moeten zien, dat uit Adobe Experience Platform voortkomt en de gebeurtenis van de segmentkwalificatie bevat.

![Gegevensinname](./images/destsdk10.png)

Volgende stap: [Samenvatting en voordelen](./summary.md)

[Ga terug naar module 6](./real-time-cdp-build-a-segment-take-action.md)

[Terug naar alle modules](../../overview.md)
