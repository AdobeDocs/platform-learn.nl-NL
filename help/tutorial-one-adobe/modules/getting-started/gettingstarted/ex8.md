---
title: Aan de slag - Postman instellen
description: Aan de slag - Postman instellen
kt: 5342
doc-type: tutorial
exl-id: fc1ee238-cce8-40a9-aba7-3605019a0077
source-git-commit: a1da1c73cbddacde00211190a1ca3d36f7a2c329
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Optie 2: PostBuster instellen

>[!IMPORTANT]
>
>Als u geen werknemer van Adobe bent, volg de instructies om Postman [&#128279;](./ex7.md){target="_blank"} te installeren 0&rbrace;.  De onderstaande instructies zijn alleen bedoeld voor werknemers van Adobe.

## PostBuster installeren

Ga naar [&#x200B; https://adobe.service-now.com/esc?id=adb_esc_kb_article&sysparm_article=KB0020542 &#x200B;](https://adobe.service-now.com/esc?id=adb_esc_kb_article&sysparm_article=KB0020542){target="_blank"}.

Klik om de recentste versie van **PostBuster** te downloaden.

![&#x200B; PostBuster &#x200B;](./images/pb1.png)

Download de juiste versie voor uw besturingssysteem.

![&#x200B; PostBuster &#x200B;](./images/pb2.png)

Open PostBuster nadat het downloaden is voltooid en geïnstalleerd. Dan moet je dit zien. Klik **Invoer**.

![&#x200B; PostBuster &#x200B;](./images/pb3.png)

De download [&#x200B; postbuster.json.zip &#x200B;](./../../../assets/postman/postbuster.json.zip){target="_blank"} en haalt het op uw Desktop uit.

![&#x200B; PostBuster &#x200B;](./images/pbpb.png)

Klik **kiezen een Dossier**.

![&#x200B; PostBuster &#x200B;](./images/pb4.png)

Selecteer het dossier **postbuster.json**. Klik **Open**.

![&#x200B; PostBuster &#x200B;](./images/pb5.png)

Dan moet je dit zien. Klik **Scannen**.

![&#x200B; PostBuster &#x200B;](./images/pb6.png)

Klik **Invoer**.

![&#x200B; PostBuster &#x200B;](./images/pb7.png)

Dan moet je dit zien. Klik om de geïmporteerde verzameling te openen.

![&#x200B; PostBuster &#x200B;](./images/pb8.png)

Nu zie je je collectie. U moet nog een milieu vormen om sommige omgevingsvariabelen te houden.

![&#x200B; PostBuster &#x200B;](./images/pb9.png)

Klik **Milieu van de Basis** en klik dan **uitgeven** pictogram.

![&#x200B; PostBuster &#x200B;](./images/pb10.png)

Dan moet je dit zien.

![&#x200B; PostBuster &#x200B;](./images/pb11.png)

Kopieer hieronder milieu placeholder en kleef het in het **Milieu van de Basis**, door te vervangen wat daar is.

```json
{
	"CLIENT_SECRET": "",
	"API_KEY": "",
	"ACCESS_TOKEN": "",
	"SCOPES": [
		"openid",
		"AdobeID",
		"read_organizations", 
		"additional_info.projectedProductContext", 
		"session",
		"ff_apis",
		"firefly_api",
		"frame.s2s.all"
	],
	"TECHNICAL_ACCOUNT_ID": "",
	"IMS": "ims-na1.adobelogin.com",
	"IMS_ORG": "",
	"access_token": "",
	"IMS_TOKEN": "",
	"AZURE_STORAGE_URL": "",
	"AZURE_STORAGE_CONTAINER": "",
	"AZURE_STORAGE_SAS_READ": "",
	"AZURE_STORAGE_SAS_WRITE": "",
	"FRAME_IO_BASE_URL": "https://api.frame.io",
	"FRAME_IO_ACCOUNT_ID": "",
	"FRAME_IO_WORKSPACE_ID": ""
}
```

Dan moet je dit hebben.

![&#x200B; PostBuster &#x200B;](./images/pb12.png)

## Adobe I/O-variabelen invoeren

Ga naar [&#x200B; https://developer.adobe.com/console/home &#x200B;](https://developer.adobe.com/console/home){target="_blank"} en open uw project.

![&#x200B; de Nieuwe Integratie van Adobe I/O &#x200B;](./images/iopr.png)

Ga naar **Server-aan-Server**.

![&#x200B; de Nieuwe Integratie van Adobe I/O &#x200B;](./images/iopbvar1.png)

U moet nu de volgende waarden van uw Adobe I/O-project kopiëren en deze in uw PostBuster Base-omgeving plakken.

- Client-id
- Het Geheime cliënt (klik **verkrijgt Geheime Cliënt**)
- Technisch account-id
- Organisatie-id (schuif omlaag om uw organisatie-id te zoeken)

![&#x200B; de Nieuwe Integratie van Adobe I/O &#x200B;](./images/iopbvar2.png)

Kopieer de bovengenoemde variabelen één voor één, en kleef hen in uw **Milieu van de Basis** in PostBuster.

| Naam variabele in Adobe I/O | Naam variabele in PostBuster Base-omgeving |
|:-------------:| :---------------:| 
| Client-id | `API_KEY` |
| Clientgeheim | `CLIENT_SECRET` |
| Technisch account-id | `TECHNICAL_ACCOUNT_ID` |
| Organisatie-ID | `IMS_ORG` |

Nadat u deze variabelen één voor één hebt gekopieerd, zou uw Milieu van de Basis van PostBuster als dit moeten kijken.

Klik **dicht**.

![&#x200B; de Nieuwe Integratie van Adobe I/O &#x200B;](./images/iopbvar3.png)

In **Adobe IO - OAuth** inzameling, selecteer het verzoek genoemd **POST - krijg het Token van de Toegang** en selecteer **verzend**.

![&#x200B; de Nieuwe Integratie van Adobe I/O &#x200B;](./images/iopbvar3a.png)

U zou een gelijkaardige reactie moeten zien die de volgende informatie bevat:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| token_type | **drager** |
| access_token | **eyJhbGciOiJS...** |
| verloopt_in | **86399** |

Adobe I/O **drager-teken** heeft een specifieke waarde (zeer lange access_token) en een vervalvenster en is nu geldig voor 24 uren. Dit betekent dat als u Postman na 24 uur wilt gebruiken voor interactie met Adobe API&#39;s, u een nieuw token moet genereren door dit verzoek opnieuw uit te voeren.

![&#x200B; de Nieuwe Integratie van Adobe I/O &#x200B;](./images/iopbvar4.png)

Uw PostBuster-omgeving is nu geconfigureerd en werkt. Je hebt deze oefening nu voltooid.

## Volgende stappen

Ga naar [&#x200B; Toepassingen om &#x200B;](./ex9.md){target="_blank"} te installeren

Ga terug naar [&#x200B; Begonnen het worden &#x200B;](./getting-started.md){target="_blank"}

Ga terug naar [&#x200B; Alle modules &#x200B;](./../../../overview.md){target="_blank"}
