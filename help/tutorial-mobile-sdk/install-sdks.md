---
title: Adobe Experience Platform Mobile SDK's installeren
description: Leer hoe u de Adobe Experience Platform Mobile SDK kunt implementeren in een mobiele app.
jira: KT-14627
exl-id: 98d6f59e-b8a3-4c63-ae7c-8aa11e948f59
source-git-commit: 463a5d54e99ddf6587fe19081c07025f7caf648e
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 0%

---

# Adobe Experience Platform Mobile SDK&#39;s installeren

>[!CONTEXTUALHELP]
>id="platform_mobile_sdk_tutorial_install"
>title="Adobe Experience Platform Mobile SDK&#39;s installeren"
>abstract="Leer hoe u de Adobe Experience Platform Mobile SDK kunt implementeren in een mobiele app."

Leer hoe u de Adobe Experience Platform Mobile SDK kunt implementeren in een mobiele app.

## Vereisten

* Opvolger bouwde met succes een markeringsbibliotheek met de uitbreidingen die in de [ vorige les ](configure-tags.md) worden beschreven.
* Identiteitskaart van het Dossier van het Milieu van de ontwikkeling van [ Mobiele Installatieinstructies ](configure-tags.md#generate-sdk-install-instructions).
* Gedownload lege [ steekproef app ](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) {target="_blank"}.
* Ervaring met [ Xcode ](https://developer.apple.com/xcode/) {target="_blank"}.

## Leerdoelstellingen

In deze les zult u:

* Voeg de vereiste SDKs aan uw project toe gebruikend de Swift Manager van het Pakket.
* Registreer de extensies.

>[!NOTE]
>
>In een mobiele app-implementatie zijn de termen &quot;extensies&quot; en &quot;SDK&#39;s&quot; bijna uitwisselbaar.

## Swift Package Manager

In plaats van het gebruiken van CocoaPods en een dossier van de Pod (zoals die in [ worden geschetst produceert SDK installeert instructies ](./configure-tags.md#generate-sdk-install-instructions)), voegt u individuele pakketten toe gebruikend de inheemse Manager van het Pakket van Xcode Swift. Het Xcode-project heeft al alle pakketafhankelijkheden die voor u zijn toegevoegd. Het scherm Xcode **[!UICONTROL Package Dependencies]** moet er als volgt uitzien:

![ Afhankelijkheden van het Pakket Xcode ](assets/xcode-package-dependencies.png){zoomable="yes"}


In Xcode kunt u **[!UICONTROL File]** > **[!UICONTROL Add Packages...]** gebruiken om pakketten toe te voegen. De onderstaande tabel bevat koppelingen naar de URL&#39;s die u zou gebruiken om pakketten toe te voegen. De koppelingen leiden u ook naar meer informatie over elk specifiek pakket.

| Pakket | Beschrijving |
|---|---|
| [ Kern AEP ](https://github.com/adobe/aepsdk-core-ios) | De extensies `AEPCore` , `AEPServices` en `AEPIdentity` vertegenwoordigen de basis van de Adobe Experience Platform SDK. Elke toepassing die de SDK gebruikt, moet deze bevatten. Deze modules bevatten een gemeenschappelijke reeks functionaliteit en de diensten die door alle uitbreidingen van SDK worden vereist.<br/><ul><li>`AEPCore` bevat implementatie van de gebeurtenishub. De hub van de Gebeurtenis is het mechanisme dat voor het leveren van gebeurtenissen tussen app en SDK wordt gebruikt. De hub van de Gebeurtenis wordt ook gebruikt voor het delen van gegevens tussen uitbreidingen.</li><li>`AEPServices` biedt verschillende herbruikbare implementaties die nodig zijn voor platformondersteuning, zoals netwerken, schijftoegang en databasebeheer.</li><li>`AEPIdentity` implementeert de integratie met Adobe Experience Platform Identity-services.</li><li>`AEPSignal` staat voor de Adobe Experience Platform SDK&#39;s Signal-extensie waarmee marketers een &quot;signaal&quot; naar hun apps kunnen sturen om gegevens naar externe doelen te verzenden of om URL&#39;s te openen.</li><li>`AEPLifecycle` vertegenwoordigt de Levenscyclusuitbreiding van SDK van Adobe Experience Platform die helpt metriek van de toepassingslevenscyclus zoals toepassingsinstallatie of verbeteringsinformatie, toepassingslancering en zittingsinformatie, apparateninformatie, en om het even welke extra contextgegevens te verzamelen die door de toepassingsontwikkelaar worden verstrekt.</li></ul> |
| [ AEP Edge ](https://github.com/adobe/aepsdk-edge-ios) | Met de mobiele extensie Adobe Experience Platform Edge Network (`AEPEdge` ) kunt u gegevens naar het Adobe Edge-netwerk verzenden vanuit een mobiele toepassing. Deze uitbreiding staat u toe om de mogelijkheden van Adobe Experience Cloud op een robuustere manier uit te voeren, veelvoudige oplossingen van de Adobe door middel van één netwerkvraag te dienen, en deze informatie gelijktijdig door te sturen aan Adobe Experience Platform.<br/> de mobiele uitbreiding van de Edge Network is een uitbreiding voor Adobe Experience Platform SDK en vereist `AEPCore` en `AEPServices` uitbreidingen voor gebeurtenis behandeling, evenals de `AEPEdgeIdentity` uitbreiding voor het terugwinnen van de identiteiten, zoals ECID. |
| [ AEP Edge Identity ](https://github.com/adobe/aepsdk-edgeidentity-ios) | Met de AEP Edge Identity Mobile-extensie (`AEPEdgeIdentity`) kunnen identiteitsgegevens van gebruikers van een mobiele toepassing worden verwerkt wanneer de Adobe Experience Platform SDK en de Edge Network-extensie worden gebruikt. |
| [ AEP Edge Toestemming ](https://github.com/adobe/aepsdk-edgeconsent-ios) | Met de mobiele extensie AEP Consent Collection Collection (`AEPConsent` ) kunt u toestemmingsvoorkeuren verzamelen vanuit de mobiele toepassing wanneer u de Adobe Experience Platform SDK en de extensie Edge Network gebruikt. |
| [ AEP het Profiel van de Gebruiker ](https://github.com/adobe/aepsdk-userprofile-ios) | De extensie Adobe Experience Platform User Profile Mobile (`AEPUserProfile`) is een extensie voor het beheren van gebruikersprofielen voor de Adobe Experience Platform SDK. |
| [ Plaatsen AEP ](https://github.com/adobe/aepsdk-places-ios) | De uitbreiding van Plaatsen AEP (`AEPPlaces`) staat u toe om geolocatiegebeurtenissen te volgen zoals die in de interface van Plaatsen van de Adobe en in de regels van de Markering van de Inzameling van Gegevens van de Adobe worden bepaald. |
| [ AEP Overseinen ](https://github.com/adobe/aepsdk-messaging-ios) | Met de extensie AEP Messaging (`AEPMessaging` ) kunt u tokens voor pushmeldingen verzenden en doorklikken op pushberichten naar de Adobe Experience Platform. |
| [ AEP optimaliseert ](https://github.com/adobe/aepsdk-optimize-ios) | De extensie AEP optimaliseren (`AEPOptimize`) biedt API&#39;s om realtime workflows voor personalisatie in de Adobe Experience Platform Mobile SDK&#39;s mogelijk te maken met Adobe Target of Adobe Journey Optimizer Offer decisioning. Voor deze functie zijn `AEPCore` - en `AEPEdge` -extensies nodig om verpersoonlijkingsquery-gebeurtenissen naar het Experience Edge-netwerk te verzenden. |
| [ AEP Assurance ](https://github.com/adobe/aepsdk-assurance-ios) | Assurance (alias project Griffon) is een nieuwe, vernieuwende extensie (`AEPAssurance`) waarmee u kunt controleren, testen, simuleren en valideren hoe u gegevens verzamelt of ervaringen aanbiedt in uw mobiele app. Met deze extensie wordt uw app voor Assurance ingeschakeld. |


## Extensies importeren

Navigeer in Xcode naar **[!DNL Luma]** > **[!DNL Luma]** > **[!UICONTROL AppDelegate]** en controleer of de volgende importbewerkingen deel uitmaken van dit bronbestand.

```swift
// import AEP MobileSDK libraries
import AEPCore
import AEPServices
import AEPIdentity
import AEPSignal
import AEPLifecycle
import AEPEdge
import AEPEdgeIdentity
import AEPEdgeConsent
import AEPUserProfile
import AEPPlaces
import AEPMessaging
import AEPOptimize
import AEPAssurance
```

Doe hetzelfde voor **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]** .

## AppDelegate bijwerken

Navigeer aan **[!DNL Luma]** > **[!DNL Luma]** > **AppDelegate** in de navigator van het Project van Xcode.

1. Vervang de `@AppStorage` waarde `YOUR_ENVIRONMENT_ID_GOES_HERE` voor `environmentFileId` aan de waarde van identiteitskaart van het Dossier van het Milieu van de Ontwikkelomgeving die u van markeringen in [ teruggewonnen produceert SDK installeert instructies ](configure-tags.md#generate-sdk-install-instructions).

   ```swift
   @AppStorage("environmentFileId") private var environmentFileId = "YOUR_ENVIRONMENT_ID_GOES_HERE"
   ```

1. Voeg de volgende code toe aan de functie `application(_, didFinishLaunchingWithOptions)` .

   ```swift
   // Define extensions
   let extensions = [
       AEPIdentity.Identity.self,
       Lifecycle.self,
       Signal.self,
       Edge.self,
       AEPEdgeIdentity.Identity.self,
       Consent.self,
       UserProfile.self,
       Places.self,
       Messaging.self,
       Optimize.self,
       Assurance.self
   ]
   
   // Register extensions
   MobileCore.registerExtensions(extensions, {
       // Use the environment file id assigned to this application via Adobe Experience Platform Data Collection
       Logger.aepMobileSDK.info("Luma - using mobile config: \(self.environmentFileId)")
       MobileCore.configureWith(appId: self.environmentFileId)
   
       // set this to false or comment it when deploying to TestFlight (default is false),
       // set this to true when testing on your device.
       MobileCore.updateConfigurationWith(configDict: ["messaging.useSandbox": true])
       if appState != .background {
           // only start lifecycle if the application is not in the background
           MobileCore.lifecycleStart(additionalContextData: nil)
       }
   
       // assume unknown, adapt to your needs.
       MobileCore.setPrivacyStatus(.unknown)
   })
   ```

De bovenstaande code doet het volgende:

1. Registreert de vereiste extensies.
1. Vormt MobileCore en andere uitbreidingen om uw configuratie van het markeringsbezit te gebruiken.
1. Schakelt foutopsporingslogbestand in. Meer details en de opties kunnen in de [ Mobiele documentatie van SDK van Adobe Experience Platform ](https://developer.adobe.com/client-sdks/documentation/getting-started/enable-debug-logging/) worden gevonden.
1. Start levenscycluscontrole. Zie [ Levenscyclus ](lifecycle-data.md) stap in het leerprogramma voor meer details.
1. Hiermee stelt u de standaardtoestemming in op onbekend. Zie ](consent.md) stap 0} van de Toestemming {in het leerprogramma voor meer details.[

>[!IMPORTANT]
>
>Zorg ervoor dat u `MobileCore.configureWith(appId: self.environmentFileId)` bijwerkt met de `appId` op basis van de `environmentFileId` -code uit de tagomgeving waarvoor u ontwikkelt (ontwikkelen, opvoeren of produceren).
>

>[!SUCCESS]
>
>U hebt nu de benodigde pakketten geïnstalleerd en uw project bijgewerkt om de vereiste Adobe Experience Platform Mobile SDK-extensies die u voor de rest van de zelfstudie gaat gebruiken, correct te registreren.
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene terugkoppelen willen delen, of suggesties over toekomstige inhoud hebben, hen op deze [ Communautaire besprekingspost van de Experience League ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) delen

Volgende: **[Opstelling Assurance](assurance.md)**
