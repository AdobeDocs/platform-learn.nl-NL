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
source-git-commit: 00ef0f40fb3d82f0c06428a35c0e402f46ab6774
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 1%

---

# Identiteiten toewijzen

<!-- 30 min-->

In deze les, zullen wij identiteitsnaamruimten creëren en identiteitsgebieden toevoegen aan onze schema&#39;s. Na het doen van dit, zullen wij ook de schemaverhoudingen van de vorige les kunnen voltooien.

Met de Adobe Experience Platform Identity Service kunt u uw klanten en hun gedrag beter zien door identiteiten tussen apparaten en systemen te overbruggen, zodat u in real-time een indrukwekkende, persoonlijke digitale ervaring kunt bieden. Identiteitsvelden en naamruimten zijn de lijm die verschillende gegevensbronnen samenvoegt om het 360 graden klantenprofiel in real time te bouwen.

**Architecten van Gegevens** zullen identiteiten buiten dit leerprogramma moeten in kaart brengen.

Voordat u de oefeningen start, bekijkt u deze korte video voor meer informatie over identiteit in Adobe Experience Platform:
>[!VIDEO](https://video.tv.adobe.com/v/27841?learn=on)

>[!NOTE]
>
>Identiteitsvelden zijn alleen vereist als u realtime klantprofielen maakt. Ze zijn niet vereist als u alleen gegevens in het datumpeer opneemt.

<!--explain identity maps-->
<!--explain the strategy behind the identity selection, how these identities will join all the data together-->

## Vereiste machtigingen

In [ vorm toestemmingen ](configure-permissions.md) les, u opstelling alle toegangscontroles die worden vereist om deze les te voltooien.

<!--
* Permission items **[!UICONTROL Identity Management]** > **[!UICONTROL View Identity Namespaces]** and **[!UICONTROL Manage Identity Namespaces]**
* Permission item **[!UICONTROL Data Modeling]** > **[!UICONTROL View Schemas]** and **[!UICONTROL Manage Schemas]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
* Developer-role access to the `Luma Tutorial Platform` product profile (for API)
-->

## Naamruimte identiteit maken

In deze oefening, zullen wij identiteitsnaamruimten voor de gebieden van de douaneIdentiteit van Luma, `loyaltyId`, `crmId`, en `productSku` creëren. Identiteitsnaamruimten spelen een kritieke rol in de bouw van klantenprofielen in real time, aangezien twee passende waarden in zelfde namespace twee gegevensbronnen toestaan om een identiteitsgrafiek te vormen.


### Naamruimten maken in de gebruikersinterface

Laten we beginnen met het maken van een naamruimte voor het Luma Loyalty-schema:

1. Ga in de gebruikersinterface van het Platform naar **[!UICONTROL Identities]** in de linkernavigatie
1. U zult merken dat er verschillende naamruimten beschikbaar zijn die buiten de box vallen. Selecteer de knop **[!UICONTROL Create identity namespace]**
1. Geef de volgende gegevens op:

   | Veld | Waarde |
   |---------------|-----------|
   | Weergavenaam | Loyalty-id luminantie |
   | Identiteitssymbool | lumaLoyaltyId |
   | Type | Cross-device |

1. Selecteren **[!UICONTROL Create]**

   ![ creeer Namespaces ](assets/identity-createNamespace.png)

Stel nu een andere naamruimte in voor het schema Luminageproductcatalogus met de volgende details:

| Veld | Waarde |
|---------------|-----------|
| Weergavenaam | Luminageproduct SKU |
| Identiteitssymbool | lumaProductSKU |
| Type | Id van niet-personen |



## Identiteitsnaamruimte maken met API

We maken onze CRM-naamruimte via API.

>[!NOTE]
>
>Als u liever de API-oefeningen overslaat, kunt u de CRM-naamruimte vrij maken via de gebruikersinterfacemethode die u met de volgende details hebt gebruikt:
>
> 1. Als **[!UICONTROL Display name]** gebruikt u `Luma CRM Id`
> 1. Als **[!UICONTROL Identity symbol]** gebruikt u `lumaCrmId`
> 1. Als **[!UICONTROL Type]** gebruikt u Cross-device

Laten we naamruimte maken `Luma CRM Id` :

1. De download [ Identiteitsdienst.postman_collection.json ](https://raw.githubusercontent.com/adobe/experience-platform-postman-samples/master/apis/experience-platform/Identity%20Service.postman_collection.json) aan uw `Luma Tutorial Assets` omslag
1. De verzameling importeren in [!DNL Postman]
1. Als u geen toegangstoken hebt, open het verzoek **[!DNL OAuth: Request Access Token]** en selecteer **verzend** om een nieuw toegangstoken te verzoeken.
1. Selecteer de aanvraag **[!UICONTROL Identity Service]> [!UICONTROL Identity Namespace] > [!UICONTROL Create a new identity namespace] .**
1. Plak het volgende als [!DNL Body] van de aanvraag:

   ```json
   {
       "name": "Luma CRM Id",
       "code": "lumaCrmId",
       "idType": "Cross_device"
   }
   ```

1. Druk **verzenden** knoop en u zou a **200 O.K.** reactie moeten krijgen:

   ![ Namespace van de Identiteit ](assets/identity-createUsingApi.png)

Als u terugkeert naar de gebruikersinterface, zou u uw drie nieuwe douanenamespaces nu moeten zien:
![ Identiteitsnaamruimte ](assets/identity-newIdentities.png)


## Identiteitsvelden in schema&#39;s labelen

Nu we onze naamruimten hebben, bestaat de volgende stap uit het bijwerken van onze schema&#39;s om onze identiteitsvelden een label te geven.


### XDM-velden labelen voor primaire identiteit

Elk schema dat met het Profiel van de Klant in real time wordt gebruikt wordt vereist om een primaire gespecificeerde identiteit te hebben. Elke opgenomen record moet een waarde voor dat veld hebben.

Voeg een primaire identiteit toe aan `Luma Loyalty Schema`:

1. De `Luma Loyalty Schema` openen
1. Selecteer de `Luma Identity profile field group`
1. Selecteer het veld `loyaltyId`
1. Het selectievakje **[!UICONTROL Identity]** inschakelen
1. Schakel ook het selectievakje **[!UICONTROL Primary Identity]** in
1. De naamruimte `Luma Loyalty Id` selecteren in het vervolgkeuzemenu **[!UICONTROL Identity namespaces]**
1. Selecteren **[!UICONTROL Apply]**
1. Selecteren **[!UICONTROL Save]**

   ![ Primaire identiteit ](assets/identity-loyalty-primary.png)

Herhaal het proces voor een deel van uw andere schema:

1. In `Luma CRM Schema` geeft u het veld `crmId` een label als de primaire identiteit met de naamruimte `Luma CRM Id` .
1. In `Luma Offline Purchase Events Schema` geeft u het veld `loyaltyId` een label als de primaire identiteit met de naamruimte `Luma Loyalty Id` .
1. In `Luma Product Catalog Schema` geeft u het veld `productSku` een label als de primaire identiteit met de naamruimte `Luma Product SKU` .

>[!NOTE]
>
>De gegevens die met SDK van het Web worden verzameld zijn een uitzondering op de typische praktijk van het etiketteren van identiteitsgebieden in het schema. Het Web SDK gebruikt de Kaart van de Identiteit aan etiketidentiteiten *op de implementatiekant* en zo zullen wij de identiteiten voor `Luma Web Events Schema` bepalen wanneer wij het Web SDK op de website van de Luma uitvoeren. In die latere les, zullen wij identiteitskaart van de Bezoeker van het Experience Cloud (ECID) als primaire identiteitskaart en crmId als secundaire identiteitskaart verzamelen.

Door onze selectie van primaire identiteiten is het duidelijk hoe `Luma CRM Schema` verbinding kan maken met `Luma Offline Purchase Events Schema` omdat beide `loyaltyId` als id gebruiken. Maar hoe kunnen we onze offlineaankopen aan online gedrag verbinden? Hoe kunnen we de aangekochte producten indelen in onze productcatalogus? Wij zullen extra identiteitsgebieden en schemaverhoudingen gebruiken.

<!--use a visual-->

### XDM-velden labelen voor secundaire identiteit

U kunt meerdere identiteitsvelden toevoegen aan een schema. Niet-primaire identiteiten worden vaak secundaire identiteiten genoemd. Als u offline aankopen wilt verbinden met onlinegedrag, voegen we de crmId als een secundaire id toe aan onze `Luma Loyalty Schema` en latere gegevens over webgebeurtenissen. Werk de `Luma Loyalty Schema` bij:

1. De `Luma Loyalty Schema` openen
1. Selecteren `Luma Identity Profile Field group`
1. Veld `crmId` selecteren
1. Het selectievakje **[!UICONTROL Identity]** inschakelen
1. De naamruimte `Luma CRM Id` selecteren in het vervolgkeuzemenu **[!UICONTROL Identity namespaces]**
1. Selecteer **[!UICONTROL Apply]** en selecteer vervolgens de knop **[!UICONTROL Save]** om uw wijzigingen op te slaan

   ![ Secundaire Identiteit ](assets/identity-loyalty-secondaryId.png)

## De schemarelaties voltooien

Nu onze identiteitsgebieden geëtiketteerd hebben, kunnen wij de opstelling van de schemaverhoudingen tussen de productcatalogus van Luma en de gebeurtenisschema&#39;s voltooien:

1. De `Luma Offline Purchase Events Schema` openen
1. **[!UICONTROL Commerce Details]** -veldgroep selecteren
1. Selecteren **[!UICONTROL productListItems]** > **[!UICONTROL SKU]** -veld
1. Het selectievakje **[!UICONTROL Relationship]** inschakelen
1. Selecteer `Luma Product Catalog Schema` als de **[!UICONTROL Reference schema]**
1. `Luma Product SKU` moet automatisch worden gevuld als de **[!UICONTROL Reference Identity namespace]**
1. Selecteren **[!UICONTROL Apply]**
1. Selecteren **[!UICONTROL Save]**

   ![ gebied van de Verwijzing ](assets/identity-offlinePurchase-relationship.png)

Herhaal dit proces om een relatie te maken tussen de `Luma Web Events Schema` en de `Luma Product Catalog Schema` .

Nadat u de relatie hebt gedefinieerd, wordt deze zowel in de sectie **[!UICONTROL Composition]** als in de sectie **[!UICONTROL Structure]** van de schema-editor aangegeven.

![ visualisatie van de Verhouding in de schemageditor ](assets/identity-webEvents-relationship.png)

<!--need to verify that the relationship schema works-->

## Aanvullende bronnen

* [ documentatie van de Dienst van de Identiteit ](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=nl)
* [ Identiteitsdienst API ](https://www.adobe.io/experience-platform-apis/references/identity-service/)

Nu onze identiteiten op zijn plaats zijn, kunnen wij [ onze datasets ](create-datasets.md) tot stand brengen!
