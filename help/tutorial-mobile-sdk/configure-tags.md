---
title: Een eigenschap voor tags configureren voor Platform Mobile SDK-implementaties
description: Leer hoe u een eigenschap tag in de interface [!UICONTROL Data Collection] configureert.
feature: Mobile SDK,Tags
jira: KT-14626
exl-id: 0c4b00cc-34e3-4d08-945e-3fd2bc1b6ccf
source-git-commit: 008d3ee066861ea9101fe9fe99ccd0a088b63f23
workflow-type: tm+mt
source-wordcount: '1036'
ht-degree: 1%

---

# Een eigenschap voor een tag configureren

Leer hoe u een eigenschap tag in de interface [!UICONTROL Data Collection] configureert.

Tags in Adobe Experience Platform zijn de volgende generatie mogelijkheden voor tagbeheer van Adobe. Met labels kunnen klanten eenvoudig analyses, marketing en advertentietags implementeren en beheren die nodig zijn om relevante klantervaringen te stimuleren. Leer meer over [ Markeringen ](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home) in de productdocumentatie.

## Vereisten

Om de les te voltooien, moet u toestemming hebben om een markeringsbezit tot stand te brengen. Het is ook nuttig om basislijninzicht in markeringen te hebben.

>[!NOTE]
>
> Platform Launch (Kant van de Cliënt) is nu [ Markeringen ](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)

## Leerdoelstellingen

In deze les zult u:

* Installeer en configureer de extensies voor mobiele tags.
* Genereer de SDK-installatie-instructies.

## Eerste configuratie

1. Maak een nieuwe eigenschap voor mobiele tags in de interface voor gegevensverzameling:
   1. Selecteer **[!UICONTROL Tags]** in de linkernavigatie.
   1. Selecteren **[!UICONTROL New Property]**
      ![ creeer een markeringsbezit ](assets/tags-new-property.png){zoomable="yes"}.
   1. Voer bij **[!UICONTROL Name]** `Luma Mobile App Tutorial` in.
   1. Selecteer **[!UICONTROL Platform]** voor **[!UICONTROL Mobile]** .
   1. Selecteer **[!UICONTROL Save]** .

      ![ vorm het markeringsbezit ](assets/tags-property-config.png){zoomable="yes"}

      >[!NOTE]
      >
      > Standaardinstellingen voor toestemming voor de op randen gebaseerde mobiele SDK-implementaties, zoals de toestemming die u in deze les doet, zijn afkomstig van de instelling [!UICONTROL Consent extension] en niet van de instelling [!UICONTROL Privacy] in de configuratie van de eigenschap Tag. U voegt en vormt de uitbreiding van de Toestemming later in deze les toe. Voor meer info, zie [ de documentatie ](https://developer.adobe.com/client-sdks/edge/consent-for-edge-network/).


1. Open de nieuwe eigenschap.
1. Een bibliotheek maken:

   1. Ga naar **[!UICONTROL Publishing Flow]** in de linkernavigatie.
   1. Selecteer **[!UICONTROL Add Library]**.

      ![ Uitgezocht voeg Bibliotheek ](assets/tags-create-library.png){zoomable="yes"} toe

   1. Voer bij **[!UICONTROL Name]** `Initial Build` in.
   1. Selecteer **[!UICONTROL Environment]** voor **[!UICONTROL Development (development)]** .
   1. Selecteer ![ toevoegen knoop ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **[!UICONTROL Add All Changed Resources]**.
   1. Selecteer **[!UICONTROL Save and Build to Development]**.

      ![ bouwt de Bibliotheek ](assets/tags-save-library.png){zoomable="yes"}

   1. Selecteer ten slotte **[!UICONTROL Initial Build]** als werkbibliotheek in het menu **[!UICONTROL Select a working library]** .
      ![ Uitgezocht als het werk bibliotheek ](assets/tags-working-library.png){zoomable="yes"}
1. Extensies controleren:

   1. Zorg ervoor dat **[!UICONTROL Initial Build]** is geselecteerd als de standaardbibliotheek.

   1. Selecteer **[!UICONTROL Extensions]** in het linkerspoor.

   1. Selecteer het tabblad **[!UICONTROL Installed]**. 

      De extensies [!UICONTROL Mobile Core] en [!UICONTROL Profile] moeten vooraf zijn geïnstalleerd.

      ![ geïnstalleerde Markeringen ](assets/tags-installed.png){zoomable="yes"}

## Extensieconfiguratie

1. Zorg ervoor dat u zich in **[!UICONTROL Extensions]** bevindt binnen de eigenschap voor uw mobiele app.

1. Selecteer **[!UICONTROL Catalog]**.

   ![ aanvankelijke opstelling ](assets/tags-starting.png){zoomable="yes"}

1. Gebruik het ![ gebied van het Onderzoek ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Search_18_N.svg) **[!UICONTROL Search]** het vinden van de **uitbreiding van de Identiteit**.

   1. Zoeken naar `Identity` .

   2. Selecteer de extensie **[!UICONTROL Identity]** .

   3. Selecteer **[!UICONTROL Install]**.

      ![ Identiteitsinstallatie ](assets/tags-identity-install.png){zoomable="yes"}

   Voor deze extensie is geen verdere configuratie vereist.

1. Gebruik het ![ gebied van het Onderzoek ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Search_18_N.svg) **[!UICONTROL Search]** om de **Assurance van AEP** uitbreiding te vinden en te installeren.

   Voor deze extensie is geen verdere configuratie vereist.

1. Gebruik het ![ gebied van het Onderzoek ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Search_18_N.svg) **[!UICONTROL Search]** om de **toestemming** uitbreiding te vinden en te installeren. In het configuratiescherm:

   1. Selecteer **[!UICONTROL Pending]**. In deze zelfstudie beheert u de toestemming verder in de toepassing. Leer meer over de uitbreiding van de Toestemming in [ de documentatie ](https://developer.adobe.com/client-sdks/documentation/consent-for-edge-network/).
   1. Selecteer **[!UICONTROL Save to Library]**.

      ![ toestemmingsmontages ](assets/tags-extension-consent.png){zoomable="yes"}

1. Gebruik het ![ gebied van het Onderzoek ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Search_18_N.svg) **[!UICONTROL Search]** om de **Edge Network van Adobe Experience Platform** uitbreiding te vinden en te installeren.

   1. In **[!UICONTROL Datastreams]** selecteer **[!UICONTROL Datastream]** dat u in de [ vorige stap ](create-datastream.md) voor elk van de milieu&#39;s, bijvoorbeeld **[!DNL Luma Mobile App]** creeerde.

   1. Als deze nog niet is gevuld, geeft u de **[!UICONTROL Edge Network domain]** within **[!UICONTROL Domain Configuration]** op. Het Edge Network-domein is de naam van uw organisatie, gevolgd door `data.adobedc.net`, bijvoorbeeld `techmarketingdemos.data.adobedc.net` .

   1. Selecteer **[!UICONTROL Save to Library]** in het menu **[!UICONTROL Save to Library and Build]** .

      ![ de montages van het randnetwerk ](assets/tags-extension-edge.png){zoomable="yes"}

Uw bibliotheek is gemaakt voor de nieuwe extensies en configuraties. Een <span style="color:green">●</span> in de knop **[!UICONTROL Initial Build]** geeft aan dat de build is gelukt.


## SDK-installatie-instructies genereren

Tags bieden u instructies en codefragmenten om de Adobe Experience Platform Mobile SDK in uw app te installeren.

>[!BEGINTABS]

>[!TAB  iOS ]

1. Selecteer **[!UICONTROL Environments]** in het linkerspoor.

1. Selecteer **[!UICONTROL Development]** installeer pictogram ![ Doos ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg).

   ![ milieu&#39;s het homescherm ](assets/tags-environments.png){zoomable="yes"}

1. Selecteer de tab **[!UICONTROL Mobile Install Instructions]** in het dialoogvenster **[!UICONTROL iOS]** .

1. U kunt ![ Exemplaar ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) de instructies aan opstelling uw project kopiëren gebruikend CocoaPods. CocoaPods worden gebruikt om SDK-versies en -downloads te beheren. Om meer te leren, te herzien gelieve de [ documentatie CocoaPods ](https://cocoapods.org/).

   [ installeert instructies ](https://developer.adobe.com/client-sdks/documentation/getting-started/get-the-sdk/) verstrekt u een goed uitgangspunt voor implementatie.

   Voor de rest van dit leerprogramma, bent u **niet** gebruikend de instructies CocoaPods. In plaats daarvan gebruikt u de native Swift Package Manager (SPM)-gebaseerde setup.

1. Selecteer de tab **[!UICONTROL Swift]** onder **[!UICONTROL Add Initialization Code]** . Dit codeblok laat zien hoe u de vereiste SDK&#39;s kunt importeren en de extensies kunt registreren bij het starten. Deze invoer en registratie wordt behandeld meer in detail in [ installeert SDKs ](install-sdks.md).

1. Het exemplaar ![ Exemplaar ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) **[!UICONTROL Environment File ID]** en slaat het op een plaats op aangezien u het later nodig hebt. Deze unieke id verwijst naar uw ontwikkelomgeving. Elke omgeving (Productie, Staging, Ontwikkeling) heeft zijn eigen unieke id-waarde.

   ![ installeer instructies ](assets/tags-install-instructions.png){zoomable="yes"}

>[!TAB  Android ]

1. Selecteer **[!UICONTROL Environments]** in het linkerspoor.
1. Selecteer **[!UICONTROL Development]** installeer pictogram ![ Doos ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Box_18_N.svg).

   ![ milieu&#39;s het homescherm ](assets/tags-environments.png){zoomable="yes"}

1. Selecteer de tab **[!UICONTROL Mobile Install Instructions]** in het dialoogvenster **[!UICONTROL Android]** .
1. U kunt ![ Exemplaar ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) de instructies aan opstelling uw project kopiëren gebruikend Gradle. Gradle wordt gebruikt om SDK-versies en -downloads te beheren. Om meer te leren, te herzien gelieve de [ documentatie van de Gradle ](https://gradle.org/)

   [ installeert instructies ](https://developer.adobe.com/client-sdks/documentation/getting-started/get-the-sdk/) verstrekt u een goed uitgangspunt voor implementatie.

1. Dit codeblok laat zien hoe u de vereiste SDK&#39;s kunt importeren en de extensies kunt registreren bij het starten. Deze invoer en registratie wordt behandeld meer in detail in [ installeert SDKs ](install-sdks.md).

1. Het exemplaar ![ Exemplaar ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) **[!UICONTROL Environment File ID]** en slaat het op een plaats op aangezien u het later nodig hebt. Deze unieke id verwijst naar uw ontwikkelomgeving. Elke omgeving (Productie, Staging, Ontwikkeling) heeft zijn eigen unieke id-waarde.

   ![ installeer instructies ](assets/tags-install-instructions-android.png){zoomable="yes"}

>[!ENDTABS]

>[!NOTE]
>
>De installatie-instructies moeten worden beschouwd als een beginpunt en niet als definitieve documentatie. De recentste versies van SDK en codesteekproeven kunnen in de officiële [ documentatie ](https://developer.adobe.com/client-sdks/home/) worden gevonden.

## Architectuur van mobiele tags

Als u bekend bent met de webversie van Tags, voorheen Starten, is het belangrijk dat u de verschillen op mobiele apparaten begrijpt.

* Op het web wordt een tag-eigenschap gerenderd naar JavaScript die vervolgens (gewoonlijk) wordt gehost in de cloud. Er wordt rechtstreeks in de website naar dat JavaScript-bestand verwezen.

* In een eigenschap voor mobiele tags worden regels en configuraties gerenderd in JSON-bestanden die worden gehost in de cloud. De JSON-bestanden worden gedownload en gelezen door de Mobile Core-extensie in de mobiele app. Extensies zijn afzonderlijke SDK&#39;s die samenwerken. Als u een extensie toevoegt aan de eigenschap tag, moet u de app ook bijwerken. Als u een extensie-instelling wijzigt of een regel maakt, worden deze wijzigingen doorgevoerd in de app nadat u de bijgewerkte tagbibliotheek hebt gepubliceerd. Dankzij deze flexibiliteit kunt u instellingen wijzigen (zoals Adobe Analytics-rapportsuite-id). U kunt ook het gedrag van uw app wijzigen (met gegevenselementen en regels, zoals u in latere lessen ziet) zonder de code in uw app te wijzigen en opnieuw naar de App Store te verzenden.

>[!SUCCESS]
>
>U kunt nu een eigenschap voor mobiele tags gebruiken in de rest van deze zelfstudie.
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren van Adobe Experience Platform Mobile SDK. Als u vragen hebt, algemene terugkoppelen willen delen, of suggesties over toekomstige inhoud hebben, hen op deze [ Communautaire besprekingspost van Experience League ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796) delen

Volgende: **[installeer SDKs](install-sdks.md)**
