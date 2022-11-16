---
title: Zie uw Profiel van de Klant in real time in actie in het Centrum van de Vraag
description: Zie uw Profiel van de Klant in real time in actie in het Centrum van de Vraag
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
exl-id: 457347ca-1ce5-4699-bd30-735abdc7b450
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 1%

---

# 3.6 Zie uw profiel van de Klant in real time in actie in het Centrum van de Vraag

In deze oefening, is het doel om u door de klantenreis te laten lopen en als echte klant te handelen.

Op deze website hebben we Adobe Experience Platform geïmplementeerd. Elke actie wordt beschouwd als een ervaringsgebeurtenis en wordt verzonden naar Adobe Experience Platform in real-time, waardoor het profiel van de Klant in real-time wordt gehydrateerd.

In een vroegere oefening, begon u als anonieme klant die de plaats doorbladerde, en na een paar stappen, werd u een bekende klant.

Wanneer die zelfde klant uiteindelijk hun telefoon ophaalt en uw vraagcentrum roept, is het cruciaal dat de informatie van andere kanalen onmiddellijk beschikbaar is, zodat de ervaring van het vraagcentrum relevant en gepersonaliseerd kan zijn.

## 3.6.1 De CX-app gebruiken

Als deel van ons Systeem van de Demo, hebben wij een CX App malplaatje gecreeerd dat kan worden gebruikt om een milieu van het vraagcentrum te simuleren. Ga als volgt te werk om een dergelijk CX App-project te maken.

Ga naar [https://builder.adobedemo.com/projects](https://builder.adobedemo.com/projects). Klikken **Nieuw project**.

U ziet dan uw CX App-project. Klik op het project om het te openen.

![Demo](./images/cxapp3.png)

Ga in uw CX App-project naar **Integraties**. Selecteer het bezit van de Inzameling van Gegevens van Adobe Experience Platform dat in Module 0 werd gecreeerd. U moet de eigenschap selecteren die **(inschakelen)** in zijn naam. Klik vervolgens op **Uitvoeren**.

![Demo](./images/cxapp4.png)

Dan zie je dit.

![Demo](./images/cxapp5.png)

In het deelvenster Profielviewer kunt u de volgende combinaties van id&#39;s en naamruimten zien:

![Klantprofiel](./images/identities.png)

| Identiteit | Naamruimte |
|:-------------:| :---------------:|
| Experience Cloud ID (ECID) | 12507560687324495704459439363261812234 |
| E-mailid | woutervangeluwe+06022022-01@gmail.com |
| Mobiel nummer-id | +32473622044+06022022-01 |

Wanneer de klant uw vraagcentrum roept, kan het telefoonaantal worden gebruikt om de klant te identificeren. In deze oefening, zult u het telefoonaantal gebruiken om het profiel van de klant in CX App terug te winnen.

Selecteren **Telefoonnummer** in de vervolgkeuzelijst en voer het telefoonnummer in dat u op de website hebt gebruikt. Actief **Enter**.

![Demo](./images/19.png)

U zult nu de informatie zien die idealiter in het Centrum van de Vraag zou worden getoond, zodat de werknemers van het Centrum van de Vraag alle relevante informatie beschikbaar wanneer het spreken aan een klant hebben.

![Demo](./images/20.png)

Volgende stap: [Samenvatting en voordelen](./summary.md)

[Ga terug naar module 3](./real-time-customer-profile.md)

[Terug naar alle modules](../../overview.md)
