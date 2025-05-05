---
title: Zelfstudie Adobe Experience Cloud implementeren in mobiele apps
description: Leer hoe u de mobiele Adobe Experience Cloud-toepassingen implementeert. Deze zelfstudie begeleidt u door een implementatie van Experience Cloud-toepassingen in een voorbeeldtoepassing Swift.
recommendations: noDisplay,catalog
last-substantial-update: 2023-11-29T00:00:00Z
exl-id: daff4214-d515-4fad-a224-f7589b685b55
source-git-commit: c08671ae28955ff090baa7aa5a47246b2196ba20
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---

# Zelfstudie Adobe Experience Cloud implementeren in mobiele apps

Leer hoe u Adobe Experience Cloud-toepassingen implementeert in uw mobiele app met Adobe Experience Platform Mobile SDK.

Experience Platform Mobile SDK is een client-side SDK die klanten van Adobe Experience Cloud in staat stelt te communiceren met zowel Adobe-toepassingen als services van derden via Adobe Experience Platform Edge Network. Zie de [ documentatie van Adobe Experience Platform Mobile SDK ](https://developer.adobe.com/client-sdks/home/) voor meer gedetailleerde informatie.

![Architectuur](assets/architecture.png)


Deze zelfstudie begeleidt u door de implementatie van Platform Mobile SDK in een voorbeeldtoepassing die Luma wordt genoemd. De [ app van de Luma ](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) heeft functionaliteit die u een realistische implementatie laat bouwen. Nadat u deze zelfstudie hebt voltooid, kunt u al uw marketingoplossingen implementeren via Experience Platform Mobile SDK in uw eigen mobiele apps.

De lessen zijn ontworpen voor iOS en geschreven in Swift/SwiftUI, maar veel van de concepten zijn ook van toepassing op Android™.

Na het voltooien van deze zelfstudie kunt u het volgende doen:

* Maak een schema met gebruik van standaard- en aangepaste veldgroepen.
* Stel een gegevensstroom in.
* Configureer een eigenschap voor een mobiele tag.
* Stel een Experience Platform-gegevensset in (optioneel).
* Tagextensies installeren en implementeren in een app.
* Ga correct de parameters van Experience Cloud tot a [ webview ](web-views.md) over.
* Valideer de implementatie gebruikend [ Adobe Experience Platform Assurance ](assurance.md).
* Voeg de volgende Adobe Experience Cloud-toepassingen/extensies toe:
   * [Adobe Experience Platform Edge (XDM)](events.md)
   * [Levenscyclusgegevensverzameling](lifecycle-data.md)
   * [Toestemming](consent.md)
   * [Identiteit](identity.md)
   * [Profiel](profile.md)
   * [Plaatsen](places.md)
   * [Analytics](analytics.md)
   * [Experience Platform](platform.md)
   * [Push messaging (Push messaging) met Journey Optimizer](journey-optimizer-push.md)
   * [In-app messaging met Journey Optimizer](journey-optimizer-inapp.md)
   * [Besluitbeheer met Journey Optimizer](journey-optimizer-offers.md)
   * [Target](target.md)


>[!NOTE]
>
>Een gelijkaardige multi-oplossingsleerprogramma is beschikbaar voor [ SDK van het Web ](../tutorial-web-sdk/overview.md).

## Machtigingen

In deze lessen wordt aangenomen dat u een Adobe-id en de vereiste gebruikersrechten hebt om de oefeningen te voltooien. Als dat niet het geval is, moet u contact opnemen met uw Adobe-beheerder om toegang aan te vragen.

* In de Inzameling van Gegevens, moet u:
   * **[!UICONTROL Platforms]**—machtigingsitem **[!UICONTROL Mobile]**
   * **[!UICONTROL Property Rights]** - wijs items toe aan **[!UICONTROL Develop]** , **[!UICONTROL Approve]** , **[!UICONTROL Publish]** , **[!UICONTROL Manage Extensions]** en **[!UICONTROL Manage Environments]** .
   * **[!UICONTROL Company Rights]**—Items toestaan aan **[!UICONTROL Manage Properties]**

     Voor meer informatie over markeringstoestemmingen, zie {de toestemmingen van 0} Gebruiker voor markeringen [&#128279;](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html?lang=en){target="_blank"} in de productdocumentatie.
* In Experience Platform moet u beschikken over:
   * **[!UICONTROL Data Modeling]** - machtigingsitems om schema&#39;s te beheren en weer te geven.
   * **[!UICONTROL Identity Management]** - machtigingsitems om naamruimten voor identiteiten te beheren en weer te geven.
   * **[!UICONTROL Data Collection]** - machtigingsitems om gegevensstromen te beheren en weer te geven.

   * Als u de klant bent van een toepassing op basis van een platform, zoals Real-Time CDP, Journey Optimizer of Customer Journey Analytics, en de bijbehorende lessen uitvoert, moet u ook het volgende doen:
      * **[!UICONTROL Data Management]** - toestemmingspunten om datasets te beheren en te bekijken.
      * Een ontwikkelings **zandbak** die u voor dit leerprogramma kunt gebruiken.

   * Voor de lessen van Journey Optimizer, hebt u toestemmingen nodig om de **duw- berichtdienst** te vormen en een **app oppervlakte**, a **reis**, a **bericht** te creëren, en **bericht stelt** vooraf in. Voor Beslissingsbeheer, hebt u de juiste toestemmingen nodig om aanbiedingen **en** besluiten **te beheren zoals [ hier ](https://experienceleague.adobe.com/docs/journey-optimizer/using/access-control/privacy/high-low-permissions.html?lang=en#decisions-permissions) wordt beschreven.**

* Voor Adobe Analytics, moet u weten welke **rapportreeksen** u kunt gebruiken om dit leerprogramma te voltooien.

* Voor Adobe Target moet u toestemming hebben om activiteiten te maken en activeren.


>[!NOTE]
>
>Als deel van dit leerprogramma, creeert u schema&#39;s, datasets, identiteiten, etc. Als meerdere personen deze zelfstudie in één sandbox doorlopen, kunt u bij het maken van deze objecten overwegen een identificatie toe te voegen of vooraf in te stellen als onderdeel van uw naamgevingsconventies. Voeg bijvoorbeeld ` - <your name or initials>` toe aan de naam van het object dat u moet maken.

## Versiehistorie

* 29 nov. 2023: ingrijpende revisie met nieuwe voorbeeldapp en nieuwe lessen voor in-app messaging, beslissingsbeheer en Adobe Target.
* 9 mrt. 2022: eerste publicatie

## De app Luma downloaden

U kunt twee versies van de voorbeeldtoepassing downloaden. Beide versie kan worden gedownload/worden gekloond van [ Github ](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App). U vindt twee mappen:


1. [ Begin ](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}: een project zonder code of met placeholdercode voor het grootste deel van de code van Experience Platform Mobile SDK u moet gebruiken om de hands-on oefeningen in dit leerprogramma te voltooien.
1. [ Einde ](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}: een versie met de volledige implementatie voor verwijzing.

>[!NOTE]
>
>U gebruikt iOS als platform, [!DNL Swift] als programmeertaal, [!DNL SwiftUI] als UI-framework en [!DNL Xcode] als de geïntegreerde ontwikkelomgeving (IDE). Veel van de beschreven implementatieconcepten zijn echter vergelijkbaar voor andere ontwikkelingsplatforms. Velen hebben deze zelfstudie al voltooid met weinig tot geen ervaring in iOS/Swift(UI). U hoeft geen expert te zijn om de lessen te voltooien, maar u kunt meer uit de lessen halen als u de code comfortabel kunt lezen en begrijpen.


U kunt de definitieve versie van de app downloaden van de App Store.

[![ Download ](assets/download-app.svg) ](https://apps.apple.com/us/app/luma-app/id6466588487)


Laten we beginnen!

>[!SUCCESS]
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene terugkoppelen willen delen, of suggesties over toekomstige inhoud hebben, hen op deze [ Communautaire besprekingspost van Experience League ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) delen.

Volgende: **[creeer een schema XDM](create-schema.md)**
