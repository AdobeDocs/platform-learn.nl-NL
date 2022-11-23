---
title: Machtigingen voor de zelfstudie configureren
description: Leer hoe te om toegang tot het Web SDK van het Experience Platform te verzoeken en de toestemming te vormen die wordt vereist om Adobe Experience Cloud met het leerprogramma van SDK van het Web te voltooien.
feature: Access Control
exl-id: d7c4f2c3-cf3c-4587-88f8-82113d250084
source-git-commit: 7377d87394d52bc9ed1f35f071a57bc341d5f969
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 2%

---

# Machtigingen voor de zelfstudie configureren

Leer hoe te om toegang tot het Web SDK van het Experience Platform te verzoeken en de toestemming te vormen die wordt vereist om dit leerprogramma te voltooien. Om Platform Web SDK uit te voeren gebruikend markeringen in de interface van de Inzameling van Gegevens, moet u de juiste gebruikerstoestemmingen hebben die binnen worden gevormd [Admin Console](https://adminconsole.adobe.com).

## Gegevensverzameling

* machtiging hebben om **[!UICONTROL Ontwikkelen]**, **[!UICONTROL Bewerken]**, **[!UICONTROL Goedkeuren]**, **[!UICONTROL Publiceren]**, **[!UICONTROL Extensies beheren]**, **[!UICONTROL Omgevingen beheren]**, en **[!UICONTROL Eigenschappen beheren]**. Zie voor meer informatie over labels [de documentatie](https://experienceleague.adobe.com/docs/experience-platform/tags/admin/user-permissions.html).
* Als u de facultatieve gebeurtenis zult voltooien die les door:sturen, een productvergunning hebben die rand door:sturen en toestemmingspunt omvat **[!UICONTROL Platforms]** > **[!UICONTROL Rand]**

## Experience Platform

Deze eigenschappen zouden aan alle klanten van Experience Cloud beschikbaar moeten zijn, zelfs als u geen klant van een op Platform-gebaseerde toepassing zoals in real time CDP bent.

* Toegang tot de **standaardproductie**, **&quot;Prod&quot;** sandbox (.
* Toegang tot **[!UICONTROL Schema&#39;s beheren]** en **[!UICONTROL Schema&#39;s weergeven]** krachtens **[!UICONTROL Gegevensmodellering]**
* Toegang tot **[!UICONTROL Identiteitsnaamruimten beheren]** en **[!UICONTROL Identiteitsnaamruimten weergeven]** krachtens **[!UICONTROL Identity Management]**
* Toegang tot **[!UICONTROL Gegevensstromen beheren]** en **[!UICONTROL Gegevensstromen weergeven]** krachtens **[!UICONTROL Gegevensverzameling]**
* Als u een klant bent van een toepassing op basis van een Platform en u de [Experience Platform instellen](setup-experience-platform.md) les, zou u ook moeten hebben:
   * Toegang tot een **ontwikkeling** sandbox.
   * Alle machtigingsitems onder **[!UICONTROL Gegevensbeheer]**, en **[!UICONTROL Profielbeheer]**:


Voor meer informatie over de toegangscontrole van het Platform, zie [de documentatie](https://experienceleague.adobe.com/docs/experience-platform/access-control/home.html).

## Adobe Analytics

Voor de optionele Adobe Analytics les moet je beschikken over [beheerdersrechten voor de instellingen van de rapportsuite, verwerkingsregels en Analysis Workspace](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html)

## Adobe Target

Voor de optionele Adobe Target les moet je beschikken over [Editor of fiatteur](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html#section_8C425E43E5DD4111BBFC734A2B7ABC80) toegang.

## Adobe Audience Manager

* Voor de facultatieve les van de Audience Manager, moet u toegang hebben tot creeer, lees, en schrijf eigenschappen, segmenten, en bestemmingen. Raadpleeg de zelfstudie over voor meer informatie [Op rol-Gebaseerd Toegangsbeheer van Audience Manager](https://experienceleague.adobe.com/docs/audience-manager-learn/tutorials/setup-and-admin/user-management/setting-permissions-with-role-based-access-control.html?lang=en).

Nu bent u klaar om de eerste configuratiestappen te beginnen.

[Volgende: ](configure-schemas.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over Adobe Experience Platform Web SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
