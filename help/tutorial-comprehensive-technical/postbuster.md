---
title: PostBuster - Adobe werknemers
description: PostBuster - Adobe werknemers
doc-type: multipage-overview
exl-id: a798e9d7-bb99-4390-885f-5fbd2ef4cee9
source-git-commit: 9c1b30dc0fcca6b4324ec7c8158699fa273cdc90
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# PostBuster

>[!IMPORTANT]
>
>De onderstaande instructies zijn alleen bedoeld voor Adobe werknemers.

>[!IMPORTANT]
>
>Door de onderstaande instructies op te volgen, beschikt u al de vereiste API-verzamelingen die in deze oefeningen zullen worden gebruikt:
>
>- [ 2.1.3 visualiseer uw eigen real-time klantenprofiel - API ](./modules/rtcdp-b2c/module2.1/ex3.md)
>- [ 2.3.6 Doelen SDK ](./modules/rtcdp-b2c/module2.3/ex6.md)
>- [ 3.3.6 test uw besluit gebruikend API ](./modules/ajo-b2c/module3.3/ex6.md)
>- [ 5.1.8 de Dienst API van de Vraag ](./modules/datadistiller/module5.1/ex8.md)

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

Selecteer het dossier **aep_tutorial.json**. Klik **Open**.

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
		"read_organizations",
		"additional_info.projectedProductContext",
		"session",
		"ff_apis",
		"firefly_api"
	],
	"TECHNICAL_ACCOUNT_ID": "",
	"IMS": "ims-na1.adobelogin.com",
	"IMS_ORG": "",
	"access_token": "",
	"IMS_TOKEN": "",
	"QS_QUERY_ID": "",
	"SANDBOX_NAME": ""
}
```

Dan moet je dit hebben.

![ PostBuster ](./assets/images/pb12.png)

Na het creëren van uw Adobe IO project, zou uw milieu als dit moeten kijken. U hoeft dit nu niet te doen, dit wordt later opgelost.

![ PostBuster ](./assets/images/pb13.png)

>[!NOTE]
>
>![ Indexen van de Tech ](./assets/images/techinsiders.png){width="50px" align="left"}
>
>Als u vragen hebt, wil algemene terugkoppelen van hebben suggesties over toekomstige inhoud delen, gelieve direct contactTech Insiders, door een e-mail naar **techinsiders@adobe.com** te verzenden.

[Terug naar alle modules](./overview.md)
