---
title: Levenscyclusgegevens verzamelen
description: Leer hoe u levenscyclusgegevens kunt verzamelen in een mobiele app.
hide: true
exl-id: a3b26e45-2a17-4b44-aec0-fdf83526a273
source-git-commit: 4a12f8261cf1fb071bc70b6a04c34f6c16bcce64
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Levenscyclusgegevens verzamelen

Leer hoe u levenscyclusgegevens kunt verzamelen in een mobiele app.

Met de Levenscyclusextensie van de Adobe Experience Platform Mobile SDK kunt u levenscyclusgegevens van uw mobiele app verzamelen. De uitbreiding van het Netwerk van Adobe Experience Platform Edge verzendt deze levenscyclusgegevens naar het Netwerk van de Rand van het Platform waar het dan aan andere toepassingen en de diensten volgens uw gegevensstroomconfiguratie door:sturen. Meer informatie over de [Levenscyclusextensie](https://developer.adobe.com/client-sdks/documentation/lifecycle-for-edge-network/) in de productdocumentatie.


## Vereisten

* App met SDK&#39;s geïnstalleerd en geconfigureerd met succes gemaakt en uitgevoerd. Als onderdeel van deze les bent u al begonnen met levenscycluscontrole. Zie [SDK&#39;s installeren - AppDelegate bijwerken](install-sdks.md#update-appdelegate) ter beoordeling.
* Geregistreerd de uitbreiding van de Verzekering zoals die in wordt beschreven [vorige les](install-sdks.md).

## Leerdoelstellingen

In deze les zult u:

<!--
* Add lifecycle field group to the schema.
* -->
* Zorg voor nauwkeurige levenscyclusmetrische gegevens door de toepassing correct te starten/pauzeren wanneer deze van de voorgrond naar de achtergrond gaat.
* Gegevens verzenden van de app naar Platform Edge Network.
* Valideren bij Betrouwbaarheid.

<!--
## Add lifecycle field group to schema

The Consumer Experience Event field group you added in the [previous lesson](create-schema.md) already contains the lifecycle fields, so you can skip this step. If you don't use Consumer Experience Event field group in your own app, you can add the lifecycle fields by doing the following:

1. Navigate to the schema interface as described in the [previous lesson](create-schema.md).
1. Open the **Luma Mobile App Event Schema** schema and select **[!UICONTROL Add]** next to Field groups.
    ![select add](assets/lifecycle-add.png)
1. In the search bar, enter "lifecycle".
1. Select the checkbox next to **[!UICONTROL AEP Mobile Lifecycle Details]**.
1. Select **[!UICONTROL Add field groups]**.
    ![add field group](assets/lifecycle-lifecycle-field-group.png)
1. Select **[!UICONTROL Save]**.
    ![save](assets/lifecycle-lifecycle-save.png)
-->

## Wijzigingen in implementatie

Nu kunt u uw project bijwerken om de levenscyclusgebeurtenissen te registreren.

1. Navigeren naar **[!DNL Luma]** > **[!DNL Luma]** > **[!UICONTROL SceneDelegate]** in de Xcode-projectnavigator.

1. Als uw toepassing wordt gestart en de toepassing wordt hervat vanuit een achtergrondstatus, kan iOS mogelijk uw `sceneWillEnterForeground:` afgevaardigde methode en dit is waar u een gebeurtenis van het levenscyclusbegin wilt teweegbrengen. Deze code toevoegen aan `func sceneWillEnterForeground(_ scene: UIScene)`:

   ```swift
   // When in foreground start lifecycle data collection
   MobileCore.lifecycleStart(additionalContextData: nil)
   ```

1. Wanneer de app op de achtergrond wordt geplaatst, wilt u de verzameling van levenscyclusgegevens uit de app pauzeren `sceneDidEnterBackground:` gedelegeerde methode. Deze code toevoegen aan  `func sceneDidEnterBackground(_ scene: UIScene)`:

   ```swift
   // When in background pause lifecycle data collection
   MobileCore.lifecyclePause()
   ```

## Valideren met betrouwbaarheid

1. Controleer de [installatie-instructies](assurance.md#connecting-to-a-session) om de simulator of het apparaat aan te sluiten op Betrouwbaarheid.
1. Verzend de app naar de achtergrond. Controleren op **[!UICONTROL LevenscyclusPauze]** gebeurtenissen in de gebruikersinterface van de verzekering.
1. Breng de app naar de voorgrond. Controleren op **[!UICONTROL LevenscyclusHervatten]** gebeurtenissen in de gebruikersinterface van de verzekering.
   ![levenscyclus valideren](assets/lifecycle-lifecycle-assurance.png)


## Gegevens doorsturen naar Platform Edge Network

De vorige oefening verzendt de voor- en achtergrondgebeurtenissen naar Adobe Experience Platform Mobile SDK. Om deze gebeurtenissen aan het Netwerk van de Rand van het Platform door:sturen:

1. Selecteren **[!UICONTROL Regels]** in de eigenschap Tags.
   ![Regel maken](assets/rule-create.png)
1. Selecteren **[!UICONTROL Eerste build]** als de te gebruiken bibliotheek.
1. Selecteren **[!UICONTROL Nieuwe regel maken]**.
   ![Nieuwe regel maken](assets/rules-create-new.png)
1. In de **[!UICONTROL Regel maken]** scherm, enter `Application Status` for **[!UICONTROL Naam]**.
1. Selecteren ![Toevoegen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Toevoegen]** onder **[!UICONTROL EVENTS]**.
   ![Dialoogvenster Regel maken](assets/rule-create-name.png)
1. In de **[!UICONTROL Gebeurtenisconfiguratie]** stap:
   1. Selecteren **[!UICONTROL Mobiele kern]** als de **[!UICONTROL Extensie]**.
   1. Selecteren **[!UICONTROL Voorgrond]** als de **[!UICONTROL Type gebeurtenis]**.
   1. Selecteren **[!UICONTROL Wijzigingen behouden]**.
      ![Configuratie van regelgebeurtenissen](assets/rule-event-configuration.png)
1. Terug in de **[!UICONTROL Regel maken]** scherm, selecteren ![Toevoegen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Toevoegen]** naast **[!UICONTROL Mobiele kern - Voorgrond]**.
   ![Volgende gebeurtenisconfiguratie](assets/rule-event-configuration-next.png)
1. In de **[!UICONTROL Gebeurtenisconfiguratie]** stap:
   1. Selecteren **[!UICONTROL Mobiele kern]** als de **[!UICONTROL Extensie]**.
   1. Selecteren **[!UICONTROL Achtergrond]** als de **[!UICONTROL Type gebeurtenis]**.
   1. Selecteren **[!UICONTROL Wijzigingen behouden]**.
      ![Configuratie van regelgebeurtenissen](assets/rule-event-configuration-background.png)
1. Terug in de **[!UICONTROL Regel maken]** scherm, selecteren ![Toevoegen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Toevoegen]** ondergronds **[!UICONTROL ACTIES]**.
   ![Handeling voor toevoegen regel](assets/rule-action-button.png)
1. In de **[!UICONTROL Configuratie van handelingen]** stap:
   1. Selecteren **[!UICONTROL Adobe Experience Edge Network]** als de **[!UICONTROL Extensie]**.
   1. Selecteren **[!UICONTROL Door gebeurtenis naar Edge Network]** als de **[!UICONTROL Type handeling]**.
   1. Selecteren **[!UICONTROL Wijzigingen behouden]**.
      ![Configuratie van handelingen regel](assets/rule-action-configuration.png)
1. Selecteren **[!UICONTROL Opslaan in bibliotheek]**.
   ![Regel - Opslaan in bibliotheek](assets/rule-save-to-library.png)
1. Selecteren **[!UICONTROL Opbouwen]** om de bibliotheek opnieuw op te bouwen.
   ![Regel - Opbouwen](assets/rule-build.png)

Zodra u met succes het bezit hebt gebouwd, worden de gebeurtenissen verzonden naar het Netwerk van de Rand van het Platform, en de gebeurtenissen door:sturen aan andere toepassingen en de diensten volgens uw gegevensstroomconfiguratie.

U moet **[!UICONTROL Toepassing sluiten (achtergrond)]** en **[!UICONTROL Toepassing starten (voorgrond)]** gebeurtenissen met XDM-gegevens in Verzekering.

![levenscyclus valideren die naar Platform Edge is verzonden](assets/lifecycle-edge-assurance.png)

>[!SUCCESS]
>
>U hebt nu uw app zo ingesteld dat toepassingsstatusgebeurtenissen (voorgrond, achtergrond) naar het Adobe Experience Platform Edge Network en alle services die u in uw gegevensstroom hebt gedefinieerd, worden verzonden.
>
> Bedankt dat u tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)

Volgende: **[Gebeurtenisgegevens bijhouden](events.md)**
