---
title: Zelfstudie Adobe Experience Cloud implementeren in mobiele apps
description: Leer hoe u de mobiele Adobe Experience Cloud-toepassingen implementeert. Deze zelfstudie begeleidt u door een implementatie van Experience Cloud-toepassingen in een voorbeeldtoepassing Swift.
recommendations: noDisplay,catalog
last-substantial-update: 2023-11-29T00:00:00Z
exl-id: daff4214-d515-4fad-a224-f7589b685b55
source-git-commit: 4bd8d0cdcf9c5d29434de4968a048fd46e163b54
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 0%

---

# Zelfstudie Adobe Experience Cloud implementeren in mobiele apps

Leer hoe u Adobe Experience Cloud-toepassingen implementeert in uw mobiele app met de Adobe Experience Platform Mobile SDK.

Experience Platform Mobile SDK is een client-side SDK waarmee klanten van Adobe Experience Cloud via het Adobe Experience Platform Edge Network kunnen communiceren met zowel Adobe-toepassingen als services van derden. Zie de [Adobe Experience Platform Mobile SDK-documentatie](https://developer.adobe.com/client-sdks/home/) voor meer gedetailleerde informatie.

![Architectuur](assets/architecture.png)


Deze zelfstudie begeleidt u bij de implementatie van de Platform Mobile SDK in een voorbeeldtoepassing die Luma wordt genoemd. De [Luma-app](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) heeft functionaliteit waarmee u een realistische implementatie kunt maken. Nadat u deze zelfstudie hebt voltooid, kunt u al uw marketingoplossingen implementeren via Experience Platform Mobile SDK in uw eigen mobiele apps.

De lessen zijn ontworpen voor iOS en geschreven in Swift/SwiftUI, maar veel van de concepten zijn ook van toepassing op Android™.

Na het voltooien van deze zelfstudie kunt u het volgende doen:

* Maak een schema met gebruik van standaard- en aangepaste veldgroepen.
* Stel een gegevensstroom in.
* Configureer een eigenschap voor een mobiele tag.
* Opstelling een dataset van het Experience Platform (facultatief).
* Tagextensies installeren en implementeren in een app.
* Geef Experience Cloud-parameters correct door aan een [webweergave](web-views.md).
* De implementatie valideren met [Adobe Experience Platform Assurance](assurance.md).
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
>Een vergelijkbare zelfstudie met meerdere oplossingen is beschikbaar voor [Web SDK](../tutorial-web-sdk/overview.md).

## Vereisten

In deze lessen, wordt verondersteld dat u een Adobe identiteitskaart en de vereiste gebruiker-vlakke toestemmingen hebt om de oefeningen te voltooien. Zo niet, dan moet u contact opnemen met de beheerder van de Adobe om toegang aan te vragen.

* In de Inzameling van Gegevens, moet u:
   * **[!UICONTROL Platforms]**—machtigingsitem **[!UICONTROL Mobiel]**
   * **[!UICONTROL Eigendomsrechten]**—machtigingsitems naar **[!UICONTROL Ontwikkelen]**, **[!UICONTROL Goedkeuren]**, **[!UICONTROL Publiceren]**, **[!UICONTROL Extensies beheren]**, en **[!UICONTROL Omgevingen beheren]**.
   * **[!UICONTROL Bedrijfsrechten]**—machtigingsitems naar **[!UICONTROL Eigenschappen beheren]** en, als het voltooien van de optionele pushberichtles, **[!UICONTROL App Configurations beheren]**

     Zie voor meer informatie over tagmachtigingen [Gebruikersmachtigingen voor tags](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html?lang=en){target="_blank"} in de productdocumentatie.
* In Experience Platform moet u beschikken over:
   * **[!UICONTROL Gegevensmodellering]**—machtigingsitems om schema&#39;s te beheren en weer te geven.
   * **[!UICONTROL Identity Management]**—machtigingsitems om naamruimten te beheren en weer te geven.
   * **[!UICONTROL Gegevensverzameling]**—machtigingsitems om gegevensstromen te beheren en weer te geven.

   * Als u de klant bent van een toepassing op basis van een platform, zoals Real-Time CDP, Journey Optimizer of Customer Journey Analytics, en de verwante lessen uitvoert die u ook moet hebben:
      * **[!UICONTROL Gegevensbeheer]**—toestemmingspunten om datasets te beheren en te bekijken.
      * Een ontwikkeling **sandbox** die u voor deze zelfstudie kunt gebruiken.

   * Voor de Journey Optimizer-lessen hebt u machtigingen nodig om de **pushmeldingsservice** en om een **toepassingsoppervlak**, **reis**, **message**, en **berichtvoorinstellingen**. Voor Beslissingsbeheer hebt u de juiste machtigingen nodig om **aanbiedingen beheren** en **besluiten** zoals beschreven [hier](https://experienceleague.adobe.com/docs/journey-optimizer/using/access-control/privacy/high-low-permissions.html?lang=en#decisions-permissions).

* Voor Adobe Analytics moet je weten welke **rapportsuites** u kunt deze zelfstudie voltooien.

* Voor Adobe Target moet u toestemming hebben om activiteiten te maken en activeren.


>[!NOTE]
>
>Als deel van dit leerprogramma, creeert u schema&#39;s, datasets, identiteiten, etc. Als meerdere personen deze zelfstudie in één sandbox doorlopen, kunt u bij het maken van deze objecten overwegen een identificatie toe te voegen of vooraf in te stellen als onderdeel van uw naamgevingsconventies. Voeg bijvoorbeeld ` - <your name or initials>` op de naam van het object dat u moet maken.

## Versiehistorie

* 29 nov. 2023: ingrijpende revisie met nieuwe voorbeeldapp en nieuwe lessen voor in-app messaging, beslissingsbeheer en Adobe Target.
* 9 mrt. 2022: eerste publicatie

## De app Luma downloaden

U kunt twee versies van de voorbeeldtoepassing downloaden. Beide versies kunnen worden gedownload/gekloond vanaf [Github](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App). U vindt twee mappen:


1. [Start](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}: een project zonder code of met placeholdercode voor het grootste deel van de Experience Platform Mobiele SDK code u moet gebruiken om de hands-on oefeningen in dit leerprogramma te voltooien.
1. [Voltooien](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}: een versie met de volledige implementatie ter referentie.


>[!NOTE]
>
>U gebruikt iOS als platform, [!DNL Swift] als programmeertaal, [!DNL SwiftUI] als UI-framework en [!DNL Xcode] als de geïntegreerde ontwikkelomgeving (IDE). Veel van de beschreven implementatieconcepten zijn echter vergelijkbaar voor andere ontwikkelingsplatforms. Velen hebben deze zelfstudie al voltooid met weinig tot geen ervaring in iOS/Swift(UI). U hoeft geen expert te zijn om de lessen te voltooien, maar u kunt meer uit de lessen halen als u de code comfortabel kunt lezen en begrijpen.


Laten we beginnen!

>[!SUCCESS]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796).

Volgende: **[Een XDM-schema maken](create-schema.md)**
