---
title: Zelfstudie Adobe Experience Cloud implementeren in mobiele apps
description: Leer hoe u de mobiele Adobe Experience Cloud-toepassingen implementeert. Deze zelfstudie begeleidt u door een implementatie van Experience Cloud-toepassingen in een voorbeeld van een Swift- of Android-app.
recommendations: noDisplay,catalog
last-substantial-update: 2023-11-29T00:00:00Z
exl-id: daff4214-d515-4fad-a224-f7589b685b55
source-git-commit: 342bb7efbe868622c4bc08e02568bce948fed61c
workflow-type: tm+mt
source-wordcount: '996'
ht-degree: 0%

---

# Zelfstudie Adobe Experience Cloud implementeren in mobiele apps

Leer hoe u Adobe Experience Cloud-toepassingen implementeert in uw mobiele app met de Adobe Experience Platform Mobile SDK.

Experience Platform Mobile SDK is een client-side SDK die klanten van Adobe Experience Cloud in staat stelt te communiceren met zowel Adobe-toepassingen als services van derden via Adobe Experience Platform Edge Network. Zie de [&#x200B; documentatie van Adobe Experience Platform Mobile SDK &#x200B;](https://developer.adobe.com/client-sdks/home/) voor meer gedetailleerde informatie.

![Architectuur](assets/architecture.png){zoomable="yes"}


Deze zelfstudie begeleidt u door de implementatie van Platform Mobile SDK in een voorbeeldtoepassing met de naam Luma. De app Luma heeft functionaliteit waarmee u een realistische implementatie kunt maken. Nadat u deze zelfstudie hebt voltooid, kunt u al uw marketingoplossingen implementeren via Experience Platform Mobile SDK in uw eigen mobiele apps.

De lessen zijn bedoeld voor:

* iOS, met behulp van de programmeertaal Swift en het SwiftUI-framework.
* Android, met de programmeertaal Kotlin en Java en het JetPack Compose-framework.

Na het voltooien van deze zelfstudie kunt u het volgende doen:

* Maak een schema met gebruik van standaard- en aangepaste veldgroepen.
* Stel een gegevensstroom in.
* Configureer een eigenschap voor een mobiele tag.
* Stel een Experience Platform-gegevensset in (optioneel).
* Tagextensies installeren en implementeren in een app.
* Ga correct de parameters van Experience Cloud tot a [&#x200B; webview &#x200B;](web-views.md) over.
* Valideer de implementatie gebruikend [&#x200B; Adobe Experience Platform Assurance &#x200B;](assurance.md).
* Voeg de volgende Adobe Experience Cloud-toepassingen of -extensies toe:
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
>Een gelijkaardige multi-oplossingsleerprogramma is beschikbaar voor [&#x200B; SDK van het Web &#x200B;](../tutorial-web-sdk/overview.md).

## Machtigingen

In deze lessen wordt aangenomen dat u een Adobe-id en de vereiste gebruikersrechten hebt om de oefeningen te voltooien. Als dat niet het geval is, moet u contact opnemen met uw Adobe-beheerder om toegang aan te vragen.

* In de Inzameling van Gegevens, moet u:
   * **[!UICONTROL Platforms]**—machtigingsitem **[!UICONTROL Mobile]**
   * **[!UICONTROL Property Rights]** - wijs items toe aan **[!UICONTROL Develop]** , **[!UICONTROL Approve]** , **[!UICONTROL Publish]** , **[!UICONTROL Manage Extensions]** en **[!UICONTROL Manage Environments]** .
   * **[!UICONTROL Company Rights]**—Items toestaan aan **[!UICONTROL Manage Properties]**

     Voor meer informatie over markeringstoestemmingen, zie {de toestemmingen van 0} Gebruiker voor markeringen [&#x200B; in de productdocumentatie.](https://experienceleague.adobe.com/en/docs/experience-platform/tags/admin/user-permissions){target="_blank"}
* In Experience Platform moet u beschikken over:
   * **[!UICONTROL Data Modeling]** - machtigingsitems om schema&#39;s te beheren en weer te geven.
   * **[!UICONTROL Identity Management]** - machtigingsitems om naamruimten voor identiteiten te beheren en weer te geven.
   * **[!UICONTROL Data Collection]** - machtigingsitems om gegevensstromen te beheren en weer te geven.

   * Als u de klant bent van een op een platform gebaseerde toepassing zoals Real-Time CDP, Journey Optimizer of Customer Journey Analytics, en van plan bent om de verwante lessen te doen zou u ook moeten hebben:
      * **[!UICONTROL Data Management]** - toestemmingspunten om datasets te beheren en te bekijken.
      * Een ontwikkelings **zandbak** die u voor dit leerprogramma kunt gebruiken.

   * Voor de lessen van Journey Optimizer, hebt u toestemmingen nodig om de **duw- berichtdienst** te vormen en een **app oppervlakte**, a **reis**, a **bericht** te creëren, en **bericht stelt** vooraf in. Bovendien, voor Beslissingsbeheer, hebt u de juiste toestemmingen nodig om aanbiedingen **en** besluiten **te beheren, zoals die in** niveaus van de Toestemming [&#x200B; worden beschreven.](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/access-control/high-low-permissions)

* Voor Adobe Analytics, moet u weten welke **rapportreeksen** u kunt gebruiken om dit leerprogramma te voltooien.

* Voor Adobe Target moet u toestemming hebben om activiteiten te maken en activeren.


>[!NOTE]
>
>Als deel van dit leerprogramma, creeert u schema&#39;s, datasets, identiteiten, etc. Als meerdere personen deze zelfstudie in één sandbox doorlopen, kunt u bij het maken van deze objecten overwegen een identificatie toe te voegen of vooraf in te stellen als onderdeel van uw naamgevingsconventies. Voeg bijvoorbeeld ` - <your name or initials>` toe aan de naam van het object dat u moet maken.

## Versiehistorie

* 9 september 2025:
   * Android-versie van de app met bijbehorende instructies.
   * Updates voor wijzigingen in de functionaliteit van de toepassingsoppervlakte en de campagne in Journey Optimizer.
* 29 nov. 2023: ingrijpende revisie met nieuwe voorbeeldapp en nieuwe lessen voor in-app messaging, beslissingsbeheer en Adobe Target.
* 9 mrt. 2022: eerste publicatie

## De app Luma downloaden

>[!BEGINTABS]

>[!TAB  iOS ]

U kunt twee versies van de voorbeeldtoepassing downloaden. Beide versies kunnen van [&#x200B; GitHub &#x200B;](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) worden gedownload/worden gekloond. U vindt twee mappen:

1. [&#x200B; Begin &#x200B;](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}: een project zonder code of met placeholder code voor het grootste deel van de code van Experience Platform Mobile SDK u moet gebruiken om de hands-on oefeningen in dit leerprogramma te voltooien.
1. [&#x200B; Einde &#x200B;](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}: een versie met de volledige implementatie voor verwijzing.

U gebruikt iOS als platform, [!DNL Swift] als programmeertaal, [!DNL SwiftUI] als UI-framework en [!DNL Xcode] als de geïntegreerde ontwikkelomgeving (IDE). Veel van de beschreven implementatieconcepten zijn echter vergelijkbaar voor andere ontwikkelingsplatforms. Velen hebben deze zelfstudie al met succes voltooid met weinig tot geen eerdere ontwikkelervaring voor iOS en Swift(UI). U hoeft geen expert te zijn om de lessen te voltooien, maar u kunt meer uit de lessen halen als u de code comfortabel kunt lezen en begrijpen.

U kunt de definitieve versie van de app downloaden van de App Store.

[![&#x200B; Download &#x200B;](assets/download-app.svg) &#x200B;](https://apps.apple.com/us/app/luma-app/id6466588487)

>[!TAB  Android ]

U kunt twee versies van de voorbeeldtoepassing downloaden. Beide versies kunnen van [&#x200B; GitHub &#x200B;](https://github.com/adobe/Luma-Android) worden gedownload of worden gekloond. U vindt twee mappen:

1. [&#x200B; Begin &#x200B;](https://github.com/adobe/Luma-Android){target="_blank"}: een project zonder code of met placeholder code voor het grootste deel van de code van Experience Platform Mobile SDK u moet gebruiken om de hands-on oefeningen in dit leerprogramma te voltooien.
1. [&#x200B; Einde &#x200B;](https://github.com/adobe/Luma-Android){target="_blank"}: een versie met de volledige implementatie voor verwijzing.

U gebruikt Android als platform, [!DNL Kotlin] + [!DNL Java] als programmeertaal, [!DNL JetPack Compose] als kader UI en [!DNL Android Studio] als geïntegreerde ontwikkelomgeving (winde). Veel van de beschreven implementatieconcepten zijn echter vergelijkbaar voor andere ontwikkelingsplatforms. Velen hebben deze zelfstudie al voltooid met weinig tot geen ervaring in Android / Kotlin+Java / JetPack Compose. U hoeft geen expert te zijn om de lessen te voltooien, maar u kunt meer uit de lessen halen als u de code comfortabel kunt lezen en begrijpen.

Als u verkiest, kunt u [&#x200B; zich bij een test voor een geproduceerde versie &#x200B;](https://play.google.com/apps/internaltest/4700642199234438150) van app van Google Play aansluiten.


>[!ENDTABS]

Laten we beginnen!

>[!SUCCESS]
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene terugkoppelen willen delen, of suggesties over toekomstige inhoud hebben, hen op deze [&#x200B; Communautaire besprekingspost van Experience League &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) delen.

Volgende: **[creeer een schema XDM](create-schema.md)**
