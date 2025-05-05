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
source-git-commit: 286c85aa88d44574f00ded67f0de8e0c945a153e
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Een sandbox maken

<!--25min-->

In deze les maakt u een sandbox voor de ontwikkelomgeving die u voor de rest van de zelfstudie wilt gebruiken.

Sandboxen bieden geïsoleerde omgevingen waarin u functionaliteit kunt uitproberen zonder bronnen en gegevens te combineren met uw productieomgeving. Voor meer details, zie de [ zandbakdocumentatie ](https://experienceleague.adobe.com/docs/experience-platform/sandbox/home.html?lang=nl).

**de Architecten van Gegevens 0&rbrace; en** Ingenieurs van Gegevens **zullen zandbakken buiten dit leerprogramma moeten tot stand brengen.**

Voordat u de oefeningen start, bekijkt u deze korte video voor meer informatie over sandboxen:
>[!VIDEO](https://video.tv.adobe.com/v/29838/?learn=on&enablevpops)

## Vereiste machtigingen

In [ vorm toestemmingen ](configure-permissions.md) les, u opstelling alle toegangscontroles die worden vereist om deze les te voltooien.

<!--
* Permission items **[!UICONTROL Sandbox Administration]** > **[!UICONTROL View Sandboxes]** and **[!UICONTROL Manage Sandboxes]**
* Permission item **[!UICONTROL Sandboxes]** > **[!UICONTROL Prod]**
* User-role access to the `Luma Tutorial Platform` product profile
* Admin-level access to the `Luma Tutorial Platform` product profile
-->

## Een sandbox maken

Laten we een sandbox maken:

1. Logboek in de [ interface van Adobe Experience Platform ](https://experience.adobe.com/platform)
1. Ga naar **[!UICONTROL Sandboxes]** in de linkernavigatie
1. Selecteren **[!UICONTROL Create sandbox]** rechtsboven
   ![ Uitgezochte creeer zandbak ](assets/sandbox-createSandbox.png)

1. Selecteer **[!UICONTROL Development]** als de **[!UICONTROL Type]**
1. Geef uw sandbox een naam `luma-tutorial` (voeg uw naam aan het einde toe)
1. Titel uw zelfstudie `Luma Tutorial` (voeg uw naam aan het einde toe)
1. Selecteer de knop **[!UICONTROL Create]**
   ![ creeer uw zandbak ](assets/sandbox-nameSandbox.png)
   >[!NOTE]
   >
   >Hoewel u willekeurige waarden kunt gebruiken voor de naam en de titel van uw sandbox, wordt het aanbevolen de voorgestelde waarden in acht te nemen, omdat we in de zelfstudie naar deze labels zullen verwijzen. Als er meerdere personen in uw organisatie zijn die deze zelfstudie voltooien, kunt u uw naam aan het einde van de sandboxtitel en -naam toevoegen, bijvoorbeeld luma-tutorial-ignatiusjreilly.

Het duurt ongeveer 30 seconden om zandbakken tot stand te brengen, waarin tijd &quot;[!UICONTROL Creating]&quot;statusvertoningen. Wanneer de zandbak volledig wordt gecreeerd, toont het als &quot;[!UICONTROL Active]&quot;:
![ Actieve status ](assets/sandbox-active.png)

Wacht tot uw zandbak &quot;[!UICONTROL Active]&quot;alvorens aan de volgende oefening te blijven is.

## De nieuwe sandbox toevoegen aan de rol

Wanneer de sandbox actief is, moet u deze in uw rol opnemen om deze te kunnen gebruiken. Als u deze aan uw rol wilt toevoegen (hiervoor hebt u systeembeheer of productbeheerdersrechten nodig):

1. Naar het [!UICONTROL Permissions] -scherm gaan
1. De rol `Luma Tutorial Platform` openen
1. Naar keuze _verwijdert_ de `Prod` zandbak uit de rol
1. De sandbox `Luma Tutorial` toevoegen
1. Selecteren **[!UICONTROL Save]**
1. Selecteer **[!UICONTROL Edit]** in de [!UICONTROL Sandboxes] -rij

   ![ voeg het Luminantieleerprogramma ](assets/sandbox-addLumaTutorial.png) toe

1. Laad de pagina opnieuw (of houd Shift ingedrukt en laad de pagina opnieuw). U moet nu in de sandbox `Luma Tutorial` staan of deze moet in de vervolgkeuzelijst van de sandbox worden weergegeven
1. Schakel over naar de `Luma Tutorial` -sandbox als deze nog niet aanwezig is

   ![ bevestigt zandbak ](assets/sandbox-confirmDropdown.png)

Groot, hebt u uw zandbak gecreeerd en is klaar aan [ Opstelling Developer Console en Postman ](set-up-developer-console-and-postman.md)!
