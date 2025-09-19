---
title: ACCS verbinden met AEM Assets CS
description: ACCS verbinden met AEM Assets CS
kt: 5342
doc-type: tutorial
source-git-commit: 16229700449660a085549a37013e015a5e20ba9e
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# 1.5.3 ACCS verbinden met AEM Assets CS

>[!IMPORTANT]
>
>Om deze oefening te voltooien, moet u toegang tot een werkende AEM Sites en Assets CS met milieu EDS hebben.
>
>Als u zulk een milieu nog niet hebt, ga [ Adobe Experience Manager Cloud Service &amp; Edge Delivery Services ](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"} uitoefenen. Volg de instructies daar, en u zult toegang tot zulk een milieu hebben.

>[!IMPORTANT]
>
>Als u eerder een AEM CS-programma hebt geconfigureerd met een AEM Sites- en Assets CS-omgeving, kan het zijn dat uw AEM CS-sandbox is geminimaliseerd. Gezien het feit dat het vernietigen van zo&#39;n zandbak 10 tot 15 minuten duurt, zou het een goed idee zijn om het ontruimingsproces nu te beginnen zodat u niet op een later tijdstip hoeft te wachten.

![ ACCS+AEM Assets ](./images/accsaemassets1.png)


## 1.5.3.4 Update config.json

Voeg het onderstaande codefragment toe onder regel 6 `"ac-environment-id":XXX` :

```json
 "commerce-assets-enabled": "true",
```



Volgende Stap: [ Samenvatting &amp; Voordelen ](./summary.md){target="_blank"}

Ga terug naar [ Adobe Commerce as a Cloud Service ](./accs.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}
