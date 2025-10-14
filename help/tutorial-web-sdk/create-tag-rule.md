---
title: Tagregels maken voor Platform Web SDK
description: Leer hoe u een gebeurtenis naar Platform Edge Network verzendt met uw XDM-object met behulp van een tagregel. Deze les maakt deel uit van de zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Tags
jira: KT-15403
exl-id: e06bad06-3ee3-475f-9b10-f0825a48a312
source-git-commit: 7ccbaaf4db43921f07c971c485e1460a1a7f0334
workflow-type: tm+mt
source-wordcount: '1761'
ht-degree: 0%

---

# Tagregels maken

Leer hoe u gebeurtenissen naar de Adobe Experience Platform Edge Network kunt verzenden met uw XDM-object aan de hand van tagregels. Een labelregel is een combinatie van gebeurtenissen, voorwaarden en handelingen die de eigenschap van de tag opgeeft iets te doen. Met het Web SDK van het Platform, worden de regels gebruikt om gebeurtenissen naar Platform Edge Network met de juiste gegevens te verzenden.

## Leerdoelstellingen

Aan het einde van deze les kunt u het volgende doen:

* Een naamgevingsconventie gebruiken voor het beheer van regels binnen tags
* Een gebeurtenis verzenden met XDM-velden met de acties Variabele bijwerken en Gebeurtenis verzenden
* Meerdere sets XDM-velden stapelen over meerdere regels
* Afzonderlijke of volledige arraygegevenselementen toewijzen aan het XDM-object
* Een labelregel publiceren naar een ontwikkelingsbibliotheek


## Vereisten

U bent vertrouwd met de markeringen van de Inzameling van Gegevens en de [&#x200B; de demomoeplaats van de Luma &#x200B;](https://luma.enablementadobe.com/content/luma/us/en.html) en hebt de vorige lessen in het leerprogramma voltooid:

* [Een XDM-schema configureren](configure-schemas.md)
* [Naamruimte configureren](configure-identities.md)
* [Een gegevensstroom configureren](configure-datastream.md)
* [Web SDK-extensie installeren](install-web-sdk.md)
* [Gegevenselementen maken](create-data-elements.md)
* [Identiteiten maken](create-identities.md)

## Naamgevingsconventies

Als u regels in tags wilt beheren, kunt u het beste een standaardnaamgevingsconventie volgen. In deze zelfstudie wordt een naamgevingsconventie gebruikt die uit vijf delen bestaat:

* [**plaats**] - [**gebeurtenis**] - [**doel**] - [**orde**]

waar;

1. **plaats** is de pagina of de pagina&#39;s op de plaats waar de regel in brand steekt
1. **gebeurtenis** is de trekker voor de regel
1. **doel** is de belangrijkste actie die door de regel wordt uitgevoerd
1. **orde** is de orde waarin de regel met betrekking tot andere regels zou moeten in brand steken
<!-- minor update -->

## Tagregels maken

In tags worden regels gebruikt om handelingen (aanroepen naar brand) onder verschillende omstandigheden uit te voeren. De de etikettenuitbreiding van SDK van het Web van het Platform omvat twee acties die in deze les worden gebruikt:

* **[!UICONTROL Update variable]** wijst gegevenselementen toe aan eigenschappen in een XDM-object
* **[!UICONTROL Send Event]** verzendt het XDM-object naar Experience Platform Edge Network

In de rest van deze les:

1. Maak een regel met de handeling **[!UICONTROL Update variable]** om een &quot;globale configuratie&quot; van XDM-velden te definiëren.

1. Maak aanvullende regels met de handeling **[!UICONTROL Update variable]** die onze &quot;globale configuratie&quot; overschrijven en onder bepaalde voorwaarden aanvullende XDM-velden leveren (bijvoorbeeld door productdetails op productpagina&#39;s toe te voegen).

1. Maak een andere regel met de handeling **[!UICONTROL Send Event]** , die het volledige XDM-object naar Adobe Experience Platform Edge Network verzendt.

Al deze regels zullen behoorlijk gebruikend de &quot;[!UICONTROL order]&quot;optie worden gesequenced.

Deze video geeft een overzicht van het proces:

>[!VIDEO](https://video.tv.adobe.com/v/3454033/?learn=on&enablevpops&captions=dut)

### Algemene configuratievelden

Een labelregel maken voor de globale XDM-velden:

1. Open de eigenschap tag die u voor deze zelfstudie gebruikt

1. Ga naar **[!UICONTROL Rules]** in de linkernavigatie

1. Selecteer de knop **[!UICONTROL Create New Rule]**

   ![&#x200B; creeer een regel &#x200B;](assets/rules-create.png)

1. Naam van de regel `all pages - library loaded - set global variables - 1`

1. Selecteer in de sectie **[!UICONTROL Events]** de optie **[!UICONTROL Add]**

   ![&#x200B; Naam de regel en voeg een gebeurtenis &#x200B;](assets/rule-name-new.png) toe

1. Gebruik **[!UICONTROL Core Extension]** en selecteer **[!UICONTROL Library Loaded (Page Top)]** als **[!UICONTROL Event Type]**

1. Selecteer **[!UICONTROL Advanced]** vervolgkeuzelijst en voer `1` in als de **[!UICONTROL Order]**

   >[!NOTE]
   >
   > Hoe lager de volgordenummer, des te eerder de waarde wordt uitgevoerd. Daarom geven wij onze &quot;globale configuratie&quot;een laag orde aantal.

1. Selecteer **[!UICONTROL Keep Changes]** om terug te keren naar het hoofdregelscherm
   ![&#x200B; Uitgezochte Bibliotheek Geladen Trekker &#x200B;](assets/create-tag-rule-trigger-loaded.png)

1. Selecteer in de sectie **[!UICONTROL Actions]** de optie **[!UICONTROL Add]**

1. Als **[!UICONTROL Extension]** selecteert u **[!UICONTROL Adobe Experience Platform Web SDK]**

1. Als **[!UICONTROL Action Type]** selecteert u **[!UICONTROL Update variable]**

1. Als **[!UICONTROL Data element]**, selecteer `xdm.variable.content` u in [&#x200B; creeerde gegevenselementen &#x200B;](create-data-elements.md) les

   ![&#x200B; veranderlijk Schema van de Update &#x200B;](assets/create-rule-update-variable.png)

Wijs nu de [!UICONTROL data elements] toe aan de [!UICONTROL schema] die door uw XDM-object wordt gebruikt. U kunt toewijzen aan afzonderlijke eigenschappen of volledige objecten. In dit voorbeeld koppelt u de eigenschappen aan individuele eigenschappen:

1. Het veld eventType zoeken en selecteren

1. Voer de waarde in `web.webpagedetails.pageViews`

   >[!TIP]
   >
   > Als u wilt weten welke waarden in het veld `eventType` moeten worden ingevuld, gaat u naar de schemapagina en selecteert u het veld `eventType` om de voorgestelde waarden op de rechterrails weer te geven. U kunt desgewenst ook een nieuwe waarde invoeren.
   > ![&#x200B; eventType stelde waarden op de schema&#39;s pagina voor &#x200B;](assets/create-tag-rule-eventType.png)

1. Zoek vervolgens het `identityMap` -object in het schema en selecteer het.

1. Toewijzen aan het gegevenselement `identityMap.loginID`

   ![&#x200B; veranderlijke identiteitskaart van de Update kaart &#x200B;](assets/create-rule-variable-identityMap.png)


   >[!TIP]
   >
   > XDM gebieden zullen niet in het netwerkverzoek worden omvat als het gegevenselement ongeldig is. Wanneer de gebruiker niet wordt geverifieerd en het gegevenselement `identityMap.loginID` null is, wordt het object `identityMap` dus niet verzonden. Daarom kunnen we het definiëren in onze &quot;mondiale configuratie&quot;.

1. Omlaag schuiven totdat u het object **`web`** bereikt

1. Selecteren om te openen

1. Wijs de volgende gegevenselementen toe aan de overeenkomstige `web` XDM-variabelen

   * **`web.webPageDetials.name`** t/m `%page.pageInfo.pageName%`
   * **`web.webPageDetials.server`** t/m `%page.pageInfo.server%`
   * **`web.webPageDetials.siteSection`** t/m `%page.pageInfo.hierarchie1%`

1. `web.webPageDetials.pageViews.value` instellen op `1`

   ![&#x200B; Update veranderlijke inhoud &#x200B;](assets/create-rule-xdm-variable-content.png)

   >[!TIP]
   >
   > Hoewel Adobe Analytics een baken niet hoeft te verwerken als paginaweergave als `eventType` is ingesteld op `web.webpagedetails.pageViews` of `web.webPageDetails.pageViews.value` , is het handig om over een standaardmanier te beschikken om een paginaweergave aan te geven voor andere downstreamtoepassingen.


1. Selecteer **[!UICONTROL Keep Changes]** en **[!UICONTROL Save]** vervolgens de regel in het volgende scherm om het maken van de regel te voltooien


### Productpaginavelden

Start nu **[!UICONTROL Update variable]** in extra, gerangschikte regels om het XDM-object te verrijken voordat u het naar [!UICONTROL Platform Edge Network] verzendt.

>[!TIP]
>
>De regelvolgorde bepaalt welke regel het eerst wordt uitgevoerd wanneer een gebeurtenis wordt geactiveerd. Als twee regels hetzelfde gebeurtenistype hebben, wordt eerst de regel met het laagste getal uitgevoerd.
> 

Eerst volgt u de productweergaven op de pagina met productdetails van Luma:

1. Selecteren **[!UICONTROL Add Rule]**
1. Naam geven [!UICONTROL `ecommerce - library loaded - set product details variables - 20`]
1. Selecteer het ![+-symbool &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) onder Gebeurtenis om een nieuwe trigger toe te voegen
1. Onder **[!UICONTROL Extension]** selecteert u **[!UICONTROL Core]**
1. Onder **[!UICONTROL Event Type]** selecteert u **[!UICONTROL Library Loaded (Page Top)]**
1. Selecteer deze optie om **[!UICONTROL Advanced Options]** te openen en typ in `20` . Deze ordewaarde verzekert de regellooppas _na_ `all pages - library loaded - set global variables - 1` die de globale configuratie plaatst.
1. Selecteren **[!UICONTROL Keep changes]**

   ![&#x200B; de regels van Analytics XDM &#x200B;](assets/set-up-analytics-pdp.png)

1. Onder **[!UICONTROL Conditions]** selecteert u **[!UICONTROL Add]**
1. **[!UICONTROL Logic Type]** behouden als **[!UICONTROL Regular]**
1. **[!UICONTROL Extension]** behouden als **[!UICONTROL Core]**
1. **[!UICONTROL Condition Type]** selecteren als **[!UICONTROL Path Without Query String]**
1. Schakel rechts de schakeloptie **[!UICONTROL Regex]** in
1. Onder **[!UICONTROL path equals]** set `/products/` . Voor de Luma-demo-site zorgt deze ervoor dat de regel alleen op productpagina&#39;s wordt geactiveerd
1. Selecteren **[!UICONTROL Keep Changes]**

   ![&#x200B; de regels van Analytics XDM &#x200B;](assets/set-up-analytics-product-condition.png)

1. Onder **[!UICONTROL Actions]** select **[!UICONTROL Add]**
1. Extensie **[!UICONTROL Adobe Experience Platform Web SDK]** selecteren
1. **[!UICONTROL Action Type]** selecteren als **[!UICONTROL Update variable]**
1. Selecteer `xdm.variable.content` als de **[!UICONTROL Data element]**
1. Omlaag schuiven naar het `commerce` -object
1. Open het object **[!UICONTROL productViews]** en stel **[!UICONTROL value]** in op `1`

   ![&#x200B; de Mening van het opstellingsProduct &#x200B;](assets/set-up-analytics-prodView.png)

   >[!TIP]
   >
   >Als u commerce.productViews.value=1 instelt in XDM, wordt automatisch toegewezen aan de gebeurtenis `prodView` in Analytics

1. Omlaag schuiven naar `eventType` en instellen op `commerce.productViews`

   >[!NOTE]
   >
   >Omdat deze regel een hogere volgorde heeft, overschrijft deze de `eventType` die is ingesteld in de regel &quot;globale configuratie&quot;. `eventType` kan slechts één waarde bevatten en we raden u aan deze waarde in te stellen met de meest waardevolle gebeurtenis.

1. Omlaag schuiven naar en array selecteren `productListItems`
1. Selecteren **[!UICONTROL Provide individual items]**
1. Selecteren **[!UICONTROL Add Item]**

   ![&#x200B; Plaatsende gebeurtenis van de productmening &#x200B;](assets/set-up-analytics-xdm-individual.png)

   >[!CAUTION]
   >
   >**`productListItems`** is een `array` gegevenstype zodat het verwacht dat gegevens worden ingevoerd als een verzameling elementen. Vanwege de gegevenslaagstructuur van de demo-site van Luma en omdat het alleen mogelijk is om één product tegelijk weer te geven op de Luministsite, voegt u afzonderlijke items toe. Afhankelijk van de structuur van de gegevenslaag kunt u bij de implementatie op uw eigen website mogelijk een volledige array opgeven.

1. Selecteren om te openen **[!UICONTROL Item 1]**
1. Toewijzen **`productListItems.item1.SKU`** aan `%product.productInfo.sku%`

   ![&#x200B; de objectenVariabele van het Product SKU XDM &#x200B;](assets/set-up-analytics-sku.png)

1. Selecteren **[!UICONTROL Keep Changes]**

1. Selecteer **[!UICONTROL Save]** om de regel op te slaan


### Kaarten weergeven

U kunt een volledige array toewijzen aan een XDM-object, mits de array overeenkomt met de indeling van het XDM-schema. Het aangepaste element met codegegevens `cart.productInfo` dat u eerder hebt gemaakt, doorloopt het `digitalData.cart.cartEntries` gegevenslaagobject op Luma en zet dit om in de vereiste indeling van het `productListItems` -object van het XDM-schema.

Zie de vergelijking hieronder van de gegevenslaag van de Luminasite (links) met het vertaalde gegevenselement (rechts) voor illustratie:

![&#x200B; XDM voorwerp matrixformaat &#x200B;](assets/data-element-xdm-array.png)

Vergelijk het gegevenselement met de `productListItems` -structuur (hint, it should match).

>[!IMPORTANT]
>
>Numerieke variabelen worden omgezet met tekenreekswaarden in de gegevenslaag, zoals `price` en `qty` , die opnieuw worden opgemaakt naar getallen in het gegevenselement. Deze formaatvereisten zijn belangrijk voor gegevensintegriteit in Platform en worden bepaald tijdens [&#x200B; vormen schema&#39;s &#x200B;](configure-schemas.md) stap. In het voorbeeld gebruikt **[!UICONTROL quantity]** het gegevenstype **[!UICONTROL Integer]** .
>&#x200B;> ![Gegevenstype XDM-schema &#x200B;](assets/set-up-analytics-quantity-integer.png)

Laten we nu onze array toewijzen aan het XDM-object:


1. Een nieuwe regel maken met de naam `ecommerce - library loaded - set shopping cart variables - 20`
1. Selecteer het ![+-symbool &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) onder Gebeurtenis om een nieuwe trigger toe te voegen
1. Onder **[!UICONTROL Extension]** selecteert u **[!UICONTROL Core]**
1. Onder **[!UICONTROL Event Type]** selecteert u **[!UICONTROL Library Loaded (Page Top)]**
1. Selecteren om **[!UICONTROL Advanced Options]** te openen, typ in `20`
1. Selecteren **[!UICONTROL Keep Changes]**

   ![&#x200B; de regels van Analytics XDM &#x200B;](assets/set-up-analytics-cart-sequence.png)

1. Onder **[!UICONTROL Conditions]** selecteert u **[!UICONTROL Add]**
1. **[!UICONTROL Logic Type]** behouden als **[!UICONTROL Regular]**
1. **[!UICONTROL Extensions]** behouden als **[!UICONTROL Core]**
1. **[!UICONTROL Condition Type]** selecteren als **[!UICONTROL Path Without Query String]**
1. Op het recht, **laat** niet **[!UICONTROL Regex]** knevel toe
1. Onder **[!UICONTROL path equals]** set `/content/luma/us/en/user/cart.html` . Voor de demo-site Luma zorgt deze optie ervoor dat de regel alleen triggers op de cartpagina bevat
1. Selecteren **[!UICONTROL Keep Changes]**

   ![&#x200B; de regels van Analytics XDM &#x200B;](assets/set-up-analytics-cart-condition.png)

1. Onder **[!UICONTROL Actions]** select **[!UICONTROL Add]**
1. Extensie **[!UICONTROL Adobe Experience Platform Web SDK]** selecteren
1. **[!UICONTROL Action Type]** selecteren als **[!UICONTROL Update variable]**
1. Selecteer `xdm.variable.content` als de **[!UICONTROL Data element]**
1. Schuif omlaag naar het `commerce` -object en selecteer dit om het te openen.
1. Open het object **[!UICONTROL productListViews]** en stel **[!UICONTROL value]** in op `1`

   ![&#x200B; de Mening van het opstellingsProduct &#x200B;](assets/set-up-analytics-cart-view.png)

   >[!TIP]
   >
   >Door commerce.productListViews.value=1 in XDM in te stellen, wordt automatisch toegewezen aan de gebeurtenis `scView` in Analytics

1. Selecteren `eventType` en instellen op `commerce.productListViews`

1. Omlaag schuiven naar en array selecteren **[!UICONTROL productListItems]**

1. Selecteren **[!UICONTROL Provide entire array]**

1. Toewijzen aan gegevenselement **`cart.productInfo`**

1. Selecteren **[!UICONTROL Keep Changes]**

1. Selecteer **[!UICONTROL Save]** om de regel op te slaan

Maak twee andere regels voor afhandeling en aankoop volgens hetzelfde patroon, met de onderstaande verschillen:

**Naam van de Regel**: `ecommerce  - library loaded - set checkout variables - 20`

1. **[!UICONTROL Condition]**: /content/luma/us/en/user/checkout.html
1. `eventType` instellen op `commerce.checkouts`
1. `commerce.checkout.value` instellen op `1`

   >[!TIP]
   >
   >Dit is gelijk aan het instellen van de gebeurtenis `scCheckout` in Analytics


**Naam van de Regel**: `ecommerce - library loaded - set purchase variables -  20`

1. **[!UICONTROL Condition]**: /content/luma/us/en/user/checkout/order/thank-you.html
1. `eventType` instellen op `commerce.purchases`
1. `commerce.purchases.value` instellen op `1`

   >[!TIP]
   >
   >Dit is gelijk aan het instellen van de gebeurtenis `purchase` in Analytics

1. `commerce.order.purchaseID` instellen op het gegevenselement `cart.orderId`
1. Stel `commerce.order.currencyCode` in op de hardcoded waarde `USD`

   ![&#x200B; Plaatsende purchaseID voor Analytics &#x200B;](assets/set-up-analytics-purchase.png)

   >[!TIP]
   >
   >Dit is gelijk aan het instellen van `s.purchaseID` - en `s.currencyCode` -variabelen in Analytics

1. Omlaag schuiven naar en array selecteren **[!UICONTROL productListItems]**
1. Selecteren **[!UICONTROL Provide entire array]**
1. Toewijzen aan gegevenselement **`cart.productInfo.purchase`**
1. Selecteren **[!UICONTROL Keep Changes]**
1. Selecteren **[!UICONTROL Save]**

Als u klaar bent, worden de volgende regels gemaakt.

![&#x200B; de regels van Analytics XDM &#x200B;](assets/set-up-analytics-rules.png)


### Gebeurtenisregel verzenden

Nu u de variabelen hebt ingesteld, kunt u de regel maken om het volledige XDM-object naar Platform Edge Network te verzenden met de handeling **[!UICONTROL Send event]** .

1. Selecteer aan de rechterkant **[!UICONTROL Add Rule]** om een andere regel te maken

1. Naam van de regel `all pages - library loaded - send event - 50`

1. Selecteer in de sectie **[!UICONTROL Events]** de optie **[!UICONTROL Add]**

1. Gebruik **[!UICONTROL Core Extension]** en selecteer `Library Loaded (Page Top)` als **[!UICONTROL Event Type]**

1. Selecteer **[!UICONTROL Advanced]** dropdown en ga `50` in **[!UICONTROL Order]** in. Zo zorgt u ervoor dat deze regel wordt geactiveerd na alle andere regels die u hebt geconfigureerd (met `1` of `20` als hun [!UICONTROL Order] ).

1. Selecteer **[!UICONTROL Keep Changes]** om terug te keren naar het hoofdregelscherm
   ![&#x200B; Uitgezochte Bibliotheek Geladen Trekker &#x200B;](assets/create-tag-rule-trigger-loaded-send.png)

1. Selecteer in de sectie **[!UICONTROL Actions]** de optie **[!UICONTROL Add]**

1. Als **[!UICONTROL Extension]** selecteert u **[!UICONTROL Adobe Experience Platform Web SDK]**

1. Als **[!UICONTROL Action Type]** selecteert u **[!UICONTROL Send event]**

1. Als **[!UICONTROL XDM]** selecteert u het gegevenselement `xdm.variable.content` dat in de vorige les is gemaakt

1. Selecteer **[!UICONTROL Keep Changes]** om terug te keren naar het hoofdregelscherm

   ![&#x200B; voeg de Send actie van de Gebeurtenis &#x200B;](assets/create-rule-send-event-action.png) toe
1. Selecteer **[!UICONTROL Save]** om de regel op te slaan

   ![&#x200B; sparen de regel &#x200B;](assets/create-rule-save-rule.png)

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
>Bedankt dat je tijd hebt geïnvesteerd in het leren over Adobe Experience Platform Web SDK. Als u vragen hebt, algemene terugkoppelen wilt delen, of suggesties over toekomstige inhoud hebben, gelieve hen op deze [&#x200B; Communautaire besprekingspost van Experience League te delen &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
