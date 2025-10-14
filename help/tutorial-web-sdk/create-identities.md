---
title: Identiteiten maken voor Platform Web SDK
description: Leer hoe u identiteiten in XDM maakt en het gegevenselement Identiteitskaart gebruikt om gebruikers-id's vast te leggen. Deze les maakt deel uit van de zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Web SDK, Tags, Identities
jira: KT-15402
exl-id: 7ca32dc8-dd86-48e0-8931-692bcbb2f446
source-git-commit: 7ccbaaf4db43921f07c971c485e1460a1a7f0334
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 0%

---

# Identiteiten maken

Leer hoe u identiteiten vastlegt met Adobe Experience Platform Web SDK. Vang zowel unauthenticated als voor authentiek verklaarde identiteitsgegevens over de [&#x200B; plaats van de de demo van de Luma &#x200B;](https://luma.enablementadobe.com/content/luma/us/en.html). Leer hoe te om de gegevenselementen te gebruiken u vroeger voor het verzamelen van voor authentiek verklaarde gegevens met een het gegevenselementtype van het Web SDK van het Platform riep Identiteitskaart creeerde.

Deze les richt zich op het element van de het kaartgegevens van de Identiteit beschikbaar met de de etikettenuitbreiding van Adobe Experience Platform Web SDK. U wijst gegevenselementen met een geverifieerde gebruikers-id en verificatiestatus toe aan XDM.

## Leerdoelstellingen

Aan het einde van deze les kunt u het volgende doen:

* De relatie tussen Experience Cloud-id (ECID) en FPID (First Party Device ID) begrijpen
* Het verschil begrijpen tussen niet-geverifieerde versus geverifieerde id&#39;s
* Een gegevenselement voor een identiteitsoverzicht maken

## Vereisten

U hebt inzicht in wat een gegevenslaag is, vertrouwd met de [&#x200B; de duimplaats van de Luma &#x200B;](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} gegevenslaag wordt, en weet hoe te om gegevenselementen in markeringen van verwijzingen te voorzien. U moet de vorige lessen in het leerprogramma hebben voltooid:

* [Een XDM-schema configureren](configure-schemas.md)
* [Naamruimte configureren](configure-identities.md)
* [Een gegevensstroom configureren](configure-datastream.md)
* [Web SDK-extensie geïnstalleerd in de eigenschap tag](install-web-sdk.md)
* [Gegevenselementen maken](create-data-elements.md)


## Experience Cloud-id

[&#x200B; identiteitskaart van Experience Cloud (ECID) &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/identity/features/ecid) is een gedeelde identiteit namespace die over de toepassingen van Adobe Experience Platform en van Adobe Experience Cloud wordt gebruikt. ECID vormt de basis voor de identiteit van de klant en is de standaardidentiteit voor digitale eigenschappen. ECID is de ideale id voor het bijhouden van niet-geverifieerd gebruikersgedrag, omdat deze altijd aanwezig is.

<!-- FYI I commented this out because it was breaking the build - Jack
>[!TIP]
>
> When you use the Experience Platform Web SDK to set up Adobe applications on your digital properties, the ECID is generated at the Adobe Edge server level. As such, ECID is not viewable on the client-side network request payload. You can view the ECID by seeing the Preview tab of the network request, or by using the [Adobe Experience Platform Debugger Edge Trace](set-up-analytics.md#experience-cloud-id-validation).
>![View ECID](assets/validate-dev-console-ecid.png)
-->

Lees meer over hoe [&#x200B; ECIDs gebruikend het Web SDK van het Platform &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/edge/identity/overview) wordt gevolgd.

ECID&#39;s worden ingesteld met behulp van een combinatie van eersteklas cookies en Platform Edge Network. Door gebrek, worden de eerste-partijidentiteitskoekjes geplaatst cliënt-kant door het Web SDK. Als u browserbeperkingen voor de levensduur van cookies wilt compenseren, kunt u ervoor kiezen om uw eigen server-side cookies met de identiteit van de eerste partij in te stellen. Deze identiteitscookies worden ook wel FPID&#39;s (FPID&#39;s) genoemd.

>[!IMPORTANT]
>
>De [&#x200B; uitbreiding van de Dienst van identiteitskaart van Experience Cloud &#x200B;](https://exchange.adobe.com/apps/ec/100160/adobe-experience-cloud-id-launch-extension) is niet nodig wanneer het uitvoeren van SDK van het Web van Adobe Experience Platform, aangezien de functionaliteit van de Dienst van identiteitskaart in SDK van het Web van het Platform wordt gebouwd.

## FPID (First Party Device ID)

FPIDs is eerste-partijkoekjes _u plaatst gebruikend uw eigen Webservers_ die Adobe dan gebruikt om ECID tot stand te brengen, in plaats van het gebruiken van het eerste partijkoekje dat door het Web SDK wordt geplaatst. Terwijl de browser steun kan variëren, neigen de eerderekookies duurzamer te zijn wanneer geplaatst door een server die een DNS A verslag (voor IPv4) of het verslag van AAA (voor IPv6) gebruikt, in tegenstelling tot wanneer geplaatst door een DNS CNAME of code van JavaScript.

Nadat een FPID-cookie is ingesteld, kan de waarde ervan worden opgehaald en naar Adobe worden verzonden wanneer gebeurtenisgegevens worden verzameld. Verzamelde FPID&#39;s worden gebruikt als zaden om ECID&#39;s te genereren op Platform Edge Network, die de standaard-id&#39;s blijven in Adobe Experience Cloud-toepassingen.

Hoewel FPIDs niet in deze zelfstudie wordt gebruikt, wordt u aangemoedigd om FPIDs in uw eigen implementatie van SDK van het Web te gebruiken. Lees meer over [&#x200B; het apparaat IDs van de Eerste partij in het Web SDK van het Platform &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/edge/identity/first-party-device-ids)

>[!CAUTION]
>
> FPID is een alternatieve manier om de ECID te genereren met behulp van een cookie die door uw webservers is ingesteld. Het wordt niet gebruikt voor het identificeren van geverifieerde gebruikers.

## Geverifieerde id

Zoals hierboven vermeld, wordt aan alle bezoekers van uw digitale eigenschappen een ECID toegewezen door Adobe bij het gebruik van Platform Web SDK. ECID is de standaardidentiteit voor het bijhouden van niet-geverifieerd digitaal gedrag.

U kunt een voor authentiek verklaarde gebruikersidentiteitskaart ook verzenden zodat het Platform [&#x200B; Grafieken van de Identiteit &#x200B;](https://experienceleague.adobe.com/nl/docs/platform-learn/tutorials/identities/understanding-identity-and-identity-graphs) kan tot stand brengen en het Doel kan zijn [&#x200B; Identiteitskaart van de Derde &#x200B;](https://experienceleague.adobe.com/nl/docs/target/using/audiences/visitor-profiles/3rd-party-id) plaatsen. Het instellen van de geverifieerde id gebeurt met behulp van het gegevenstype [!UICONTROL Identity Map] data element.

Het gegevenselement [!UICONTROL Identity Map] maken:

1. Ga naar **[!UICONTROL Data Elements]** en selecteer **[!UICONTROL Add Data Element]**

1. **[!UICONTROL Name]** Het gegevenselement `identityMap.loginID`

1. Als **[!UICONTROL Extension]** selecteert u `Adobe Experience Platform Web SDK`

1. Als **[!UICONTROL Data Element Type]** selecteert u `Identity map`

1. Hierdoor wordt rechts in de **[!UICONTROL Data Collection interface]** een schermgebied voor u gevraagd om de identiteit te configureren:

   ![&#x200B; de interface van de Inzameling van Gegevens &#x200B;](assets/identity-identityMap-setup.png)

1. Als **[!UICONTROL Namespace]**, selecteer `lumaCrmId` namespace die u eerder in [&#x200B; creeerde vormen de 3&rbrace; les van Identiteiten &lbrace;vormt. &#x200B;](configure-identities.md) Als deze niet in de vervolgkeuzelijst wordt weergegeven, typt u deze.

1. Nadat **[!UICONTROL Namespace]** is geselecteerd, moet een id worden ingesteld. Selecteer het `user.profile.attributes.username` gegevenselement dat vroeger in [&#x200B; wordt gecreeerd creeer gegevenselementen &#x200B;](create-data-elements.md#create-data-elements-to-capture-the-data-layer) les, die een identiteitskaart vangt wanneer de gebruikers in de plaats van de Luma worden geregistreerd.

   <!--  >[!TIP]
    >
    >You can verify the **[!UICONTROL Luma CRM ID]** is collected in a data element on the web property by going to the [Luma Demo site](https://luma.enablementadobe.com/content/luma/us/en.html), logging in, [switching the tag environment](validate-with-debugger.md#use-the-experience-platform-debugger-to-map-to-your-tag-property) to your own, and typing `_satellite.getVar("user.profile.attributes.username")` in the web browser developer console.
    >
    >   ![Data Element  ID ](assets/identity-data-element-customer-id.png)
    -->

1. Als **[!UICONTROL Authenticated state]** selecteert u **[!UICONTROL Authenticated]**
1. Selecteren **[!UICONTROL Primary]**

1. Selecteren **[!UICONTROL Save]**

   ![&#x200B; de interface van de Inzameling van Gegevens &#x200B;](assets/identity-id-namespace.png)

>[!TIP]
>
> Adobe raadt aan identiteiten die een persoon, zoals `Luma CRM Id` , vertegenwoordigen, als de [!UICONTROL primary] -identiteit te verzenden.
>
> Als het identiteitsoverzicht de persoon-id bevat (bijvoorbeeld `Luma CRM Id` ), wordt de persoon-id de [!UICONTROL primary] identity. Anders wordt `ECID` de [!UICONTROL primary] identiteit.




<!--
1. Once the data element is configured in **[!UICONTROL Data Collection interface]**, it can be tested on the Luma web property like any other Data Element. Enter the following script in the browser developer console
   
   
   ```
   _satellite.getVar('identityMap.loginID')
   ```  

   ![Data Collection interface](assets/identity-consoleIdentityDataElement.png)
   
   >[!NOTE]
   >
   >ECID identifier will NOT populate in the Data Element, as this is configured already with Platform Web SDK.   
-->

Aan het einde van deze stappen moeten de volgende gegevenselementen worden gemaakt:

| Core Extension Data Elements | Platform Web SDK Extension Data Elements |
-----------------------------|-------------------------------
| `cart.orderId` | `data.variable` |
| `cart.productInfo` | `identityMap.loginID` |
| `cart.productInfo.purchase` | `xdm.variable.content` |
| `page.pageInfo.hierarchie1` | |
| `page.pageInfo.pageName` | |
| `page.pageInfo.server` | |
| `product.category` | |
| `product.productInfo.sku` | |
| `product.productInfo.title` | |
| `user.profile.attributes.loggedIn` | |
| `user.profile.attributes.username` | |

Met deze gegevenselementen op zijn plaats, bent u klaar om gegevens naar Platform Edge Network te verzenden door een regel in markeringen te creëren.

>[!NOTE]
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren over Adobe Experience Platform Web SDK. Als u vragen hebt, algemene terugkoppelen wilt delen, of suggesties over toekomstige inhoud hebben, gelieve hen op deze [&#x200B; Communautaire besprekingspost van Experience League te delen &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
