---
title: Offer Decisioning - Test uw besluit met behulp van de API
description: Uw besluit testen met behulp van de API
kt: 5342
doc-type: tutorial
exl-id: 52f90b9f-32ea-49c2-af5d-8742ca8b3b4e
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# 3.3.6 Test uw beslissing met de API

## 3.3.6.1 Werken met de Offer Decisioning API met Postman

>[!IMPORTANT]
>
>Als u een werknemer van Adobe bent, te volgen gelieve de instructies hier om [ PostBuster ](./../../../../modules/getting-started/gettingstarted/ex8.md) te gebruiken.

Download [ deze Inzameling van Postman voor Offer Decisioning ](./../../../../assets/postman/postman_offer-decisioning.zip) aan uw Desktop en unzip het. Dan heb je het volgende:

![ OD API ](./images/unzip.png)

Dit bestand staat nu op uw bureaublad:

- `_AJO- Decisioning Service.postman_collection.json`

In [ oefent 2.1.3 uit - de authentificatie van Postman aan Adobe I/O ](./../../../../modules/delivery-activation/rtcdp-b2c/rtcdpb2c-1/ex3.md) u Postman installeerde. U moet Postman opnieuw gebruiken voor deze oefening.

Open Postman en importeer het bestand `_AJO- Decisioning Service.postman_collection.json` . Deze verzameling is dan beschikbaar in Postman.

![ de Nieuwe Integratie van Adobe I/O ](./images/postmanui.png)

U hebt nu alles wat u nodig hebt in Postman om te gaan communiceren met Adobe Experience Platform via de API&#39;s.

Alvorens u hieronder APIs kunt gebruiken, ben zeker om het gebruiken van de inzameling **Adobe IO opnieuw voor authentiek te verklaren - OAuth** die u in Uitoefening 2.1.3 vormde.

![ de Nieuwe Integratie van Adobe I/O ](./images/postmanui1.png)


### 3.3.6.2 Aanbiedingen ophalen voor klantprofiel

Klik om het verzoek **POST te openen - krijg Aanbiedingen voor het Profiel van de Klant**. Het eerste ding om bij te werken is de **variabele van de Kopbal** voor **x-zandbak-naam**. Stel dit in op `--aepSandboxName--` .

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

## Volgende stappen

Ga naar [ Samenvatting en voordelen ](./summary.md){target="_blank"}

Ga terug naar [ Offer Decisioning ](offer-decisioning.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}
