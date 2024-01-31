---
title: Tagregels maken
description: Leer hoe u een gebeurtenis naar het Platform Edge Network kunt verzenden met uw XDM-object aan de hand van een tagregel. Deze les maakt deel uit van de Zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Tags
source-git-commit: aff41fd5ecc57c9c280845669272e15145474e50
workflow-type: tm+mt
source-wordcount: '2005'
ht-degree: 0%

---

# Tagregels maken

Leer hoe u gebeurtenissen naar het Platform Edge Network kunt verzenden met uw XDM-object aan de hand van tagregels. Een labelregel is een combinatie van gebeurtenissen, voorwaarden en handelingen die de eigenschap van de tag opgeeft iets te doen.

>[!NOTE]
>
> Voor demonstratiedoeleinden bouwen de oefeningen in deze les op het voorbeeld dat tijdens wordt gebruikt [Identiteiten maken](create-identities.md) stap; verzenden van een XDM-gebeurtenisactie om inhoud en identiteiten van gebruikers op de [Luma-demosite](https://luma.enablementadobe.com/content/luma/us/en.html).


## Leerdoelstellingen

Aan het einde van deze les kunt u het volgende doen:

* Een naamgevingsconventie gebruiken voor het beheer van regels binnen tags
* Verzend een XDM-gebeurtenis met de actietypen Variabele bijwerken en Gebeurtenis verzenden in een tagregel
* Een labelregel publiceren naar een ontwikkelingsbibliotheek


## Vereisten

U bent vertrouwd met de tags voor gegevensverzameling en de [Luma-demosite](https://luma.enablementadobe.com/content/luma/us/en.html)en u moet de volgende lessen uit het verleden hebben geleerd in de zelfstudie:

* [Een XDM-schema configureren](configure-schemas.md)
* [Naamruimte configureren](configure-identities.md)
* [Een gegevensstroom configureren](configure-datastream.md)
* [Web SDK-extensie geïnstalleerd in de eigenschap Tag](install-web-sdk.md)
* [Gegevenselementen maken](create-data-elements.md)
* [Identiteiten maken](create-identities.md)

## Naamgevingsconventies

Voor een beter beheer van de regels in tags is het raadzaam een standaardnaamgevingsconventie te volgen. In deze zelfstudie wordt een naamgevingsconventie gebruikt die uit drie delen bestaat:

* [**locatie**] - [**event**] - [**gereedschap**] (**opeenvolging**)

waar;

1. **locatie** is de pagina of pagina&#39;s op de plaats waar de regel wordt geactiveerd
1. **event** is de trigger voor de regel
1. **gereedschap** is de specifieke toepassing of toepassingen die in de actiestap voor die regel worden gebruikt
1. **opeenvolging** is de volgorde waarin de regel ten opzichte van andere regels moet worden toegepast
<!-- minor update -->

## Tagregels maken

In tags worden regels gebruikt om handelingen (aanroepen naar brand) onder verschillende omstandigheden uit te voeren. De de etikettenuitbreiding van SDK van het Web van het Platform omvat twee acties die in deze les zullen worden gebruikt:

* **[!UICONTROL Variabele bijwerken]** koppelen gegevenselementen aan XDM-velden
* **[!UICONTROL Gebeurtenis verzenden]** Hiermee wordt het XDM-object naar het Edge Network-Experience Platform verzonden

Eerst definiëren we een regel met de **[!UICONTROL Variabele bijwerken]** handeling, die een &quot;globale configuratie&quot;van XDM gebieden bepaalt wij op elke pagina van de plaats (bijvoorbeeld, de paginanaam) willen verzenden.

Vervolgens kunnen we aanvullende regels definiëren met de **[!UICONTROL Variabele bijwerken]** handeling die de globale XDM-velden aanvult met extra velden die alleen onder bepaalde omstandigheden beschikbaar zijn (bijvoorbeeld productdetails toevoegen op productpagina&#39;s).

Tot slot zullen wij met de **[!UICONTROL Gebeurtenis verzenden]** handeling die het volledige XDM-object naar Adobe Experience Platform Edge Network verzendt.


### Regels voor variabelen bijwerken

#### Algemene velden

Een labelregel maken voor de globale XDM-velden:

1. Open de eigenschap tag die u voor deze zelfstudie gebruikt

1. Ga naar **[!UICONTROL Regels]** in de linkernavigatie

1. Selecteer de **[!UICONTROL Nieuwe regel maken]** knop

   ![Een regel maken](assets/rules-create.png)

1. Naam van de regel `all pages global content variables - page bottom - AA (order 1)`

1. In de **[!UICONTROL Gebeurtenissen]** sectie, selecteert u **[!UICONTROL Toevoegen]**

   ![Geef de regel een naam en voeg een gebeurtenis toe](assets/rule-name-new.png)

1. Gebruik de **[!UICONTROL Core Extension]** en selecteert u `Page Bottom` als de **[!UICONTROL Type gebeurtenis]**

1. Onder de **[!UICONTROL Naam]** veld, naam geven `Core - Page Bottom - order 1`. Hierdoor kunt u de trigger met een betekenisvolle naam beschrijven.

1. Selecteren **[!UICONTROL Geavanceerd]** vervolgkeuzelijst en Enter `1` in **[!UICONTROL Volgorde]**

   >[!NOTE]
   >
   > Hoe hoger het getal dat u invoert, hoe hoger de bewerking in de algemene volgorde waarin deze wordt geactiveerd.

1. Selecteren **[!UICONTROL Wijzigingen behouden]** om op het belangrijkste regelscherm terug te keren
   ![Trigger onder pagina selecteren](assets/create-tag-rule-trigger-bottom.png)

1. In de **[!UICONTROL Handelingen]** sectie, selecteert u **[!UICONTROL Toevoegen]**

1. Als de **[!UICONTROL Extensie]**, selecteert u **[!UICONTROL Adobe Experience Platform Web SDK]**

1. Als de **[!UICONTROL Type handeling]**, selecteert u **[!UICONTROL Variabele bijwerken]**

1. Als de **[!UICONTROL Gegevenselement]**, selecteert u de `xdm.variable.content` u in [Gegevenselementen maken](create-data-elements.md) les

   ![Variabel schema bijwerken](assets/create-rule-update-variable.png)

Wijs nu uw [!UICONTROL gegevenselementen] aan de [!UICONTROL schema] wordt gebruikt door uw XDM-object.

>[!NOTE]
> 
> U kunt toewijzen aan afzonderlijke eigenschappen of volledige objecten. In dit voorbeeld wijst u een afbeelding toe aan afzonderlijke eigenschappen.


1. Schuif omlaag totdat u de **`web`** object

1. Selecteren om te openen

1. Wijs de volgende gegevenselementen toe aan de overeenkomstige `web` XDM-variabelen

   * **`web.webPageDetials.name`** tot `%page.pageInfo.pageName%`
   * **`web.webPageDetials.server`** tot `%page.pageInfo.server%`
   * **`web.webPageDetials.siteSection`** tot `%page.pageInfo.hierarchie1%`

1. Set `web.webPageDetials.pageViews.value` tot `1`

   ![Variabele inhoud bijwerken](assets/create-rule-xdm-variable-content.png)

1. Zoek vervolgens de `identityMap` object in het schema en selecteer het

1. Toewijzen aan `identityMap.loginID` gegevenselement

   ![Variabele-identiteitskaart bijwerken](assets/create-rule-variable-identityMap.png)

1. Zoek vervolgens het veld eventType en selecteer dit.

1. Voer de waarde in `web.webpagedetails.pageViews`

   >[!WARNING]
   >
   > In dit vervolgkeuzemenu worden de **`xdm.eventType`** in het XDM-object. Hoewel u in dit veld ook vrije-formulierlabels kunt typen, wordt u ten zeerste aangeraden **niet** omdat het negatieve effecten heeft op Platform.

   >[!TIP]
   >
   > Om te begrijpen welke waarden in te vullen `eventType` veld, moet u naar de schemapagina gaan en de `eventType` veld om de voorgestelde waarden op het rechterspoor weer te geven.

   >[!TIP]
   >
   > while `web.webPageDetials.pageViews.value` noch `eventType` instellen op `web.webpagedetails.pageViews` Adobe Analytics is vereist om een baken als paginaweergave te verwerken. Het is handig om over een standaardmanier te beschikken om een paginaweergave voor andere downstreamtoepassingen aan te geven.

   ![Variabele-identiteitskaart bijwerken](assets/create-tag-rule-eventType.png)


1. Selecteren **[!UICONTROL Wijzigingen behouden]** en vervolgens **[!UICONTROL Opslaan]** de regel in het volgende scherm om het maken van de regel te voltooien


#### Verrijk het voorwerp XDM gebruikend extra regels met de Update veranderlijke actie

U kunt **[!UICONTROL Variabele bijwerken]**  in meerdere, gerangschikte regels om het XDM-object te verrijken voordat het naar [!UICONTROL Platform Edge Network].

>[!TIP]
>
>De regelvolgorde bepaalt welke regel het eerst wordt uitgevoerd wanneer een gebeurtenis wordt geactiveerd. Als twee regels hetzelfde gebeurtenistype hebben, wordt eerst de regel met het laagste getal uitgevoerd.
> 
>![regelvolgorde](assets/set-up-analytics-sequencing.png)

##### Productpaginavelden

Eerst volgt u de productweergaven op de pagina met productdetails van Luma:

1. Selecteren **[!UICONTROL Regel toevoegen]**
1. Naam geven  [!UICONTROL `ecommerce - pdp page bottom - AA (order 20)`]
1. Selecteer de ![+ symbool](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) onder Gebeurtenis om een nieuwe trigger toe te voegen
1. Onder **[!UICONTROL Extensie]**, selecteert u **[!UICONTROL Kern]**
1. Onder **[!UICONTROL Type gebeurtenis]**, selecteert u **[!UICONTROL Pagina onder]**
1. Naam geven `Core - Page Bottom - order 20`
1. Selecteren om te openen **[!UICONTROL Geavanceerde opties]**, typt u `20`. Dit verzekert de regellooppas na `all pages global content variables - page bottom - AA (order 1)` dat de globale inhoudsvariabelen plaatst, maar vóór `all pages send event - page bottom - AA (order 50)` die de XDM-gebeurtenis verzendt.

   ![XDM-regels voor analyse](assets/set-up-analytics-pdp.png)

1. Onder **[!UICONTROL Voorwaarden]**, selecteert u **[!UICONTROL Toevoegen]**
1. Verlaten **[!UICONTROL Logische typen]** als **[!UICONTROL Standaard]**
1. Verlaten **[!UICONTROL Extensies]** als **[!UICONTROL Kern]**
1. Selecteren **[!UICONTROL Type voorwaarde]** als **[!UICONTROL Pad zonder queryreeks]**
1. Schakel rechts de optie **[!UICONTROL Regex]** schakelen
1. Onder **[!UICONTROL pad is gelijk aan]** set `/products/`. Voor de Luma-demo-site zorgt deze ervoor dat de regel alleen op productpagina&#39;s wordt geactiveerd
1. Selecteren **[!UICONTROL Wijzigingen behouden]**

   ![XDM-regels voor analyse](assets/set-up-analytics-product-condition.png)

1. Onder **[!UICONTROL Handelingen]** selecteren **[!UICONTROL Toevoegen]**
1. Selecteren **[!UICONTROL Adobe Experience Platform Web SDK]** extension
1. Selecteren **[!UICONTROL Type handeling]** als **[!UICONTROL Variabele bijwerken]**
1. Omlaag schuiven naar de `commerce` en selecteert u deze om het te openen.
1. Open de **[!UICONTROL productViews]** object en set **[!UICONTROL value]** tot `1`

   ![Productweergave instellen](assets/set-up-analytics-prodView.png)

   >[!TIP]
   >
   >Het plaatsen van commerce.productViews.value=1 in XDM brengt automatisch aan `prodView` gebeurtenis in Analytics


1. Omlaag schuiven naar en selecteren `productListItems` array
1. Selecteren **[!UICONTROL Afzonderlijke items opgeven]**
1. Selecteren **[!UICONTROL Item toevoegen]**

   ![Weergavegebeurtenis product instellen](assets/set-up-analytics-xdm-individual.png)

   >[!CAUTION]
   >
   >De **`productListItems`** is een `array` gegevenstype zodat verwacht het gegevens binnen als inzameling van elementen komen. Vanwege de gegevenslaagstructuur van de demo-site van Luma en omdat het alleen mogelijk is om één product tegelijk weer te geven op de Luministsite, voegt u afzonderlijke items toe. Afhankelijk van de structuur van de gegevenslaag kunt u bij de implementatie op uw eigen website mogelijk een volledige array opgeven.

1. Selecteren om te openen **[!UICONTROL Item 1]**
1. Kaart **`productListItems.item1.SKU`** tot `%product.productInfo.sku%`

   ![Product SKU XDM-objectvariabele](assets/set-up-analytics-sku.png)

1. Zoeken `eventType` en stel deze in op `commerce.productViews`

1. Selecteren **[!UICONTROL Wijzigingen behouden]**

1. Selecteren **[!UICONTROL Opslaan]** om de regel op te slaan




### Kaarten weergeven

U kunt een volledige array toewijzen aan een XDM-object, mits de array overeenkomt met de indeling van het XDM-schema. Het gegevenselement van de aangepaste code `cart.productInfo` u hebt eerdere lussen gemaakt via de `digitalData.cart.cartEntries` gegevenslaagobject op Luma en zet dit om in de vereiste indeling van het `productListItems` object van het XDM-schema.

Zie de vergelijking hieronder van de gegevenslaag van de Luminasite (links) met het vertaalde gegevenselement (rechts) voor illustratie:

![XDM-objectmatrixindeling](assets/data-element-xdm-array.png)

Vergelijk het gegevenselement met de `productListItems` structuur (hint, it should match).

>[!IMPORTANT]
>
>Numerieke variabelen worden omgezet met tekenreekswaarden in de gegevenslaag, zoals `price` en `qty` opnieuw opgemaakt naar getallen in het gegevenselement. Deze formaatvereisten zijn belangrijk voor gegevensintegriteit in Platform en worden bepaald tijdens [vormen schema&#39;s](configure-schemas.md) stap. In het voorbeeld: **[!UICONTROL hoeveelheid]** gebruikt de **[!UICONTROL Geheel]** gegevenstype.
> ![Gegevenstype XDM-schema](assets/set-up-analytics-quantity-integer.png)

Laten we nu onze array toewijzen aan het XDM-object&quot;


1. Een nieuwe regel maken met de naam `ecommerce - cart page bottom - AA (order 20)`
1. Selecteer de ![+ symbool](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) onder Gebeurtenis om een nieuwe trigger toe te voegen
1. Onder **[!UICONTROL Extensie]**, selecteert u **[!UICONTROL Kern]**
1. Onder **[!UICONTROL Type gebeurtenis]**, selecteert u **[!UICONTROL Pagina onder]**
1. Naam geven `Core - Page Bottom - order 20`
1. Selecteren om te openen **[!UICONTROL Geavanceerde opties]**, typt u `20`
1. Selecteren **[!UICONTROL Wijzigingen behouden]**

   ![XDM-regels voor analyse](assets/set-up-analytics-cart-sequence.png)

1. Onder **[!UICONTROL Voorwaarden]**, selecteert u **[!UICONTROL Toevoegen]**
1. Verlaten **[!UICONTROL Logische typen]** als **[!UICONTROL Standaard]**
1. Verlaten **[!UICONTROL Extensies]** als **[!UICONTROL Kern]**
1. Selecteren **[!UICONTROL Type voorwaarde]** als **[!UICONTROL Pad zonder queryreeks]**
1. Rechts **niet** de **[!UICONTROL Regex]** schakelen
1. Onder **[!UICONTROL pad is gelijk aan]** set `/content/luma/us/en/user/cart.html`. Voor de demo-site Luma zorgt deze optie ervoor dat de regel alleen triggers op de cartpagina bevat
1. Selecteren **[!UICONTROL Wijzigingen behouden]**

   ![XDM-regels voor analyse](assets/set-up-analytics-cart-condition.png)

1. Onder **[!UICONTROL Handelingen]** selecteren **[!UICONTROL Toevoegen]**
1. Selecteren **[!UICONTROL Adobe Experience Platform Web SDK]** extension
1. Selecteren **[!UICONTROL Type handeling]** als **[!UICONTROL Variabele bijwerken]**
1. Omlaag schuiven naar de `commerce` en selecteert u deze om het te openen.
1. Open de **[!UICONTROL productListViews]** object en set **[!UICONTROL value]** tot `1`

   ![Productweergave instellen](assets/set-up-analytics-cart-view.png)

   >[!TIP]
   >
   >Het plaatsen van commerce.productListViews.value=1 in XDM brengt automatisch aan toe `scView` gebeurtenis in Analytics



1. Omlaag schuiven naar en selecteren **[!UICONTROL productListItems]** array

1. Selecteren **[!UICONTROL Volledige array opgeven]**

1. Toewijzen aan **`cart.productInfo`** gegevenselement

1. Selecteren `eventType` en instellen op `commerce.productListViews`

1. Selecteren **[!UICONTROL Wijzigingen behouden]**

1. Selecteren **[!UICONTROL Opslaan]** om de regel op te slaan

Maak twee andere regels voor afhandeling en aankoop volgens hetzelfde patroon, met de onderstaande verschillen:

**Naam van regel**: `ecommerce - checkout page bottom - AA (order 20)`

* **[!UICONTROL Voorwaarde]**: /content/luma/us/en/user/checkout.html
* Set `eventType` tot `commerce.checkouts`
* Set **XDM Commerce, gebeurtenis**: commerce.checkout.value to `1`

  >[!TIP]
  >
  >Dit is gelijk aan de instelling `scCheckout` gebeurtenis in Analytics

**Naam van regel**: `ecommerce - purchase page bottom - AA (order 20)`

* **[!UICONTROL Voorwaarde]**: /content/luma/us/en/user/checkout/order/thank-you.html
* Set `eventType` tot `commerce.purchases`
* Set **XDM Commerce, gebeurtenis**: commerce.purchase.value to `1`

  >[!TIP]
  >
  >Dit is gelijk aan de instelling `purchase` gebeurtenis in Analytics

Er zijn aanvullende stappen voor het vastleggen van alle vereiste `purchase` gebeurtenisvariabelen:

1. Openen **[!UICONTROL handel]** object
1. Open de **[!UICONTROL bestellen]** object
1. Kaart **[!UICONTROL purchaseID]** aan de `cart.orderId` gegevenselement
1. Set **[!UICONTROL currencyCode]** op de hardcoderingswaarde `USD`

   ![Aankoop-id instellen voor Analytics](assets/set-up-analytics-purchase.png)

   >[!TIP]
   >
   >Dit is gelijk aan de instelling `s.purchaseID` en `s.currencyCode` variabelen in Analytics


1. Omlaag schuiven naar en selecteren **[!UICONTROL productListItems]** array
1. Selecteren **[!UICONTROL Volledige array opgeven]**
1. Toewijzen aan **`cart.productInfo.purchase`** gegevenselement
1. Selecteren **[!UICONTROL Opslaan]**

Als u klaar bent, worden de volgende regels gemaakt.

![XDM-regels voor analyse](assets/set-up-analytics-rules.png)


### Gebeurtenis Send

Nu u de variabelen hebt ingesteld, kunt u de tweede regel maken om het XDM-object naar Platform Edge Network te verzenden met de **[!UICONTROL Gebeurtenis Send]** actietype.

1. Selecteer rechts de optie **[!UICONTROL Regel toevoegen]** om een andere regel te creëren

1. Naam van de regel `all pages send event - page bottom - AA (order 50)`

1. In de **[!UICONTROL Gebeurtenissen]** sectie, selecteert u **[!UICONTROL Toevoegen]**

1. Gebruik de **[!UICONTROL Core Extension]** en selecteert u `Page Bottom` als de **[!UICONTROL Type gebeurtenis]**

1. Onder de **[!UICONTROL Naam]** veld, naam geven `Core - Page Bottom - order 50`. Hierdoor kunt u de trigger met een betekenisvolle naam beschrijven.

1. Selecteren **[!UICONTROL Geavanceerd]** vervolgkeuzelijst en Enter `50` in **[!UICONTROL Volgorde]**. Dit zorgt ervoor dat de tweede regel wordt geactiveerd na de eerste regel die u hebt ingesteld om te activeren als `1`.

1. Selecteren **[!UICONTROL Wijzigingen behouden]** om op het belangrijkste regelscherm terug te keren
   ![Trigger onder pagina selecteren](assets/create-tag-rule-trigger-bottom-send.png)

1. In de **[!UICONTROL Handelingen]** sectie, selecteert u **[!UICONTROL Toevoegen]**

1. Als de **[!UICONTROL Extensie]**, selecteert u  **[!UICONTROL Adobe Experience Platform Web SDK]**

1. Als de  **[!UICONTROL Type handeling]**, selecteert u  **[!UICONTROL Gebeurtenis Send]**

1. Als de **[!UICONTROL XDM]**, selecteert u de `xdm.variable.content` gegevenselement dat in de vorige les is gemaakt

1. Selecteren **[!UICONTROL Wijzigingen behouden]** om op het belangrijkste regelscherm terug te keren

   ![De handeling Verzendgebeurtenis toevoegen](assets/create-rule-send-event-action.png)
1. Selecteren **[!UICONTROL Opslaan]** om de regel op te slaan

   ![De regel opslaan](assets/create-rule-save-rule.png)

## De regel in een bibliotheek publiceren

Vervolgens publiceert u de regel naar de ontwikkelomgeving, zodat u kunt controleren of deze werkt.

Een bibliotheek maken:

1. Ga naar **[!UICONTROL Publishing Flow]** in de linkernavigatie

1. Selecteren **[!UICONTROL Bibliotheek toevoegen]**

   ![Bibliotheek toevoegen selecteren](assets/rule-publish-library.png)
1. Voor de **[!UICONTROL Naam]**, enter `Luma Web SDK Tutorial`
1. Voor de **[!UICONTROL Omgeving]**, selecteert u `Development`
1. Selecteren  **[!UICONTROL Alle gewijzigde bronnen toevoegen]**

   >[!NOTE]
   >
   >    Naast de Adobe Experience Platform Web SDK-extensie en de `all pages global content variables - page bottom - AA (order 50)` regel, ziet u de markeringscomponenten die in vorige lessen worden gecreeerd. De Core-extensie bevat de basis-JavaScript die is vereist voor alle eigenschappen van webtags.

1. Selecteren **[!UICONTROL Opslaan en bouwen voor ontwikkeling]**

   ![De bibliotheek maken en bouwen](assets/create-tag-rule-library-changes.png)

Het kan enkele minuten duren voordat de bibliotheek is gemaakt en wanneer deze is voltooid, wordt links van de naam van de bibliotheek een groene stip weergegeven:

![Samenstellen voltooid](assets/create-rule-development-success.png)

Zoals u kunt zien op het tabblad [!UICONTROL Publishing Flow] screen, is er veel meer aan het het publiceren proces dat buiten het werkingsgebied van deze zelfstudie is. Deze zelfstudie gebruikt slechts één bibliotheek in uw ontwikkelomgeving.

Nu bent u bereid om de gegevens in het verzoek te bevestigen gebruikend het Adobe Experience Platform Debugger.

[Volgende ](validate-with-debugger.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over de SDK van Adobe Experience Platform Web. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
