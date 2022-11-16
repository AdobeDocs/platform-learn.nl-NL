---
title: Een sandbox maken
seo-title: Create a sandbox | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Een sandbox maken
description: In deze les maakt u een sandbox voor de ontwikkelomgeving die u voor de rest van de zelfstudie kunt gebruiken.
role: Data Architect, Data Engineer
feature: Sandboxes
kt: 4348
thumbnail: 4348-create-a-sandbox.jpg
exl-id: a04afada-52a1-4812-8fa2-14be72e68614
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Een sandbox maken

<!--25min-->

In deze les maakt u een sandbox voor de ontwikkelomgeving die u voor de rest van de zelfstudie wilt gebruiken.

Sandboxen bieden geïsoleerde omgevingen waarin u functionaliteit kunt uitproberen zonder bronnen en gegevens te combineren met uw productieomgeving. Zie voor meer informatie de [sandboxdocumentatie](https://experienceleague.adobe.com/docs/experience-platform/sandbox/home.html).

**Gegevensarchitecten** en **Gegevensengineers** moet buiten deze zelfstudie sandboxen maken.

Voordat u de oefeningen start, bekijkt u deze korte video voor meer informatie over sandboxen:
>[!VIDEO](https://video.tv.adobe.com/v/29838/?quality=12&learn=on)

## Vereiste machtigingen

In de [Machtigingen configureren](configure-permissions.md) les, plaatst u opstelling alle toegangscontroles die worden vereist om deze les te voltooien.

<!--
* Permission items **[!UICONTROL Sandbox Administration]** > **[!UICONTROL View Sandboxes]** and **[!UICONTROL Manage Sandboxes]**
* Permission item **[!UICONTROL Sandboxes]** > **[!UICONTROL Prod]**
* User-role access to the `Luma Tutorial Platform` product profile
* Admin-level access to the `Luma Tutorial Platform` product profile
-->

## Een sandbox maken

Laten we een sandbox maken:

1. Aanmelden bij [Adobe Experience Platform](https://experience.adobe.com/platform) interface
1. Ga naar **[!UICONTROL Sandboxen]** in de linkernavigatie
1. Selecteren **[!UICONTROL Sandbox maken]** rechtsboven
   ![Sandbox maken selecteren](assets/sandbox-createSandbox.png)

1. Selecteren **[!UICONTROL Ontwikkeling]** als de **[!UICONTROL Type]**
1. Geef uw sandbox een naam `luma-tutorial` (Denk na toevoegend uw naam aan het eind)
1. Titel uw zelfstudie `Luma Tutorial` (Denk na toevoegend uw naam aan het eind)
1. Selecteer **[!UICONTROL Maken]** knop
   ![Uw sandbox maken](assets/sandbox-nameSandbox.png)
   >[!NOTE]
   >
   >Hoewel u willekeurige waarden kunt gebruiken voor de naam en de titel van uw sandbox, wordt het aanbevolen de voorgestelde waarden in acht te nemen, omdat we in de zelfstudie naar deze labels zullen verwijzen. Als er meerdere personen in uw organisatie zijn die deze zelfstudie voltooien, kunt u uw naam aan het einde van de sandboxtitel en -naam toevoegen, bijvoorbeeld luma-tutorial-ignatiusjreilly.

Het maken van sandboxen duurt ongeveer 30 seconden, gedurende welke tijd een &quot;[!UICONTROL Maken]&quot; weergegeven. Wanneer de sandbox volledig is gemaakt, wordt deze weergegeven als &quot;[!UICONTROL Actief]&quot;:
![Actieve status](assets/sandbox-active.png)

Wacht tot uw sandbox &quot;[!UICONTROL Actief]&quot; voordat u doorgaat met de volgende oefening.

## De nieuwe sandbox toevoegen aan het productprofiel

Wanneer de sandbox actief is, moet u deze in uw productprofiel opnemen om deze te kunnen gebruiken. Zo voegt u het toe aan uw productprofiel:

1. Meld u aan bij het tabblad [Admin Console](https://adminconsole.adobe.com)
1. Ga naar **[!UICONTROL Producten > Adobe Experience Platform]**
1. Open de `Luma Tutorial Platform` profiel

   ![Selecteer het productprofiel](assets/sandbox-selectProfile.png)

1. Ga naar de **[!UICONTROL Machtigingen]** tab

1. Op de [!UICONTROL Sandboxen] rij, selecteren **[!UICONTROL Bewerken]**

   ![Bewerken selecteren](assets/sandbox-selectSandboxes.png)

1. _Verwijderen_ de **[!UICONTROL Prod]** sandbox die u oorspronkelijk aan het profiel hebt toegewezen
1. Selecteer **[!UICONTROL +]** pictogram om de nieuwe `Luma Tutorial` sandbox naar rechterkolom
1. Selecteren **[!UICONTROL Opslaan]** om de bijgewerkte machtigingen op te slaan

   ![De sandbox naar de andere kolom verplaatsen](assets/sandbox-addLumaTutorial.png)

1. Ga terug naar het browsertabblad met Experience Platform
1. Laad de pagina opnieuw (of houd Shift ingedrukt en laad de pagina opnieuw). U moet nu ofwel in het deelvenster `Luma Tutorial` sandbox of wordt weergegeven in de vervolgkeuzelijst van de sandbox
1. Naar de `Luma Tutorial` sandbox als u er nog niet in bent

   ![Sandbox bevestigen](assets/sandbox-confirmDropdown.png)

Geweldig, u hebt uw sandbox gemaakt en bent klaar om [Developer Console en Postman instellen](set-up-developer-console-and-postman.md)!
