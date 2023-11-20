---
title: Overschakelen van labelomgevingen met Adobe Experience Cloud Debugger
description: Leer hoe u het Experience Cloud Debugger kunt gebruiken om verschillende tags in te sluiten. Deze les maakt deel uit van de zelfstudie Experience Cloud implementeren in websites.
exl-id: 29972a00-e5e0-4fe0-a71c-c2ca106938be
source-git-commit: 2483409b52562e13a4f557fe5bdec75b5afb4716
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# Tagomgevingen wisselen met het Experience Cloud Debugger

In deze les gebruikt u de [Adobe Experience Platform Debugger-extensie](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob) om de eigenschap tag te vervangen die op de [Luma-demosite](https://luma.enablementadobe.com/content/luma/us/en.html) met uw eigen eigenschap.

Deze techniek wordt omgevingsomschakeling genoemd en is later handig wanneer u met tags op uw eigen website werkt. U kunt uw productiewebsite in uw browser, maar met uw *ontwikkeling* tagomgeving. Hierdoor kunt u met vertrouwen wijzigingen in tags doorvoeren en valideren, onafhankelijk van uw reguliere code-releases.  Per slot van rekening is deze scheiding van marketing markeringsversies van uw regelmatige codeversies één van de belangrijkste redenen klanten in de eerste plaats labels gebruiken!

>[!NOTE]
>
>Adobe Experience Platform Launch wordt in Adobe Experience Platform geïntegreerd als een reeks technologieën voor gegevensverzameling. Verschillende terminologiewijzigingen zijn geïmplementeerd in de interface die u tijdens het gebruik van deze inhoud moet onthouden:
>
> * Platform launch (clientzijde) is nu **[[!DNL tags]](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl)**
> * Platform launch Server-zijde is nu **[[!DNL event forwarding]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html)**
> * Edge-configuraties zijn nu **[[!DNL datastreams]](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)**

## Leerdoelen

Aan het eind van deze les, zult u kunnen:

* Foutopsporing gebruiken om een andere tagomgeving te laden
* Gebruik Foutopsporing om te controleren of u een andere tagomgeving hebt geladen

## Krijg URL van uw Milieu van de Ontwikkeling

1. Open in de eigenschap Tag de optie `Environments` page

1. In de **[!UICONTROL Ontwikkeling]** rij, klik het Install pictogram ![Installatiepictogram](images/launch-installIcon.png) om het modale

1. Klik op het pictogram Copy ![Pictogram kopiëren](images/launch-copyIcon.png) om de insluitcode naar het klembord te kopiëren

1. Klikken **[!UICONTROL Sluiten]** om het modale

   ![Installatiepictogram](images/launch-copyInstallCode.png)

## De URL van de tag op de demopsite van Luma vervangen

1. Open de [Luma-demosite](https://luma.enablementadobe.com/content/luma/us/en.html) in uw Chrome-browser

1. Open de [Experience Platform debugger-extensie](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob) door op de knop ![Foutopsporingspictogram](images/icon-debugger.png) pictogram

   ![Klik op het pictogram Foutopsporing](images/switchEnvironments-openDebugger.png)

1. De momenteel geïmplementeerde eigenschap tag wordt weergegeven op het tabblad Overzicht

   ![tagomgeving weergegeven in Foutopsporing](images/switchEnvironments-debuggerOnWeRetail-prod.png)

1. Ga naar het tabblad Gereedschappen
1. Naar de sectie schuiven **[!UICONTROL Insluitcode starten vervangen]**
1. Zorg ervoor dat het tabblad Chroom met de Luminantiesite de focus heeft achter Foutopsporing (niet het tabblad met deze zelfstudie of het tabblad met de interface voor gegevensverzameling).  Plak de insluitcode in het klembord in het invoerveld
1. Schakel de functie Toepassen op luma.enablementadobe.com in en uit, zodat alle pagina&#39;s op de Luministsite worden toegewezen aan uw tag-eigenschap
1. Klik op de knop **[!UICONTROL Opslaan]** knop

   ![tagomgeving weergegeven in Foutopsporing](images/switchEnvironments-debugger-save.png)

1. Laad de Luminasite opnieuw en controleer het tabblad Samenvatting van Foutopsporing. Onder de sectie van de Lancering, zou u uw Bezit van de Ontwikkeling nu moeten zien wordt gebruikt. Bevestig dat zowel de Naam van het bezit van u als dat het Milieu &quot;ontwikkeling&quot;zegt.

   ![tagomgeving weergegeven in Foutopsporing](images/switchEnvironments-debuggerOnWeRetail.png)

>[!NOTE]
>
>De foutopsporing slaat deze configuratie op en vervangt de insluitcodes van de tag wanneer u terugkeert naar de Luministensite. Het heeft geen invloed op andere sites die u in andere geopende tabbladen bezoekt. Als u wilt voorkomen dat Foutopsporing de insluitcode vervangt, klikt u op de knop **[!UICONTROL Verwijderen]** naast de insluitcode op het tabblad Gereedschappen van Foutopsporing.

Terwijl u de zelfstudie voortzet, gebruikt u deze techniek om de Luministsite toe te wijzen aan uw eigen tageigenschap om de implementatie van de tag te valideren. Wanneer u labels gaat gebruiken op uw productiewebsite, kunt u met dezelfde techniek wijzigingen valideren.

[Volgende &quot;Voeg de Adobe Experience Platform Identity Service toe&quot; >](id-service.md)
