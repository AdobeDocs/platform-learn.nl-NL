---
title: Developer Console en Postman instellen
seo-title: Set up Developer Console and Postman | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Developer Console en Postman instellen
description: In deze les stelt u een project in in de Adobe Developer Console en biedt u [!DNL Postman] Verzamelingen waarmee u API's voor Platforms kunt gaan gebruiken.
role: Data Architect, Data Engineer
feature: API
jira: KT-4348
thumbnail: 4348-set-up-developer-console-and-postman.jpg
exl-id: 72b541fa-3ea1-4352-b82b-c5b79ff98491
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '1320'
ht-degree: 0%

---

# Ontwikkelaarsconsole instellen en [!DNL Postman]

<!--30min-->

In deze les stelt u een project in in de Adobe Developer Console en downloadt u [!DNL Postman] verzamelingen, zodat u API&#39;s voor Platforms kunt gebruiken.

Om de API-oefeningen in deze zelfstudie te voltooien, [Download de Postman-app voor uw besturingssysteem.](https://www.postman.com/downloads/) Hoewel Postman niet vereist is voor het gebruik van Experience Platform-API&#39;s, maakt het API-workflows eenvoudiger en biedt Adobe Experience Platform tientallen Postman-verzamelingen om u te helpen API-aanroepen uit te voeren en te leren hoe ze werken. De rest van deze zelfstudie gaat uit van enige praktische kennis van Postman. Raadpleeg voor hulp de [Postman-documentatie](https://learning.postman.com/).

Platform is in de eerste plaats gebaseerd op de ingebouwde API. Hoewel er ook interfaceopties zijn voor alle belangrijke taken, kunt u de Platform-API op een bepaald moment gebruiken. U kunt bijvoorbeeld gegevens invoeren, items verplaatsen tussen sandboxen, routinetaken automatiseren of nieuwe functies voor Platforms gebruiken voordat de gebruikersinterface is gemaakt.

**Gegevensarchitecten** en **Gegevensengineers** buiten deze zelfstudie moet mogelijk Platform API worden gebruikt.

## Vereiste machtigingen

In de [Machtigingen configureren](configure-permissions.md) les, plaatst u opstelling alle toegangscontroles die worden vereist om deze les te voltooien.

<!--
* Permission item Sandboxes > `Luma Tutorial`
* Developer-role access to the `Luma Tutorial Platform` product profile
-->

## Adobe Developer-console instellen

Adobe Developer Console is de ontwikkelaarsbestemming om tot Adobe APIs &amp; SDKs toegang te hebben, aan bijna gebeurtenissen in real time te luisteren, functies in runtime in werking te stellen, of plugins of de toepassingen van de Bouwer van de App te bouwen. U gebruikt deze voor toegang tot de Experience Platform-API. Zie voor meer informatie de [Adobe Developer Console-documentatie](https://www.adobe.io/apis/experienceplatform/console/docs.html)

1. Een map op uw lokale computer maken met de naam `Luma Tutorial Assets` voor bestanden die worden gebruikt in de zelfstudie.

1. Open de [Adobe Developer Console](https://console.adobe.io){target="_blank"}

1. Meld u aan en bevestig dat u zich in de juiste organisatie bevindt

1. Selecteren **[!UICONTROL Nieuw project maken]** in [!UICONTROL Snel starten] -menu.

   ![Nieuw project maken](assets/adobeio-createNewProject.png)


1. Selecteer in het nieuwe project de optie **[!UICONTROL Project bewerken]** knop
1. Wijzig de **[!UICONTROL Projecttitel]** tot `Luma Tutorial API Project` (voeg uw naam aan het eind toe, als de veelvoudige mensen van uw bedrijf dit leerprogramma nemen)
1. Selecteren **[!UICONTROL Opslaan]**

   ![Config. Adobe Developer Console Project API](assets/adobeio-renameProject.png)


1. Selecteren **[!UICONTROL API toevoegen]**

   ![Config. Adobe Developer Console Project API](assets/adobeio-addAPI.png)

1. Filter de lijst door **[!UICONTROL Adobe Experience Platform]**

1. Selecteer in de lijst met beschikbare API&#39;s de optie **[!UICONTROL Experience Platform-API]** en selecteert u **[!UICONTROL Volgende]**.

   ![Config. Adobe Developer Console Project API](assets/adobeio-AEPAPI.png)

1. Selecteren **[!UICONTROL Server-naar-server]** als referentie en selecteer **[!UICONTROL Volgende]**.
   ![OAuth Server-aan-Server selecteren](assets/adobeio-choose-auth.png)

1. Selecteer `AEP-Default-All-Users` productprofiel en selecteer **[!UICONTROL Configureerde API opslaan]**

   ![Productprofiel selecteren](assets/adobeio-selectProductProfile.png)

1. Nu is uw project voor de ontwikkelaarsconsole gemaakt!

1. In de **[!UICONTROL Uitproberen]** van de pagina selecteert u **[!UICONTROL Downloaden naar Postman]** en selecteer vervolgens **[!UICONTROL Server-naar-server]** om de [!DNL Postman] milieu-json-bestand. Sla de `oauth_server_to_server.postman_environment.json` in uw `Luma Tutorial Assets` map.


   ![Config. Adobe Developer Console Project API](assets/adobeio-io-api.png)

## Systeembeheerder de API-referentie aan de rol toevoegen

Als u de API-referentie wilt gebruiken voor interactie met het Experience Platform, moet u een System Admin (Systeembeheer) de API-referenties toewijzen aan de rol die in de vorige les is gemaakt.  Als u geen Systeembeheerder bent, verzendt u deze:

1. De [!UICONTROL Naam] van uw API-referentie (`Credential in Luma Tutorial API Project`)
1. De [!UICONTROL E-mail technische account] van uw referentie (dit zal System Admin helpen de referentie vinden)

   ![[!UICONTROL Naam] en [!UICONTROL E-mail technische account] van uw referentie](assets/postman-credentialDetails.png)

Hier volgen de instructies voor de systeembeheerder:

1. Aanmelden [Adobe Experience Platform](https://platform.adobe.com)
1. Selecteren **[!UICONTROL Machtigingen]** in de linkernavigatie die u naar [!UICONTROL Rollen] scherm
1. Open de `Luma Tutorial Platform` rol
   ![De rol openen](assets/postman-openRole.png)
1. Selecteer **[!UICONTROL API-referenties]** tab
1. Selecteren **[!UICONTROL API-referenties toevoegen]**
   ![Credentials toevoegen](assets/postman-addCredential.png)
1. Zoek de `Credential in Luma Tutorial API Project` referentie, filteren met de [!UICONTROL E-mail technische account] verstrekt door de tutorial deelnemer, als de lijst lang is
1. Selecteer de referentie
1. Selecteren **[!UICONTROL Opslaan]**


   ![Credentials toevoegen](assets/postman-findCredential.png)

## Postman instellen

>[!CAUTION]
>
>De Postman-interface wordt regelmatig bijgewerkt. De schermafbeeldingen in deze zelfstudie zijn gemaakt met Postman 10.15.1 voor Mac, maar de interfaceopties zijn mogelijk gewijzigd.


1. Downloaden en installeren [[!DNL Postman]](https://www.postman.com/downloads/)
1. Openen [!DNL Postman] en een werkruimte maken
   ![Importomgeving](assets/postman-createWorkspace.png)

1. Importeer het gedownloade JSON-omgevingsbestand. `oauth_server_to_server.postman_environment.json`
   ![Importomgeving](assets/postman-importEnvironment.png)
1. In [!DNL Postman]selecteert u de omgeving in het vervolgkeuzemenu

1. Selecteer het pictogram om de omgevingsvariabelen weer te geven:

   ![Omgeving wijzigen](assets/postman-changeEnvironment.png)


### Sandbox-naam en Tenant-id toevoegen

De `SANDBOX_NAME` en `TENANT_ID` en `CONTAINER_ID` De variabelen worden niet opgenomen in de Adobe Developer Console-export en dus voegen we ze handmatig toe:

1. In [!DNL Postman], opent u de **Omgevingsvariabelen**
1. Selecteer **Bewerken** koppeling rechts van de naam van de omgeving
1. In de **Nieuw veld voor variabele toevoegen**, enter `SANDBOX_NAME`
1. Voer in beide waardevelden `luma-tutorial`, de naam die we in de vorige les aan onze sandbox gaven. Als u een andere naam hebt gebruikt voor uw sandbox, bijvoorbeeld luma-tutorial-ignatiusjreilly, moet u die waarde gebruiken.
1. In de **Nieuw veld voor variabele toevoegen**, enter `TENANT_ID`
1. Ga naar uw webbrowser en zoek de huurder-id van uw bedrijf op door naar de interface van het Experience Platform te gaan en het gedeelte van de URL te extraheren *na het @-teken*. Mijn huurder-id is bijvoorbeeld `techmarketingdemos` maar de uwe is anders :

   ![Het verkrijgen van huurder identiteitskaart van de interface URL van het Platform](assets/postman-getTenantId.png)

1. Deze waarde kopiëren en terugkeren naar de [!DNL Postman] Het scherm Omgevingen beheren
1. Plak de id van de huurder in beide waardevelden
1. In de **Nieuw veld voor variabele toevoegen**, enter `CONTAINER_ID`
1. Enter `global` in beide waardevelden

   >[!NOTE]
   >
   >`CONTAINER_ID` is een veld waarvan de waarde tijdens de zelfstudie meerdere keren wordt gewijzigd. Wanneer `global` wordt gebruikt, communiceert API met Adobe-Geleverde elementen in uw Platform rekening. Wanneer `tenant` wordt gebruikt, communiceert de API met uw eigen aangepaste elementen.

1. Selecteren **Opslaan**

   ![SANDBOX_NAME, TENANT_ID en CONTAINER_ID velden toegevoegd als omgevingsvariabelen](assets/postman-addEnvFields.png)



## API-aanroepen maken

### Een toegangstoken ophalen

Adobe biedt een uitgebreide set [!DNL Postman] verzamelingen waarmee u de API van het Experience Platform kunt verkennen. Deze verzamelingen bevinden zich in de [Adobe Experience Platform Postman Samples GitHub repo](https://github.com/adobe/experience-platform-postman-samples). U zou referentie deze repo aangezien u dit vele tijden door dit leerprogramma en later zult gebruiken aangezien u Experience Platform voor uw eigen bedrijf uitvoert.

De eerste verzameling werkt met de Adobe Identity Management Service (IMS)-API&#39;s. Het is een handige manier om een toegangstoken op te halen vanuit Postman.

Om het toegangstoken te produceren:

1. Download de [Identity Management Service APIs-collectie](https://github.com/adobe/experience-platform-postman-samples/blob/master/apis/ims/Identity%20Management%20Service.postman_collection.json) aan uw `Luma Tutorial Assets` map
1. De verzameling importeren in [!DNL Postman]
1. Selecteer de aanvraag **Auth: Toegangstoken aanvragen** aanvragen en selecteren **Verzenden**
1. U moet een `200 OK` reactie met een toegangstoken in de reactie

   ![Tokens aanvragen](assets/postman-requestToken.png)

1. Het toegangstoken zou automatisch als **ACCESS_TOKEN** omgevingsvariabele van uw [!DNL Postman] milieu.

   ![Postman](assets/postman-config.png)


### Interactie met een Platform-API

Nu maken een Platform API vraag om te bevestigen dat wij alles correct hebben gevormd.

Open de [Experience Platform [!DNL Postman] verzamelingen in GitHub](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform). Deze pagina bevat veel verzamelingen voor verschillende Platform-API&#39;s. Ik beveel ten stelligste aan dat er een bladwijzer wordt gemaakt.

Nu, maken onze eerste API vraag:

1. Download de [Schema Registry API collectie](https://raw.githubusercontent.com/adobe/experience-platform-postman-samples/master/apis/experience-platform/Schema%20Registry%20API.postman_collection.json) aan uw `Luma Tutorial Assets` map
1. Importeren in [!DNL Postman]
1. Openen **Schema Registry API > Schema&#39;s > Lijstschema&#39;s**
1. Kijk naar de **Params** en **Kopteksten** tabs en noteren hoe ze enkele omgevingsvariabelen bevatten die we eerder hebben ingevoerd.
1. De **Headers > Accepteren, waardeveld** is ingesteld op `application/vnd.adobe.xed-id+json`. De API&#39;s voor schemaregistratie vereisen een van deze [opgegeven headerwaarden accepteren](https://experienceleague.adobe.com/docs/experience-platform/xdm/api/getting-started.html?lang=en#accept) die verschillende formaten in de reactie verstrekken.
1. Selecteren **Verzenden** om uw eerste Platform API-aanroep te maken!

Hopelijk is het gelukt `200 OK` reactie met een lijst van de beschikbare Adobe-Geleide schema&#39;s XDM in uw zandbak, zoals hieronder afgebeeld.

![Eerste API-aanroep in Postman](assets/postman-firstAPICall.png)

Als uw vraag niet succesvol was, neem een ogenblik om het gebruiken van de details van de foutenreactie van de API vraag te zuiveren en de stappen hierboven te herzien. Als u vast komt te zitten, vraagt u dan om hulp in de [Forum van de Gemeenschap](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform/ct-p/adobe-experience-platform-community) U kunt ook de koppeling rechts van deze pagina gebruiken om een uitgave vast te leggen.

Met uw Platform toestemmingen, zandbak, en [!DNL Postman] instellen, kunt u [modelgegevens in schema&#39;s](model-data-in-schemas.md)!
