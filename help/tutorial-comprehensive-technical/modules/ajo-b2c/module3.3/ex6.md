---
title: Offer decisioning - Test uw besluit met behulp van de API
description: Uw besluit testen met behulp van de API
kt: 5342
doc-type: tutorial
exl-id: 75515a3e-5df8-42ed-95dc-daae60ee9c72
source-git-commit: fc24f3c9fb1683db35026dc53d0aaa055aa87e34
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# 3.3.6 Test uw beslissing met de API

## 3.3.6.1 Werken met de Offer decisioning-API met Postman

Download [ deze Inzameling van Postman voor Offer decisioning ](./../../../assets/postman/postman_offer-decisioning.zip) aan uw Desktop en unzip het. Dan heb je het volgende:

![ OD API ](./images/unzip.png)

Dit bestand staat nu op uw bureaublad:

- `_AJO- Decisioning Service.postman_collection.json`

In [ oefent 2.1.3 uit - de authentificatie van Postman aan Adobe I/O ](./../../../modules/rtcdp-b2c/module2.1/ex3.md) u Postman installeerde. U moet Postman opnieuw gebruiken voor deze oefening.

Open Postman en importeer het bestand `_AJO- Decisioning Service.postman_collection.json` . Deze verzameling is dan beschikbaar in Postman.

![ Adobe I/O Nieuwe Integratie ](./images/postmanui.png)

U hebt nu alles wat u nodig hebt in Postman om te gaan communiceren met Adobe Experience Platform via de API&#39;s.

Alvorens u hieronder APIs kunt gebruiken, ben zeker om het gebruiken van de inzameling **Adobe IO - OAuth** opnieuw voor authentiek te verklaren die u in Uitoefening 2.1.3 vormde.

![ Adobe I/O Nieuwe Integratie ](./images/postmanui1.png)


### 3.3.6.2 Aanbiedingen ophalen voor klantprofiel

Klik om de verzoek **POST te openen - krijg Aanbiedingen voor het Profiel van de Klant**. Het eerste ding om bij te werken is de **variabele van de Kopbal** voor **x-zandbak-naam**. Stel dit in op `--aepSandboxName--` .

![ OD API ](./images/api23.png)

Voor dit verzoek zijn er een aantal velden die moeten worden bijgewerkt. Ga naar **Lichaam**.

- **xdm:placementId**
- **xdm:activityId**
- **xdm:id**
- **xdm:itemCount** (verander het in een waarde van keus)

![ OD API ](./images/api24.png)

Het gebied **xdm:activityId** moet worden ingevuld. U kunt dat ophalen in de gebruikersinterface van Adobe Experience Platform, zoals hieronder aangegeven.

![ OD API ](./images/activityid.png)

Het veld **[!UICONTROL xdm:placementId]** moet worden ingevuld. U kunt dat ophalen in de gebruikersinterface van Adobe Experience Platform, zoals hieronder aangegeven. In het onderstaande voorbeeld ziet u de placementId voor de plaatsing **[!UICONTROL Web - Image]** .

![ OD API ](./images/placementid.png)

Voor het gebied **xdm:id**, ga het e-mailadres van het klantenprofiel in voor wie u een aanbieding zou willen verzoeken. Klik op **[!UICONTROL Send]** als alle waarden naar wens zijn ingesteld.

![ OD API ](./images/api24a.png)

Tot slot zult u dan het resultaat zien van welk soort gepersonaliseerde aanbieding en welke activa aan deze klant moeten worden getoond. In dit voorbeeld zijn twee objecten aangevraagd en zoals je kunt zien, zijn twee persoonlijke voorstellen geretourneerd. 1 aanbieding voor Apple Watch en een ander voorstel voor Galaxy Watch 7.

![ OD API ](./images/api25.png)

Je hebt deze oefening nu voltooid.

Volgende Stap: [ Samenvatting en voordelen ](./summary.md)

[Terug naar module 3.3](./offer-decisioning.md)

[Terug naar alle modules](./../../../overview.md)
