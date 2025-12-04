---
title: Brand Concierge implementeren met tags voor gegevensverzameling
description: Brand Concierge implementeren met tags voor gegevensverzameling
kt: 5342
doc-type: tutorial
source-git-commit: 3704abb57e9fa64c2ff6d6914b6da8b46a5f44aa
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# 1.4.3 Brand Concierge implementeren met tags voor gegevensverzameling

>[!IMPORTANT]
>
>Aan deze oefening wordt gewerkt en is nog niet klaar.

## Codes gegevensverzameling, eigenschap

Brand Concierge moet gegevens naar Adobe Experience Platform verzenden. Hiervoor moet Web SDK (of alloy.js) worden geïmplementeerd op uw website.

Om dat mogelijk te maken, moet u nu een bezit van de Markeringen van de Inzameling van Gegevens creëren.

Ga naar [&#x200B; https://experience.adobe.com/ &#x200B;](https://experience.adobe.com/){target="_blank"}. Open **Inzameling van Gegevens**.

![&#x200B; Brand Concierge &#x200B;](./images/aep101.png)

Klik **Nieuw Bezit**.

![&#x200B; Brand Concierge &#x200B;](./images/aep102.png)

Voer de naam `--aepUserLdap-- - CitiSignal Website + Brand Concierge` in en voer ook het domein van uw website in.

Klik **sparen**.

![&#x200B; Brand Concierge &#x200B;](./images/aep103.png)

Zoek de eigenschap en open deze.

![&#x200B; Brand Concierge &#x200B;](./images/aep104.png)

Ga naar **Uitbreidingen** en dan naar **Catalogus**.

![&#x200B; Brand Concierge &#x200B;](./images/aep105.png)

Onderzoek naar `web sdk` en klik dan de uitbreiding **SDK van het Web van Adobe Experience Platform**. Klik **installeren**.

![&#x200B; Brand Concierge &#x200B;](./images/aep106.png)

Dan moet je dit zien. U hoeft hier alleen de details voor uw gegevensstroom op te geven. Schuif een beetje omlaag om dat te doen.

![&#x200B; Brand Concierge &#x200B;](./images/aep107.png)

Voor alle 3 milieu&#39;s **Productie**, **het Opvoeren** en **Ontwikkeling**, gelieve het volgende te selecteren:

- **Sandbox**: `--aepUserLdap-- - bc`
- **DataStream**: `--aepUserLdap-- - Brand Concierge`

Klik **sparen**.

![&#x200B; Brand Concierge &#x200B;](./images/aep108.png)

Dan moet je dit zien. Ga naar **Regels**.

![&#x200B; Brand Concierge &#x200B;](./images/aep108a.png)

Klik **creëren Nieuwe Regel**.

![&#x200B; Brand Concierge &#x200B;](./images/aep109.png)

Voer de naam in: `Homepage`. Dan, klik **+ toevoegen** onder **GEBEURTENISSEN**.

![&#x200B; Brand Concierge &#x200B;](./images/aep110.png)

Selecteer de volgende opties:

- **Uitbreiding**: **Kern**
- **Type van Gebeurtenis**: **Geladen Bibliotheek (de Boven van de Pagina)**

Klik **houden Veranderingen**.

![&#x200B; Brand Concierge &#x200B;](./images/aep111.png)

Dan moet je dit zien. Klik **+ toevoegen** onder **VOORWAARDEN**.

![&#x200B; Brand Concierge &#x200B;](./images/aep112.png)

Selecteer de volgende opties:

- **Type Logica**: **Regelmatig**
- **Uitbreiding**: **Kern**
- **Type van Voorwaarde**: **Weg zonder het Koord van de Vraag**
- **weg evenaart...**: ga uw websitedomein, in dit geval in `https://vangeluw.adobedemosystem.com/`

Klik **houden Veranderingen**.

![&#x200B; Brand Concierge &#x200B;](./images/aep113.png)

Dan moet je dit zien. Klik **+ toevoegen** onder **Acties**.

![&#x200B; Brand Concierge &#x200B;](./images/aep114.png)

Selecteer de volgende opties:

- **Uitbreiding**: **Kern**
- **Type van Actie**: **de Code van de Douane**
- **Taal**: **JavaScript**

Klik **Open Redacteur**.

![&#x200B; Brand Concierge &#x200B;](./images/aep115.png)

Plak de volgende code:

```javascript
window["alloy"]("sendEvent", {
        conversation: {fetchConversationalExperience: true}
    }).then(result=> {
        console.log("Conversation experience fetched", result);
        window["alloy"]("bootstrapConversationalExperience", {
            selector: "#brand-concierge-mount",
						// src: "main.js",
            src: "https://experience-stage.adobe.net/solutions/experience-platform-brand-concierge-web-agent/static-assets/main.js",
            stylingConfigurations: window.styleConfiguration,
						stickySession: true
        })
    });
```

Klik **sparen**.

![&#x200B; Brand Concierge &#x200B;](./images/aep116.png)

Dan moet je dit zien. Klik **houden Veranderingen**.

![&#x200B; Brand Concierge &#x200B;](./images/aep117.png)

Dan moet je dit zien. Klik **sparen**.

![&#x200B; Brand Concierge &#x200B;](./images/aep118.png)

Ga naar **het Publiceren Stroom**. Klik **toevoegen Bibliotheek**.

![&#x200B; Brand Concierge &#x200B;](./images/aep119.png)

Ga de naam in: `Dev`, selecteer **Ontwikkeling (ontwikkeling)** voor het milieu en klik dan **toevoegen Alle Gewijzigde Middelen**.

Klik **sparen &amp; bouwt voor Ontwikkeling**.

![&#x200B; Brand Concierge &#x200B;](./images/aep120.png)

Na een paar minuten wordt uw bibliotheek gemaakt. Wacht tot u de **groene punt** naast **Dev** ziet. Dan, ga naar **Milieu&#39;s**.

![&#x200B; Brand Concierge &#x200B;](./images/aep121.png)

Klik **installeer** pictogram voor het **milieu van de Ontwikkeling**.

![&#x200B; Brand Concierge &#x200B;](./images/aep122.png)

Dan moet je dit zien. Klik de **exemplaar** knoop om de weg van uw bibliotheek te kopiëren. U moet dit op uw website implementeren.

Het bibliotheekpad moet er als volgt uitzien:
`<script src="https://assets.adobedtm.com/XXXXXXX/XXXXXXXX/launch-XXXXXXXXX-development.min.js" async></script>`

![&#x200B; Brand Concierge &#x200B;](./images/aep123.png)

Ga terug naar [&#x200B; Brand Concierge &#x200B;](./brandconcierge.md){target="_blank"}

[&#x200B; ga terug naar Alle Modules &#x200B;](./../../../overview.md){target="_blank"}