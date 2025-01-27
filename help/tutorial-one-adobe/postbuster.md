---
title: Voorwerk
description: Voorwerk
doc-type: multipage-overview
source-git-commit: 7b76e7714d2a390d84393ce21a19063b56508ac1
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# PostBuster

>[!IMPORTANT]
>
>De onderstaande instructies zijn alleen bedoeld voor Adobe werknemers.

## PostBuster installeren

Ga naar [ https://adobe.service-now.com/esc?id=adb_esc_kb_article&amp;sysparm_article=KB0020542 ](https://adobe.service-now.com/esc?id=adb_esc_kb_article&amp;sysparm_article=KB0020542).

Klik om de recentste versie van **PostBuster** te downloaden.

![ PostBuster ](./assets/images/pb1.png)

Download de juiste versie voor uw besturingssysteem.

![ PostBuster ](./assets/images/pb2.png)

Open PostBuster nadat het downloaden is voltooid en geïnstalleerd. Dan moet je dit zien. Klik **Invoer**.

![ PostBuster ](./assets/images/pb3.png)

De download [ postbuster.json.zip ](./assets/postman/postbuster.json.zip) en haalt het op uw Desktop uit.

![ PostBuster ](./assets/images/pbpb.png)

Klik **kiezen een Dossier**.

![ PostBuster ](./assets/images/pb4.png)

Selecteer het dossier **postbuster.json**. Klik **Open**.

![ PostBuster ](./assets/images/pb5.png)

Dan moet je dit zien. Klik **Scannen**.

![ PostBuster ](./assets/images/pb6.png)

Klik **Invoer**.

![ PostBuster ](./assets/images/pb7.png)

Dan moet je dit zien. Klik om de geïmporteerde verzameling te openen.

![ PostBuster ](./assets/images/pb8.png)

Nu zie je je collectie. U moet nog een milieu vormen om sommige omgevingsvariabelen te houden.

![ PostBuster ](./assets/images/pb9.png)

Klik **Milieu van de Basis** en klik dan **uitgeven** pictogram.

![ PostBuster ](./assets/images/pb10.png)

Dan moet je dit zien.

![ PostBuster ](./assets/images/pb11.png)

Kopieer hieronder milieu placeholder en kleef het in het **Milieu van de Basis**.

```json
{
	"CLIENT_SECRET": "",
	"API_KEY": "",
	"ACCESS_TOKEN": "",
	"SCOPES": [
		"openid",
		"AdobeID",
		"ff_apis",
		"firefly_api"
	],
	"TECHNICAL_ACCOUNT_ID": "",
	"IMS": "ims-na1.adobelogin.com",
	"IMS_ORG": "",
	"access_token": "",
	"IMS_TOKEN": "",
	"AZURE_STORAGE_URL": "",
	"AZURE_STORAGE_CONTAINER": "",
	"AZURE_STORAGE_SAS_READ": "",
	"AZURE_STORAGE_SAS_WRITE": ""
}
```

Dan moet je dit hebben.

![ PostBuster ](./assets/images/pb12.png)

Na het gaan door de **module van de Diensten van de Firefly 0} {, zou uw milieu als dit moeten kijken.** U hoeft dit nu niet te doen, dit wordt later opgelost.

![ PostBuster ](./assets/images/pb13.png)

>[!NOTE]
>
>![ Indexen van de Tech ](./assets/images/techinsiders.png){width="50px" align="left"}
>
>Als u vragen hebt, wil algemene terugkoppelen van hebben suggesties over toekomstige inhoud delen, gelieve direct contactTech Insiders, door een e-mail naar **techinsiders@adobe.com** te verzenden.

[Terug naar alle modules](./overview.md)
