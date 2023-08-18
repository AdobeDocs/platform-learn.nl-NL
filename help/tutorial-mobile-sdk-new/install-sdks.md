---
title: Adobe Experience Platform Mobile SDK's installeren
description: Leer hoe u de Adobe Experience Platform Mobile SDK in een mobiele app implementeert.
hide: true
hidefromtoc: true
source-git-commit: ca83bbb571dc10804adcac446e2dba4fda5a2f1d
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 0%

---

# Adobe Experience Platform Mobile SDK&#39;s installeren

Leer hoe u de Adobe Experience Platform Mobile SDK in een mobiele app implementeert.

## Vereisten

* Tagbibliotheek is gemaakt met de extensies die in het dialoogvenster [vorige les](configure-tags.md).
* Bestandsidentiteitskaart voor ontwikkelomgeving van de [Instructies voor mobiele installatie](configure-tags.md#generate-sdk-install-instructions).
* Gedownload, leeg [voorbeeldapp](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App{target="_blank"}).
* Ervaring met [XCode](https://developer.apple.com/xcode/{target="_blank"}).

## Leerdoelstellingen

In deze les zult u:

* Voeg de vereiste SDK&#39;s toe aan uw project met gebruik van Swift Package Manager.
* Registreer de extensies.

>[!NOTE]
>
>In een mobiele app-implementatie zijn de termen &quot;extensies&quot; en &quot;SDK&#39;s&quot; bijna uitwisselbaar.

## Swift Package Manager

In plaats van CocoaPods te gebruiken en een Poddossier te gebruiken (zoals die in de Mobiele Installatieinstructies worden geschetst, zie [SDK-installatie-instructies genereren](./configure-tags.md#generate-sdk-install-instructions)), voegt u afzonderlijke pakketten toe met gebruik van de native Swift Package Manager van Xcode.

In Xcode gebruiken **[!UICONTROL Bestand]** > **[!UICONTROL Pakketten toevoegen...]** en installeer alle pakketten die in de onderstaande tabel worden vermeld. Selecteer de koppeling van het pakket in de tabel om de volledige URL voor het specifieke pakket te verkrijgen.

| Pakket | Beschrijving |
|---|---|
| [AEP Core](https://github.com/adobe/aepsdk-core-ios.git) | De `AEPCore`, `AEPServices`, en `AEPIdentity` extensies vormen de basis voor de SDK van Adobe Experience Platform. Elke toepassing die de SDK gebruikt, moet deze bevatten. Deze modules bevatten een gemeenschappelijke reeks functionaliteit en diensten die door alle uitbreidingen van SDK worden vereist.<br/>`AEPCore` Bevat implementatie van de Hub van de Gebeurtenis. De hub van de Gebeurtenis is het mechanisme dat voor het leveren van gebeurtenissen tussen app en SDK wordt gebruikt. De hub van de Gebeurtenis wordt ook gebruikt voor het delen van gegevens tussen uitbreidingen.<br/>`AEPServices` verstrekt verscheidene herbruikbare implementaties nodig voor platformsteun, met inbegrip van voorzien van een netwerk, schijftoegang, en gegevensbestandbeheer.<br/>`AEPIdentity` implementeert de integratie met Adobe Experience Platform Identity-services.<br/>`AEPSignal` vertegenwoordigt de Signal-extensie van de Adobe Experience Platform SDK waarmee marketers een &quot;signaal&quot; naar hun apps kunnen sturen om gegevens naar externe doelen te verzenden of om URL&#39;s te openen.<br/>`AEPLifecycle` vertegenwoordigt de Levenscyclusuitbreiding van de SDK van Adobe Experience Platform die helpt metriek van de toepassingslevenscyclus zoals toepassingsinstallatie of verbeteringsinformatie, toepassingslancering en zittingsinformatie, apparateninformatie, en om het even welke extra contextgegevens te verzamelen die door de toepassingsontwikkelaar worden verstrekt. |
| [AEP rand](https://github.com/adobe/aepsdk-edge-ios.git) | Met de mobiele extensie Adobe Experience Platform Edge Network kunt u gegevens verzenden naar het Adobe Edge Network vanuit een mobiele toepassing. Deze uitbreiding staat u toe om de mogelijkheden van Adobe Experience Cloud op een robuustere manier uit te voeren, veelvoudige oplossingen van de Adobe door middel van één netwerkvraag te dienen, en deze informatie gelijktijdig door te sturen aan Adobe Experience Platform.<br/>De mobiele extensie van Edge Network is een extensie voor de Adobe Experience Platform SDK en vereist de opdracht `AEPCore` en `AEPServices` extensies voor gebeurtenisafhandeling en de `AEPEdgeIdentity` voor het ophalen van de identiteiten, zoals ECID. |
| [AEP Edge Identity](https://github.com/adobe/aepsdk-edgeidentity-ios.git) | Met de mobiele extensie AEP Edge Identity kunnen identiteitsgegevens van gebruikers van een mobiele toepassing worden verwerkt wanneer de SDK van Adobe Experience Platform en de extensie Edge Network worden gebruikt. |
| [AEP randgoedkeuring](https://github.com/adobe/aepsdk-edgeconsent-ios.git) | Met de mobiele extensie AEP Consent Collection Collection kunnen toestemmingsvoorkeuren worden verzameld vanuit de mobiele toepassing wanneer de SDK van Adobe Experience Platform en de Edge Network-extensie worden gebruikt. |
| [AEP-gebruikersprofiel](https://github.com/adobe/aepsdk-userprofile-ios.git) | De extensie Adobe Experience Platform-gebruikersprofiel voor mobiele apparaten is een extensie voor het beheren van gebruikersprofielen voor de Adobe Experience Platform-SDK. |
| [AEP-plaatsen](https://github.com/adobe/aepsdk-places-ios) | Adobe Experience Platform Places-extensie is een extensie voor de Adobe Experience Platform Swift SDK. Met de extensie AEPPlaces kunt u gebeurtenissen voor geolocatie bijhouden zoals gedefinieerd in de gebruikersinterface van Plaatsen van Adobe en in de regels voor het starten van Adoben. |
| [AEP-berichten](https://github.com/adobe/aepsdk-messaging-ios.git) | De extensie AEP Messaging is een extensie voor de Adobe Experience Platform Swift SDK. Met de AEP Messaging-extensie kunt u tokens voor pushmeldingen verzenden en doorklikken op pushberichten doorsturen naar de Adobe Experience Platform. |
| [AEP optimaliseren](https://github.com/adobe/aepsdk-optimize-ios) | De extensie AEP optimaliseren biedt API&#39;s om realtime workflows voor personalisatie in de Adobe Experience Platform Mobile SDK&#39;s mogelijk te maken met Adobe Target of Adobe Journey Optimizer Offer decisioning. Hiervoor is `AEPCore` en `AEPEdge` extensies om verpersoonlijkingsquerygebeurtenissen naar het Edge-netwerk van Experience te verzenden. |
| [AEP-betrouwbaarheid](https://github.com/adobe/aepsdk-assurance-ios.git) | Betrouwbaarheid (alias project Griffon) is een nieuw, vernieuwend product waarmee u kunt controleren, testen, simuleren en valideren hoe u gegevens verzamelt of ervaringen opdoet in uw mobiele app. |


Nadat u alle pakketten hebt geïnstalleerd, voert u uw Xcode **[!UICONTROL Pakketafhankelijke onderdelen]** scherm moet er als volgt uitzien:

![Xcode-pakketafhankelijke](assets/xcode-package-dependencies.png)


## Extensies importeren

In Xcode in de bron voor **[!UICONTROL AppDelegate]** en **[!UICONTROL MobileSDK]**, voegt u de volgende importbewerkingen toe.

```swift
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

## AppDelegate bijwerken

In **AppDelegate**,

1. Stel de `@AppStorage` waarde voor `environmentFileId` naar de waarde voor het bestand-id van de ontwikkelomgeving die u hebt opgehaald van de tags in stap 6 van [SDK-installatie-instructies genereren](configure-tags.md#generate-sdk-install-instructions).

   ```swift
   @AppStorage("environmentFileId") private var environmentFileId = "b5cbd1a1220e/1857ef6cacb5/launch-2594f26b23cd-development"
   ```

1. Voeg de volgende gemarkeerde code toe aan de `application(_, didFinishLaunchingWithOptions)` functie.

   ```swift {highlight="10-39"}
   func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
   
       UNUserNotificationCenter.current().delegate = self
   
       // step-init-start
       MobileCore.setLogLevel(.trace)
       let appState = application.applicationState;
   
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
   
           // update version and build
           Logger.configuration.info("Luma - Updating version and build number...")
           SettingsBundleHelper.setVersionAndBuildNumber()
       })
   
       // register push notification
       registerForPushNotifications(application: application)
   
       // set up core location
       let locationManager = LocationManager()
       locationManager.requestAuthorisation()
   
       return true
   }
   ```

De bovenstaande code doet het volgende:

1. Registreert de vereiste extensies.
1. Vormt MobileCore en andere uitbreidingen om uw configuratie van het markeringsbezit te gebruiken.
1. Schakelt foutopsporingslogbestand in. Meer details en opties vindt u in het gedeelte [Adobe Experience Platform Mobile SDK-documentatie](https://developer.adobe.com/client-sdks/documentation/getting-started/enable-debug-logging/).

>[!IMPORTANT]
>
>Zorg ervoor dat u bijwerkt `MobileCore.configureWith(appId: self.environmentFileId)` met de `appId` op basis van de `environmentFileId` vanuit de tagomgeving waarvoor u ontwikkelt (ontwikkelen, opvoeren of produceren).
>

>[!SUCCESS]
>
>U hebt nu de benodigde pakketten geïnstalleerd en uw project bijgewerkt om de vereiste Adobe Experience Platform Mobile SDK-extensies die u voor de rest van de zelfstudie gaat gebruiken, correct te registreren.<br/>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Volgende: **[Betrouwbaarheid instellen](assurance.md)**
