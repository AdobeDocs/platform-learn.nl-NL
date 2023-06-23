---
title: Machtigingen configureren
seo-title: Configure permissions | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Machtigingen configureren
description: In deze les, zult u Adobe Experience Platform gebruikerstoestemmingen vormen gebruikend Adobe Admin Console.
role: Data Architect, Data Engineer
feature: Access Control
jira: KT-4348
thumbnail: 4348-configure-permissions.jpg
exl-id: ca01f99e-f10c-4bf0-bef2-b011ac29a565
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '1204'
ht-degree: 1%

---

# Machtigingen configureren

<!--30min-->

In deze les configureert u Adobe Experience Platform-gebruikersmachtigingen met [!DNL Adobe's Admin Console] en de [!UICONTROL Machtigingen] in de interface van het Platform.

Toegangsbeheer is een sleutelfunctie voor privacy in Experience Platform en wij raden u aan de machtigingen tot het minimum te beperken dat vereist is voor het uitvoeren van hun taakfuncties. Zie de [Documentatie over toegangsbeheer](https://experienceleague.adobe.com/docs/experience-platform/access-control/home.html) voor meer informatie .

Data Architects en Data Engineers zijn krachtige gebruikers van Adobe Experience Platform en u hebt veel machtigingen nodig om deze zelfstudie en later in uw dagelijkse werk te kunnen voltooien. Data Architects zijn waarschijnlijk betrokken bij het beheer van *andere gebruikers van Platform* op hun bedrijf, zoals marketers, analisten en data wetenschappers. Aangezien u deze les voltooit, denk over hoe u deze eigenschappen zou kunnen gebruiken om andere gebruikers bij uw bedrijf te beheren.

**Gegevensarchitecten** Vaak vormen toestemmingen voor andere gebruikers buiten dit leerprogramma.

>[!IMPORTANT]
>
>Een beheerder van het Systeem van de producten van Adobe Experience Cloud moet enkele stappen in deze les voltooien, die in de sectiekoppen wordt geroepen. Als u geen Beheerder van het Systeem bent, te bereiken gelieve bij uw bedrijf en hen te vragen deze taken voltooien. Er is ook een taak die zij tijdens [Developer Console en Postman instellen](set-up-developer-console-and-postman.md) les.

## Over de Admin Console

De [!DNL Admin Console] is de interface die wordt gebruikt om gebruikerstoegang tot alle producten van Adobe Experience Cloud te beheren. Voor toegang tot Platform, moet een gebruiker of in de Admin Console worden toegevoegd en dan worden elk van hun korrelige toestemmingspunten beheerd in het scherm van Toestemmingen van Adobe Experience Platform.


Hier volgt een kort overzicht van de rollen die voor Platform bestaan:

* **Gebruikers** van een productprofiel kunnen taken in de gebruikersinterface van het Platform uitvoeren op basis van de machtigingen die in het productprofiel zijn toegewezen.
* **Ontwikkelaars** kan API-referenties en -projecten maken in de Adobe Developer Console, zodat u de Experience Platform API kunt gaan gebruiken
* **Productbeheerders** U kunt gebruikers en ontwikkelaars toevoegen aan het Adobe Experience Platform-product in de Adobe Admin Console en de toegang van gebruikers in korreligheid beheren in het scherm Machtigingen van de interface van het Platform.
* **Systeembeheerders** U kunt productbeheerders toevoegen en in wezen alle machtigingen voor alle Adobe Experience Cloud-producten beheren.

## Een gebruiker en ontwikkelaar toevoegen aan de `AEP-Default-All-Users` productprofiel (vereist een systeembeheerder of productbeheerder)

Hierbij voegt u of een systeembeheerder of productbeheerder u toe als gebruiker en ontwikkelaar in het Adobe Experience Platform-product van de Adobe Admin Console.

>[!NOTE]
>
>Als u een Beheerder van het Systeem bent die een collega bijstaat die deze zelfstudie neemt, denk na toevoegend uw collega als a *Productbeheerder* voor Adobe Experience Platform. Als productbeheerder kunnen ze deze stappen zelfstandig uitvoeren en in de toekomst andere gebruikers in de Experience Platform beheren.

De tutorial-deelnemer toevoegen als een [!UICONTROL Gebruiker] en [!UICONTROL Ontwikkelaar]:

1. Aanmelden bij [Adobe Admin Console](https://adminconsole.adobe.com)
1. Selecteren **[!UICONTROL Producten]** op de bovenste navigatie
1. Selecteren **Adobe Experience Platform**
   ![Adobe Experience Platform selecteren](assets/adminconsole-experiencePlatform.png)
1. U hebt mogelijk al meerdere profielen in uw Experience Platform-instantie. Selecteer `AEP-Default-All-Users` profiel
   ![Selecteer Nieuw profiel toevoegen](assets/adminconsole-newProfile.png)

1. Ga naar de **[!UICONTROL Gebruikers]** tab
1. Selecteer **[!UICONTROL Gebruiker toevoegen]** knop
   ![Gebruiker toevoegen selecteren](assets/adminconsole-addUser.png)
1. Voltooi de workflow om de zelfstudie-deelnemer als gebruiker toe te voegen aan het productprofiel

1. Ga naar de **[!UICONTROL Ontwikkelaars]** tab
1. Selecteer **[!UICONTROL Ontwikkelaar toevoegen]** knop
   ![Gebruiker toevoegen selecteren](assets/adminconsole-addDeveloper.png)
1. Voltooi de workflow om de tutorial deelnemer als ontwikkelaar toe te voegen aan het productprofiel


## Een rol toevoegen in Adobe Experience Platform (hiervoor is een systeembeheerder of productbeheerder vereist)

De korrelige toestemmingen aan Experience Platform worden beheerd in het scherm van Toestemmingen van de interface van het Platform. Alleen systeem- en productbeheerders hebben toegang tot dit scherm, dus als u geen beheerdersrechten hebt, hebt u hulp nodig van iemand die dit doet.

De toestemmingen worden beheerd in Rollen. Een rol maken voor de zelfstudie:

1. Aanmelden [Adobe Experience Platform](https://platform.adobe.com)
1. Selecteren **[!UICONTROL Machtigingen]** in de linkernavigatie die u naar [!UICONTROL Rollen] scherm
1. Selecteren **[!UICONTROL Rol maken]**

   ![Rol maken in Experience Platform](assets/permissions-addRole.png)
1. Naam van de rol `Luma Tutorial Platform` (voeg de naam van de deelnemer aan de zelfstudie toe aan het einde als meerdere personen van uw bedrijf deze zelfstudie volgen) en selecteer **[!UICONTROL Bevestigen]**

   ![Rol maken in Experience Platform](assets/permissions-nameRole.png)


1. Voeg alle toestemmingspunten voor de volgende middelen toe gebruikend  **[!UICONTROL +]** en **[!UICONTROL Alles toevoegen]**:

   1. Gegevensmodellering
   1. Data management
   1. Profielbeheer
   1. Identity Management
   1. Sandbox-beheer
   1. Query-service
   1. Gegevensverzameling
   1. Gegevensbeheer
   1. Dashboards
   1. Waarschuwingen

      ![Machtigingsitems toevoegen](assets/permissions-addPermissionItems.png)

1. Onder de Ingestie van Gegevens, voeg de Manage Bronnen en de punten van de de toestemmingstoestemming van de Mening toe.

1. Nadat u alle machtigingsitems hebt toegevoegd, moet u de knop Opslaan selecteren
   ![Machtigingsitems opslaan](assets/permissions-savePermissions.png)

U zult een paar kleine updates van deze rol na [Een sandbox maken](create-a-sandbox.md) en [Developer Console en Postman instellen](set-up-developer-console-and-postman.md) lessen.

## Een productprofiel voor gegevensverzameling maken (hiervoor is een systeembeheerder of productbeheerder vereist)

In deze oefening, zult u of een Beheerder van het Systeem bij uw bedrijf een productprofiel voor de Inzameling van Gegevens (vroeger genoemd als Adobe Experience Platform Launch) creëren en zult u als beheer van het productprofiel toevoegen.

>[!NOTE]
>
>Als u een Beheerder bent van het Systeem die een collega met deze leerprogramma bijstaat, denk na toevoegend hen als a *Productbeheerder* voor gegevensverzameling. Als Beheerder van het Product, zullen zij deze stappen op hun kunnen voltooien en andere gebruikers van de Inzameling van Gegevens in de toekomst beheren.

Het productprofiel maken:

1. In de [!DNL Adobe Admin Console] Ga naar het Adobe Experience Platform Data Collection-product
1. Een nieuw profiel met de naam toevoegen `Luma Tutorial Data Collection` (voeg de naam van de deelnemer aan de zelfstudie toe aan het einde als meerdere personen van uw bedrijf deze zelfstudie volgen)
1. Schakel de **[!UICONTROL Eigenschappen]** > **[!UICONTROL Automatisch opnemen]** instellen
1. Wijs op dit punt geen eigenschappen of machtigingen toe
1. De tutorial-deelnemer toevoegen als beheerder van dit profiel

Nadat u deze stappen hebt uitgevoerd, dient u te controleren of de `Luma Tutorial Data Collection` -profiel is ingesteld met één beheerder.
![Gegevensverzamelingsprofiel is gemaakt](assets/adminconsole-dc-profileCreated.png)

## Het productprofiel voor gegevensverzameling configureren

Nu bent u beheerder van de `Luma Tutorial Data Collection` productprofiel u kunt de toestemmingen en de rollen vormen u de leerprogramma zult moeten voltooien.

### Machtigingen toevoegen

Nu gaat u de afzonderlijke machtigingsitems toevoegen aan het profiel:

1. In de [Adobe Admin Console](https://adminconsole.adobe.com), ga naar **[!UICONTROL Producten]** > **[!UICONTROL Gegevensverzameling]**
1. Open de `Luma Tutorial Data Collection` profiel
1. Ga naar de **[!UICONTROL Machtigingen]** tab
1. Openen **[!UICONTROL Platforms]**
1. Zorg ervoor dat alle beschikbare platforms zijn geselecteerd (u ziet mogelijk verschillende opties op basis van uw licentie)
1. **[!UICONTROL Opslaan]** alle wijzigingen
   ![Platforms toevoegen](assets/adminconsole-launch-addPlatforms.png)
1. Openen **[!UICONTROL Eigenschappen]**
1. Zorg ervoor dat de **[!UICONTROL Automatisch opnemen]** toggle is Uit zodat u geen toegang tot eigenschappen hebt (wij zullen later toevoegen)
1. **[!UICONTROL Opslaan]** alle wijzigingen
   ![Eigenschappen verwijderen](assets/adminconsole-launch-removeProperties.png)
1. Openen **[!UICONTROL Eigendomsrechten]**
1. Selecteren **[!UICONTROL Alles toevoegen]** om alle eigenschapsmachtigingen toe te voegen
1. **[!UICONTROL Opslaan]**
   ![Eigenschappen verwijderen](assets/adminconsole-launch-addPropertyRights.png)
1. Openen **[!UICONTROL Bedrijfsrechten]**
1. Toevoegen **[!UICONTROL Eigenschappen beheren]**
1. Selecteren **[!UICONTROL Opslaan]**
   ![Eigenschappen verwijderen](assets/adminconsole-launch-companyRights.png)


### uzelf toevoegen als gebruiker

Voeg nu uzelf toe als gebruiker aan het profiel Gegevensverzameling:

1. Ga naar de **[!UICONTROL Gebruikers]** tab
1. Selecteer **[!UICONTROL Gebruiker toevoegen]** knop
   ![Gebruiker toevoegen selecteren](assets/adminconsole-launch-addUser.png)
1. Voltooi de workflow om uzelf als gebruiker toe te voegen aan het productprofiel

U te hoeven niet om zich als Ontwikkelaar voor de Inzameling van Gegevens toe te voegen.

Nu hebt u bijna alle vereiste machtigingen om de zelfstudie te voltooien! Er zullen nog twee tweelingen zijn die je in de [!DNL Adobe Admin Console], inclusief één na u [een sandbox maken](create-a-sandbox.md)!
