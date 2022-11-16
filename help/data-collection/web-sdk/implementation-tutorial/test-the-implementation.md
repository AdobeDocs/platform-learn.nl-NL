---
title: De implementatie testen
description: De implementatie testen
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
kt: 10447
hide: true
hidefromtoc: true
exl-id: e2213c23-d395-4c57-8c6c-0319cd0fb0ac
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---

# De implementatie testen

Nu u uw webpagina hebt ingesteld en uw Adobe Experience Platform-tagbibliotheek hebt geïmplementeerd, is het tijd om de implementatie te testen.

Open de productpagina in uw browser. U kunt dit doen door op _Bestand_ dan _Bestand openen..._ in uw browser of u kunt uw pagina op een webserver hosten en de juiste URL invoeren.

Nadat de pagina is geladen, ziet u zoiets als volgt:

![Webpagina](../../assets/implementation-strategy/webpage.png)

Het is niet mooi, maar het zal het werk doen.

## Inspect instellen voor de paginaweergave en de gebeurtenissen in de productweergave

Open de ontwikkelaarsgereedschappen in uw browser en klik op het netwerkdeelvenster. Vernieuw de pagina.

Op dit punt, zou u vier verzoeken moeten zien:

1. product.html - Uw webpagina.
2. launch-##########-development.js - Uw opstartwaribliotheek.
3. interactie - De gebeurtenis van de paginamening die naar de server wordt verzonden.
4. interactie - De gebeurtenis van de productmening die naar de server wordt verzonden.

Voel vrij om de lading van elk verzoek te inspecteren. Voor de eerste `interact` verzoek, zou u de lading moeten kunnen zien die met wordt verzonden `eventType` van `web.webpagedetails.pageViews`.

![Verzoek om inspectie van paginaweergave](../../assets/implementation-strategy/webpage-page-viewed-inspection.png)

Voor de tweede `interact` verzoek, zou u de lading moeten kunnen zien die met wordt verzonden `eventType` van `commerce.productViews`.

![Verzoek om inspectie van de productweergave](../../assets/implementation-strategy/webpage-product-view-inspection.png)

Voel u vrij om rond de rest van de gegevens die worden verzonden, met inbegrip van de productinformatie te trekken.

## Inspect: open winkelwagentje en toevoegen aan winkelwagentjes

Klik nu op de knop _Toevoegen aan winkelwagentje_ knop.

U zou twee extra verzoeken moeten zien, eerste met een `eventType` van `commerce.productListOpens` (voor het openen van een nieuw winkelwagentje) en de tweede met een `eventType` van `commerce.productListAdds` (voor het toevoegen van het product aan het winkelwagentje).

## Inspect: de gebeurtenis click voor de download-app

Afhankelijk van browser, kan het klikken van een verbinding die u van de huidige pagina weg navigeert uw netwerkpaneel ontruimen. Omdat u het netwerkverzoek voor de verbinding wilt inspecteren klikt gebeurtenis die onmiddellijk voorkomt alvorens u vanaf de pagina navigeert, zult u uw browser moeten vormen om netwerklogboeken over pagina&#39;s te bewaren. Dit wordt gedaan door of _Logbestand behouden_ in het netwerkvenster (Chrome, Safari, Edge) of op een tandwielpictogram klikken en een _Logboeken behouden_ in het weergegeven menu (Firefox).

Klik nu op de knop _De app downloaden_ koppeling.

U moet er nog een zien `interact` verzoek verschijnt in het netwerkpaneel. Als u het verzoek inspecteert, zou u moeten vinden `eventType` van `web.webinteraction.linkClicks` en details over de koppeling waarop is geklikt.

## Controleren of de gegevens in de Adobe Experience Platform-gegevensset worden ontvangen

Nu verzoeken worden verzonden, zult u ook willen controleren of de gegevens veilig in de dataset van Adobe Experience Platform aankomen u creeerde. Begin door naar de [!UICONTROL Gegevenssets] bekijken in Adobe Experience Platform.

Selecteer de gegevensset die u eerder hebt gemaakt.

U moet misschien een paar minuten wachten, maar u zou spoedig aanwijzingen moeten zien van gegevens die worden verwerkt en in uw dataset worden opgenomen. U zou ook moeten zien of de verwerking slaagde of ontbrak. Als het ontbrak, zult u kunnen zien waarom het ontbrak. De mislukkingen komen typisch voor omdat de gegevens u verzendt niet het schema aanpast en u zult uw gegevens of schema dienovereenkomstig moeten aanpassen.

![Gegevensset-opname](../../assets/implementation-strategy/dataset-ingestion.png)

## De extensie Adobe Experience Platform Debugger gebruiken

Voor meer inzicht in hoe uw implementatie zich zowel op browser als op Adobe servers gedraagt, controleer de browser van Foutopsporing van Adobe Experience Platform browser uitbreiding!

[Adobe Experience Platform Debugger-extensie voor Chrome](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob)

[Adobe Experience Platform Debugger-extensie voor Firefox](https://addons.mozilla.org/en-US/firefox/addon/adobe-experience-platform-dbg/)
