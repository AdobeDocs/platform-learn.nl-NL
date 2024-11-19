---
title: Foundation - Real-time klantprofiel - Visualiseer uw eigen real-time klantprofiel - API
description: Foundation - Real-time klantprofiel - Visualiseer uw eigen real-time klantprofiel - API
kt: 5342
doc-type: tutorial
exl-id: fe07d873-f4de-437e-815e-e6e6c06a691c
source-git-commit: 3a19e88e820c63294eff38bb8f699a9f690afcb9
workflow-type: tm+mt
source-wordcount: '2295'
ht-degree: 0%

---

# 2.1.3 Visualiseer uw eigen real-time klantprofiel - API

In deze oefening, zult u Postman en Adobe I/O gebruiken om Adobe Experience Platform APIs te vragen om uw eigen real-time klantenprofiel te bekijken.

## Context

In het profiel van de Klant in real time, worden alle profielgegevens getoond naast gebeurtenisgegevens, evenals bestaande segmentlidmaatschap. De getoonde gegevens kunnen van overal, van de toepassingen van de Adobe en externe oplossingen komen. Dit is de krachtigste weergave in Adobe Experience Platform, het ervaringssysteem.

Het profiel van de Klant in real time kan door alle toepassingen van de Adobe, maar ook door externe oplossingen zoals de Centers van de Vraag of in-store clienteling apps worden verbruikt. De manier om dit te doen is die externe oplossingen met Adobe Experience Platform APIs te verbinden.

## Uw id&#39;s

In het deelvenster Profielviewer op de website kunt u meerdere identiteiten vinden. Elke identiteit is gekoppeld aan een naamruimte.

![ Profiel van de Klant ](./images/identities.png)

Op het röntgenpaneel, kunnen wij vier verschillende combinaties identiteitskaart en Namespaces zien:

| Identiteit | Naamruimte |
|:-------------:| :---------------:|
| Experience Cloud-id (ECID) | 79943948563923140522865572770524243489 |
| Experience Cloud-id (ECID) | 70559351147248820114888181867542007989 |
| E-mailid | woutervangeluwe+18112024-01@gmail.com |
| Mobiel nummer-id | +32473622044+18112024-01 |

Onthoud deze id&#39;s voor de volgende stap.

## Uw Adobe I/O-project configureren

In deze oefening zult u Adobe I/O vrij intensief aan vraag tegen Platform APIs gebruiken. Volg de onderstaande stappen om Adobe I/O in te stellen.

Ga naar [ https://developer.adobe.com/console/home](https://developer.adobe.com/console/home)

![ Adobe I/O Nieuwe Integratie ](./images/iohome.png)

Selecteer de juiste Adobe Experience Platform-instantie in de rechterbovenhoek van het scherm. Uw instantie is `--aepImsOrgName--` . Klik **creëren nieuw project**.

![ Adobe I/O Nieuwe Integratie ](./images/iocomp.png)

Selecteer **+ toevoegen aan Project** en selecteren **API**.

![ Adobe I/O Nieuwe Integratie ](./images/adobe_io_access_api.png)

U zult dan dit zien:

![ Adobe I/O Nieuwe Integratie ](./images/api1.png)

Klik het **pictogram van Adobe Experience Platform**.
/images/api2.png)

Selecteer **Experience Platform API** en klik **daarna**.

![ Adobe I/O Nieuwe Integratie ](./images/api3.png)

Dit zie je nu. Geef een naam op voor de referentie: `--aepUserLdap-- - OAuth credential` . Klik **daarna**.

![ Adobe I/O Nieuwe Integratie ](./images/api4.png)

Vervolgens moet u een productprofiel selecteren waarmee wordt gedefinieerd welke machtigingen beschikbaar zijn voor deze integratie.

Selecteer de vereiste productprofielen.

>[!NOTE]
>
> De namen van productprofielen variëren in uw Adobe Experience Platform-instantie omdat dit instantiespectine is. U moet ten minste één productprofiel selecteren met de juiste toegangsrechten, die zijn ingesteld in de Adobe Admin Console en de interface voor AEP-machtigingen.

Klik **sparen Vormde API**.

![ Adobe I/O Nieuwe Integratie ](./images/api9.png)

Uw Adobe I/O-integratie is nu klaar.

![ Adobe I/O Nieuwe Integratie ](./images/api11.png)

Klik de **Download voor Postman** knoop en klik dan **OAuth Server-aan-Server** om een milieu van Postman te downloaden (wacht tot het milieu wordt gedownload, kan dit een paar seconden) nemen.

![ Adobe I/O Nieuwe Integratie ](./images/iopm.png)

Uw IO-project heeft momenteel een algemene naam. Je moet je integratie een vriendelijke naam geven. Klik op **Project X** (of gelijkaardige naam) zoals vermeld

![ Adobe I/O Nieuwe Integratie ](./images/api13.png)

Klik **uitgeven Project**.

![ Adobe I/O Nieuwe Integratie ](./images/api14.png)

Voer een naam en beschrijving in voor uw integratie: `--aepUserLdap-- AEP Tutorial` .

Klik **sparen**.

![ Adobe I/O Nieuwe Integratie ](./images/api15.png)

Uw Adobe I/O-integratie is nu voltooid.

![ Adobe I/O Nieuwe Integratie ](./images/api16.png)

>[!NOTE]
>
>Er is een extra stap om ervoor te zorgen dat dit Adobe I/O project toegang tot de toestemmingsmontages van Adobe Experience Platform heeft. De API-referentie van uw project moet worden toegevoegd aan de interface voor machtigingen van Adobe Experience Platform, waarvoor toegangsrechten voor systeembeheerders vereist zijn. De stappen worden hieronder beschreven, maar u kunt uw Beheerder van het Systeem moeten contacteren om dit voor u te laten verwerken voor het geval u niet de vereiste toegangsrechten hebt.

## AEP-machtigingen voor API-referentie

Ga naar [ Adobe Experience Platform ](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

Ga naar **Toestemmingen**, **Rollen**, en klik het relevante productprofiel.

>[!NOTE]
>
> De namen van productprofielen variëren in uw Adobe Experience Platform-instantie omdat dit instantiespectine is. U moet ten minste één productprofiel selecteren met de juiste toegangsrechten, die zijn ingesteld in de Adobe Admin Console en de interface voor AEP-machtigingen.

![ Toestemmingen ](./images/perm1.png)

Klik **API geloofsbrieven**.

![ Toestemmingen ](./images/perm2.png)

Klik op **+ Add API credentials**.

![ Toestemmingen ](./images/perm3.png)

Selecteer het pas gecreëerde project van Adobe I/O en klik **sparen**.

![ Toestemmingen ](./images/perm4.png)

## Postman-verificatie naar Adobe I/O

Ga naar [ https://www.postman.com/downloads/ ](https://www.postman.com/downloads/).

Download en installeer de relevante versie van Postman voor uw besturingssysteem.

![ Adobe I/O Nieuwe Integratie ](./images/getstarted.png)

Start de toepassing nadat u Postman hebt geïnstalleerd.

In Postman zijn er twee concepten: omgevingen en verzamelingen.

- Het milieu bevat al uw milieuvariabelen die min of meer samenhangend zijn. In het milieu, zult u dingen zoals IMSOrg van ons milieu van het Platform, naast veiligheidsgeloofsbrieven zoals uw Privé Sleutel en anderen vinden. Het omgevingsbestand is het bestand dat u tijdens de vorige Adobe I/O-installatie hebt gedownload. De naam ziet er als volgt uit: **`oauth_server_to_server.postman_environment.json`** .

- De verzameling bevat een aantal API-aanvragen die u kunt gebruiken. We gebruiken twee verzamelingen
   - 1 Verzameling voor verificatie naar Adobe I/0
   - 1 Verzameling voor de oefeningen in deze module
   - 1 inzameling voor de oefeningen in de module van Real-Time CDP, voor de Authoring van de Bestemming

Gelieve te downloaden het dossier [ postman.zip ](./../../../assets/postman/postman_profile.zip) aan uw lokale Desktop.

In dit {**dossier 0} postman.zip, zult u de volgende dossiers vinden:**

- `Adobe IO - OAuth.postman_collection.json`
- `AEP Tutorial.postman_collection.json`
- `Destination_Authoring_API.json`

Pak het {**dossier 0} postman.zip uit en sla deze 3 dossiers in een omslag op uw Desktop, samen met het gedownloade milieu van Postman van Adobe I/O op. U hebt deze 4 bestanden nodig in die map:**

![ Adobe I/O Nieuwe Integratie ](./images/pmfolder.png)

Ga terug naar Postman. Klik **Invoer**.

![ Adobe I/O Nieuwe Integratie ](./images/postmanui.png)

Klik **dossiers**.

![ Adobe I/O Nieuwe Integratie ](./images/choosefiles.png)

Navigeer naar de map op uw bureaublad waarin u de vier gedownloade bestanden hebt uitgepakt. Selecteer deze 4 dossiers tezelfdertijd en klik **Open**.

![ Adobe I/O Nieuwe Integratie ](./images/selectfiles.png)

Na het klikken **Open**, zal Postman u een overzicht van het Milieu en de Inzamelingen tonen u op het punt staat in te voeren. Klik **Invoer**.

![ Adobe I/O Nieuwe Integratie ](./images/impconfirm.png)

U hebt nu alles wat u nodig hebt in Postman om te gaan communiceren met Adobe Experience Platform via de API&#39;s.

Het eerste wat je moet doen, is ervoor zorgen dat je op de juiste manier geverifieerd bent. Om voor authentiek te worden verklaard, moet u om een toegangstoken verzoeken.

Zorg ervoor dat u het juiste Milieu hebt geselecteerd alvorens om het even welk verzoek uit te voeren. U kunt de momenteel geselecteerde omgeving controleren door de vervolgkeuzelijst Omgeving in de rechterbovenhoek te controleren.

De geselecteerde omgeving moet een naam hebben die vergelijkbaar is met deze, `--aepUserLdap-- OAuth Credential` .

![ Postman ](./images/envselemea.png)

Uw Postman-omgeving en -verzamelingen zijn nu geconfigureerd en werken. U kunt nu verifiëren van Postman naar Adobe I/O.

In de **Adobe IO - OAuth** inzameling, selecteer het verzoek met de naam **POST - krijg het Token van de Toegang**. Klik **verzenden**.

![ Postman ](./images/ioauth.png)

Na een paar seconden, zou u een reactie moeten zien die in de **1} sectie van het Lichaam {van Postman wordt getoond:**

![ Postman ](./images/ioauthresp.png)

Als uw configuratie succesvol was, zou u een gelijkaardige reactie moeten zien die de volgende informatie bevat:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| token_type | **drager** |
| access_token | **eyJhbGciOiJSU...jrNZ6mdaQ** |
| verloopt_in | **86399** |

Adobe I/O heeft u a **drager** - teken, met een specifieke waarde (zeer lange access_token) en een vervalvenster gegeven.

De token die we hebben ontvangen, is nu 24 uur geldig. Dit betekent dat na 24 uur, als u Postman wilt gebruiken om aan Adobe I/O voor authentiek te verklaren, u een nieuw teken zult moeten produceren door dit verzoek opnieuw in werking te stellen.

## Real-time klantprofiel-API, schema: profiel

Nu kunt u doorgaan en uw eerste aanvraag naar de realtime-API&#39;s van het klantprofiel van Platform verzenden.

In Postman, bepaal de plaats van de inzameling **Leerprogramma AEP**.

![ Postman ](./images/coll_enablement.png)

In **1. De verenigde Dienst van het Profiel**, klik het eerste verzoek met de naam **UPS - het Profiel van de GET door identiteitskaart van de Entiteit &amp; NS**.

![ Postman ](./images/upscall.png)

Voor dit verzoek zijn er drie vereiste variabelen:

| Sleutel | Waarde | Definitie |
|:-------------:| :---------------:| :---------------:| 
| entiteitId | **identiteitskaart** | de specifieke klant-id |
| entiteitIdNS | **namespace** | de specifieke naamruimte die van toepassing is op de id |
| schema.name | **_xdm.context.profile** | het specifieke schema waarvoor u informatie wilt ontvangen |

Dus als u Adobe Experience Platform API&#39;s wilt vragen om u alle profielgegevens voor uw eigen ECID terug te geven, moet u de aanvraag als volgt configureren:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| entiteitId | **yourECID** |
| entiteitIdNS | **ecid** |
| schema.name | **_xdm.context.profile** |

![ Postman ](./images/callecid.png)

U zou ook de **Kopbal** - gebieden van uw verzoek moeten verifiëren. Ga naar **Kopballen**. U zult dan dit zien:

![ Postman ](./images/callecidheaders.png)

>[!NOTE]
>
>U moet de naam opgeven van de Adobe Experience Platform-sandbox die u gebruikt. De naam van de x-sandbox moet `--aepSandboxName--` zijn.

| Sleutel | Waarde |
| ----------- | ----------- |
| x-sandbox-name | `--aepSandboxName--` |



Zodra u de zandbaknaam hebt gecontroleerd, verzendt de klik **** om uw verzoek naar Platform te verzenden.

U zou een directe reactie van Platform moeten krijgen, die u iets als dit toont:

![ Postman ](./images/callecidresponse.png)

Dit is de volledige reactie van Platform:

```javascript
{
    "A2_ETHkJxMvxbiEmIZlAj8Qn": {
        "entityId": "A2_ETHkJxMvxbiEmIZlAj8Qn",
        "mergePolicy": {
            "id": "64e4b0ed-dfc3-4084-8e67-643e977168d7"
        },
        "sources": [
            "672a10cdb015162aefedfc0f",
            "672a10b1a05e282aee19737c"
        ],
        "tags": [
            "0938B898-469A-4513-8E86-87464307120F:va7",
            "3ba34930-405e-4b31-aafa-bac22d35203e:va7"
        ],
        "identityGraph": [
            "G7z3JAFBY4I6Rzg",
            "A2_ETHkJxMvxbiEmIZlAj8Qn",
            "BkFvK4QcJpSPByuDGF4UAS0wMQ",
            "BUF9zMKLrXq72p4HpbsHv1SDGF4UAS0wMUBnbWFpbC5jb20",
            "A29btmFXmrfrYbXQWISCT9ZD"
        ],
        "entity": {
            "_experienceplatform": {
                "identification": {
                    "core": {
                        "ecid": "79943948563923140522865572770524243489",
                        "phoneNumber": "+32473622044+18112024-01",
                        "email": "woutervangeluwe+18112024-01@gmail.com"
                    }
                }
            },
            "userAccount": {
                "ID": "3688250"
            },
            "pushNotificationDetails": [
                {
                    "denylisted": false,
                    "token": "2E0945F186CE5ED8CBFD1EB519A8CF38BA2B28A67FB381D45AA15EE37D289214",
                    "identity": {
                        "namespace": {
                            "code": "ECID"
                        },
                        "id": "70559351147248820114888181867542007989"
                    },
                    "platform": "apns",
                    "appID": "com.adobe.demosystem.dxdemo"
                }
            ],
            "personalEmail": {
                "address": "woutervangeluwe+18112024-01@gmail.com"
            },
            "_repo": {
                "createDate": "2024-11-18T10:39:12.296Z"
            },
            "extSourceSystemAudit": {
                "lastUpdatedDate": "2024-11-19T07:46:52.001Z"
            },
            "testProfile": true,
            "mobilePhone": {
                "number": "+32473622044"
            },
            "consents": {
                "metadata": {
                    "time": "2024-11-19T07:46:52.001Z"
                },
                "idSpecific": {
                    "ECID": {
                        "70559351147248820114888181867542007989": {
                            "collect": {
                                "val": "y"
                            }
                        }
                    }
                }
            },
            "person": {
                "name": {
                    "lastName": "Van Geluwe",
                    "firstName": "Wouter"
                }
            },
            "userActivityRegions": {
                "IRL1": {
                    "captureTimestamp": "2024-11-19T07:46:51.239Z"
                }
            },
            "identityMap": {
                "ecid": [
                    {
                        "id": "70559351147248820114888181867542007989"
                    },
                    {
                        "id": "79943948563923140522865572770524243489"
                    }
                ],
                "email": [
                    {
                        "id": "woutervangeluwe+18112024-01@gmail.com"
                    }
                ],
                "phone": [
                    {
                        "id": "+32473622044+18112024-01"
                    }
                ],
                "userid": [
                    {
                        "id": "3688250"
                    }
                ]
            }
        },
        "lastModifiedAt": "2024-11-19T07:47:23Z"
    }
}
```

Dit zijn momenteel alle beschikbare profielgegevens in Platform voor deze ECID.

U hoeft de ECID niet te gebruiken om profielgegevens aan te vragen via het realtime klantprofiel van het platform. U kunt elke id in een naamruimte gebruiken om deze gegevens aan te vragen.

Laten wij terug naar Postman gaan en doen alsof wij het vraagcentrum zijn, en een verzoek verzenden naar Platform die namespace van **Telefoon** en uw mobiel aantal specificeren.

Dus als u aan de API&#39;s van het Platform wilt vragen om u alle profielinformatie voor een specifieke Telefoon terug te geven, zult u het verzoek als volgt moeten vormen:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| entiteitId | **uw telefoonaantal** |
| entiteitIdNS | **telefoon** (vervang ecid door telefoon) |
| schema.name | **_xdm.context.profile** |

Als uw telefoonaantal speciale symbolen zoals **+** bevat, moet u uw volledig telefoonaantal selecteren, met de rechtermuisknop klikken en **EncodeURIComponent** klikken.

![ Postman ](./images/encodephone.png)

Dan heb je het volgende:

![ Postman ](./images/callmobilenr.png)

U zou ook de **Kopbal** - gebieden van uw verzoek moeten verifiëren. Ga naar **Kopballen**. U zult dan dit zien:

![ Postman ](./images/callecidheaders.png)

>[!NOTE]
>
>U moet de naam opgeven van de Adobe Experience Platform-sandbox die u gebruikt. De naam van de x-sandbox moet `--aepSandboxName--` zijn.

| Sleutel | Waarde |
| ----------- | ----------- |
| x-sandbox-name | `--aepSandboxName--` |


Klik **verzenden** en verifieer de reactie, zult u zien dat het het zelfde zoals vóór is toen u ECID als identiteit gebruikte.

![ Postman ](./images/callmobilenrresponse.png)

Laten wij het zelfde ding voor uw e-mailadres doen door namespace van **e-mail** en uw e-mailadres te specificeren.

Dus als u aan de API&#39;s van Platform wilt vragen om u alle profielgegevens voor een specifiek e-mailadres terug te geven, moet u de aanvraag als volgt configureren:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| entiteitId | **u remail** |
| entiteitIdNS | **e-mail** (vervang Telefoon met e-mail) |
| schema.name | **_xdm.context.profile** |

Als uw e-mailadres speciale symbolen zoals **+** bevat, moet u uw volledig e-mailadres selecteren, met de rechtermuisknop klikken en **EncodeURIComponent** klikken.

![ Postman ](./images/encodeemail.png)

Dan heb je het volgende:

![ Postman ](./images/callemail.png)

U zou ook de **Kopbal** - gebieden van uw verzoek moeten verifiëren. Ga naar **Kopballen**. U zult dan dit zien:

>[!NOTE]
>
>U moet de naam opgeven van de Adobe Experience Platform-sandbox die u gebruikt. De naam van de x-sandbox moet `--aepSandboxName--` zijn.

![ Postman ](./images/callecidheaders.png)

| Sleutel | Waarde |
| ----------- | ----------- |
| x-sandbox-name | `--aepSandboxName--` |

Klik **verzenden** en verifieer de reactie, zult u opnieuw zien dat het het zelfde zoals vóór met ECID en telefoonaantal is.

![ Postman ](./images/callemailresponse.png)

Dit is een zeer belangrijke vorm van flexibiliteit die aan merken wordt aangeboden. Dit betekent dat elke omgeving een aanvraag naar Platform kan verzenden met behulp van een eigen id en naamruimte, zonder dat de complexiteit van meerdere naamruimten en id&#39;s wordt begrepen.

Als voorbeeld:

- Het Centrum van de Vraag kan gegevens van Platform verzoeken gebruikend de namespace **telefoon**
- Het Systeem van de Loyaliteit kan gegevens van Platform verzoeken gebruikend namespace **e-mail**
- online toepassingen kunnen namespace **gebruiken ecid**

Het Centrum van de Vraag weet niet noodzakelijk welk soort herkenningsteken in het Systeem van de Loyalty wordt gebruikt en het Systeem van de Loyalty weet niet noodzakelijk welk soort herkenningsteken door online toepassingen wordt gebruikt. Elk afzonderlijk systeem kan de informatie gebruiken die ze hebben en begrijpen om de informatie te krijgen die ze nodig hebben, wanneer ze die nodig hebben.

## Real-time klantprofiel-API, schema: profiel en ExperienceEvent

Nadat de API&#39;s van het platform zijn gecontroleerd op profielgegevens, kunnen we nu hetzelfde doen met ExperienceEvent-gegevens.

In Postman, bepaal de plaats van de inzameling **Leerprogramma AEP**.

![ Postman ](./images/coll_enablement.png)

In **1. De verenigde Dienst van het Profiel**, selecteer het tweede verzoek met de naam **UPS - het Profiel van de GET &amp; EE door identiteitskaart van de Entiteit &amp; NS**.

![ Postman ](./images/upseecall.png)

Voor dit verzoek zijn vier vereiste variabelen:

| Sleutel | Waarde | Definitie |
|:-------------:| :---------------:|  :---------------:| 
| schema.name | **_xdm.context.experienceEvent** | het specifieke schema waarvoor u informatie wilt ontvangen. In dit geval, zoeken wij gegevens die tegen het schema ExperienceEvent in kaart worden gebracht. |
| relatedSchema.name | **_xdm.context.profile** | Terwijl wij gegevens zoeken die tegen het schema ExperienceEvent in kaart worden gebracht, moeten wij een identiteit specificeren waarvoor wij die gegevens willen ontvangen. Het schema dat toegang tot identiteit heeft is het profiel-schema, zodat is relatedSchema hier het profiel-schema. |
| relatedEntiteitId | **identiteitskaart** | de specifieke klant-I D |
| relatedEntiteitIdNS | **namespace** | de specifieke naamruimte die van toepassing is op de id |

Dus als u aan de API&#39;s van Platform wilt vragen om u alle profielgegevens voor uw eigen ecid terug te geven, moet u de aanvraag als volgt configureren:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| schema.name | **_xdm.context.experienceEvent** |
| relatedSchema.name | **_xdm.context.profile** |
| relatedEntiteitId | **yourECID** |
| relatedEntiteitIdNS | **ecid** |

![ Postman ](./images/eecallecid.png)

U zou ook de **Kopbal** - gebieden van uw verzoek moeten verifiëren. Ga naar **Kopballen**. U zult dan dit zien:

![ Postman ](./images/eecallecidheaders.png)

>[!NOTE]
>
>U moet de naam opgeven van de Adobe Experience Platform-sandbox die u gebruikt. De naam van de x-sandbox moet `--aepSandboxName--` zijn.

| Sleutel | Waarde |
| ----------- | ----------- |
| x-sandbox-name | `--aepSandboxName--` |

Klik **verzenden** om uw verzoek naar Platform te verzenden.

U zou een directe reactie van Platform moeten krijgen, die u iets als dit toont:

![ Postman ](./images/eecallecidresponse.png)

Hieronder volgt de volledige reactie van Platform. In dit voorbeeld zijn er acht ExperienceEvents gekoppeld aan de ECID van deze klant. Bekijk hieronder de verschillende variabelen op het verzoek, aangezien wat u hieronder ziet het directe gevolg van uw configuratie in Lancering in vorige oefeningen is.

Wanneer het röntgendeelvenster de ExperienceEvent-informatie weergeeft, gebruikt het de onderstaande payload om de informatie te parseren en op te halen, zoals de productnaam (zoek naar productName in de onderstaande payload) en de productafbeelding URL (zoek naar productImageUrl in de onderstaande payload).

```javascript
{
    "_page": {
        "orderby": "timestamp",
        "start": "b1325606-9b96-4e51-b7dd-73aacf527c72-0",
        "count": 14,
        "next": ""
    },
    "children": [
        {
            "relatedEntityId": "A2_ETHkJxMvxbiEmIZlAj8Qn",
            "entityId": "b1325606-9b96-4e51-b7dd-73aacf527c72-0",
            "sourceId": "672a10b1074ceb2af0aa7034",
            "timestamp": 1731923802848,
            "entity": {
                "environment": {
                    "ipV4": "141.134.241.99",
                    "type": "browser",
                    "browserDetails": {
                        "userAgentClientHints": {
                            "mobile": false,
                            "platform": "macOS",
                            "brands": [
                                {
                                    "brand": "Chromium",
                                    "version": "130"
                                },
                                {
                                    "brand": "Google Chrome",
                                    "version": "130"
                                },
                                {
                                    "brand": "Not?A_Brand",
                                    "version": "99"
                                }
                            ]
                        },
                        "userAgent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/130.0.0.0 Safari/537.36",
                        "viewportHeight": 992,
                        "viewportWidth": 1920
                    }
                },
                "web": {
                    "webPageDetails": {
                        "name": "Home",
                        "viewName": "Home",
                        "pageViews": {
                            "value": 1
                        },
                        "URL": "https://dsn.adobe.com/web/vangeluw-QIMU"
                    },
                    "webReferrer": {
                        "URL": "https://auth.services.adobe.com/"
                    }
                },
                "_experienceplatform": {
                    "interactionDetails": {
                        "core": {
                            "channel": "web"
                        }
                    },
                    "demoEnvironment": {
                        "brandName": "vangeluw-QIMU"
                    },
                    "identification": {
                        "core": {
                            "ecid": "79943948563923140522865572770524243489"
                        }
                    }
                },
                "implementationDetails": {
                    "name": "https://ns.adobe.com/experience/alloy/reactor",
                    "version": "2.24.0+2.27.0",
                    "environment": "browser"
                },
                "identityMap": {
                    "ECID": [
                        {
                            "id": "79943948563923140522865572770524243489",
                            "authenticatedState": "ambiguous",
                            "primary": true
                        }
                    ]
                },
                "eventType": "web.webpagedetails.pageViews",
                "_id": "b1325606-9b96-4e51-b7dd-73aacf527c72-0",
                "placeContext": {
                    "localTime": "2024-11-18T10:56:42.848+01:00",
                    "localTimezoneOffset": -60
                },
                "device": {
                    "screenOrientation": "landscape",
                    "screenWidth": 1920,
                    "screenHeight": 1080
                },
                "timestamp": "2024-11-18T09:56:42.848Z"
            },
            "lastModifiedAt": "2024-11-18T09:56:45Z"
        },
    "_links": {
        "next": {
            "href": ""
        }
    }
}
```

Dit zijn momenteel alle beschikbare ExperienceEvent-gegevens in Platform voor deze ECID.

U hoeft de ECID niet te gebruiken om ExperienceEvent-gegevens aan te vragen vanuit Adobe Experience Platform in real-time profiel. U kunt elke id in een naamruimte gebruiken om deze gegevens aan te vragen.

Volgende Stap: [ 2.1.4 leidt tot een segment - UI ](./ex4.md)

[Terug naar module 2.1](./real-time-customer-profile.md)

[Terug naar alle modules](../../../overview.md)
