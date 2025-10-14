---
title: SDK vervangen - De Adobe Target-implementatie in uw mobiele app migreren naar de extensie Offer Decisioning en Target
description: Leer hoe u de SDK kunt vervangen bij het migreren van de Adobe Target naar de extensie Offer Decisioning en Target Mobile.
exl-id: f1b77cad-792b-4a80-acff-e1a2f29250e1
source-git-commit: 876e664a213aec954105bf2d5547baab5d8a84ea
workflow-type: tm+mt
source-wordcount: '726'
ht-degree: 0%

---

# De Target SDK vervangen door de Optimize SDK

Leer hoe u de SDK&#39;s van Adobe Target vervangt door de SDK&#39;s van Optimize in uw mobiele implementatie. Een basisvervanging bestaat uit de volgende stappen:

* Afhankelijkheden bijwerken in het Podfile of het `build.gradle` bestand
* Import bijwerken
* Toepassingscode bijwerken


>[!INFO]
>
>In het ecosysteem van Adobe Experience Platform Mobile SDK worden extensies geïmplementeerd door SDK&#39;s die zijn geïmporteerd in uw toepassingen en die verschillende namen kunnen hebben:
>
> * **SDK van het Doel** voert de **uitbreiding van Adobe Target** uit
> * **optimaliseer SDK** voert **Offer Decisioning en de uitbreiding van het Doel** uit

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


>[!TAB  optimaliseer SDK ]

`Podfile` afhankelijkheden na migreren

```Swift
use_frameworks!
target 'YourAppTarget' do
    pod 'AEPCore', '~> 5.0'
    pod 'AEPEdge', '~> 5.0'
    pod 'AEPEdgeIdentity', '~> 5.0'
    pod 'AEPOptimize', '~> 5.0'
end
```

>[!TAB  Doel SDK ]

`Podfile` afhankelijkheden voordat er wordt gemigreerd

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

## Importeren en code bijwerken

+++ Android-voorbeeld

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
            o -> Log.d("MainApp", "Offer Decisioning and Target Mobile SDK was initialized.")
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

Veel API&#39;s voor doelextensies hebben een equivalente aanpak met de Offer Decisioning- en Target-extensie die in de onderstaande tabel wordt beschreven. Voor meer details over de [&#x200B; functies &#x200B;](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/api-reference/), verwijs naar de API verwijzing.

| Doelextensie | Offer Decisioning en Target-extensie | Notities |
| --- | --- | --- | 
| [&#x200B; prefetchContent &#x200B;](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#prefetchcontent){target=_blank} | [&#x200B; updateProposities &#x200B;](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/api-reference/#updatepropositionswithcompletionhandlerandtimeout){target=_blank} |  |
| [&#x200B; retrieveLocationContent &#x200B;](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#retrievelocationcontent){target=_blank} | [&#x200B; getProposities &#x200B;](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/api-reference/#getpropositionswithtimeout){target=_blank} | Wanneer u de API van `getPropositions` gebruikt, wordt geen externe aanroep gemaakt om niet-caching-bereik op te halen in de SDK. |
| [&#x200B; displayedLocations &#x200B;](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#retrievelocationcontent){target=_blank} | [&#x200B; Aanbieding -> getoond () &#x200B;](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank} | Daarnaast kan de methode `generateDisplayInteractionXdm` Offer worden gebruikt om de XDM voor itemweergave te genereren. Daarna kan de Edge-netwerk SDK sendEvent-API worden gebruikt om extra XDM-gegevens met een vrije vorm toe te voegen en een Experience Event naar de externe server te verzenden. |
| [&#x200B; clickedLocation &#x200B;](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#clickedlocation){target=_blank} | [&#x200B; Aanbieding -> uitgelijnd () &#x200B;](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank} | Daarnaast kan de methode `generateTapInteractionXdm` Aanbieding worden gebruikt om de XDM voor het tikken van items te genereren. Daarna kan de Edge-netwerk SDK sendEvent-API worden gebruikt om extra XDM-gegevens met een vrije vorm toe te voegen en een Experience Event naar de externe server te verzenden. |
| [&#x200B; clearPrefetchCache &#x200B;](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#clickedlocation){target=_blank} | [&#x200B; clearCachedProposities &#x200B;](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank} |  |
| [&#x200B; resetExperience &#x200B;](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#resetexperience){target=_blank} | nvt | Gebruik [&#x200B; removeIdentity &#x200B;](https://developer.adobe.com/client-sdks/edge/identity-for-edge-network/api-reference/#removeidentity){target=_blank} API van Identiteit voor de uitbreiding van Edge Network voor SDK ophouden verzendend het bezoekersherkenningsteken naar het netwerk van Edge. Voor meer details, zie [&#x200B; de removeIdentity API documentatie &#x200B;](https://developer.adobe.com/client-sdks/edge/identity-for-edge-network/api-reference/#removeidentity). <br><br> Nota: De `resetIdentities` API van de Mobiele Kern ontruimt alle opgeslagen identiteiten in SDK, met inbegrip van Experience Cloud identiteitskaart (ECID) en het zou spaarzaam moeten worden gebruikt! |
| [&#x200B; getSessionId &#x200B;](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#getsessionid){target=_blank} | nvt | `state:store` reactiehandgreep bevat informatie over sessies. De Edge-netwerkextensie helpt het te beheren door items in een niet-verlopen frameopslag aan volgende aanvragen toe te voegen. |
| [&#x200B; setSessionId &#x200B;](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#setsessionid){target=_blank} | nvt | `state:store` reactiehandgreep bevat informatie over sessies. De Edge-netwerkextensie helpt het te beheren door items in een niet-verlopen frameopslag aan volgende aanvragen toe te voegen. |
| [&#x200B; getThirdPartyId &#x200B;](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#getthirdpartyid){target=_blank} | nvt | Gebruik de updateIdentities-API van Identity voor de Edge Network-extensie om de id-waarde van derden op te geven. Dan, vorm derde identiteitskaart namespace in de datastream. Voor meer details, zie [&#x200B; de mobiele documentatie van Identiteitskaart van de Derde van het Doel &#x200B;](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id). |
| [&#x200B; setThirdPartyId &#x200B;](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#setthirdpartyid){target=_blank} | nvt | Gebruik de updateIdentities-API van Identity voor de Edge Network-extensie om de id-waarde van derden op te geven. Dan, vorm derde identiteitskaart namespace in de datastream. Voor meer details, zie [&#x200B; de mobiele documentatie van Identiteitskaart van de Derde van het Doel &#x200B;](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#target-third-party-id). |
| [&#x200B; getTntId &#x200B;](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#gettntid){target=_blank} | nvt | `locationHint:result` reactiehandgreep bevat de informatie over de doellocatiehint. Aangenomen wordt dat Target edge zich op dezelfde locatie bevindt als Experience Edge. <br> <br> het netwerkuitbreiding van Edge gebruikt de het plaatswenk van EdgeNetwork om de het netwerkcluster van Edge te bepalen om verzoeken naar te verzenden. Als u Edge-netwerklocatiehint wilt delen met SDK&#39;s (hybride apps), gebruikt u `getLocationHint` - en `setLocationHint` -API&#39;s van de Edge Network-extensie. Voor meer details, zie [&#x200B; de `getLocationHint` API documentatie &#x200B;](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint). |
| [&#x200B; setTntId &#x200B;](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#gettntid){target=_blank} | nvt | [&#x200B; locationHint:resultaat &#x200B;](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#setlocationhint){target=_blank} reactiehandvat draagt de informatie van de de plaatshint van het Doel. Aangenomen wordt dat Target edge zich op dezelfde locatie bevindt als Experience Edge. <br> <br> het netwerkuitbreiding van Edge gebruikt de het plaatswenk van EdgeNetwork om de het netwerkcluster van Edge te bepalen om verzoeken naar te verzenden. Als u Edge-netwerklocatiehint wilt delen met SDK&#39;s (hybride apps), gebruikt u `getLocationHint` - en `setLocationHint` -API&#39;s van de Edge Network-extensie. Voor meer details, zie [&#x200B; de `getLocationHint` API documentatie &#x200B;](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#getlocationhint). |


Daarna, leer hoe te [&#x200B; verzoeken en activiteiten &#x200B;](retrieve-activities.md) aan de pagina teruggeven.

>[!NOTE]
>
>We helpen u graag succesvol te zijn met uw mobiele doelmigratie van de doelextensie naar de Offer Decisioning en de doelextensie. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [&#x200B; deze communautaire bespreking &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-target-to-mobile-sdk-on-edge/m-p/747484#M625) te posten.
