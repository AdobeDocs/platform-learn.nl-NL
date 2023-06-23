---
title: Identiteiten toewijzen
seo-title: Map identities | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Identiteiten toewijzen
description: In deze les, zullen wij identiteitsnaamruimten creëren en identiteitsgebieden toevoegen aan onze schema's.
role: Data Architect
feature: Profiles
jira: KT-4348
thumbnail: 4348-map-identities.jpg
exl-id: e17ffabc-049c-42ff-bf0a-8cc31d665dfa
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 2%

---

# Identiteiten toewijzen

<!-- 30 min-->

In deze les, zullen wij identiteitsnaamruimten creëren en identiteitsgebieden toevoegen aan onze schema&#39;s. Na het doen van dit, zullen wij ook de schemaverhoudingen van de vorige les kunnen voltooien.

Met de Adobe Experience Platform Identity Service kunt u uw klanten en hun gedrag beter zien door identiteiten tussen apparaten en systemen te overbruggen, zodat u in real-time een indrukwekkende, persoonlijke digitale ervaring kunt bieden. Identiteitsvelden en naamruimten zijn de lijm die verschillende gegevensbronnen samenvoegt om het 360 graden klantenprofiel in real time te bouwen.

**Gegevensarchitecten** moet identiteiten buiten deze zelfstudie toewijzen.

Voordat u de oefeningen start, bekijkt u deze korte video voor meer informatie over identiteit in Adobe Experience Platform:
>[!VIDEO](https://video.tv.adobe.com/v/27841?quality=12&learn=on)

>[!NOTE]
>
>Identiteitsvelden zijn alleen vereist als u realtime klantprofielen maakt. Ze zijn niet vereist als u alleen gegevens in het datumpeer opneemt.

<!--explain identity maps-->
<!--explain the strategy behind the identity selection, how these identities will join all the data together-->

## Vereiste machtigingen

In de [Machtigingen configureren](configure-permissions.md) les, plaatst u opstelling alle toegangscontroles die worden vereist om deze les te voltooien.

<!--
* Permission items **[!UICONTROL Identity Management]** > **[!UICONTROL View Identity Namespaces]** and **[!UICONTROL Manage Identity Namespaces]**
* Permission item **[!UICONTROL Data Modeling]** > **[!UICONTROL View Schemas]** and **[!UICONTROL Manage Schemas]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)
-->

## Naamruimte identiteit maken

Hierbij maken we naamruimten voor aangepaste identiteitsvelden van Luma. `loyaltyId`, `crmId`, en `productSku`. Identiteitsnaamruimten spelen een kritieke rol in de bouw van klantenprofielen in real time, aangezien twee passende waarden in zelfde namespace twee gegevensbronnen toestaan om een identiteitsgrafiek te vormen.


### Naamruimten maken in de gebruikersinterface

Laten we beginnen met het maken van een naamruimte voor het Luma Loyalty-schema:

1. Ga in de gebruikersinterface van het Platform naar **[!UICONTROL Identiteiten]** in de linkernavigatie
1. U zult merken dat er verschillende naamruimten beschikbaar zijn die buiten de box vallen. Selecteer **[!UICONTROL Naamruimte maken]** knop
1. Geef de volgende gegevens op:

   | Veld | Waarde |
   |---------------|-----------|
   | Weergavenaam | Loyalty-id luminantie |
   | Identiteitssymbool | lumaLoyaltyId |
   | Type | Cross-device |

1. Selecteer **[!UICONTROL Maken]**

   ![Naamruimten maken](assets/identity-createNamespace.png)

Stel nu een andere naamruimte in voor het schema Luminageproductcatalogus met de volgende details:

| Veld | Waarde |
|---------------|-----------|
| Weergavenaam | Luma Product SKU |
| Identiteitssymbool | lumaProductSKU |
| Type | Id van niet-personen |



## Identiteitsnaamruimte maken met API

We maken onze CRM-naamruimte via API.

>[!NOTE]
>
>Als u liever de API-oefeningen overslaat, kunt u de CRM-naamruimte vrij maken via de gebruikersinterfacemethode die u met de volgende details hebt gebruikt:
>
> 1. Als de **[!UICONTROL Weergavenaam]**, gebruik `Luma CRM Id`
> 1. Als de **[!UICONTROL Identiteitssymbool]**, gebruik `lumaCrmId`
> 1. Als de **[!UICONTROL Type]**, gebruikt u Cross-device

We maken de naamruimte Identiteit `Luma CRM Id`:

1. Downloaden [Identity Service.postman_collection.json](https://raw.githubusercontent.com/adobe/experience-platform-postman-samples/master/apis/experience-platform/Identity%20Service.postman_collection.json) aan uw `Luma Tutorial Assets` map
1. De verzameling importeren in [!DNL Postman]
1. Als u geen toegangstoken hebt, open het verzoek **[!DNL OAuth: Request Access Token]** en selecteert u **Verzenden** om een nieuw toegangstoken aan te vragen.
1. Selecteer de aanvraag **[!UICONTROL Identiteitsservice] > [!UICONTROL Naamruimte van identiteit] > [!UICONTROL Een nieuwe naamruimte maken].**
1. Plak het volgende als de [!DNL Body] van het verzoek:

   ```json
   {
       "name": "Luma CRM Id",
       "code": "lumaCrmId",
       "idType": "Cross_device"
   }
   ```

1. Druk op **Verzenden** en u moet een **200 OK** reactie:

   ![Naamruimte van identiteit](assets/identity-createUsingApi.png)

Als u terugkeert naar de gebruikersinterface, zou u uw drie nieuwe douanenamespaces nu moeten zien:
![Naamruimte van identiteit ](assets/identity-newIdentities.png)


## Identiteitsvelden in schema&#39;s labelen

Nu we onze naamruimten hebben, bestaat de volgende stap uit het bijwerken van onze schema&#39;s om onze identiteitsvelden een label te geven.


### XDM-velden labelen voor primaire identiteit

Elk schema dat met het Profiel van de Klant in real time wordt gebruikt wordt vereist om een primaire gespecificeerde identiteit te hebben. Elke opgenomen record moet een waarde voor dat veld hebben.

Laten we een primaire identiteit toevoegen aan de `Luma Loyalty Schema`:

1. Open de `Luma Loyalty Schema`
1. Selecteer het `Luma Identity profile field group`
1. Selecteer `loyaltyId` field
1. Controleer de **[!UICONTROL Identiteit]** box
1. Controleer de **[!UICONTROL Primaire identiteit]** vak, ook
1. Selecteer `Luma Loyalty Id` naamruimte van **[!UICONTROL Identiteitsnaamruimten]** druppel
1. Selecteren **[!UICONTROL Toepassen]**
1. Selecteren **[!UICONTROL Opslaan]**

   ![Primaire identiteit ](assets/identity-loyalty-primary.png)

Herhaal het proces voor een deel van uw andere schema:

1. In de `Luma CRM Schema`, de `crmId` veld als primaire identiteit met de `Luma CRM Id` namespace
1. In de `Luma Offline Purchase Events Schema`, de `loyaltyId` veld als primaire identiteit met de `Luma Loyalty Id` namespace
1. In de `Luma Product Catalog Schema`, de `productSku` veld als primaire identiteit met de `Luma Product SKU` namespace

>[!NOTE]
>
>De gegevens die met SDK van het Web worden verzameld zijn een uitzondering op de typische praktijk van het etiketteren van identiteitsgebieden in het schema. De SDK van het Web gebruikt de Kaart van de Identiteit om identiteiten te etiketteren *aan de kant van de uitvoering* en zo zullen wij de identiteiten voor `Luma Web Events Schema` wanneer wij SDK van het Web op de website van de Luma uitvoeren. In die latere les, zullen wij Experience Cloud Bezoeker identiteitskaart (ECID) als primaire identiteitskaart en crmId als secundaire identiteitskaart verzamelen.

Met onze selectie van primaire identiteiten is het duidelijk om te zien hoe `Luma CRM Schema` kan verbinding maken met de `Luma Offline Purchase Events Schema` aangezien zij beide `loyaltyId` als id. Maar hoe kunnen we onze offlineaankopen aan online gedrag verbinden? Hoe kunnen we de aangeschafte producten indelen in onze productcatalogus? Wij zullen extra identiteitsgebieden en schemaverhoudingen gebruiken.

<!--use a visual-->

### XDM-velden labelen voor secundaire identiteit

U kunt meerdere identiteitsvelden toevoegen aan een schema. Niet-primaire identiteiten worden vaak secundaire identiteiten genoemd. Om offline aankopen aan online gedrag te verbinden, zullen wij crmId als secundaire herkenningsteken aan ons toevoegen `Luma Loyalty Schema` en later in de gegevens van webgebeurtenissen. Laten we de `Luma Loyalty Schema`:

1. Open de `Luma Loyalty Schema`
1. Selecteer `Luma Identity Profile Field group`
1. Selecteren `crmId` field
1. Controleer de **[!UICONTROL Identiteit]** box
1. Selecteer `Luma CRM Id` naamruimte van **[!UICONTROL Identiteitsnaamruimten]** druppel
1. Selecteren **[!UICONTROL Toepassen]** en selecteer vervolgens de **[!UICONTROL Opslaan]** knop om uw wijzigingen op te slaan

   ![Secundaire identiteit](assets/identity-loyalty-secondaryId.png)

## De schemarelaties voltooien

Nu onze identiteitsgebieden geëtiketteerd hebben, kunnen wij de opstelling van de schemaverhoudingen tussen de productcatalogus van Luma en de gebeurtenisschema&#39;s voltooien:

1. Open de `Luma Offline Purchase Events Schema`
1. Selecteren **[!UICONTROL Handelsgegevens]** veldgroep
1. Selecteren **[!UICONTROL productListItems]** > **[!UICONTROL SKU]** field
1. Controleer de **[!UICONTROL Relatie]** box
1. Selecteren `Luma Product Catalog Schema` als de **[!UICONTROL Referentieschema]**
1. `Luma Product SKU` automatisch vullen als de **[!UICONTROL Naamruimte voor verwijzingen]**
1. Selecteren **[!UICONTROL Toepassen]**
1. Selecteren **[!UICONTROL Opslaan]**

   ![Referentieveld](assets/identity-offlinePurchase-relationship.png)

Herhaal dit proces om een relatie tot stand te brengen tussen `Luma Web Events Schema` en de `Luma Product Catalog Schema`.

Na het definiëren van de relatie wordt deze aangegeven in zowel de **[!UICONTROL Samenstelling]** en **[!UICONTROL Structuur]** van de schema-editor.

![Relatie-visualisatie in de schema-editor](assets/identity-webEvents-relationship.png)

<!--need to verify that the relationship schema works-->

## Aanvullende bronnen

* [Identiteitsdocumentatie](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=nl)
* [Identiteitsservice-API](https://www.adobe.io/experience-platform-apis/references/identity-service/)

Nu onze identiteiten er zijn, kunnen we [onze gegevenssets maken](create-datasets.md)!
