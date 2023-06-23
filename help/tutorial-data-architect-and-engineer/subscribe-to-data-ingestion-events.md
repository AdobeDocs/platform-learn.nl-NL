---
title: Abonneren op gebeurtenissen voor gegevensinvoer
seo-title: Subscribe to data ingestion events | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Abonneren op gebeurtenissen voor gegevensinvoer
description: In deze les meldt u zich aan gebeurtenissen voor het opnemen van gegevens door een webhaak in te stellen met de Adobe Developer-console en een hulpprogramma voor het ontwikkelen van online webhaken. U zult deze gebeurtenissen gebruiken om de status van uw taken van de gegevensopname in de verdere lessen te controleren.
role: Data Engineer
feature: Data Management
jira: KT-4348
thumbnail: 4348-subscribe-to-data-ingestion-events.jpg
exl-id: f4b90832-4415-476f-b496-2f079b4fcbbc
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# Abonneren op gebeurtenissen voor gegevensinvoer

<!--25min-->

In deze les meldt u zich aan gebeurtenissen voor het opnemen van gegevens door een webhaak in te stellen met de Adobe Developer-console en een hulpprogramma voor het ontwikkelen van online webhaken. U zult deze gebeurtenissen gebruiken om de status van uw taken van de gegevensopname in de verdere lessen te controleren.

**Gegevensengineers** zal aan de gebeurtenissen van de gegevensopname buiten dit leerprogramma willen intekenen.
**Gegevensarchitecten** _kan deze les overslaan_ en ga naar de [batch-opname les](ingest-batch-data.md).

## Vereiste machtigingen

In de [Machtigingen configureren](configure-permissions.md) les, plaatst u opstelling alle toegangscontroles die worden vereist om deze les te voltooien, specifiek:

<!--* Developer-role access to the `Luma Tutorial Platform` product profile (for API)
-->

>[!IMPORTANT]
>
> Deze meldingen die worden geactiveerd door de gebeurtenissen voor het invoeren van gegevens zijn van toepassing op _al uw sandboxen_, niet alleen uw `Luma Tutorial`. Mogelijk ziet u ook meldingen die afkomstig zijn van andere gebeurtenissen voor het invoeren van gegevens in uw account.


## Webhaak instellen

In deze oefening zullen we een webhaak maken met behulp van een online hulpprogramma met de naam webhaak.site (u kunt alle andere webhshontwikkelingsprogramma&#39;s die u liever gebruikt, gratis vervangen):

1. Open de website op een ander browsertabblad [https://webhook.site/](https://webhook.site/)
1. U krijgt een unieke URL toegewezen, die u als bladwijzer moet gebruiken, aangezien u er later in de lessen over gegevensinvoer op terugkeert:

   ![Webhaak.site](assets/ioevents-webhook-home.png)
1. Selecteer **Bewerken** knop in de bovenste navigatie
1. Als de antwoordinstantie voert u `$request.query.challenge$`. De Adobe I/O Events berichten wij opstelling later in deze les sturen een uitdaging aan de webhaak, en vereist dat het in het reactielichaam wordt omvat.
1. Selecteer **Opslaan** knop

   ![Het antwoord bewerken](assets/ioevents-webhook-editResponse.png)

## Instellen

1. Open op een ander browsertabblad het tabblad [Adobe Developer Console](https://console.adobe.io/)
1. Open uw `Luma Tutorial API Project`
1. Selecteer **[!UICONTROL Toevoegen aan project]** en selecteert u vervolgens **[!UICONTROL Gebeurtenis]**

   ![Gebeurtenis toevoegen](assets/ioevents-addEvents.png)
1. Filter de lijst door **[!UICONTROL Experience Platform]**
1. Selecteren **[!UICONTROL Meldingen van Platforms]**
1. Selecteer **[!UICONTROL Volgende]** knop
   ![Meldingen toevoegen](assets/ioevents-addNotifications.png)
1. Alle gebeurtenissen selecteren
1. Selecteer **[!UICONTROL Volgende]** knop
   ![Abonnementen selecteren](assets/ioevents-addSubscriptions.png)
1. Selecteer in het volgende scherm voor het configureren van referenties de optie **[!UICONTROL Volgende]** nogmaals klikken
   ![Het referentiescherm overslaan](assets/ioevents-clickNext.png)
1. Als de **[!UICONTROL Naam van gebeurtenisregistratie]**, enter `Platform notifications`
1. Omlaag schuiven en selecteren om het dialoogvenster **[!UICONTROL Webhaak]** sectie
1. Als de **[!UICONTROL Webhaak-URL]** plak de waarde in het menu **Uw unieke URL** veld van webhaak.site
1. Selecteer **[!UICONTROL geconfigureerde gebeurtenissen opslaan]** knop
   ![Gebeurtenissen opslaan](assets/ioevents-addWebhook.png)
1. Wacht op uw configuratie om te bewaren en u zou moeten zien dat uw `Platform notifications` De gebeurtenis is Actief met uw webhaakdetails en geen foutenmeldingen
   ![Opgeslagen configuratie](assets/ioevents-webhookConfigured.png)
1. Ga terug naar het tabblad web.site en u ziet het eerste verzoek aan de webhaak dat voortvloeit uit de validatie van de configuratie van de Developer Console:
   ![Eerste aanvraag in webshaak.site](assets/ioevents-webhook-firstRequest.png)

Dat is het voor nu, zult u meer over deze berichten in de volgende lessen leren wanneer u gegevens opneemt.

## Aanvullende bronnen

* [Webhaak.site](https://webhook.site/)
* [Documentatie over gegevensinvoer](https://experienceleague.adobe.com/docs/experience-platform/ingestion/quality/subscribe-events.html)
* [Aan de slag met de Adobe I/O Events-documentatie](https://www.adobe.io/apis/experienceplatform/events/docs.html)

Ok, laten we eindelijk beginnen [opnemen, gegevens](ingest-batch-data.md)!
