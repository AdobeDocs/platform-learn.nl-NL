---
title: Foundation - Setup van Adobe Experience Platform Data Collection en de Web SDK-extensie - Adobe Analytics en Adobe Audience Manager implementeren
description: Foundation - Setup van Adobe Experience Platform Data Collection en de Web SDK-extensie - Adobe Analytics en Adobe Audience Manager implementeren
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: e3ef6534-9af9-4b8c-86d0-46f413f4ff6d
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '560'
ht-degree: 0%

---

# 1.5 - Adobe Analytics en Adobe Audience Manager implementeren

## Context

U weet nu dat XDM-gegevens naar een platform stromen. U gaat meer weten over wat XDM bevat [Module 2](./../module2/data-ingestion.md), en hoe te om uw eigen schema te bouwen om douanevariabelen te volgen. Voor nu gaat u bekijken wat gebeurt wanneer u uw Datasstream plaatst om gegevens aan Analytics en Audience Manager door:sturen.

## 1.5.1 Variabelen in kaart brengen in analyses

De Adobe Experience Platform [!DNL Web SDK] Hiermee worden bepaalde waarden automatisch toegewezen, waardoor een nieuwe implementatie van Analytics via de Web SDK zo snel mogelijk wordt uitgevoerd. De automatisch toegewezen variabelen worden weergegeven [hier](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/adobe-analytics/automatically-mapped-vars.html#data-collection).

Voor XDM-gegevens die niet automatisch worden toegewezen aan [!DNL Adobe Analytics]kunt u [contextgegevens](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/contextdata.html) om overeen te komen met uw [schema](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html). Vervolgens kan het worden toegewezen aan [!DNL Analytics] gebruiken [verwerkingsvoorschriften](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules-configuration/t-processing-rules.html) vullen [!DNL Analytics] variabelen. De Regels van de Gegevens van de context en van de Verwerking zullen concepten vertrouwd aan die zijn geweest met Analytics in het verleden, maar maak zich geen zorgen over de details voor nu als zij nieuwe concepten zijn.

U kunt ook een standaardset handelingen en productlijsten gebruiken om gegevens te verzenden of op te halen met de AEP [!DNL Web SDK]. Zie [Producten](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/collect-commerce-data.html?lang=en#data-collection).

### Contextgegevens

Te gebruiken door [!DNL Analytics], XDM-gegevens worden afgevlakt met puntnotatie en beschikbaar gemaakt als `contextData`. In de volgende lijst met waardeparen ziet u een voorbeeld van `context data`:

```javascript
{
    "bh": "900",
    "bw": "1680",
    "c": "24",
    "c.a.d.key.[0]": "value1",
    "c.a.d.key.[1]": "value2",
    "c.a.d.object.key1": "value1",
    "c.a.d.object.key2.[0]": "value2",
    "c.a.x.environment.browserdetails.javascriptenabled": "true",
    "c.a.x.environment.type": "browser",
    "cust_hit_time_gmt": "1579781427",
    "g": "http://example.com/home",
    "gn": "home",
    "j": "1.8.5",
    "k": "Y",
    "s": "1680x1050",
    "tnta": "218287:1:0|0,218287:1:0|2,218287:1:0|1,218287:1:0|32767,218287:1:01,218287:1:0|0,218287:1:0|1,218287:1:0|0,218287:1:0|1",
    "user_agent": "Mozilla/5.0 AppleWebKit/537.36 Safari/537.36",
    "v": "Y"
}
```

### Verwerkingsregels

Alle gegevens die door het Edge-netwerk worden verzameld, zijn toegankelijk via [verwerkingsvoorschriften](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules-configuration/t-processing-rules.html). In [!DNL Analytics], kunt u verwerkingsregels gebruiken om contextgegevens in op te nemen [!DNL Analytics] variabelen.

## 1.5.2 Audience Manager op het Netwerk van de Rand van het Experience Platform

Server-kant door:sturen is geen nieuw concept voor Audience Manager, en het zelfde proces zoals vroeger van toepassing is. U kunt identiteiten ook synchroniseren.

## 1.5.3 Controleer uw gegevensstroom om gegevens naar Adobe Analytics te verzenden

Voor het geval u gegevens wilt verzenden die door Web SDK aan Adobe Analytics en Adobe Audience Manager worden verzameld, volg deze stappen.

Ga naar [https://experience.adobe.com/launch/](https://experience.adobe.com/launch/) en ga naar **DataStreams**.

Selecteer in de rechterbovenhoek van het scherm de naam van de sandbox die u wilt instellen als `--aepSandboxId--`. Open uw specifieke gegevensstroom, die genoemd wordt `--demoProfileLdap-- - Demo System Datastream`.

![Klik op het pictogram Edge Configuration in de linkernavigatie](./images/edgeconfig1b.png)

Dan zie je dit. Als u Adobe Analytics wilt inschakelen, klikt u op **+Service toevoegen**.

![AEP-foutopsporing](./images/aa2.png)

Dan zie je dit. Selecteer de service **Adobe Analytics**, waarna u de rapportsuite in Adobe Analytics moet toevoegen om gegevens naar te sturen. In deze zelfstudie is dit buiten bereik. Klikken **Annuleren**.

![AEP-foutopsporing](./images/aa3.png)

## 1.5.4 Controleer uw gegevensstroom om gegevens naar Adobe Audience Manager te verzenden

Dan zie je dit. Als u Adobe Audience Manager wilt inschakelen, klikt u op **+Service toevoegen**.

![AEP-foutopsporing](./images/aa2.png)

Dan zie je dit. Selecteer de service **Adobe Audience Manager** waarna u kunt besluiten om de koekjesbestemmingen van Adobe Audience Manager en/of bestemmingen URL toe te laten of onbruikbaar te maken. In dit leerprogramma, is deze configuratie buiten werkingsgebied. Klikken **Annuleren**.

![AEP-foutopsporing](./images/aam1.png)

Volgende stap: [1.6 Adobe Target implementeren](./ex6.md)

[Ga terug naar module 1](./data-ingestion-launch-web-sdk.md)

[Terug naar alle modules](./../../overview.md)
