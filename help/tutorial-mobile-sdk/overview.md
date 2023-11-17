---
title: Zelfstudie Adobe Experience Cloud implementeren in mobiele apps
description: Leer hoe u de mobiele Adobe Experience Cloud-toepassingen implementeert. Deze zelfstudie begeleidt u door een implementatie van Experience Cloud-toepassingen in een voorbeeldtoepassing Swift.
recommendations: noDisplay,catalog
exl-id: daff4214-d515-4fad-a224-f7589b685b55
source-git-commit: 94ca4a238c241518219fb2e8d73f775836f86d86
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 1%

---

# Zelfstudie Adobe Experience Cloud implementeren in mobiele apps

Leer hoe u Adobe Experience Cloud-toepassingen implementeert in uw mobiele app met de Adobe Experience Platform Mobile SDK.

>[!INFO]
>
> Deze zelfstudie wordt eind november 2023 vervangen door een nieuwe zelfstudie met een nieuwe mobiele voorbeeldtoepassing

Experience Platform Mobile SDK is een client-side SDK waarmee klanten van Adobe Experience Cloud via het Adobe Experience Platform Edge Network kunnen communiceren met zowel Adobe-toepassingen als services van derden. Zie de [Adobe Experience Platform Mobile SDK-documentatie](https://developer.adobe.com/client-sdks/documentation/) voor meer gedetailleerde informatie.

![build-instellingen](assets/data-collection-mobile-sdk.png)


Deze zelfstudie begeleidt u bij de implementatie van de Platform Mobile SDK in een voorbeeldtoepassing die Luma wordt genoemd. De [Luma-app](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) heeft functionaliteit waarmee u een realistische implementatie kunt maken. Nadat u deze zelfstudie hebt voltooid, kunt u al uw marketingoplossingen implementeren via Platform Mobile SDK in uw eigen mobiele apps.

De lessen zijn ontworpen voor iOS en geschreven in Swift, maar veel van de concepten zijn ook van toepassing op Android™.

Na het voltooien van deze zelfstudie kunt u het volgende doen:

* Maak een schema met gebruik van standaard- en aangepaste veldgroepen.
* Stel een gegevensstroom in.
* Configureer een eigenschap voor een mobiele tag.
* Opstelling een dataset van het Experience Platform (facultatief).
* Tagextensies installeren en implementeren in een app.
* Voeg de volgende Adobe Experience Cloud-toepassingen/extensies toe:
   * [Adobe Experience Platform Edge (XDM)](events.md)
   * [Levenscyclusgegevensverzameling](lifecycle-data.md)
   * [Adobe Analytics via XDM](analytics.md)
   * [Toestemming](consent.md)
   * [Identiteit](identity.md)
   * [Profiel](profile.md)
   * [Adobe Experience Platform](platform.md)
   * [Push messaging (Push messaging) met Journey Optimizer](journey-optimizer-push.md)
* Geef Experience Cloud-parameters correct door aan een [webweergave](web-views.md).
* De implementatie valideren met [Adobe Experience Platform Assurance](assurance.md).

>[!NOTE]
>
>Een vergelijkbare zelfstudie met meerdere oplossingen is beschikbaar voor [Web SDK](../tutorial-web-sdk/overview.md).

## Vereisten

In deze lessen wordt aangenomen dat u een Adobe-id en de vereiste machtigingen hebt om de oefeningen te voltooien. Zo niet, dan moet u contact opnemen met de beheerder van de Adobe om toegang aan te vragen.

* In de Inzameling van Gegevens, moet u:
   * **[!UICONTROL Platforms]**—machtigingsitem **[!UICONTROL Mobiel]**
   * **[!UICONTROL Eigendomsrechten]**—machtigingsitems naar **[!UICONTROL Ontwikkelen]**, **[!UICONTROL Goedkeuren]**, **[!UICONTROL Publiceren]**, **[!UICONTROL Extensies beheren]**, en **[!UICONTROL Omgevingen beheren]**.
   * **[!UICONTROL Bedrijfsrechten]**—machtigingsitems naar **[!UICONTROL Eigenschappen beheren]** en, als het voltooien van de optionele pushberichtles, **[!UICONTROL App Configurations beheren]**

     Zie voor meer informatie over tagmachtigingen [Gebruikersmachtigingen voor tags](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html?lang=en){target="_blank"} in de productdocumentatie.
* In Experience Platform moet u beschikken over:
   * **[!UICONTROL Gegevensmodellering]**—machtigingsitems om schema&#39;s te beheren en weer te geven.
   * **[!UICONTROL Identity Management]**—machtigingsitems om naamruimten te beheren en weer te geven.
   * **[!UICONTROL Gegevensverzameling]**—machtigingsitems om gegevensstromen te beheren en weer te geven.

   * Als u de klant bent van een platformgebaseerde toepassing zoals Real-Time CDP, Journey Optimizer of Customer Journey Analytics, moet u ook:
      * **[!UICONTROL Gegevensbeheer]**—toestemmingspunten om datasets te beheren en te bekijken om te voltooien _optionele platformoefeningen_ (vereist een licentie voor een toepassing op basis van een platform).
      * Een ontwikkeling **sandbox** die u voor deze zelfstudie kunt gebruiken.
* Voor Adobe Analytics moet je weten welke **rapportsuites** u kunt deze zelfstudie voltooien.

Alle klanten van het Experience Cloud zouden toegang tot de vereiste eigenschappen moeten hebben nodig om Mobiele SDK op te stellen.

Ook wordt aangenomen dat u vertrouwd bent met [!DNL Swift]. U hoeft geen expert te zijn om de lessen te voltooien, maar u krijgt er meer uit als u de code comfortabel kunt lezen en begrijpen.

## De app Luma downloaden

U kunt twee versies van de voorbeeldtoepassing downloaden.

1. [Leeg](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"} - versie zonder enige code van het Experience Cloud om de hands-on oefeningen in dit leerprogramma te voltooien
1. [Volledig geïmplementeerd](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"} - versie met volledige implementatie van het Experience Cloud ter referentie.

Laten we beginnen!


Volgende: **[Een XDM-schema maken](create-schema.md)**

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)