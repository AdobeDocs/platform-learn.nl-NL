---
title: Tagregels maken voor Platform Web SDK
description: Leer hoe u een gebeurtenis naar Platform Edge Network verzendt met behulp van tagregels. Deze les maakt deel uit van de zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Tags
jira: KT-15403
exl-id: e06bad06-3ee3-475f-9b10-f0825a48a312
source-git-commit: da65f13f95a6d1258655e8eebc76cf024221a610
workflow-type: tm+mt
source-wordcount: '1629'
ht-degree: 0%

---

# Tagregels maken

Leer hoe u gebeurtenissen naar de Adobe Experience Platform Edge Network verzendt met behulp van tagregels. Een labelregel is een combinatie van gebeurtenissen, voorwaarden en handelingen die de eigenschap van de tag opgeeft iets te doen. Met het Web SDK van het Platform, worden de regels gebruikt om gebeurtenissen naar Platform Edge Network met de juiste gegevens te verzenden.



## Leerdoelstellingen

Aan het einde van deze les kunt u het volgende doen:

* Een naamgevingsconventie gebruiken voor het beheer van regels binnen tags
* Een gebeurtenis verzenden met XDM-velden met de acties Variabele bijwerken en Gebeurtenis verzenden
* Meerdere sets XDM-velden stapelen over meerdere regels
* Afzonderlijke of volledige arraygegevenselementen toewijzen aan het XDM-object
* Een labelregel publiceren naar een ontwikkelingsbibliotheek


## Vereisten

U bent vertrouwd met de markeringen van de Inzameling van Gegevens en de [&#x200B; demowebsite van de Luma &#x200B;](https://luma.enablementadobe.com) en hebt de vorige lessen in het leerprogramma voltooid:

* [Een XDM-schema configureren](configure-schemas.md)
* [Naamruimte configureren](configure-identities.md)
* [Een gegevensstroom configureren](configure-datastream.md)
* [Web SDK-extensie installeren](install-web-sdk.md)
* [Gegevenselementen maken](create-data-elements.md)
* [Identiteiten vastleggen](create-identities.md)

## Naamgevingsconventies

Als u regels in tags wilt beheren, kunt u het beste een standaardnaamgevingsconventie volgen. In deze zelfstudie wordt een naamgevingsconventie gebruikt die uit vier delen bestaat:

* [**plaats**] - [**gebeurtenis**] - [**doel**] - [**orde**]

waar;

1. **plaats** is de pagina of de pagina&#39;s op de plaats waar de regel in brand steekt
1. **gebeurtenis** is de trekker voor de regel
1. **doel** is de belangrijkste actie die door de regel wordt uitgevoerd
1. **orde** is de orde waarin de regel met betrekking tot andere regels zou moeten in brand steken die de zelfde gebeurtenis delen
<!-- minor update -->

## Extensie Adobe Client Data Layer toevoegen

De Luma-website gebruikt een gebeurtenisgestuurde gegevenslaag met de naam Adobe Client Data Layer (ACDL). Wanneer een gebeurtenis in een gegevenslaag plaatsvindt, wordt deze in de array `adobeDataLayer` geduwd. In deze zelfstudie wordt de extensie Adobe Client Data Layer gebruikt om eenvoudig op deze gebeurtenissen te tikken om onze regels samen te stellen.

De extensie toevoegen:

1. Ga naar **[!UICONTROL Extensions]**
1. Filteren naar **[!UICONTROL Adobe Client Data Layer]**
1. Selecteren **[!UICONTROL Install]**

   ![&#x200B; voeg de uitbreiding van de Laag van de Gegevens van de Cliënt van Adobe toe &#x200B;](assets/rules-acdl-extension.png)

1. De standaardinstellingen behouden
1. Selecteren **[!UICONTROL Save]**

>[!NOTE]
>
> Het is niet noodzakelijk om de Laag van Gegevens van de Cliënt van Adobe te gebruiken om het Web SDK van Experience Platform uit te voeren. Vele andere soorten gebeurtenissen worden algemeen gebruikt in markeringen implementaties (Bibliotheek Geladen, Klaar DOM, Venster Geladen, etc.) aan brandregels.

## Tagregels maken

In labels worden regels gebruikt om handelingen uit te voeren, zoals het instellen van variabelen en het afvuren van netwerkaanroepen onder verschillende omstandigheden. De Experience Platform Web SDK tagextensie bevat twee handelingen die in regels worden gebruikt:

* **[!UICONTROL Update variable]** wijst gegevenselementen aan uw XDM of gegevensvariabelen toe
* **[!UICONTROL Send Event]** roept het netwerk op om gegevens naar Experience Platform Edge Network te verzenden

In de rest van deze les:

1. Gebruik de handeling **[!UICONTROL Update variable]** om een &quot;globale configuratie&quot; van XDM-velden te definiëren.

1. Gebruik de handeling **[!UICONTROL Update variable]** nogmaals om onze &quot;globale configuratie&quot; te negeren en extra XDM-velden onder bepaalde omstandigheden bij te dragen (bijvoorbeeld door productdetails op productpagina&#39;s toe te voegen).

1. Gebruik de handeling **[!UICONTROL Send Event]** om de gegevens naar Adobe Experience Platform Edge Network te verzenden.

Al deze regels zullen behoorlijk gebruikend de &quot;[!UICONTROL order]&quot;optie worden gesequenced.

Deze video geeft een overzicht van het proces:

>[!VIDEO](https://video.tv.adobe.com/v/3454033/?captions=dut&learn=on&enablevpops)

### Algemene configuratievelden

Een labelregel maken voor de globale XDM-velden:

1. Open de eigenschap tag die u voor deze zelfstudie gebruikt

1. Ga naar **[!UICONTROL Rules]** in de linkernavigatie

1. Selecteer de knop **[!UICONTROL Create New Rule]**

   ![&#x200B; creeer een regel &#x200B;](assets/rules-create.png)

1. Naam van de regel `all pages - adobeDataLayer push - set global variables - 1`

1. Selecteer in de sectie **[!UICONTROL Events]** de optie **[!UICONTROL Add]**

   ![&#x200B; Naam de regel en voeg een gebeurtenis &#x200B;](assets/rule-name-new.png) toe

1. Gebruik de extensie **[!UICONTROL Adobe Client Data Layer]** en selecteer **[!UICONTROL Data Pushed]** als **[!UICONTROL Event Type]**

1. Selecteer **[!UICONTROL Advanced]** vervolgkeuzelijst en voer `1` in als de **[!UICONTROL Order]**

   >[!NOTE]
   >
   > Hoe lager de volgordenummer, des te eerder de waarde wordt uitgevoerd. Daarom geven wij onze &quot;globale configuratie&quot;een laag orde aantal.

1. Luisteren naar **[!UICONTROL All Events]**
1. Selecteer **[!UICONTROL Keep Changes]** om terug te keren naar het hoofdregelscherm
   ![&#x200B; Uitgezochte Bibliotheek Geladen Trekker &#x200B;](assets/create-tag-rule-trigger-loaded.png)

1. Selecteer in de sectie **[!UICONTROL Actions]** de optie **[!UICONTROL Add]**

1. Als **[!UICONTROL Extension]** selecteert u **[!UICONTROL Adobe Experience Platform Web SDK]**

1. Als **[!UICONTROL Action Type]** selecteert u **[!UICONTROL Update variable]**

1. Als **[!UICONTROL Data element]**, selecteer `XDM Variable` u in [&#x200B; creeerde gegevenselementen &#x200B;](create-data-elements.md) les

   ![&#x200B; veranderlijk Schema van de Update &#x200B;](assets/create-rule-update-variable.png)

1. Geef nu de XDM-velden op door deze aan de juiste waarden toe te wijzen:

   | XDM-veld | Toewijzen aan |
   |---|---|
   | `eventType` | `Web Webpagedetails Page Views` (typ eerst de gesuggereerde waarden) |
   | `identityMap` | `Identity Map` data-element |
   | `web.webPageDetails.name` | `Page Name` data-element |
   | `web.webPageDetails.pageViews.value` | `1` |


   >[!TIP]
   >
   > XDM gebieden zullen niet in het netwerkverzoek worden omvat als het gegevenselement ongeldig is. Wanneer de gebruiker niet wordt geverifieerd en het gegevenselement `Identity Map` null is, wordt het object `identityMap` dus niet verzonden. Daarom kunnen we het veilig definiëren in onze &quot;mondiale configuratie&quot;.

   >[!TIP]
   >
   > Het plaatsen `web.webPageDetails.pageViews.value` verstrekt een standaardmanier om op een paginamening voor andere stroomafwaartse toepassingen te wijzen. Adobe Analytics hoeft een netwerkaanroep niet als paginaweergave te verwerken.

1. Als u klaar bent, ziet uw `XDM Variable` er ongeveer zo uit. Let op hoe de gevulde en gedeeltelijk gevulde velden worden aangeduid met de blauwe cirkels:
   ![&#x200B; Variabele XDM &#x200B;](assets/rule-xdm-variable.png)
1. Selecteer **[!UICONTROL Keep Changes]** en **[!UICONTROL Save]** de regel



### Productpaginavelden

Start nu **[!UICONTROL Update variable]** in extra, gerangschikte regels om het XDM-object te verrijken voordat u het naar [!UICONTROL Platform Edge Network] verzendt.

>[!TIP]
>
>De regelvolgorde bepaalt welke regel het eerst wordt uitgevoerd wanneer een gebeurtenis wordt geactiveerd. Als twee regels het zelfde gebeurtenistype hebben, eerst loopt de regel met het laagste orderaantal.
> 

Eerst volgt u de productweergaven op de pagina met productdetails van Luma:

1. Selecteren **[!UICONTROL Add Rule]**
1. Naam geven [!UICONTROL `product detail pages - adobeDataLayer push - set product details variables - 20`]
1. Selecteer het ![+-symbool &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) onder Gebeurtenis om een nieuwe trigger toe te voegen
1. Onder **[!UICONTROL Extension]** selecteert u **[!UICONTROL Adobe Client Data Layer]**
1. Onder **[!UICONTROL Event Type]** selecteert u **[!UICONTROL Data Pushed]**
1. Selecteer deze optie om **[!UICONTROL Advanced Options]** te openen en typ in `20` . Deze ordewaarde verzekert de regellooppas _na_ de globale veranderingsregel.
1. Luisteren naar een **[!UICONTROL Specific Event]**
1. Voer `productView` in als de **[!UICONTROL Event / Key to register for]**
1. Selecteren **[!UICONTROL Keep changes]**

   ![&#x200B; de regels van Analytics XDM &#x200B;](assets/rule-pdp-event.png)


1. Onder **[!UICONTROL Actions]** select **[!UICONTROL Add]**
1. Extensie **[!UICONTROL Adobe Experience Platform Web SDK]** selecteren
1. **[!UICONTROL Action Type]** selecteren als **[!UICONTROL Update variable]**
1. Selecteer `XDM Variable` als de **[!UICONTROL Data element]**
1. Deze XDM-velden toewijzen aan de juiste waarden:

   | XDM-veld | Toewijzen aan |
   |---|---|
   | `eventType` | `Commerce Product Views` (typ eerst de gesuggereerde waarden) |
   | `commerce.productViews.value` | `1` |
   | `productListItems.name` | `Ecommerce Product Name` data-element (eerst selecteren **[!UICONTROL Provide individual items]** en **[!UICONTROL Add Item]** ) |
   | `productListItems.sku` | `Ecommerce Product Id` data-element |

1. Selecteren **[!UICONTROL Keep Changes]**

1. Selecteer **[!UICONTROL Save]** om de regel op te slaan

   >[!NOTE]
   >
   >Omdat deze regel een hogere volgorde heeft, overschrijft deze de `eventType` die is ingesteld in de regel &quot;globale configuratie&quot;. `eventType` kan slechts één waarde bevatten en we raden u aan deze waarde in te stellen met de meest waardevolle gebeurtenis.

   >[!TIP]
   >
   >Als u commerce.productViews.value=1 instelt in XDM, wordt automatisch toegewezen aan de gebeurtenis `prodView` in Analytics


### Kaarten weergeven

U kunt een volledige array toewijzen aan een XDM-object, mits de array overeenkomt met de indeling van het XDM-schema. Het aangepaste element met codegegevens `Ecommerce Cart Products` dat u eerder hebt gemaakt, doorloopt het `adobeDataLayer.ecommerce.cart.items` gegevenslaagobject op de Luma-website en zet dit om in de vereiste indeling van het `productListItems` -object van het XDM-schema.

Zie de vergelijking hieronder van de gegevenslaag van de Luminasite (links) met het vertaalde gegevenselement (rechts) voor illustratie:

![&#x200B; XDM voorwerp matrixformaat &#x200B;](assets/data-element-xdm-array.png)


Vergelijk het gegevenselement met de `productListItems` -structuur (hint, it should match).

>[!NOTE]
>
> U kunt `_satellite.getVar('Ecommerce Cart Products')` nu niet uitvoeren in de zelfstudie.

>[!IMPORTANT]
>
>Wanneer het in kaart brengen van gebieden van uw gegevenslaag aan XDM, zorg ervoor de gebieden het gegevenstype van het XDM gebied aanpassen. In het bovenstaande voorbeeld moeten `quantity` en `priceTotal` gehele getallen zijn, anders wordt de record niet opgenomen in Platform.
> ![Gegevenstype XDM-schema &#x200B;](assets/set-up-analytics-quantity-integer.png)

Laten we nu onze array toewijzen aan het XDM-object:


1. Een nieuwe regel maken met de naam `cart page - adobeDataLayer push - set cart variables - 20`
1. Selecteer het ![+-symbool &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) onder Gebeurtenis om een nieuwe trigger toe te voegen
1. Onder **[!UICONTROL Extension]** selecteert u **[!UICONTROL Adobe Client Data Layer]**
1. Onder **[!UICONTROL Event Type]** selecteert u **[!UICONTROL Data Pushed]**
1. Selecteer deze optie om **[!UICONTROL Advanced Options]** te openen en typ in `20` . Deze ordewaarde verzekert de regellooppas _na_ de globale veranderingsregel.
1. Luisteren naar een **[!UICONTROL Specific Event]**
1. Voer `cartView` in als de **[!UICONTROL Event / Key to register for]**
1. Selecteren **[!UICONTROL Keep Changes]**


   ![&#x200B; Gebeurtenis voor de regel van de Kar &#x200B;](assets/rule-cart-event.png)

1. Onder **[!UICONTROL Actions]** select **[!UICONTROL Add]**
1. Extensie **[!UICONTROL Adobe Experience Platform Web SDK]** selecteren
1. **[!UICONTROL Action Type]** selecteren als **[!UICONTROL Update variable]**
1. Selecteer `XDM Variable` als de **[!UICONTROL Data element]**
1. Deze XDM-velden toewijzen aan de juiste waarden:

   | XDM-veld | Toewijzen aan |
   |---|---|
   | `eventType` | `Commerce Product List (Cart) Views` (typ eerst de gesuggereerde waarden) |
   | `commerce.productListViews.value` | `1` |
   | `productListItems` | `Ecommerce Cart Products` data-element (eerst selecteren **[!UICONTROL Provide entire array]** ) |

   >[!TIP]
   >
   >Door commerce.productListViews.value=1 in XDM in te stellen, wordt automatisch toegewezen aan de gebeurtenis `scView` in Analytics

1. Selecteren **[!UICONTROL Keep Changes]**

1. Selecteer **[!UICONTROL Save]** om de regel op te slaan


### Bevestigingsvelden bestellen

Maak een andere regel voor aankoopgebeurtenissen:

1. Een nieuwe regel maken met de naam `order confirmation - adobeDataLayer push - set purchase variables -  20`
1. Selecteer het ![+-symbool &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) onder Gebeurtenis om een nieuwe trigger toe te voegen
1. Onder **[!UICONTROL Extension]** selecteert u **[!UICONTROL Adobe Client Data Layer]**
1. Onder **[!UICONTROL Event Type]** selecteert u **[!UICONTROL Data Pushed]**
1. Selecteer deze optie om **[!UICONTROL Advanced Options]** te openen en typ in `20` . Deze ordewaarde verzekert de regellooppas _na_ de globale veranderingsregel.
1. Luisteren naar een **[!UICONTROL Specific Event]**
1. Voer `purchase` in als de **[!UICONTROL Event / Key to register for]**
1. Selecteren **[!UICONTROL Keep Changes]**
1. Onder **[!UICONTROL Actions]** select **[!UICONTROL Add]**
1. Extensie **[!UICONTROL Adobe Experience Platform Web SDK]** selecteren
1. **[!UICONTROL Action Type]** selecteren als **[!UICONTROL Update variable]**
1. Selecteer `XDM Variable` als de **[!UICONTROL Data element]**
1. Deze XDM-velden toewijzen aan de juiste waarden:

   | XDM-veld | Toewijzen aan |
   |---|---|
   | `eventType` | `Commerce Purchases` (typ eerst de gesuggereerde waarden) |
   | `commerce.productListViews.value` | `1` |
   | `commerce.order.purchaseID` | `Ecommerce Purchase Id` data-element |
   | `commerce.order.currencyCode` | `USD` |
   | `productListItems` | `Ecommerce Cart Products` data element(Select **[!UICONTROL Provide entire array]** first) |

   >[!TIP]
   >
   >Als u `commerce.productListViews.value` instelt op `1` , `commerce.order.purchaseID` en `commerce.order.currencyCode` in XDM, worden automatisch de variabelen `purchase` , `s.purchaseID` en `s.currencyCode` in Analytics toegewezen.


1. Selecteren **[!UICONTROL Keep Changes]**
1. Selecteren **[!UICONTROL Save]**


### Gebeurtenisregel verzenden

Nu u de variabelen hebt ingesteld, kunt u de regel maken om het volledige XDM-object naar Platform Edge Network te verzenden met de handeling **[!UICONTROL Send event]** .


1. Een nieuwe regel maken met de naam `all pages - adobeDataLayer push - send event - 50`
1. Selecteer het ![+-symbool &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) onder Gebeurtenis om een nieuwe trigger toe te voegen
1. Onder **[!UICONTROL Extension]** selecteert u **[!UICONTROL Adobe Client Data Layer]**
1. Onder **[!UICONTROL Event Type]** selecteert u **[!UICONTROL Data Pushed]**
1. Selecteer deze optie om **[!UICONTROL Advanced Options]** te openen en typ in `50` (dit is waarschijnlijk de standaardinstelling). Deze ordewaarde verzekert de regellooppas _na_ veranderlijk-plaatsende regels.
1. Luisteren naar een **[!UICONTROL All Events]**
1. Selecteren **[!UICONTROL Keep Changes]**
1. Onder **[!UICONTROL Actions]** select **[!UICONTROL Add]**
1. Extensie **[!UICONTROL Adobe Experience Platform Web SDK]** selecteren
1. **[!UICONTROL Action Type]** selecteren als **[!UICONTROL Send Event variable]**



1. Als **[!UICONTROL Action Type]** selecteert u **[!UICONTROL Send event]**

1. Als **[!UICONTROL XDM]** selecteert u het gegevenselement `XDM Variable` dat in de vorige les is gemaakt

1. Selecteer **[!UICONTROL Keep Changes]** om terug te keren naar het hoofdregelscherm

   ![&#x200B; voeg de Send actie van de Gebeurtenis &#x200B;](assets/create-rule-send-event-action.png) toe
1. Selecteer **[!UICONTROL Save]** om de regel op te slaan

   ![&#x200B; sparen de regel &#x200B;](assets/create-rule-save-rule.png)

U zou de volgende regels in uw bezit moeten hebben:

![&#x200B; verifieer lijst van regels &#x200B;](assets/create-rule-list-of-rules.png)

## De regels in een bibliotheek publiceren

Vervolgens publiceert u de regel naar de ontwikkelomgeving, zodat u kunt controleren of deze werkt.

Een bibliotheek maken:

1. Ga naar **[!UICONTROL Publishing Flow]** in de linkernavigatie

1. Selecteren **[!UICONTROL Add Library]**

   ![&#x200B; Uitgezocht voeg Bibliotheek &#x200B;](assets/rule-publish-library.png) toe
1. Voer bij **[!UICONTROL Name]** `Luma Web SDK Tutorial` in
1. Selecteer **[!UICONTROL Environment]** voor `Development`
1. Selecteren **[!UICONTROL Add All Changed Resources]**

   >[!NOTE]
   >
   >    Alle tagcomponenten die in vorige lessen zijn gemaakt, worden weergegeven. De extensie Core bevat de basis-JavaScript die door alle eigenschappen van webtags wordt vereist.

1. Selecteren **[!UICONTROL Save & Build for Development]**

   ![&#x200B; creeer en bouwt de bibliotheek &#x200B;](assets/create-tag-rule-library-changes.png)

Het kan enkele minuten duren voordat de bibliotheek is gemaakt en wanneer deze is voltooid, wordt links van de naam van de bibliotheek een groene stip weergegeven:

![&#x200B; bouwt volledig &#x200B;](assets/create-rule-development-success.png)

Zoals u op het [!UICONTROL Publishing Flow] scherm kunt zien, is er veel meer aan het het publiceren proces, dat voorbij het werkingsgebied van deze zelfstudie is. Deze zelfstudie gebruikt slechts één bibliotheek in uw ontwikkelomgeving.

U kunt nu de gegevens in de aanvraag valideren met de Adobe Experience Platform Debugger.

>[!NOTE]
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren over Adobe Experience Platform Web SDK. Als u vragen hebt, algemene terugkoppelen wilt delen, of suggesties over toekomstige inhoud hebben, gelieve hen op deze [&#x200B; Communautaire besprekingspost van Experience League te delen &#x200B;](https://experienceleaguecommunities.adobe.com/adobe-experience-platform-18/tutorial-discussion-implement-adobe-experience-cloud-with-web-sdk-tutorial-248848?profile.language=nl)
