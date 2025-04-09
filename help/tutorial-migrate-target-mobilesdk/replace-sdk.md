---
title: De SDK vervangen - Migreer de Adobe Target-implementatie in uw mobiele app naar de extensie Adobe Journey Optimizer - Decisioning
description: Meer informatie over het vervangen van de SDK bij het migreren van de extensie Adobe Target naar de Adobe Journey Optimizer - Decisioning Mobile.
exl-id: f1b77cad-792b-4a80-acff-e1a2f29250e1
source-git-commit: 2ebad2014d4c29a50af82328735258958893b42c
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---

# Vervang de doel-SDK door de SDK optimaliseren

Meer informatie over het vervangen van de Adobe Target SDK&#39;s door de Optimize SDK&#39;s in uw mobiele implementatie. Een basisvervanging bestaat uit de volgende stappen:

* Afhankelijkheden in uw Podfile of `build.gradle` bestand bijwerken
* Import bijwerken
* Toepassingscode bijwerken


>[!INFO]
>
>In het ecosysteem van Adobe Experience Platform Mobile SDK worden extensies geïmplementeerd door SDK&#39;s die zijn geïmporteerd in uw toepassingen en die verschillende namen kunnen hebben:
>
> * **SDK van het Doel** voert de **uitbreiding van Adobe Target** uit
> * **optimaliseer SDK** voert **Adobe Journey Optimizer uit - Beslissende uitbreiding**

## Afhankelijkheden bijwerken

+++Android, voorbeeld

>[!BEGINTABS]

>[!TAB  optimaliseer SDK ]

`build.gradle` afhankelijkheden na migreren

```Java
implementation platform('com.adobe.marketing.mobile:sdk-bom:3.+')
implementation 'com.adobe.marketing.mobile:core'
implementation 'com.adobe.marketing.mobile:edgeidentity'
implementation 'com.adobe.marketing.mobile:edge'
implementation 'com.adobe.marketing.mobile:optimize'
```


>[!TAB  Doel SDK ]

`build.gradle` afhankelijkheden voordat er wordt gemigreerd

```Java
implementation platform('com.adobe.marketing.mobile:sdk-bom:3.+')
implementation 'com.adobe.marketing.mobile:analytics'
implementation 'com.adobe.marketing.mobile:target'
implementation 'com.adobe.marketing.mobile:core'
implementation 'com.adobe.marketing.mobile:identity'
implementation 'com.adobe.marketing.mobile:lifecycle'
implementation 'com.adobe.marketing.mobile:signal'
implementation 'com.adobe.marketing.mobile:userprofile'
```


>[!ENDTABS]

+++

+++ iOS-voorbeeld

>[!BEGINTABS]


>[!TAB SDK optimaliseren]

`Podfile` Afhankelijkheden na migratie

```Swift
use_frameworks!
target 'YourAppTarget' do
    pod 'AEPCore', '~> 5.0'
    pod 'AEPEdge', '~> 5.0'
    pod 'AEPEdgeIdentity', '~> 5.0'
    pod 'AEPOptimize', '~> 5.0'
end
```

>[!TAB Doel SDK]

`Podfile` afhankelijkheden vóór de migratie

```Swift
use_frameworks!
pod 'AEPAnalytics', '~> 5.0'
pod 'AEPTarget', '~> 5.0'
pod 'AEPCore', '~> 5.0'
pod 'AEPIdentity', '~> 5.0'
pod 'AEPSignal', '~>5.0'
pod 'AEPLifecycle', '~>5.0'
pod 'AEPUserProfile', '~> 5.0'
```

>[!ENDTABS]

+++

## Import en code bijwerken

+++ Android voorbeeld

>[!BEGINTABS]

>[!TAB  optimaliseer SDK ]

Java-initialisatiecode na migreren

```Java
import com.adobe.marketing.mobile.MobileCore;
import com.adobe.marketing.mobile.Edge;
import com.adobe.marketing.mobile.edge.identity.Identity;
import com.adobe.marketing.mobile.optimize.Optimize;
import com.adobe.marketing.mobile.AdobeCallback;
 
public class MainApp extends Application {
 
  private final String ENVIRONMENT_FILE_ID = "YOUR_APP_ENVIRONMENT_ID";
 
    @Override
    public void onCreate() {
        super.onCreate();
 
        MobileCore.setApplication(this);
        MobileCore.configureWithAppID(ENVIRONMENT_FILE_ID);
 
        MobileCore.registerExtensions(
            Arrays.asList(Edge.EXTENSION, Identity.EXTENSION, Optimize.EXTENSION),
            o -> Log.d("MainApp", "Adobe Journey Optimizer - Decisioning Mobile SDK was initialized.")
        );
    }
}
```

>[!TAB  Doel SDK ]

Java-initialisatiecode voor migreren

```Java
import com.adobe.marketing.mobile.AdobeCallback;
import com.adobe.marketing.mobile.Analytics;
import com.adobe.marketing.mobile.Extension;
import com.adobe.marketing.mobile.Identity;
import com.adobe.marketing.mobile.Lifecycle;
import com.adobe.marketing.mobile.LoggingMode;
import com.adobe.marketing.mobile.MobileCore;
import com.adobe.marketing.mobile.Signal;
import com.adobe.marketing.mobile.Target;
import com.adobe.marketing.mobile.UserProfile;
import java.util.Arrays;
import java.util.List;
...
import android.app.Application;
...
public class MainApp extends Application {
...
    @Override
    public void onCreate() {
        super.onCreate();
        MobileCore.setApplication(this);
        MobileCore.setLogLevel(LoggingMode.DEBUG);
        ...
        List<Class<? extends Extension>> extensions = Arrays.asList(
            Analytics.EXTENSION,
            Target.EXTENSION,
            Identity.EXTENSION,
            Lifecycle.EXTENSION,
            Signal.EXTENSION,
            UserProfile.EXTENSION
        );
 
 
        MobileCore.registerExtensions(extensions, new AdobeCallback () {
            @Override
            public void call(Object o) {
                MobileCore.configureWithAppID(<Environment File ID>);
            }
        });
    }
}
```

>[!ENDTABS]

+++

+++ iOS

>[!BEGINTABS]

>[!TAB  optimaliseer SDK ]

Snelle initialisatiecode na migreren

```Swift
import AEPCore
import AEPEdge
import AEPEdgeIdentity
import AEPOptimize
 
@UIApplicationMain
final class AppDelegate: UIResponder, UIApplicationDelegate {
  var window: UIWindow?
 
  func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]? = nil) -> Bool {
 
      // register the extensions
      MobileCore.registerExtensions([Edge.self, AEPEdgeIdentity.Identity.self, Optimize.self]) {
        MobileCore.configureWith(appId: <YOUR_ENVIRONMENT_FILE_ID>) // Replace <YOUR_ENVIRONMENT_FILE_ID> with a String containing your own ID.
      }
 
      return true
  }
}
```

>[!TAB  Doel SDK ]

Snelle initialisatiecode voor migratie

```Swift
import AEPCore
import AEPAnalytics
import AEPTarget
import AEPIdentity
import AEPLifecycle
import AEPSignal
import AEPServices
import AEPUserProfile
...
@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {
    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        MobileCore.setLogLevel(.debug)
        let appState = application.applicationState
        ...
        let extensions = [
            Analytics.self,
            Target.self,
            Identity.self,
            Lifecycle.self,
            Signal.self,
            UserProfile.self
        ]
        MobileCore.registerExtensions(extensions, {
        MobileCore.configureWith(<Environment File ID>)
        if appState != .background {
            MobileCore.lifecycleStart(additionalContextData: ["contextDataKey": "contextDataVal"])
            }
        })
        ...
        return true
    }
}
```

>[!ENDTABS]

+++

## API-vergelijking

Veel API&#39;s voor Target-extensies hebben een equivalente aanpak met behulp van de Decisioning-extensie die in de onderstaande tabel wordt beschreven. Raadpleeg de API-referentie voor meer informatie over de [functies](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/api-reference/).

| Doel extensie | Uitbreiding van de besluitvorming | Notities |
| --- | --- | --- | 
| [ prefetchContent ](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#prefetchcontent){target=_blank} | [update Proposities](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/api-reference/#updatepropositionswithcompletionhandlerandtimeout){target=_blank} |  |
| [ retrieveLocationContent ](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#retrievelocationcontent){target=_blank} | [getProposities](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/api-reference/#getpropositionswithtimeout){target=_blank} | Wanneer u API gebruikt `getPropositions` , wordt er geen externe aanroep gedaan om niet-gecachete bereiken in de SDK op te halen. |
| [weergegevenLocaties](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#retrievelocationcontent){target=_blank} | [Aanbieding -> weergegeven()](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank} | Daarnaast kan de methode `generateDisplayInteractionXdm` Offer worden gebruikt om de XDM voor itemweergave te genereren. Daarna kan de Edge-netwerk SDK sendEvent-API worden gebruikt om extra XDM-gegevens met een vrije vorm toe te voegen en een Experience Event naar de externe server te verzenden. |
| [ clickedLocation ](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#clickedlocation){target=_blank} | [ Aanbieding -> uitgelijnd () ](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank} | Daarnaast kan de methode `generateTapInteractionXdm` Aanbieding worden gebruikt om de XDM voor het tikken van items te genereren. Daarna kan de Edge-netwerk SDK sendEvent-API worden gebruikt om extra XDM-gegevens met een vrije vorm toe te voegen en een Experience Event naar de externe server te verzenden. |
| [ clearPrefetchCache ](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#clickedlocation){target=_blank} | [ clearCachedProposities ](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank} |  |
| [ resetExperience ](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#resetexperience){target=_blank} | nvt | Gebruik [ removeIdentity ](https://developer.adobe.com/client-sdks/edge/identity-for-edge-network/api-reference/#removeidentity){target=_blank} API van Identiteit voor de uitbreiding van Edge Network voor SDK ophouden verzendend het bezoekersherkenningsteken naar het netwerk van Edge. Voor meer details, zie [ de removeIdentity API documentatie ](https://developer.adobe.com/client-sdks/edge/identity-for-edge-network/api-reference/#removeidentity). <br><br> Nota: De `resetIdentities` API van de Mobiele Kern ontruimt alle opgeslagen identiteiten in SDK, met inbegrip van Experience Cloud identiteitskaart (ECID) en het zou spaarzaam moeten worden gebruikt! |
| [ getSessionId ](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#getsessionid){target=_blank} | n.v.t | `state:store` De responsgreep bevat sessiegerelateerde informatie. De Edge-netwerkextensie helpt bij het beheren door niet-verlopen statuswinkelitems aan volgende verzoeken toe te voegen. |
| [ setSessionId ](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#setsessionid){target=_blank} | n.v.t | `state:store` De responsgreep bevat sessiegerelateerde informatie. De Edge-netwerkextensie helpt bij het beheren door niet-verlopen statuswinkelitems aan volgende verzoeken toe te voegen. |
| [ getThirdPartyId ](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#getthirdpartyid){target=_blank} | n.v.t | Gebruik de updateIdentities-API van de Identity for Edge Network-extensie om de ID-waarde van derden op te geven. Configureer vervolgens de ID-naamruimte van derden in de gegevensstroom. Zie [de mobiele documentatie](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id) van Target Third Party Id voor meer informatie. |
| [ setThirdPartyId ](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#setthirdpartyid){target=_blank} | nvt | Gebruik de updateIdentities-API van Identity voor de Edge Network-extensie om de id-waarde van derden op te geven. Dan, vorm derde identiteitskaart namespace in de datastream. Voor meer details, zie [ de mobiele documentatie van Identiteitskaart van de Derde van het Doel ](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id). |
| [ getTntId ](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#gettntid){target=_blank} | nvt | `locationHint:result` De responsgreep bevat de informatie over de hint voor de doellocatie. Er wordt aangenomen dat Target Edge zich op dezelfde locatie zal bevinden als Experience Edge. <br> <br>De Edge-netwerkextensie gebruikt de EdgeNetwork-locatiehint om te bepalen naar welk Edge-netwerkcluster aanvragen moeten worden verzonden. Als u een hint voor de locatie van het Edge-netwerk wilt delen met SDK&#39;s (hybride apps), gebruikt u `getLocationHint` API&#39;s `setLocationHint` van de Edge Network-extensie. Zie [de `getLocationHint` API-documentatie](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint) voor meer informatie. |
| [ setTntId ](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#gettntid){target=_blank} | n.v.t | [locationHint:de handle voor resultaatrespons](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#setlocationhint){target=_blank} bevat de informatie over de hint voor de doellocatie. Er wordt aangenomen dat Target Edge zich op dezelfde locatie zal bevinden als Experience Edge. <br> <br>De Edge-netwerkextensie gebruikt de EdgeNetwork-locatiehint om te bepalen naar welk Edge-netwerkcluster aanvragen moeten worden verzonden. Als u een hint voor de locatie van het Edge-netwerk wilt delen met SDK&#39;s (hybride apps), gebruikt u `getLocationHint` API&#39;s `setLocationHint` van de Edge Network-extensie. Zie [de `getLocationHint` API-documentatie](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint) voor meer informatie. |


Leer vervolgens hoe u activiteiten](retrieve-activities.md) kunt [aanvragen en weergeven op de pagina.

>[!NOTE]
>
>Wij zijn geëngageerd om u te helpen met uw mobiele migratie van het Doel van de uitbreiding van het Doel aan de uitbreiding van het Beslissen succesvol te zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-target-to-mobile-sdk-on-edge/m-p/747484#M625) te posten.
