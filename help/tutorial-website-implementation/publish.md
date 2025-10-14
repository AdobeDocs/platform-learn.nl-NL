---
title: De tag-eigenschap Publish
description: Leer hoe u uw eigenschap tag kunt publiceren vanuit de ontwikkelomgeving naar de omgeving voor staging en productie. Deze les maakt deel uit van de zelfstudie Experience Cloud implementeren in websites.
exl-id: dec70472-cecc-4630-b68e-723798f17a56
source-git-commit: e2594d3b30897001ce6cb2f6908d75d0154015eb
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# De tag-eigenschap Publish

Nu u enkele belangrijke oplossingen van de Adobe Experience Cloud in uw ontwikkelomgeving hebt geïmplementeerd, is het tijd om de publicatieworkflow te leren.

>[!NOTE]
>
>Adobe Experience Platform Launch wordt in Adobe Experience Platform geïntegreerd als een reeks technologieën voor gegevensverzameling. Verschillende terminologiewijzigingen zijn geïmplementeerd in de interface die u tijdens het gebruik van deze inhoud moet onthouden:
>
> * Platform launch (de Kant van de Cliënt) is nu **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl)**
> * De Server zijde van de platform launch is nu **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=nl-NL)**
> * De configuraties van Edge zijn nu **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html?lang=nl-NL)**

## Leerdoelen

Aan het eind van deze les, zult u kunnen:

1. Publish a Development library to the Staging environment
1. Een testbibliotheek aan uw productiewebsite toewijzen met Foutopsporing
1. Publish a Staging library to the Production environment

## Publish naar Staging

Nu u uw bibliotheek in de ontwikkelomgeving hebt gemaakt en gevalideerd, is het tijd om deze te publiceren naar Staging.

1. Ga naar de **[!UICONTROL Publishing Flow]** -pagina

1. Open het vervolgkeuzemenu naast uw bibliotheek en selecteer **[!UICONTROL Submit for Approval]**

   ![&#x200B; voorleggen voor Goedkeuring &#x200B;](images/publishing-submitForApproval.png)

1. Klik op de knop **[!UICONTROL Submit]** in het dialoogvenster:

   ![&#x200B; klik voorleggen in Modal &#x200B;](images/publishing-submit.png)

1. De bibliotheek wordt nu in een niet-gebouwde staat in de kolom [!UICONTROL Submitted] weergegeven:

1. Open het vervolgkeuzemenu en selecteer **[!UICONTROL Build for Staging]** :

   ![&#x200B; Bouwstijl voor het Opvoeren &#x200B;](images/publishing-buildForStaging.png)

1. Zodra het pictogram met de groene stip wordt weergegeven, kunt u een voorvertoning van de bibliotheek weergeven in de testomgeving.

In een real-life scenario, zou de volgende stap in het proces typisch zijn om uw team te hebben QA de veranderingen in de het Opvoeren bibliotheek bevestigen. Ze kunnen dit doen met Foutopsporing.

**om de Veranderingen in de het Opvoeren Bibliotheek** te bevestigen

1. Open de pagina [!UICONTROL Environments] in de eigenschap Tag

1. In de [!UICONTROL Staging] rij, klik het Install pictogram ![&#x200B; installeren pictogram &#x200B;](images/launch-installIcon.png) om modaal te openen

   ![&#x200B; ga naar de pagina van Milieu&#39;s en klik om modaal &#x200B;](images/publishing-getStagingCode.png) te openen

1. Klik het pictogram van het Exemplaar ![&#x200B; pictogram van het Exemplaar &#x200B;](images/launch-copyIcon.png) om de ingebedde code aan uw klembord te kopiëren

1. Klik op **[!UICONTROL Close]** om het modale

   ![&#x200B; installeer pictogram &#x200B;](images/publishing-copyStagingCode.png)

1. Open de [&#x200B; plaats van de Luminagedemo &#x200B;](https://luma.enablementadobe.com/content/luma/us/en.html) in uw browser van Chrome

1. Open de [&#x200B; Debugger van het Experience Platform uitbreiding &#x200B;](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob) door het ![&#x200B; Debugger pictogram &#x200B;](images/icon-debugger.png) pictogram te klikken

   ![&#x200B; klik het Debugger pictogram &#x200B;](images/switchEnvironments-openDebugger.png)

1. Ga naar het tabblad Gereedschappen

1. Plak in de sectie **[!UICONTROL Adobe Launch > Replace Launch Embed Code]** de code voor het insluiten van het plakken in het klembord
1. De **[!UICONTROL Apply across luma.enablementadobe.com]** -switch inschakelen

1. Klik op het schijfpictogram om op te slaan

   ![&#x200B; markeringsmilieu dat in Debugger &#x200B;](images/switchEnvironments-debugger-save.png) wordt getoond

1. Laad en controleer het Summiere lusje van Debugger opnieuw. Onder de sectie Starten ziet u nu dat de eigenschap Staging is geïmplementeerd en de naam van uw eigenschap (dat wil zeggen &#39;tagzelfstudie&#39; of een andere naam voor uw eigenschap) wordt weergegeven!

   ![&#x200B; markeringsmilieu dat in Debugger &#x200B;](images/publishing-debugger-staging.png) wordt getoond

In het echte leven, zodra uw team QA door de veranderingen in het het Opvoeren milieu te herzien heeft afgemeld, is het tijd om aan productie te publiceren.

## Publish naar Production

1. Ga naar de [!UICONTROL Publishing] -pagina

1. Klik in het vervolgkeuzemenu op **[!UICONTROL Approve for Publishing]** :

   ![&#x200B; goedkeuren voor het Publiceren &#x200B;](images/publishing-approveForPublishing.png)

1. Klik op de knop **[!UICONTROL Approve]** in het dialoogvenster:

   ![&#x200B; klik goedkeuren &#x200B;](images/publishing-approve.png)

1. De bibliotheek wordt nu in de kolom [!UICONTROL Approved] in de ongebouwde staat (gele punt) weergegeven:

1. Open het vervolgkeuzemenu en selecteer **[!UICONTROL Build and Publish to Production]** :

   ![&#x200B; klik Bouwstijl &amp; Publish aan Productie &#x200B;](images/publishing-buildAndPublishToProduction.png)

1. Klik op **[!UICONTROL Publish]** in het dialoogvenster:

   ![&#x200B; klik Publish &#x200B;](images/publishing-publish.png)

1. De bibliotheek wordt nu in de kolom [!UICONTROL Published] weergegeven:

   ![&#x200B; Gepubliceerd &#x200B;](images/publishing-published.png)

Dat is het! U hebt de zelfstudie voltooid en uw eerste eigenschap in tags gepubliceerd!
