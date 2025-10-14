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
>- [&#x200B; 2.1.3 visualiseer uw eigen real-time klantenprofiel - API &#x200B;](./modules/rtcdp-b2c/module2.1/ex3.md)
>- [&#x200B; 2.3.6 Doelen SDK &#x200B;](./modules/rtcdp-b2c/module2.3/ex6.md)
>- [&#x200B; 3.3.6 test uw besluit gebruikend API &#x200B;](./modules/ajo-b2c/module3.3/ex6.md)
>- [&#x200B; 5.1.8 de Dienst API van de Vraag &#x200B;](./modules/datadistiller/module5.1/ex8.md)

## PostBuster installeren

Ga naar [&#x200B; https://adobe.service-now.com/esc?id=adb_esc_kb_article&sysparm_article=KB0020542 &#x200B;](https://adobe.service-now.com/esc?id=adb_esc_kb_article&sysparm_article=KB0020542).

Klik om de recentste versie van **PostBuster** te downloaden.

![&#x200B; PostBuster &#x200B;](./assets/images/pb1.png)

Download de juiste versie voor uw besturingssysteem.

![&#x200B; PostBuster &#x200B;](./assets/images/pb2.png)

Open PostBuster nadat het downloaden is voltooid en geïnstalleerd. Dan moet je dit zien. Klik **Invoer**.

![&#x200B; PostBuster &#x200B;](./assets/images/pb3.png)

De download [&#x200B; postbuster.json.zip &#x200B;](./assets/postman/postbuster.json.zip) en haalt het op uw Desktop uit.

![&#x200B; PostBuster &#x200B;](./assets/images/pbpb.png)

Klik **kiezen een Dossier**.

![&#x200B; PostBuster &#x200B;](./assets/images/pb4.png)

Selecteer het dossier **aep_tutorial.json**. Klik **Open**.

![&#x200B; PostBuster &#x200B;](./assets/images/pb5.png)

Dan moet je dit zien. Klik **Scannen**.

![&#x200B; PostBuster &#x200B;](./assets/images/pb6.png)

Klik **Invoer**.

![&#x200B; PostBuster &#x200B;](./assets/images/pb7.png)

Dan moet je dit zien. Klik om de geïmporteerde verzameling te openen.

![&#x200B; PostBuster &#x200B;](./assets/images/pb8.png)

Nu zie je je collectie. U moet nog een milieu vormen om sommige omgevingsvariabelen te houden.

![&#x200B; PostBuster &#x200B;](./assets/images/pb9.png)

Klik **Milieu van de Basis** en klik dan **uitgeven** pictogram.

![&#x200B; PostBuster &#x200B;](./assets/images/pb10.png)

Dan moet je dit zien.

![&#x200B; PostBuster &#x200B;](./assets/images/pb11.png)

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

![&#x200B; PostBuster &#x200B;](./assets/images/pb12.png)

Na het creëren van uw Adobe IO project, zou uw milieu als dit moeten kijken. U hoeft dit nu niet te doen, dit wordt later opgelost.

![&#x200B; PostBuster &#x200B;](./assets/images/pb13.png)

>[!NOTE]
>
>![&#x200B; Indexen van de Tech &#x200B;](./assets/images/techinsiders.png){width="50px" align="left"}
>
>Als u vragen hebt, wil algemene terugkoppelen van hebben suggesties over toekomstige inhoud delen, gelieve direct contactTech Insiders, door een e-mail naar **techinsiders@adobe.com** te verzenden.

[Terug naar alle modules](./overview.md)
