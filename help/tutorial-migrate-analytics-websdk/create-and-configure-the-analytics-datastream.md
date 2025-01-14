---
title: Een gegevensstroom maken en configureren
description: Leer hoe u een nieuwe gegevensstroom maakt en configureert, zodat uw websitegegevens naar Adobe Analytics kunnen worden gerouteerd.
solution: Data Collection, Analytics
feature: Web SDK
jira: KT-16757
source-git-commit: 7ae56d997884cf1558e72c0ad553df1c5d43c081
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---


# Een gegevensstroom maken en configureren

Leer hoe u een nieuwe gegevensstroom maakt en configureert, zodat uw websitegegevens naar Adobe Analytics kunnen worden gerouteerd.

In deze les leert u hoe u het systeem maakt en configureert, zodat uw gegevens van uw website naar de Adobe Edge stromen en vervolgens van daar naar Adobe Analytics worden gerouteerd.

![ Diagram van de Architectuur ](assets/architecture_diagram.jpg)

## Een nieuwe ontwikkelingsgegevensstroom maken

1. De interface voor gegevensverzameling Adoben openen
   1. Ga in uw browser naar https://experience.adobe.com
   1. Zorg ervoor dat de juiste organisatie boven aan de pagina is geselecteerd (bijv. Adobe productie - Tech Marketing Demos in de onderstaande afbeelding)
   1. Klik op de &quot;negen punten,&quot;AKA de toepassingsschakelaar, en selecteer **Inzameling van Gegevens**

      ![ ga aan gegevensinzameling ](assets/navigate-to-data-collection.jpg)

1. Ga naar **[!UICONTROL Datastreams]** in de linkernavigatie
1. Selecteren **[!UICONTROL New Datastream]**
1. Voer de gewenste **[!UICONTROL Name]** in en voeg een indicator toe die wordt gebruikt voor de ontwikkelomgeving van Web SDK. U kunt dit bijvoorbeeld na uw site een naam geven, zoals hieronder wordt weergegeven. Noteer dit, aangezien er later naar deze naam wordt verwezen wanneer u de extensie Web SDK configureert in de eigenschap tag. Voer desgewenst een beschrijving in.

   >[!NOTE]
   >
   >U moet slechts een schema selecteren als het gebruiken van [ Prep van Gegevens voor de eigenschap van de Inzameling van Gegevens ](https://experienceleague.adobe.com/en/docs/platform-learn/data-collection/edge-network/data-prep), die wij niet in dit leerprogramma zullen doen. Ga naar de link voor meer informatie.

1. Selecteren **[!UICONTROL Save]**

   ![ creeer de datastream ](assets/create-new-datastream.jpg)

1. Zodra de gegevensstroom wordt bewaard, zal een nieuw scherm omhoog komen, latend u weten dat u geen diensten hebt die nog worden gevormd. Met andere woorden, uw gegevens worden naar Edge-servers verzonden, maar worden pas naar andere toepassingen verzonden als we een service toevoegen. We configureren de gegevensstroom nu om de gegevens naar Adobe Analytics te verzenden. Klik op **[!UICONTROL Add Service]**.
   ![ voegt de Dienst ](assets/datastream-add-service.jpg) toe
1. Selecteer **[!UICONTROL Adobe Analytics]** in het vervolgkeuzemenu voor de service.
1. Op het gebied van identiteitskaart van de rapportreeks, ga identiteitskaart (niet de titel, maar eerder rapportreeks identiteitskaart) van de reeks van het bevestigingsrapport in die u in [ creeerde creeer een de reeks van het bevestigingsrapport ](create-a-validation-report-suite.md) activiteit. Klik op **[!UICONTROL Save]**.

## Staging- en productiegegevensstromen

U zult nu **door de zelfde stappen** twee meer keer willen gaan: eens voor uw het opvoeren milieu en eens voor uw productiemilieu. Hieronder vindt u een aantal notities bij het instellen van deze twee extra gegevensstromen.

### De testgegevensstroom

* Wanneer u de gegevensstroom een naam geeft (en wanneer u de beschrijving toevoegt), kunt of moet u dezelfde naam hebben met het verschil of u &quot;staging&quot; toevoegt in plaats van &quot;development&quot;.
* Voeg de Adobe Analytics-service toe, zoals u dat eerder hebt gedaan, en stel de rapportsuite in op dezelfde suite voor ontwikkelingsrapporten.
* Als u een schonere omgeving voor het bekijken van het opvoeren van aantallen in uw rapporten van Adobe Analytics wilt, kunt u een nieuwe rapportreeks enkel voor het opvoeren tot stand brengen, en dan ervoor zorgen dat u aan die rapportreeks in de dienst van Analytics van deze gegevensstroom richt.

### De productiegegevensstroom

* Wanneer u de gegevensstroom een naam geeft (en wanneer u de beschrijving toevoegt), kunt of moet u dezelfde naam hebben met het verschil om &quot;productie&quot; toe te voegen in plaats van &quot;ontwikkeling&quot;.
* Wanneer het kiezen van de rapportreeks om de gegevens aan in kaart te brengen, in plaats van de reeks van het ontwikkelingsrapport of zelfs een nieuwe rapportreeks te kiezen, kunt u deze gegevensstroom in kaart brengen aan uw **huidige** reeks van het productierapport die door de implementatie van het AppMeasurement wordt gevoed. Op die manier kunt u, nadat u de migratie hebt voltooid en deze hebt getest en tevreden bent met de getallen, de oude code van het AppMeasurement verwijderen, de tagbibliotheken naar de productie verzenden en de nieuwe productiegegevens naar dezelfde productierapportsuite verzenden, zodat u continuïteit hebt tussen oude en nieuwe implementaties.
