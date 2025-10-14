---
title: Adobe Experience Platform Mobile SDK's installeren
description: Leer hoe u de Adobe Experience Platform Mobile SDK kunt implementeren in een mobiele app.
jira: KT-14627
exl-id: 98d6f59e-b8a3-4c63-ae7c-8aa11e948f59
source-git-commit: 008d3ee066861ea9101fe9fe99ccd0a088b63f23
workflow-type: tm+mt
source-wordcount: '1733'
ht-degree: 0%

---

# Adobe Experience Platform Mobile SDK&#39;s installeren {#tutorial_install_mobile_sdks}

>[!CONTEXTUALHELP]
>
>id="platform_mobile_sdk_tutorial_install"
>title="Adobe Experience Platform Mobile SDK&#39;s installeren"
>abstract="Leer hoe u de Adobe Experience Platform Mobile SDK kunt implementeren in een mobiele app."

Leer hoe u de Adobe Experience Platform Mobile SDK kunt implementeren in een mobiele app.

## Vereisten

* Opvolger bouwde met succes een markeringsbibliotheek met de uitbreidingen die in de [&#x200B; vorige les &#x200B;](configure-tags.md) worden beschreven.
* Identiteitskaart van het Dossier van het Milieu van de ontwikkeling van [&#x200B; Mobiele Installatieinstructies &#x200B;](configure-tags.md#generate-sdk-install-instructions).
* Gedownload [&#x200B; steekproef app voor iOS &#x200B;](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App) of [&#x200B; steekproef app voor Android &#x200B;](https://github.com/adobe/Luma-Android).
* Ervaring met [&#x200B; Xcode &#x200B;](https://developer.apple.com/xcode/) (iOS) of [&#x200B; de Studio van Android &#x200B;](https://developer.android.com/studio/intro?utm_source=android-studio) (Android)

## Leerdoelstellingen

In deze les zult u:

* Voeg de vereiste SDK&#39;s toe aan uw project.
* Registreer de extensies.

>[!NOTE]
>
>In een mobiele app implementatie, zijn de termijnen *uitbreidingen* en *SDKs* bijna onderling verwisselbaar.

>[!BEGINTABS]

>[!TAB  iOS ]

## Swift Package Manager

In plaats van het gebruiken van CocoaPods en een dossier van de Pod (zoals die in [&#x200B; worden geschetst produceert SDK installeert instructies &#x200B;](./configure-tags.md#generate-sdk-install-instructions)), voegt u individuele pakketten toe gebruikend de inheemse Manager van het Pakket van Xcode Swift. Het Xcode-project heeft al alle pakketafhankelijkheden die voor u zijn toegevoegd. Het scherm Xcode **[!UICONTROL Package Dependencies]** moet er als volgt uitzien:

![&#x200B; Afhankelijkheden van het Pakket Xcode &#x200B;](assets/xcode-package-dependencies.png){zoomable="yes"}


In Xcode kunt u **[!UICONTROL File]** > **[!UICONTROL Add Packages...]** gebruiken om pakketten toe te voegen. De onderstaande tabel bevat koppelingen naar de URL&#39;s die u zou gebruiken om pakketten toe te voegen. De koppelingen leiden u ook naar meer informatie over elk specifiek pakket.

| Pakket | Beschrijving |
|---|---|
| [&#x200B; de Kern van AEP &#x200B;](https://github.com/adobe/aepsdk-core-ios) | De extensies `AEPCore` , `AEPServices` en `AEPIdentity` vertegenwoordigen de basis van de Adobe Experience Platform SDK. Elke toepassing die de SDK gebruikt, moet deze bevatten. Deze modules bevatten een gemeenschappelijke reeks functionaliteit en de diensten die alle uitbreidingen van SDK vereisen.<br/><ul><li>`AEPCore` bevat implementatie van de gebeurtenishub. De hub van de Gebeurtenis is het mechanisme dat voor het leveren van gebeurtenissen tussen app en SDK wordt gebruikt. De hub van de Gebeurtenis wordt ook gebruikt voor het delen van gegevens tussen uitbreidingen.</li><li>`AEPServices` biedt verschillende herbruikbare implementaties die nodig zijn voor platformondersteuning, zoals netwerken, schijftoegang en databasebeheer.</li><li>`AEPIdentity` implementeert de integratie met Adobe Experience Platform Identity-services.</li><li>`AEPSignal` staat voor de Adobe Experience Platform SDK&#39;s Signal-extensie waarmee marketers een &quot;signaal&quot; naar hun apps kunnen sturen om gegevens naar externe doelen te verzenden of om URL&#39;s te openen.</li><li>`AEPLifecycle` vertegenwoordigt de Levenscyclusuitbreiding van SDK van Adobe Experience Platform die helpt metriek van de toepassingslevenscyclus zoals toepassingsinstallatie of verbeteringsinformatie, toepassingslancering en zittingsinformatie, apparateninformatie, en om het even welke extra contextgegevens te verzamelen die door de toepassingsontwikkelaar worden verstrekt.</li></ul> |
| [&#x200B; AEP Edge &#x200B;](https://github.com/adobe/aepsdk-edge-ios) | Met de mobiele extensie Adobe Experience Platform Edge Network (`AEPEdge` ) kunt u gegevens verzenden naar Adobe Edge Network vanuit een mobiele toepassing. Met deze extensie kunt u Adobe Experience Cloud-mogelijkheden op een robuustere manier implementeren, meerdere Adobe-oplossingen aanbieden via één netwerkaanroep en deze informatie tegelijkertijd doorsturen naar de Adobe Experience Platform.<br/> de mobiele uitbreiding van Edge Network is een uitbreiding voor Adobe Experience Platform SDK. De extensie vereist de extensie `AEPCore` en `AEPServices` voor gebeurtenisafhandeling en de extensie `AEPEdgeIdentity` voor het ophalen van de identiteiten, zoals ECID. |
| [&#x200B; Edge Identiteit van AEP &#x200B;](https://github.com/adobe/aepsdk-edgeidentity-ios) | Met de Adobe Experience Platform Edge Identity Mobile-extensie (`AEPEdgeIdentity`) kunnen identiteitsgegevens van gebruikers van een mobiele toepassing worden verwerkt wanneer de Adobe Experience Platform SDK en de Edge Network-extensie worden gebruikt. |
| [&#x200B; AEP Edge Toestemming &#x200B;](https://github.com/adobe/aepsdk-edgeconsent-ios) | Met de mobiele extensie Adobe Experience Platform Consent Collection Collection (`AEPConsent` ) kunt u de verzameling met voorkeuren voor toestemming van de mobiele toepassing inschakelen wanneer u de Adobe Experience Platform SDK en de Edge Network-extensie gebruikt. |
| [&#x200B; het Profiel van de Gebruiker van AEP &#x200B;](https://github.com/adobe/aepsdk-userprofile-ios) | De extensie Adobe Experience Platform User Profile Mobile (`AEPUserProfile`) is een extensie voor het beheren van gebruikersprofielen voor de Adobe Experience Platform SDK. |
| [&#x200B; Plaatsen van AEP &#x200B;](https://github.com/adobe/aepsdk-places-ios) | Met de extensie Adobe Experience Platform Places ( `AEPPlaces` ) kunt u gebeurtenissen voor geolocatie bijhouden zoals gedefinieerd in de interface Adobe Places en in de regels van de Adobe-tag voor gegevensverzameling. |
| [&#x200B; het Overseinen van AEP &#x200B;](https://github.com/adobe/aepsdk-messaging-ios) | Met de Adobe Experience Platform Messaging-extensie (`AEPMessaging`) kunt u tokens voor pushberichten en doorklikbewerkingen voor pushmeldingen verzenden naar de Adobe Experience Platform. |
| [&#x200B; AEP optimaliseren &#x200B;](https://github.com/adobe/aepsdk-optimize-ios) | De Adobe Experience Platform Optimize-extensie (`AEPOptimize`) biedt API&#39;s waarmee u realtime workflows voor personalisatie kunt inschakelen in de Adobe Experience Platform Mobile SDK&#39;s met Adobe Target of Adobe Journey Optimizer Offer Decisioning. Hiervoor zijn `AEPCore` - en `AEPEdge` -extensies nodig om verpersoonlijkingsquery-gebeurtenissen naar Experience Edge Network te verzenden. |
| [&#x200B; AEP Assurance &#x200B;](https://github.com/adobe/aepsdk-assurance-ios) | Adobe Experience Platform Assurance is een product van Adobe Experience Cloud dat u helpt bij het inspecteren, testen, simuleren en valideren van de manier waarop u gegevens verzamelt of ervaringen opdoet in uw mobiele app. |


## Extensies importeren

Open het project in Xcode in de map **[!UICONTROL Start]** van de voorbeeld-app.

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

1. Vervang de `@AppStorage` waarde `YOUR_ENVIRONMENT_ID_GOES_HERE` voor `environmentFileId` met de waarde van identiteitskaart van het Dossier van het Milieu die u van markeringen in [&#x200B; teruggewonnen produceert SDK installeert instructies &#x200B;](configure-tags.md#generate-sdk-install-instructions).

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
1. Schakelt foutopsporingslogbestand in. Meer details en de opties kunnen in de [&#x200B; Mobiele documentatie van SDK van Adobe Experience Platform &#x200B;](https://developer.adobe.com/client-sdks/documentation/getting-started/enable-debug-logging/) worden gevonden.
1. Start levenscycluscontrole. Zie [&#x200B; Levenscyclus &#x200B;](lifecycle-data.md) stap in het leerprogramma voor meer details.
1. Hiermee stelt u de standaardtoestemming in op onbekend. Zie [&#x200B; stap 0&rbrace; van de Toestemming &lbrace;in het leerprogramma voor meer details.](consent.md)

Zorg ervoor dat u `MobileCore.configureWith(appId: self.environmentFileId)` bijwerkt met de `appId` op basis van de `environmentFileId` -code uit de tagomgeving waarvoor u ontwikkelt (ontwikkelen, opvoeren of produceren).

>[!TAB  Android ]

## Gradient

U gebruikt de gebiedsdelen van [&#x200B; produceren SDK installeert instructies &#x200B;](./configure-tags.md#generate-sdk-install-instructions) om individuele pakketten toe te voegen gebruikend de integratie van de Gradle met Android Studio, heeft het project van Android Studio reeds alle pakketgebiedsdelen die voor u worden toegevoegd.

1. Selecteer ![&#x200B; FolderOutline &#x200B;](/help/assets/icons/FolderOutline.svg) als hulpmiddel.
1. Selecteer **[!UICONTROL Android]** weergave.
1. Selecteer **[!UICONTROL Gradle scripts]** > **[!UICONTROL build.gradle.kts (Module :app)]** van de linkerruit. Schuif vervolgens in het rechterdeelvenster totdat u `dependencies` ziet.

   ![&#x200B; Android de Afhankelijkheden van de Gradle &#x200B;](assets/androidstudio-package-dependencies.png){zoomable="yes"}

In Android Studio kunt u **[!UICONTROL File]** > **[!UICONTROL Project Structure...]** gebruiken om moduleafhankelijkheden toe te voegen. Selecteer **[!UICONTROL Dependencies]** en gebruik dan **[!UICONTROL Modules]** ![&#x200B; toevoegen &#x200B;](/help/assets/icons/Add.svg) om modules toe te voegen. De onderstaande tabel bevat koppelingen naar de URL&#39;s die u zou gebruiken om afhankelijkheidsmodules toe te voegen. De verbindingen leiden u ook aan meer informatie over elke specifieke module.

| Pakket <br/> com.adobe.<br/> marketing.mobile: | Beschrijving |
|---|---|
| [&#x200B; kern &#x200B;](https://github.com/adobe/aepsdk-core-android) | De extensies `MobileCore` en `Identity` vertegenwoordigen de basis van de Adobe Experience Platform SDK. Elke toepassing die de SDK gebruikt, moet deze opnemen. Deze modules bevatten een algemene set functies en services die alle SDK-extensies nodig hebben.<ul><li>`MobileCore` bevat de implementatie van de gebeurtenishub. De hub van de Gebeurtenis is het mechanisme dat voor het leveren van gebeurtenissen tussen app en SDK wordt gebruikt. De hub van de Gebeurtenis wordt ook gebruikt voor het delen van gegevens tussen uitbreidingen en verstrekt verscheidene herbruikbare implementaties nodig voor platformsteun, met inbegrip van voorzien van een netwerk, schijftoegang, en gegevensbestandbeheer.</li><li>`Identity` implementeert de integratie met Adobe Experience Platform Identity-services.</li><li>`Signal` staat voor de Adobe Experience Platform SDK Signal-extensie waarmee marketers een &quot;signaal&quot; naar hun apps kunnen sturen om gegevens naar externe bestemmingen te verzenden of URL&#39;s te openen.</li><li>`Lifecycle` vertegenwoordigt de Adobe Experience Platform SDK Lifecycle-extensie die helpt bij het verzamelen van gegevens over de levenscyclus van toepassingen, zoals installatie- of upgrademaatgegevens van toepassingen, het starten en de sessie van toepassingen, apparaatgegevens en eventuele aanvullende contextgegevens die door de ontwikkelaar van de toepassing worden verstrekt.</li></ul> |
| [&#x200B; rand &#x200B;](https://github.com/adobe/aepsdk-edge-android) | Met de mobiele extensie Adobe Experience Platform Edge Network (`AEPEdge` ) kunt u gegevens verzenden naar Adobe Edge Network vanuit een mobiele toepassing. Met deze extensie kunt u Adobe Experience Cloud-mogelijkheden op een robuustere manier implementeren, meerdere Adobe-oplossingen aanbieden via één netwerkaanroep en deze informatie tegelijkertijd doorsturen naar de Adobe Experience Platform.<br/> de mobiele uitbreiding van Edge Network is een uitbreiding voor Adobe Experience Platform SDK. De extensie vereist de extensies `Mobile Core` en `Services` voor gebeurtenisafhandeling. En de extensie `Identity for Edge Network` voor het ophalen van de identiteiten, zoals ECID. |
| [&#x200B; edgeidentity &#x200B;](https://github.com/adobe/aepsdk-edgeidentity-android) | Met de Adobe Experience Platform Edge Identity Mobile-extensie kunt u identiteitsgegevens van gebruikers van een mobiele toepassing verwerken wanneer u de Adobe Experience Platform SDK- en Edge Network-extensie gebruikt. |
| [&#x200B; edgepermission &#x200B;](https://github.com/adobe/aepsdk-edgeconsent-android) | Met de mobiele extensie Adobe Experience Platform Consent Collection Collection kunt u de verzameling voorkeuren voor toestemming van de mobiele toepassing inschakelen wanneer u de Adobe Experience Platform SDK en de Edge Network-extensie gebruikt. |
| [&#x200B; gebruikersprofiel &#x200B;](https://github.com/adobe/aepsdk-userprofile-android) | De extensie Adobe Experience Platform-gebruikersprofiel Mobile is een extensie voor het beheren van gebruikersprofielen voor de Adobe Experience Platform SDK. |
| [&#x200B; ruimten &#x200B;](https://github.com/adobe/aepsdk-places-android) | Adobe Places Service is een geo-locatieservice waarmee mobiele apps met een herkenbare locatie kunnen werken. En om de locatiecontext te begrijpen door rijke en makkelijk te gebruiken interfaces van SDK vergezeld van een flexibele gegevensbank van belangenpunten (POIs) te gebruiken. Voor meer informatie, zie de Documentatie van de Dienst van Plaatsen.<br/> deze dienst is de mobiele uitbreiding van Plaatsen voor Android 2.x Adobe Experience Platform SDK en vereist de uitbreiding van de Kern voor gebeurtenis behandeling. |
| [&#x200B; overseinen &#x200B;](https://github.com/adobe/aepsdk-messaging-android) | Met de Adobe Experience Platform Messaging-extensie kunt u pushberichten, in-app berichten en op code gebaseerde ervaringen voor uw mobiele apps inschakelen. Met deze extensie kunt u ook push-tokens van gebruikers verzamelen en interactiemetingen beheren met Adobe Experience Platform-services. |
| [&#x200B; optimaliseren &#x200B;](https://github.com/adobe/aepsdk-optimize-android) | De extensie Adobe Experience Platform Optimize biedt API&#39;s waarmee u realtime workflows voor personalisatie kunt inschakelen in de SDK&#39;s van Adobe Experience Platform met Adobe Target of Adobe Journey Optimizer Offer Decisioning. Het hangt van de Mobiele Kern af en vereist de Uitbreiding van Edge om verpersoonlijkingsvraaggebeurtenissen naar de Ervaring Edge Network te verzenden. |
| [&#x200B; verzekering &#x200B;](https://github.com/adobe/aepsdk-assurance-android) | Assurance (alias Griffon-project) is een mobiele extensie voor Adobe Experience Platform die integratie met Adobe Experience Platform Assurance mogelijk maakt. Met de extensie kunt u controleren, testen, simuleren en valideren hoe u gegevens verzamelt of ervaringen opdoet in uw mobiele app. Voor deze extensie is MobileCore vereist. |

## Extensies importeren

Navigeer in Android Studio naar **[!UICONTROL app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL LumaApplication]** en controleer of de volgende importbewerkingen deel uitmaken van het bronbestand.

```kotlin
import com.adobe.marketing.mobile.Assurance
import com.adobe.marketing.mobile.Edge
import com.adobe.marketing.mobile.Lifecycle
import com.adobe.marketing.mobile.LoggingMode
import com.adobe.marketing.mobile.Messaging
import com.adobe.marketing.mobile.MobileCore
import com.adobe.marketing.mobile.MobilePrivacyStatus
import com.adobe.marketing.mobile.Places
import com.adobe.marketing.mobile.Signal
import com.adobe.marketing.mobile.UserProfile
import com.adobe.marketing.mobile.edge.consent.Consent
import com.adobe.marketing.mobile.edge.identity.Identity
import com.adobe.marketing.mobile.optimize.Optimize
```

Doe hetzelfde voor **[!UICONTROL app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL models]** > **[!UICONTROL MobileSDK]** .


## LumaApplication bijwerken

Navigeer in de **[!UICONTROL Android]** -weergave naar **[!UICONTROL app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL LumaApplication]** in Android Studio.

1. Vervang `"YOUR_ENVIRONMENT_FILE_ID"` in `private var environmentFileId = "YOUR_ENVIRONMENT_ID_GOES_HERE"` met de waarde van identiteitskaart van het Dossier van het Milieu die u van markeringen in [&#x200B; teruggewonnen produceert SDK installeert instructies &#x200B;](configure-tags.md#generate-sdk-install-instructions).

   ```kotlin
   private var environmentFileId = "YOUR_ENVIRONMENT_ID_GOES_HERE"
   ```

1. Voeg de volgende code toe aan de functie `override fun onCreate()` in `class LumaApplication : Application()` .

   ```kotlin
   // Define extensions
   val extensions = listOf(
      Identity.EXTENSION,
      Lifecycle.EXTENSION,
      Signal.EXTENSION,
      Edge.EXTENSION,
      Consent.EXTENSION,
      UserProfile.EXTENSION,
      Places.EXTENSION,
      Messaging.EXTENSION,
      Optimize.EXTENSION,
      Assurance.EXTENSION
   )
   
   // Register extensions
   MobileCore.registerExtensions(extensions) {
   // Use the environment file id assigned to this application via Adobe Experience Platform Data Collection
     Log.i("Luma", "Using mobile config: $environmentFileId")
     MobileCore.configureWithAppID(environmentFileId)
   
     // set this to true when testing on your device, default is false.
     //MobileCore.updateConfiguration(mapOf("messaging.useSandbox" to true))
   
     // assume unknown, adapt to your needs.
     MobileCore.setPrivacyStatus(MobilePrivacyStatus.UNKNOWN)
   }
   ```

   De bovenstaande code doet het volgende:

   1. Registreert de vereiste extensies.
   1. Vormt MobileCore en andere uitbreidingen om uw configuratie van het markeringsbezit te gebruiken.
   1. Schakelt foutopsporingslogbestand in. Meer details en de opties kunnen in de [&#x200B; Mobiele documentatie van SDK van Adobe Experience Platform &#x200B;](https://developer.adobe.com/client-sdks/documentation/getting-started/enable-debug-logging/) worden gevonden.
   1. Start levenscycluscontrole. Zie [&#x200B; Levenscyclus &#x200B;](lifecycle-data.md) stap in het leerprogramma voor meer details.
   1. Hiermee stelt u de standaardtoestemming in op onbekend. Zie [&#x200B; stap 0&rbrace; van de Toestemming &lbrace;in het leerprogramma voor meer details.](consent.md)

Zorg ervoor dat u `MobileCore.configureWith(environmentFileId)` bijwerkt met de `environmentFileId` op basis van de Omgevingsbestands-id uit de tagomgeving waarvoor u ontwikkelt (ontwikkeling, staging of productie).


>[!ENDTABS]

>[!SUCCESS]
>
>U hebt nu de benodigde pakketten geïnstalleerd en uw project bijgewerkt om de vereiste Adobe Experience Platform Mobile SDK-extensies te registreren die u voor de rest van de zelfstudie gaat gebruiken.
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene terugkoppelen willen delen, of suggesties over toekomstige inhoud hebben, hen op deze [&#x200B; Communautaire besprekingspost van Experience League &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) delen

Volgende: **[Opstelling Assurance](assurance.md)**
