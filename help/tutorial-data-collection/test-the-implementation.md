---
title: De implementatie testen
description: De implementatie testen
exl-id: 66eb1d4e-32eb-45fc-8da4-8d3c04dc3c7a
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 0%

---

# De implementatie testen

Nu u uw webpagina hebt ingesteld en uw Adobe Experience Platform-tagbibliotheek hebt geïmplementeerd, is het tijd om de implementatie te testen.

1. Open de productpagina in uw browser. U kunt dit doen door op _Bestand_ dan _Bestand openen..._ in uw browser of u kunt uw pagina op een webserver hosten en de juiste URL invoeren.

Nadat de pagina is geladen, ziet u zoiets als volgt:
![Webpagina](assets/webpage.png)

Het is niet mooi, maar het doet het werk.

## Inspect instellen voor de paginaweergave en de gebeurtenissen in de productweergave

1. Open de ontwikkelaarsgereedschappen in uw browser en klik op het netwerkdeelvenster. Vernieuw de pagina.
Op dit punt, zou u vier verzoeken moeten zien:
* product.html - Uw webpagina.
* launch-##########-development.js - Uw opstartwaribliotheek.
* interactie - De gebeurtenis van de paginamening die naar de server wordt verzonden.
* interactie - De gebeurtenis van de productmening die naar de server wordt verzonden.
Inspect de lading van elk verzoek:
1. Voor de eerste `interact` verzoek, zou u de lading moeten kunnen zien die met wordt verzonden `eventType` van `web.webpagedetails.pageViews`.
   ![Verzoek om inspectie van paginaweergave](assets/webpage-page-viewed-inspection.png)
1. Voor de tweede `interact` verzoek, zou u de lading moeten kunnen zien die met wordt verzonden `eventType` van `commerce.productViews`.
   ![Verzoek om inspectie van de productweergave](assets/webpage-product-view-inspection.png)
1. Controleer de rest van de gegevens die worden verzonden, inclusief de productinformatie.

## Inspect: open winkelwagentje en toevoegen aan winkelwagentjes

1. Klik nu op **_Toevoegen aan winkelwagentje_**knop.

U zou twee extra verzoeken moeten zien, eerste met een `eventType` van `commerce.productListOpens` (voor het openen van een nieuw winkelwagentje) en de tweede met een `eventType` van `commerce.productListAdds` (voor het toevoegen van het product aan het winkelwagentje).

## Inspect: de gebeurtenis click voor de download-app

Afhankelijk van browser, kan het klikken van een verbinding die u van de huidige pagina weg navigeert uw netwerkpaneel ontruimen. Omdat u het netwerkverzoek voor de verbinding wilt inspecteren klikt gebeurtenis die onmiddellijk voorkomt alvorens u vanaf de pagina navigeert, moet u uw browser vormen om netwerklogboeken over pagina&#39;s te bewaren.

1. Netwerklogboeken behouden door een van de volgende twee controles uit te voeren **_Logbestand behouden_** in het netwerkvenster (Chrome, Safari, Edge) of op een tandwielpictogram klikken en een **_Logboeken behouden_** in het weergegeven menu (Firefox).
1. Klik op de knop **_De app downloaden_** koppeling. U moet er nog een zien `interact` verzoek verschijnt in het netwerkpaneel.
1. Zoek de aanvraag met een `eventType` van `web.webinteraction.linkClicks`en bekijk de details over de koppeling waarop is geklikt.

## Controleren of de gegevens in de Adobe Experience Platform-gegevensset worden ontvangen

Nu verzoeken worden verzonden, controleer of de gegevens veilig in de dataset van Adobe Experience Platform aankomen u creeerde.

1. Ga naar de **[!UICONTROL Gegevenssets]** bekijken in Adobe Experience Platform.
1. Selecteer [gegevensset](configure-the-server/create-a-dataset.md) die u voor deze zelfstudie hebt gemaakt.
U moet misschien een paar minuten wachten, maar u zou spoedig aanwijzingen moeten zien van gegevens die worden verwerkt en in uw dataset worden opgenomen. U zou ook moeten zien of de verwerking slaagde of ontbrak. Als het ontbrak, ziet u waarom het ontbrak. De fouten komen typisch voor omdat de gegevens u verzendt niet het schema aanpast en u moet uw gegevens of schema dienovereenkomstig aanpassen.
   ![Gegevensset-opname](assets/dataset-ingestion.png)

## De extensie Adobe Experience Platform Debugger gebruiken

Voor meer inzicht in hoe uw implementatie zich zowel op browser als op Adobe servers gedraagt, controleer de browser van Foutopsporing van Adobe Experience Platform browser uitbreiding!

[Adobe Experience Platform Debugger-extensie voor Chrome](https://chrome.google.com/webstore/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob)

[Adobe Experience Platform Debugger-extensie voor Firefox](https://addons.mozilla.org/en-US/firefox/addon/adobe-experience-platform-dbg/)

[Volgende: ](summary.md)

>[!NOTE]
>
>Dank u voor het investeren van uw tijd in het leren over de Inzameling van Gegevens. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)