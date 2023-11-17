---
title: Adobe Experience Platform Mobile SDK's installeren
description: Leer hoe u de Adobe Experience Platform Mobile SDK in een mobiele app implementeert.
hide: true
exl-id: 86348d8b-f428-465d-a79e-ce73d140da79
source-git-commit: f592fc61ad28d04eba3c1c21a0a66bda6e816a5b
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 0%

---

# Adobe Experience Platform Mobile SDK&#39;s installeren

Leer hoe u de Adobe Experience Platform Mobile SDK in een mobiele app implementeert.

## Vereisten

* Er is een tagbibliotheek gemaakt met de extensies die in het dialoogvenster [vorige les](configure-tags.md).
* Bestandsidentiteitskaart voor ontwikkelomgeving van de [Instructies voor mobiele installatie](configure-tags.md#generate-sdk-install-instructions).
* Lege bestanden gedownload [voorbeeldapp](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target="_blank"}.
* Ervaring met [Xcode](https://developer.apple.com/xcode/){target="_blank"}.

## Leerdoelstellingen

In deze les zult u:

* Voeg de vereiste SDKs aan uw project toe gebruikend de Swift Manager van het Pakket.
* Registreer de extensies.

>[!NOTE]
>
>In een mobiele app-implementatie zijn de termen &quot;extensies&quot; en &quot;SDK&#39;s&quot; bijna uitwisselbaar.

## Swift Package Manager

In plaats van CocoaPods te gebruiken en een Poddossier te gebruiken (zoals die in de Mobiele Installatieinstructies worden geschetst, zie [SDK-installatie-instructies genereren](./configure-tags.md#generate-sdk-install-instructions)), voegt u afzonderlijke pakketten toe met gebruik van de native Swift Package Manager van Xcode. Het Xcode-project heeft al alle pakketafhankelijkheden die voor u zijn toegevoegd. De Xcode **[!UICONTROL Pakketafhankelijke onderdelen]** scherm moet er als volgt uitzien:

![Xcode-pakketafhankelijke](assets/xcode-package-dependencies.png){zoomable=&quot;yes&quot;}


In Xcode kunt u **[!UICONTROL Bestand]** > **[!UICONTROL Pakketten toevoegen...]** pakketten toevoegen. De onderstaande tabel bevat koppelingen naar de URL&#39;s die u zou gebruiken om pakketten toe te voegen. De koppelingen leiden u ook naar meer informatie over elk specifiek pakket.

| Pakket | Beschrijving |
|---|---|
| [AEP Core](https://github.com/adobe/aepsdk-core-ios.git) | De `AEPCore`, `AEPServices`, en `AEPIdentity` extensies vormen de basis voor de SDK van Adobe Experience Platform. Elke toepassing die de SDK gebruikt, moet deze bevatten. Deze modules bevatten een gemeenschappelijke reeks functionaliteit en diensten die door alle uitbreidingen van SDK worden vereist.<br/><ul><li>`AEPCore` Bevat implementatie van de Hub van de Gebeurtenis. De hub van de Gebeurtenis is het mechanisme dat voor het leveren van gebeurtenissen tussen app en SDK wordt gebruikt. De hub van de Gebeurtenis wordt ook gebruikt voor het delen van gegevens tussen uitbreidingen.</li><li>`AEPServices` verstrekt verscheidene herbruikbare implementaties nodig voor platformsteun, met inbegrip van voorzien van een netwerk, schijftoegang, en gegevensbestandbeheer.</li><li>`AEPIdentity` implementeert de integratie met Adobe Experience Platform Identity-services.</li><li>`AEPSignal` vertegenwoordigt de Adobe Experience Platform SDKs Signal extension die marketers toestaat een &quot;signaal&quot;naar hun apps te verzenden om gegevens naar externe bestemmingen te verzenden of URLs te openen.</li><li>`AEPLifecycle` vertegenwoordigt de Levenscyclusuitbreiding van SDKs van Adobe Experience Platform die helpt metriek van de toepassingslevenscyclus zoals toepassingsinstallatie of verbeteringsinformatie, toepassingslancering en zittingsinformatie, apparateninformatie, en om het even welke extra die contextgegevens verzamelen door de toepassingsontwikkelaar worden verstrekt.</li></ul> |
| [AEP rand](https://github.com/adobe/aepsdk-edge-ios.git) | De mobiele extensie Adobe Experience Platform Edge Network (`AEPEdge`) kunt u gegevens naar het Adobe Edge-netwerk verzenden vanuit een mobiele toepassing. Deze uitbreiding staat u toe om de mogelijkheden van Adobe Experience Cloud op een robuustere manier uit te voeren, veelvoudige oplossingen van de Adobe door middel van één netwerkvraag te dienen, en deze informatie gelijktijdig door te sturen aan Adobe Experience Platform.<br/>De mobiele extensie van Edge Network is een extensie voor de Adobe Experience Platform SDK en vereist de opdracht `AEPCore` en `AEPServices` extensies voor gebeurtenisafhandeling en de `AEPEdgeIdentity` voor het ophalen van de identiteiten, zoals ECID. |
| [AEP Edge Identity](https://github.com/adobe/aepsdk-edgeidentity-ios.git) | De mobiele extensie AEP Edge Identity (`AEPEdgeIdentity`) maakt het mogelijk om identiteitsgegevens van gebruikers van een mobiele toepassing af te handelen wanneer de SDK van Adobe Experience Platform en de extensie Edge Network worden gebruikt. |
| [AEP randgoedkeuring](https://github.com/adobe/aepsdk-edgeconsent-ios.git) | De mobiele extensie AEP Consent Collection (`AEPConsent`) schakelt de verzameling met voorkeuren voor toestemming van de mobiele toepassing in als u de SDK van Adobe Experience Platform en de extensie Edge Network gebruikt. |
| [AEP-gebruikersprofiel](https://github.com/adobe/aepsdk-userprofile-ios.git) | De extensie Adobe Experience Platform-gebruikersprofiel (`AEPUserProfile`) is een extensie voor het beheren van gebruikersprofielen voor de Adobe Experience Platform SDK. |
| [AEP-plaatsen](https://github.com/adobe/aepsdk-places-ios) | De extensie AEP-plaatsen (`AEPPlaces`) kunt u geolocatiegebeurtenissen bijhouden zoals gedefinieerd in de interface Plaatsen van Adoben en in de regels voor de tag voor gegevensverzameling van Adoben. |
| [AEP-berichten](https://github.com/adobe/aepsdk-messaging-ios.git) | De extensie AEP-berichten (`AEPMessaging`) kunt u tokens voor pushmeldingen en doorklikfeedback voor pushmeldingen naar de Adobe Experience Platform sturen. |
| [AEP optimaliseren](https://github.com/adobe/aepsdk-optimize-ios) | De extensie AEP optimaliseren (`AEPOptimize`) bevat API&#39;s waarmee u realtime workflows voor personalisatie kunt inschakelen in de Adobe Experience Platform Mobile SDK&#39;s met Adobe Target of Adobe Journey Optimizer Offer decisioning. Hiervoor is `AEPCore` en `AEPEdge` extensies om verpersoonlijkingsquerygebeurtenissen naar het Edge-netwerk van Experience te verzenden. |
| [AEP-betrouwbaarheid](https://github.com/adobe/aepsdk-assurance-ios.git) | Betrouwbaarheid (alias Griffon-project) is een nieuwe, innovatieve uitbreiding (`AEPAssurance`) om u te helpen bij het inspecteren, testen, simuleren en valideren van de manier waarop u gegevens verzamelt of ervaringen opdoet in uw mobiele app. Met deze extensie wordt uw app voor betrouwbaarheidsverklaring ingeschakeld. |


## Extensies importeren

Navigeer in Xcode naar **[!DNL Luma]** > **[!DNL Luma]** > **[!UICONTROL AppDelegate]** en zorg ervoor dat de volgende importbewerkingen deel uitmaken van dit bronbestand.

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

Doe het zelfde voor **[!DNL Luma]** > **[!DNL Luma]** > **[!DNL Utils]** > **[!UICONTROL MobileSDK]**.

## AppDelegate bijwerken

Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **AppDelegate** in de Xcode-projectnavigator.

1. Vervang de `@AppStorage` value `YOUR_ENVIRONMENT_ID_GOES_HERE` for `environmentFileId` naar de waarde voor het bestand-id van de ontwikkelomgeving die u hebt opgehaald van de tags in stap 6 van [SDK-installatie-instructies genereren](configure-tags.md#generate-sdk-install-instructions).

   ```swift
   @AppStorage("environmentFileId") private var environmentFileId = "YOUR_ENVIRONMENT_ID_GOES_HERE"
   ```

1. Voeg de volgende code toe aan de `application(_, didFinishLaunchingWithOptions)` functie.

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
1. Schakelt foutopsporingslogbestand in. Meer details en opties vindt u in het gedeelte [Adobe Experience Platform Mobile SDK-documentatie](https://developer.adobe.com/client-sdks/documentation/getting-started/enable-debug-logging/).
1. Start levenscycluscontrole. Zie [Levenscyclus](lifecycle-data.md) voor meer informatie.
1. Hiermee stelt u de standaardtoestemming in op onbekend. Zie [Toestemming](consent.md) voor meer informatie.

>[!IMPORTANT]
>
>Zorg ervoor dat u bijwerkt `MobileCore.configureWith(appId: self.environmentFileId)` met de `appId` op basis van de `environmentFileId` vanuit de tagomgeving waarvoor u ontwikkelt (ontwikkelen, opvoeren of produceren).
>

>[!SUCCESS]
>
>U hebt nu de benodigde pakketten geïnstalleerd en uw project bijgewerkt om de vereiste Adobe Experience Platform Mobile SDK-extensies die u voor de rest van de zelfstudie gaat gebruiken, correct te registreren.<br/>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Volgende: **[Betrouwbaarheid instellen](assurance.md)**
