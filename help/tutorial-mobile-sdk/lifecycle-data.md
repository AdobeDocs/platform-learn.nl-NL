---
title: Levenscyclusgegevens verzamelen met Platform Mobile SDK
description: Leer hoe u levenscyclusgegevens kunt verzamelen in een mobiele app.
jira: KT-14630
exl-id: 75b2dbaa-2f84-4b95-83f6-2f38a4f1d438
source-git-commit: 7e7c7600457b361c2ba9616c067b9fe33fd70c5c
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 1%

---

# Levenscyclusgegevens verzamelen

Leer hoe u levenscyclusgegevens kunt verzamelen in een mobiele app.

Met de Adobe Experience Platform Mobile SDK Lifecycle-extensie kunt u levenscyclusgegevens van uw mobiele app verzamelen. De Adobe Experience Platform Edge Network-extensie verzendt deze levenscyclusgegevens naar het Platform Edge Network, waar deze vervolgens worden doorgestuurd naar andere toepassingen en services volgens uw configuratie van de gegevensstroom. Leer meer over de [ uitbreiding van de Levenscyclus ](https://developer.adobe.com/client-sdks/documentation/lifecycle-for-edge-network/) in de productdocumentatie.


## Vereisten

* App met SDK&#39;s geïnstalleerd en geconfigureerd met succes gemaakt en uitgevoerd. Als onderdeel van deze les bent u al begonnen met levenscycluscontrole. Zie [ SDKs installeren - Update AppDelegate ](install-sdks.md#update-appdelegate) aan overzicht.
* Registreerde de uitbreiding van Assurance zoals die in de [ vorige les ](install-sdks.md) wordt beschreven.

## Leerdoelstellingen

In deze les zult u:

<!--
* Add lifecycle field group to the schema.
* -->
* Zorg voor nauwkeurige levenscyclusmetrische gegevens door de toepassing correct te starten/pauzeren wanneer deze van de voorgrond naar de achtergrond gaat.
* Gegevens vanuit de app verzenden naar Platform Edge Network.
* Valideren in Assurance.

<!--
## Add lifecycle field group to schema

The Consumer Experience Event field group you added in the [previous lesson](create-schema.md) already contains the lifecycle fields, so you can skip this step. If you don't use Consumer Experience Event field group in your own app, you can add the lifecycle fields by doing the following:

1. Navigate to the schema interface as described in the [previous lesson](create-schema.md).
1. Open the **Luma Mobile App Event Schema** schema and select **[!UICONTROL Add]** next to Field groups.
    ![select add](assets/lifecycle-add.png){zoomable="yes"}
1. In the search bar, enter "lifecycle".
1. Select the checkbox next to **[!UICONTROL AEP Mobile Lifecycle Details]**.
1. Select **[!UICONTROL Add field groups]**.
    ![add field group](assets/lifecycle-lifecycle-field-group.png){zoomable="yes"}
1. Select **[!UICONTROL Save]**.
    ![save](assets/lifecycle-lifecycle-save.png){zoomable="yes"}
-->

## Wijzigingen in implementatie

Nu kunt u uw project bijwerken en de levenscyclusgebeurtenissen registreren.

>[!BEGINTABS]

>[!TAB  iOS ]

1. Navigeer naar **[!DNL Luma]** > **[!DNL Luma]** > **[!UICONTROL SceneDelegate]** in de Xcode-projectnavigator.

1. Als uw app wordt gestart en deze wordt hervat vanaf een achtergrondstatus, roept iOS mogelijk uw gedelegeerde methode `sceneWillEnterForeground:` aan. Met deze methode wilt u een start-gebeurtenis voor de levenscyclus activeren. Deze code toevoegen aan `func sceneWillEnterForeground(_ scene: UIScene)` :

   ```swift
   // When in foreground start lifecycle data collection
   MobileCore.lifecycleStart(additionalContextData: nil)
   ```

1. Wanneer de app de achtergrond betreedt, wilt u de gegevensverzameling tijdens de levenscyclus van de gedelegeerde methode van uw app voor `sceneDidEnterBackground:` pauzeren. Deze code toevoegen aan `func sceneDidEnterBackground(_ scene: UIScene)` :

   ```swift
   // When in background pause lifecycle data collection
   MobileCore.lifecyclePause()
   ```

>[!TAB  Android ]

1. Navigeer naar **[!UICONTROL app]** > **[!UICONTROL kotlin+java]** > **[!UICONTROL com.adobe.luma.tutorial.android]** > **[!UICONTROL LumaApplication]** in de Android Studio-navigator.

1. Als uw app wordt gestart en de toepassing op de achtergrond wordt hervat, roept Android mogelijk uw overschrijving `fun onActivityResumed function` aan en u wilt met deze functie een gebeurtenis voor het starten van de levenscyclus activeren. Deze code toevoegen aan `override fun onActivityResumed(activity: Activity)` :

   ```kotlin
   // When in foreground start lifecycle data collection
   MobileCore.lifecycleStart(null)
   ```

1. Wanneer de app de achtergrond betreedt, wilt u de gegevensverzameling tijdens de levenscyclus van de functie `override fun onActivityPaused` van uw app pauzeren. Deze code toevoegen aan `override fun onActivityPaused(activity: Activity)` :

   ```kotlin
   // When in background pause lifecycle data collection
   MobileCore.lifecyclePause()
   ```

>[!ENDTABS]


## Valideren met Assurance

1. Herzie de [ sectie van opstellingsinstructies ](assurance.md#connecting-to-a-session) om uw simulator of apparaat met Assurance te verbinden.
1. Verzend de app naar de achtergrond. Controleren op **[!UICONTROL LifecyclePause]** -gebeurtenissen in de gebruikersinterface van Assurance.
1. Breng de app naar de voorgrond. Controleren op **[!UICONTROL LifecycleResume]** -gebeurtenissen in de gebruikersinterface van Assurance.
   ![ bevestigt levenscyclus ](assets/lifecycle-lifecycle-assurance.png){zoomable="yes"}


## Gegevens doorsturen naar Platform Edge Network

De vorige oefening verzendt de voor- en achtergrondgebeurtenissen naar Adobe Experience Platform Mobile SDK. Deze gebeurtenissen doorsturen naar Platform Edge Network:

1. Selecteer **[!UICONTROL Rules]** in de eigenschap Codes.
   ![ creeer Regel ](assets/rule-create.png){zoomable="yes"}
1. Selecteer **[!UICONTROL Initial Build]** als de bibliotheek die u wilt gebruiken.
1. Selecteer **[!UICONTROL Create New Rule]**.
   ![ creeer Nieuwe Regel ](assets/rules-create-new.png){zoomable="yes"}
1. Typ **[!UICONTROL Create Rule]** for `Application Status` in het scherm **[!UICONTROL Name]** .
1. Selecteer ![ toevoegen ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add]** hieronder **[!UICONTROL EVENTS]**.
   ![ creeer de dialoog van de Regel ](assets/rule-create-name.png){zoomable="yes"}
1. In de stap **[!UICONTROL Event Configuration]** :
   1. Selecteer **[!UICONTROL Mobile Core]** als de **[!UICONTROL Extension]** .
   1. Selecteer **[!UICONTROL Foreground]** als de **[!UICONTROL Event Type]** .
   1. Selecteer **[!UICONTROL Keep Changes]**.
      ![ Configuratie van de Gebeurtenis van de Regel ](assets/rule-event-configuration.png){zoomable="yes"}
1. Terug in het **[!UICONTROL Create Rule]** scherm, uitgezocht ![ voeg ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add]** naast **[!UICONTROL Mobile Core - Foreground]** toe.
   ![ Volgende gebeurtenisconfiguratie ](assets/rule-event-configuration-next.png){zoomable="yes"}
1. In de stap **[!UICONTROL Event Configuration]** :
   1. Selecteer **[!UICONTROL Mobile Core]** als de **[!UICONTROL Extension]** .
   1. Selecteer **[!UICONTROL Background]** als de **[!UICONTROL Event Type]** .
   1. Selecteer **[!UICONTROL Keep Changes]**.
      ![ Configuratie van de Gebeurtenis van de Regel ](assets/rule-event-configuration-background.png){zoomable="yes"}
1. Terug in het **[!UICONTROL Create Rule]** scherm, uitgezocht ![ voeg ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) toe **[!UICONTROL Add]** onder **[!UICONTROL ACTIONS]**.

   ![ Regel voegt Actie ](assets/rule-action-button.png){zoomable="yes"} toe

1. In de stap **[!UICONTROL Action Configuration]** :
   1. Selecteer **[!UICONTROL Adobe Experience Edge Network]** als de **[!UICONTROL Extension]** .
   1. Selecteer **[!UICONTROL Forward event to Edge Network]** als de **[!UICONTROL Action Type]** .
   1. Selecteer **[!UICONTROL Keep Changes]**.
      ![ Configuratie van de Actie van de Regel ](assets/rule-action-configuration.png){zoomable="yes"}
1. Selecteer **[!UICONTROL Save to Library]**.
   ![ Regel - sparen aan Bibliotheek ](assets/rule-save-to-library.png){zoomable="yes"}
1. Selecteer **[!UICONTROL Build]** om de bibliotheek opnieuw samen te stellen.
   ![ Regel - bouw ](assets/rule-build.png){zoomable="yes"}

Zodra u met succes het bezit hebt gebouwd, worden de gebeurtenissen verzonden naar Platform Edge Network, en de gebeurtenissen door:sturen aan andere toepassingen en de diensten volgens uw datastreamconfiguratie.

Gebeurtenissen **[!UICONTROL Application Close (Background)]** en **[!UICONTROL Application Launch (Foreground)]** die XDM-gegevens bevatten, worden weergegeven in Assurance.

![ bevestigt levenscyclus die naar Platform Edge wordt verzonden ](assets/lifecycle-edge-assurance.png){zoomable="yes"}

>[!SUCCESS]
>
>U hebt nu uw app zo ingesteld dat toepassingsstatusgebeurtenissen (voorgrond, achtergrond) naar de Adobe Experience Platform Edge Network en alle services die u in uw gegevensstroom hebt gedefinieerd, worden verzonden.
>
> Bedankt dat je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene terugkoppelen willen delen, of suggesties over toekomstige inhoud hebben, hen op deze [ Communautaire besprekingspost van Experience League ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) delen

Volgende: **[de gebeurtenisgegevens van het Spoor](events.md)**
