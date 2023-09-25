---
title: Een sandbox maken
seo-title: Create a sandbox | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Een sandbox maken
description: In deze les maakt u een sandbox voor de ontwikkelomgeving die u voor de rest van de zelfstudie kunt gebruiken.
role: Data Architect, Data Engineer
feature: Sandboxes
jira: KT-4348
thumbnail: 4348-create-a-sandbox.jpg
exl-id: a04afada-52a1-4812-8fa2-14be72e68614
source-git-commit: 00ef0f40fb3d82f0c06428a35c0e402f46ab6774
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 1%

---

# Een sandbox maken

<!--25min-->

In deze les maakt u een sandbox voor de ontwikkelomgeving die u voor de rest van de zelfstudie wilt gebruiken.

Sandboxen bieden geïsoleerde omgevingen waarin u functionaliteit kunt uitproberen zonder bronnen en gegevens te combineren met uw productieomgeving. Zie voor meer informatie de [sandboxdocumentatie](https://experienceleague.adobe.com/docs/experience-platform/sandbox/home.html?lang=nl).

**Gegevensarchitecten** en **Gegevensengineers** moet buiten deze zelfstudie sandboxen maken.

Voordat u de oefeningen start, bekijkt u deze korte video voor meer informatie over sandboxen:
>[!VIDEO](https://video.tv.adobe.com/v/29838/?learn=on)

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
1. Selecteer de **[!UICONTROL Maken]** knop
   ![Uw sandbox maken](assets/sandbox-nameSandbox.png)
   >[!NOTE]
   >
   >Hoewel u willekeurige waarden kunt gebruiken voor de naam en de titel van uw sandbox, wordt het aanbevolen de voorgestelde waarden in acht te nemen, omdat we in de zelfstudie naar deze labels zullen verwijzen. Als er meerdere personen in uw organisatie zijn die deze zelfstudie voltooien, kunt u uw naam aan het einde van de sandboxtitel en -naam toevoegen, bijvoorbeeld luma-tutorial-ignatiusjreilly.

Het maken van sandboxen duurt ongeveer 30 seconden, gedurende welke tijd een &quot;[!UICONTROL Maken]&quot; weergegeven. Wanneer de sandbox volledig is gemaakt, wordt deze weergegeven als &quot;[!UICONTROL Actief]&quot;:
![Actieve status](assets/sandbox-active.png)

Wacht tot uw sandbox &quot;[!UICONTROL Actief]&quot; voordat u doorgaat met de volgende oefening.

## De nieuwe sandbox toevoegen aan de rol

Wanneer de sandbox actief is, moet u deze in uw rol opnemen om deze te kunnen gebruiken. Als u deze aan uw rol wilt toevoegen (hiervoor hebt u systeembeheer of productbeheerdersrechten nodig):

1. Ga naar de [!UICONTROL Machtigingen] scherm
1. Open de `Luma Tutorial Platform` rol
1. Optioneel _remove_ de `Prod` sandbox van de rol
1. Voeg de `Luma Tutorial` sandbox
1. Selecteren **[!UICONTROL Opslaan]**
1. Op de [!UICONTROL Sandboxen] rij, selecteren **[!UICONTROL Bewerken]**

   ![Luminantieleiding toevoegen](assets/sandbox-addLumaTutorial.png)

1. Laad de pagina opnieuw (of houd Shift ingedrukt en laad de pagina opnieuw). U moet nu ofwel in het deelvenster `Luma Tutorial` sandbox of wordt weergegeven in de vervolgkeuzelijst van de sandbox
1. Schakel over naar de `Luma Tutorial` sandbox als u er nog niet in bent

   ![Sandbox bevestigen](assets/sandbox-confirmDropdown.png)

Geweldig, u hebt uw sandbox gemaakt en bent klaar om [Developer Console en Postman instellen](set-up-developer-console-and-postman.md)!
