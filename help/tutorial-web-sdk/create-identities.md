---
title: Identiteiten maken voor Platform Web SDK
description: Leer hoe u identiteiten in XDM maakt en het gegevenselement Identiteitskaart gebruikt om gebruikers-id's vast te leggen. Deze les maakt deel uit van de Zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Web SDK, Tags, Identities
jira: KT-15402
exl-id: 7ca32dc8-dd86-48e0-8931-692bcbb2f446
source-git-commit: c5318809bfd475463bac3c05d4f35138fb2d7f28
workflow-type: tm+mt
source-wordcount: '848'
ht-degree: 0%

---

# Identiteiten maken

Leer hoe u identiteiten vastlegt met Adobe Experience Platform Web SDK. Leg niet-geverifieerde en geverifieerde identiteitsgegevens vast op het tabblad [Luma-demosite](https://luma.enablementadobe.com/content/luma/us/en.html). Leer hoe te om de gegevenselementen te gebruiken u vroeger voor het verzamelen van voor authentiek verklaarde gegevens met een het gegevenselementtype van SDK van het Web van het Platform riep Identiteitskaart creeerde.

Deze les richt zich op het element van de het kaartgegevens van de Identiteit beschikbaar met de de etikettenuitbreiding van SDK van het Web van Adobe Experience Platform. U wijst gegevenselementen met een geverifieerde gebruikers-id en verificatiestatus toe aan XDM.

## Leerdoelstellingen

Aan het einde van deze les kunt u het volgende doen:

* Begrijp het verband tussen Experience Cloud ID (ECID) en eerste partij Apparaat ID (FPID)
* Het verschil begrijpen tussen niet-geverifieerde versus geverifieerde id&#39;s
* Een gegevenselement voor een identiteitsoverzicht maken

## Vereisten

U hebt inzicht in wat een gegevenslaag is, u bent vertrouwd met de [Luma-demosite](https://luma.enablementadobe.com/content/luma/us/en.html){target="_blank"} en weet hoe u naar gegevenselementen in tags kunt verwijzen. U moet de vorige lessen in het leerprogramma hebben voltooid:

* [Een XDM-schema configureren](configure-schemas.md)
* [Naamruimte configureren](configure-identities.md)
* [Een gegevensstroom configureren](configure-datastream.md)
* [Web SDK-extensie geïnstalleerd in de eigenschap Tag](install-web-sdk.md)
* [Gegevenselementen maken](create-data-elements.md)


## Experience Cloud-id

De [Experience Cloud-id (ECID)](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/ecid) is een naamruimte voor gedeelde identiteit die wordt gebruikt in Adobe Experience Platform- en Adobe Experience Cloud-toepassingen. ECID vormt de basis voor de identiteit van de klant en is de standaardidentiteit voor digitale eigenschappen. ECID is de ideale id voor het bijhouden van niet-geverifieerd gebruikersgedrag, omdat deze altijd aanwezig is.

<!-- FYI I commented this out because it was breaking the build - Jack
>[!TIP]
>
> When you use the Experience Platform Web SDK to set up Adobe applications on your digital properties, the ECID is generated at the Adobe Edge server level. As such, ECID is not viewable on the client-side network request payload. You can view the ECID by seeing the Preview tab of the network request, or by using the [Adobe Experience Platform Debugger Edge Trace](set-up-analytics.md#experience-cloud-id-validation).
>![View ECID](assets/validate-dev-console-ecid.png)
-->

Meer informatie over hoe [ECIDs wordt gevolgd gebruikend het Web SDK van het Platform](https://experienceleague.adobe.com/en/docs/experience-platform/edge/identity/overview).

ECID&#39;s worden ingesteld met behulp van een combinatie van cookies van de eerste fabrikant en Platform Edge Network. Door gebrek, worden de koekjes van de eerste-partijidentiteit geplaatst cliënt-kant door het Web SDK. Als u browserbeperkingen voor de levensduur van cookies wilt compenseren, kunt u ervoor kiezen om uw eigen server-side cookies met de identiteit van de eerste partij in te stellen. Deze identiteitscookies worden ook wel FPID&#39;s (FPID&#39;s) genoemd.

>[!IMPORTANT]
>
>De [Experience Cloud ID Service-extensie](https://exchange.adobe.com/apps/ec/100160/adobe-experience-cloud-id-launch-extension) is niet nodig wanneer het uitvoeren van het Web SDK van Adobe Experience Platform, aangezien de functionaliteit van de Dienst van identiteitskaart in het Web SDK van het Platform wordt gebouwd.

## FPID (First Party Device ID)

FPID&#39;s zijn cookies van de eerste fabrikant _u kunt instellen met uw eigen webservers_ welke Adobe dan gebruikt om ECID tot stand te brengen, in plaats van het eerste partijkoekje te gebruiken dat door SDK van het Web wordt geplaatst. Terwijl de browser steun kan variëren, neigen de eerderekookies duurzamer te zijn wanneer geplaatst door een server die een DNS A verslag (voor IPv4) of het verslag van AAA (voor IPv6) gebruikt, in tegenstelling tot wanneer geplaatst door een DNS CNAME of code JavaScript.

Nadat een FPID-cookie is ingesteld, kan de waarde ervan worden opgehaald en naar de Adobe worden verzonden wanneer gebeurtenisgegevens worden verzameld. Verzamelde FPID&#39;s worden gebruikt als zaden om ECID&#39;s te genereren op Platform Edge Network, die de standaard-id&#39;s blijven in Adobe Experience Cloud-toepassingen.

Hoewel FPIDs niet in dit leerprogramma wordt gebruikt, wordt u aangemoedigd om FPIDs in uw eigen implementatie van SDK van het Web te gebruiken. Meer informatie over [Eerste partij apparaat IDs in het Web SDK van het Platform](https://experienceleague.adobe.com/en/docs/experience-platform/edge/identity/first-party-device-ids)

>[!CAUTION]
>
> FPID is een alternatieve manier om de ECID te genereren met behulp van een cookie die door uw webservers is ingesteld. Het wordt niet gebruikt voor het identificeren van geverifieerde gebruikers.

## Geverifieerde id

Zoals hierboven vermeld, wordt aan alle bezoekers van uw digitale eigenschappen een ECID toegewezen door Adobe wanneer het gebruiken van het Web SDK van het Platform. ECID the default identity for tracking unauthenticated digital behavior.

U kunt ook een geverifieerde gebruikers-id verzenden, zodat Platform [Identiteitsgrafiek](https://experienceleague.adobe.com/en/docs/platform-learn/tutorials/identities/understanding-identity-and-identity-graphs) en Target kan zijn [Id van derde partij](https://experienceleague.adobe.com/en/docs/target/using/audiences/visitor-profiles/3rd-party-id). Het plaatsen van voor authentiek verklaarde identiteitskaart wordt gedaan door te gebruiken [!UICONTROL Identity Map] type gegevenselement.

Als u de opdracht [!UICONTROL Identity Map] gegevenselement:

1. Ga naar **[!UICONTROL Data Elements]** en selecteert u **[!UICONTROL Add Data Element]**

1. **[!UICONTROL Name]** het gegevenselement `identityMap.loginID`

1. Als de **[!UICONTROL Extension]**, selecteert u `Adobe Experience Platform Web SDK`

1. Als de **[!UICONTROL Data Element Type]**, selecteert u `Identity map`

1. Hiermee wordt een schermgebied rechts in het venster **[!UICONTROL Data Collection interface]** voor u om de identiteit te vormen:

   ![Interface voor gegevensverzameling](assets/identity-identityMap-setup.png)

1. Als de  **[!UICONTROL Namespace]**, selecteert u de `lumaCrmId` naamruimte die u eerder hebt gemaakt in het dialoogvenster [Identiteiten configureren](configure-identities.md) les. Als deze niet in de vervolgkeuzelijst wordt weergegeven, typt u deze.

1. Na de **[!UICONTROL Namespace]** is geselecteerd, moet een id worden ingesteld. Selecteer de `user.profile.attributes.username` gegevenselement dat eerder in het dialoogvenster [Gegevenselementen maken](create-data-elements.md#create-data-elements-to-capture-the-data-layer) les, die een identiteitskaart vangt wanneer de gebruikers in de plaats van de Luma worden geregistreerd.

   <!--  >[!TIP]
    >
    >You can verify the **[!UICONTROL Luma CRM ID]** is collected in a data element on the web property by going to the [Luma Demo site](https://luma.enablementadobe.com/content/luma/us/en.html), logging in, [switching the tag environment](validate-with-debugger.md#use-the-experience-platform-debugger-to-map-to-your-tag-property) to your own, and typing `_satellite.getVar("user.profile.attributes.username")` in the web browser developer console.
    >
    >   ![Data Element  ID ](assets/identity-data-element-customer-id.png)
    -->

1. Als de **[!UICONTROL Authenticated state]**, selecteert u **[!UICONTROL Authenticated]**
1. Selecteren **[!UICONTROL Primary]**

1. Selecteren **[!UICONTROL Save]**

   ![Interface voor gegevensverzameling](assets/identity-id-namespace.png)

>[!TIP]
>
> Adobe beveelt aan identiteiten te verzenden die een persoon vertegenwoordigen, zoals `Luma CRM Id`als de [!UICONTROL primary] identiteit.
>
> Als het identiteitsoverzicht de personsidentificatie bevat (bijvoorbeeld `Luma CRM Id`), wordt de persoon-id de [!UICONTROL primary] identiteit. Anders, `ECID` wordt de [!UICONTROL primary] identiteit.




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

Met deze gegevenselementen op zijn plaats, bent u bereid om te beginnen gegevens naar de Edge Network van het Platform te verzenden door een regel in markeringen te creëren.

[Volgende: ](create-tag-rule.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over de SDK van Adobe Experience Platform Web. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
