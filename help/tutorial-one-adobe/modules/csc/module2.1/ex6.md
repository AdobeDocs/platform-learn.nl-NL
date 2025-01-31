---
title: AEM CS - Geavanceerd aangepast blok
description: AEM CS - Geavanceerd aangepast blok
kt: 5342
doc-type: tutorial
source-git-commit: 2f53c8da2cbe833120fa6555c65b8b753bfa4f8d
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 2%

---

# 2.1.6 AEM Edge Delivery Services MarTech-insteekmodule

Met de AEM MarTech-insteekmodule kunt u snel een complete MarTech-stapel instellen voor uw AEM project.

>[!NOTE]
>
>Deze insteekmodule is momenteel beschikbaar voor klanten in samenwerking met AEM Engineering via co-innovatieprojecten. U kunt meer informatie over [ https://github.com/adobe-rnd/aem-martech ](https://github.com/adobe-rnd/aem-martech) vinden.

Navigeer aan de omslag die u voor uw **burgerschap** bewaarplaats GitHub gebruikt. Klik de omslagnaam met de rechtermuisknop aan en selecteer dan **Nieuwe Terminal bij Omslag**.

![ AEMCS ](./images/mtplugin1.png)

Dan zie je dit. Plak het volgende bevel en de slag **gaat** binnen.

```
git subtree add --squash --prefix plugins/martech https://github.com/adobe/aem-experimentation.git main
```

Dan moet je dit zien.

![ AEMCS ](./images/mtplugin3.png)

Navigeer aan de omslag die u voor uw **burgerschap** GitHub bewaarplaats gebruikt, open de omslag **stoppen**. U zou een omslag moeten nu zien genoemd **martech**.

![ AEMCS ](./images/mtplugin4.png)


In de Code van Visual Studio, open het dossier **head.html**. Kopieer de hieronder code en kleef het in het dossier **head.html**.

```javascript
<link rel="preload" as="script" crossorigin="anonymous" href="/plugins/martech/src/index.js"/>
<link rel="preload" as="script" crossorigin="anonymous" href="/plugins/martech/src/alloy.min.js"/>
<link rel="preconnect" href="https://edge.adobedc.net"/>
<!-- change to adobedc.demdex.net if you enable third party cookies -->
```

Sla uw wijzigingen op.

![ AEMCS ](./images/mtplugin5.png)

In de Code van Visual Studio, ga naar de omslag **manuscripten** en open het dossier **scripts.js**. Kopieer de hieronder code en kleef het in het dossier **scripts.js**, onder de bestaande de invoermanuscripten.

```javascript
import {
  initMartech,
  updateUserConsent,
  martechEager,
  martechLazy,
  martechDelayed,
} from '../plugins/martech/src/index.js';
```

Sla uw wijzigingen op.

![ AEMCS ](./images/mtplugin6.png)

```javascript
const isConsentGiven = true;
  const martechLoadedPromise = initMartech(
    // The WebSDK config
    // Documentation: https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/commands/configure/overview#configure-js
    {
      datastreamId: "045c5ee9-468f-47d5-ae9b-a29788f5948f",
      orgId: "907075E95BF479EC0A495C73@AdobeOrg",
      onBeforeEventSend: (payload) => {
        // set custom Target params 
        // see doc at https://experienceleague.adobe.com/en/docs/platform-learn/migrate-target-to-websdk/send-parameters#parameter-mapping-summary
        payload.data.__adobe.target ||= {};

        // set custom Analytics params
        // see doc at https://experienceleague.adobe.com/en/docs/analytics/implementation/aep-edge/data-var-mapping
        payload.data.__adobe.analytics ||= {};
      },

      // set custom datastream overrides
      // see doc at:
      // - https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/commands/datastream-overrides
      // - https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/overrides
      edgeConfigOverrides: {
        // Override the datastream id
        // datastreamId: '...'

        // Override AEP event datasets
        // com_adobe_experience_platform: {
        //   datasets: {
        //     event: {
        //       datasetId: '...'
        //     }
        //   }
        // },

        // Override the Analytics report suites
        // com_adobe_analytics: {
        //   reportSuites: ['...']
        // },

        // Override the Target property token
        // com_adobe_target: {
        //   propertyToken: '...'
        // }
      },
    },
    // The library config
    {
      launchUrls: ["https://assets.adobedtm.com/b754ed1bed61/b9f7c7c484de/launch-28b548849fb9.min.js"],
      personalization: !!getMetadata('target') && isConsentGiven,
    },
  );
```

![ AEMCS ](./images/mtplugin8.png)

![ AEMCS ](./images/mtplugin7.png)

```javascript
if (main) {
    decorateMain(main);
    await Promise.all([
      martechLoadedPromise.then(martechEager),
      waitForLCP(LCP_BLOCKS),
    ]);
  }
```

![ AEMCS ](./images/mtplugin10.png)

```javascript
await martechLazy();
```

![ AEMCS ](./images/mtplugin9.png)

```javascript
window.setTimeout(() => {
    martechDelayed();
    return import('./delayed.js');
  }, 3000);
```

![ AEMCS ](./images/mtplugin11.png)


![ AEMCS ](./images/mtplugin12.png)


![ AEMCS ](./images/mtplugin13.png)

U kunt nu de wijzigingen in uw website bekijken door naar `main--citisignal--XXX.aem.page/us/en` en/of `main--citisignal--XXX.aem.live/us/en` te gaan, nadat u XXX hebt vervangen door uw GitHub-gebruikersaccount, die in dit voorbeeld `woutervangeluwe` is.

In dit voorbeeld wordt de volledige URL als volgt:
`https://main--citisignal--woutervangeluwe.aem.page/us/en` en/of `https://main--citisignal--woutervangeluwe.aem.live/us/en` .

Volgende Stap: [ Samenvatting &amp; Voordelen ](./summary.md){target="_blank"}

[ ga terug naar Module 2.1 ](./aemcs.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}
