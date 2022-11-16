---
title: Adobe Experience Platform Mobile SDK's installeren
description: Leer hoe u de Adobe Experience Platform Mobile SDK in een mobiele app implementeert.
exl-id: 98d6f59e-b8a3-4c63-ae7c-8aa11e948f59
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Adobe Experience Platform Mobile SDK&#39;s installeren

Leer hoe u de Adobe Experience Platform Mobile SDK in een mobiele app implementeert.

## Vereisten

* Tagbibliotheek is gemaakt met de extensies die zijn beschreven in het dialoogvenster [vorige les](configure-tags.md).
* Bestand-id voor ontwikkelomgeving van de [Instructies voor mobiele installatie](configure-tags.md#generate-sdk-install-instructions).
* Gedownload, leeg [voorbeeldapp](https://github.com/Adobe-Marketing-Cloud/Luma-iOS-Mobile-App){target=&quot;_blank&quot;}.
* Ervaring met [XCode](https://developer.apple.com/xcode/){target=&quot;_blank&quot;}.
* Basis [opdrachtregel](https://en.wikipedia.org/wiki/Command-line_interface){target=&quot;_blank&quot;} kennis.

## Leerdoelstellingen

In deze les zult u:

* Werk het CocoaPod-bestand bij.
* Importeer de vereiste SDK&#39;s.
* Registreer de extensies.

>[!NOTE]
>
>In een mobiele app-implementatie zijn de termen &quot;extensies&quot; en &quot;SDK&#39;s&quot; bijna uitwisselbaar.


## PodFile bijwerken

>[!NOTE]
>
> Als u niet bekend bent met CocoaPods, raadpleeg dan de officiële [gids Aan de slag](https://guides.cocoapods.org/using/getting-started.html).

Installeren is doorgaans een eenvoudige sudo-opdracht:

```console
sudo gem install cocoapods
```

Als u CocoaPods hebt geïnstalleerd, opent u het Podfile.

![eerste podbestand](assets/mobile-install-initial-podfile.png)

Werk het bestand bij en voeg de volgende pods toe:

```swift
pod 'AEPCore', '~> 3'
pod 'AEPEdge', '~> 1'
pod 'AEPUserProfile', '~> 3'
pod 'AEPAssurance', '~> 3'
pod 'AEPServices', '~> 3'
pod 'AEPEdgeConsent', '~> 1'
pod 'AEPLifecycle', '~>3'
pod 'AEPMessaging', '~>1'
pod 'AEPEdgeIdentity', '~>1'
pod 'AEPSignal', '~>3'
```

>[!NOTE]
>
> `AEPMessaging` is alleen vereist als u pushberichten wilt implementeren met Adobe Journey Optimizer. Lees de zelfstudie op [pushberichten implementeren met Adobe Journey Optimizer](journey-optimizer-push.md) voor meer informatie .

Nadat u de wijzigingen in het Podfile hebt opgeslagen, navigeert u samen met uw project naar de map en voert u de opdracht `pod install` om uw wijzigingen te installeren.

![pod installeren](assets/mobile-install-podfile-install.png)

>[!NOTE]
>
> Als u &quot;Geen Podfile gevonden in de projectfolder krijgt.&quot; fout, is uw terminal in de verkeerde omslag. Navigeer naar de map met het Podfile dat u hebt bijgewerkt en probeer het opnieuw.

Als u wilt upgraden naar de nieuwste versie, voert u de opdracht `pod update` gebruiken.

>[!INFO]
>
>Als u CocoaPods niet kunt gebruiken in uw eigen toepassingen, kunt u meer informatie over andere toepassingen [ondersteunde implementaties](https://github.com/adobe/aepsdk-core-ios#binaries) in het GitHub-project.

## CocoaPods maken

Om CocoaPods te bouwen, open `Luma.xcworkspace`en selecteert u **Product**, gevolgd door **Opbouwmap opschonen**.

>[!NOTE]
>
> U moet mogelijk instellen **Alleen actieve architectuur maken** tot **Nee**. Om dit te doen, selecteer het project van Pods van de projectnavigator, uitgezocht **Instellingen samenstellen** en stelt de **Actieve architectuur maken** tot **Nee**.

U kunt het project nu bouwen en in werking stellen.

![build-instellingen](assets/mobile-install-build-settings.png)

>[!NOTE]
>
>Het Luma-project is gemaakt met Xcode v12.5 op een M1-chipset en wordt uitgevoerd op de iOS-simulator. Als u een verschillende opstelling gebruikt, kunt u uw bouwstijlmontages moeten veranderen om op uw architectuur te wijzen.
>
>Als uw build niet is gelukt, probeert u de **Actieve architectuur maken** > **Foutopsporing** instellen op **Ja**.
>
>Simulatorconfiguratie &quot;iPod touch (7e generatie)&quot; werd gebruikt tijdens het ontwerpen van deze zelfstudie.

## Extensies importeren

In elk van de `.swift` voegt u de volgende importbewerkingen toe. Starten door aan toe te voegen `AppDelegate.swift`.

```swift
import AEPUserProfile
import AEPAssurance
import AEPEdge
import AEPCore
import AEPEdgeIdentity
import AEPEdgeConsent
import AEPLifecycle
import AEPMessaging //Optional, used for AJO push messaging
import AEPSignal
import AEPServices
```

## AppDelegate bijwerken

In de `AppDelegate.swift` bestand, voeg de volgende code toe aan `didFinishLaunchingWithOptions`. Vervang currentAppId door de waarde voor het bestand-id van de ontwikkelomgeving die u hebt opgehaald van de tags in het dialoogvenster [vorige les](configure-tags.md).

```swift
let currentAppId = "b5cbd1a1220e/bae66382cce8/launch-88492c6dcb6e-development"

let extensions = [Edge.self, Assurance.self, Lifecycle.self, UserProfile.self, Consent.self, AEPEdgeIdentity.Identity.self, Messaging.self]

MobileCore.setLogLevel(.trace)

MobileCore.registerExtensions(extensions, {
    MobileCore.configureWith(appId: currentAppId)
})
```

`Messaging.self` is alleen vereist als u pushberichten via Adobe Journey Optimizer wilt implementeren zoals beschreven [hier](journey-optimizer-push.md).

De bovenstaande code doet het volgende:

* Registreert de vereiste extensies.
* Vormt MobileCore en andere uitbreidingen om uw configuratie van het markeringsbezit te gebruiken.
* Schakelt foutopsporingslogbestand in. Meer details en opties vindt u in het gedeelte [Mobiele SDK-documentatie](https://aep-sdks.gitbook.io/docs/getting-started/enable-debug-logging).

>[!IMPORTANT]
>In een productie-app moet u van appId wisselen op basis van de huidige omgeving (dev/stag/prod).

Volgende: **[Betrouwbaarheid instellen](assurance.md)**

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)