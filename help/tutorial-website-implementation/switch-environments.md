---
title: Overschakelen van labelomgevingen met Adobe Experience Cloud Debugger
description: Leer hoe u met Foutopsporing in de cloud verschillende insluitcodes kunt laden. Deze les maakt deel uit van de zelfstudie Experience Cloud implementeren in websites.
exl-id: 29972a00-e5e0-4fe0-a71c-c2ca106938be
source-git-commit: 935b8d18b6aef506fc5f48c64331803fe8a7ea9e
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---

# Overschakelen van labelomgevingen met Experience Cloud Debugger

In deze les zult u de [ uitbreiding van Adobe Experience Platform Debugger ](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob) gebruiken om het markeringsbezit te vervangen dat op de [ Luma demo plaats ](https://luma.enablementadobe.com/content/luma/us/en.html) met uw eigen bezit wordt hard gecodeerd.


>[!WARNING]
>
> Deze zelfstudie en de bijbehorende Luma-website-oefeningen blijven niet meer behouden en zijn afhankelijk van oudere JavaScript-bibliotheken. Om de huidige beste praktijken te leren, te gebruiken gelieve [ Adobe Experience Cloud met het leerprogramma van SDK van het Web uit te voeren ](https://experienceleague.adobe.com/en/docs/platform-learn/implement-web-sdk/overview).

Deze techniek wordt omgevingsomschakeling genoemd en is later handig wanneer u met tags op uw eigen website werkt. U zult uw productiewebsite in uw browser, maar met uw *ontwikkelings* markeringsmilieu kunnen laden. Hierdoor kunt u met vertrouwen wijzigingen in tags doorvoeren en valideren, onafhankelijk van uw reguliere code-releases.  Per slot van rekening is deze scheiding van marketing markeringsversies van uw regelmatige codeversies één van de belangrijkste redenen klanten in de eerste plaats labels gebruiken!


## Leerdoelen

Aan het eind van deze les, zult u kunnen:

* Foutopsporing gebruiken om een andere tagomgeving te laden
* Gebruik Foutopsporing om te controleren of u een andere tagomgeving hebt geladen

## Krijg URL van uw Milieu van de Ontwikkeling

1. Open de pagina `Environments` in de eigenschap Tag

1. In de **[!UICONTROL Development]** rij, klik het Install pictogram ![ installeren pictogram ](images/launch-installIcon.png) om modaal te openen

1. Klik het pictogram van het Exemplaar ![ pictogram van het Exemplaar ](images/launch-copyIcon.png) om de ingebedde code aan uw klembord te kopiëren

1. Klik op **[!UICONTROL Close]** om het modale

   ![ installeer pictogram ](images/launch-copyInstallCode.png)

## De URL van de tag op de demopsite van Luma vervangen

1. Open de [ plaats van de Luminagedemo ](https://luma.enablementadobe.com/content/luma/us/en.html) in uw browser van Chrome

1. Open de [ Debugger van Experience Platform uitbreiding ](https://chromewebstore.google.com/detail/adobe-experience-platform/bfnnokhpnncpkdmbokanobigaccjkpob) door het ![ Debugger pictogram ](images/icon-debugger.png) pictogram te klikken

   ![ klik het Debugger pictogram ](images/switchEnvironments-openDebugger.png)

1. De momenteel geïmplementeerde eigenschap tag wordt weergegeven op het tabblad Overzicht

   ![ markeringsmilieu dat in Debugger ](images/switchEnvironments-debuggerOnWeRetail-prod.png) wordt getoond

1. Ga naar het tabblad Gereedschappen
1. Naar de sectie schuiven **[!UICONTROL Replace Launch Embed Code]**
1. Zorg ervoor dat het Chrome-tabblad met de Luminantiesite de focus heeft achter Foutopsporing (niet het tabblad met deze zelfstudie of het tabblad met de interface voor gegevensverzameling).  Plak de insluitcode in het klembord in het invoerveld
1. Schakel de functie Toepassen op luma.enablementadobe.com in en uit, zodat alle pagina&#39;s op de Luministsite worden toegewezen aan uw tag-eigenschap
1. Klik op de knop **[!UICONTROL Save]**

   ![ markeringsmilieu dat in Debugger ](images/switchEnvironments-debugger-save.png) wordt getoond

1. Laad de Luminasite opnieuw en controleer het tabblad Samenvatting van Foutopsporing. Onder de sectie van de Lancering, zou u uw Bezit van de Ontwikkeling nu moeten zien wordt gebruikt. Bevestig dat zowel de Naam van het bezit van u als dat het Milieu &quot;ontwikkeling&quot;zegt.

   ![ markeringsmilieu dat in Debugger ](images/switchEnvironments-debuggerOnWeRetail.png) wordt getoond

>[!NOTE]
>
>De foutopsporing slaat deze configuratie op en vervangt de insluitcodes van de tag wanneer u terugkeert naar de Luministensite. Het heeft geen invloed op andere sites die u in andere geopende tabbladen bezoekt. Als u wilt voorkomen dat Foutopsporing de insluitcode vervangt, klikt u op de knop **[!UICONTROL Remove]** naast de insluitcode op het tabblad Extra van Foutopsporing.

Terwijl u de zelfstudie voortzet, gebruikt u deze techniek om de Luministsite toe te wijzen aan uw eigen tageigenschap om de implementatie van de tag te valideren. Wanneer u labels gaat gebruiken op uw productiewebsite, kunt u met dezelfde techniek wijzigingen valideren.

[Volgende &quot;Voeg de Adobe Experience Platform Identity Service toe&quot; >](id-service.md)
