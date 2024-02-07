---
title: Identiteiten maken
description: Leer hoe u identiteiten in XDM maakt en het gegevenselement Identiteitskaart gebruikt om gebruikers-id's vast te leggen. Deze les maakt deel uit van de Zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Tags
source-git-commit: ef3d374f800905c49cefba539c1ac16ee88c688b
workflow-type: tm+mt
source-wordcount: '894'
ht-degree: 0%

---

# Identiteiten maken

Leer hoe te om identiteiten met het Web SDK van het Experience Platform te vangen. Leg niet-geverifieerde en geverifieerde identiteitsgegevens vast op het tabblad [Luma-demosite](https://luma.enablementadobe.com/content/luma/us/en.html). Leer hoe te om de gegevenselementen te gebruiken u vroeger voor het verzamelen van voor authentiek verklaarde gegevens met een het gegevenselementtype van SDK van het Web van het Platform riep Identiteitskaart creeerde.

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

De [Experience Cloud-id (ECID)](https://experienceleague.adobe.com/docs/experience-platform/identity/ecid.html?lang=en) is een naamruimte voor gedeelde identiteit die wordt gebruikt in Adobe Experience Platform- en Adobe Experience Cloud-toepassingen. ECID vormt de basis voor de identiteit van de klant en is de standaardidentiteit voor digitale eigenschappen. Hierdoor is ECID de ideale id voor het bijhouden van niet-geverifieerd gebruikersgedrag omdat dit altijd aanwezig is

<!-- FYI I commented this out because it was breaking the build - Jack
>[!TIP]
>
> When you use the Experience Platform Web SDK to set up Adobe applications on your digital properties, the ECID is generated at the Adobe Edge server level. As such, ECID is not viewable on the client-side network request payload. You can view the ECID by seeing the Preview tab of the network request, or by using the [Adobe Experience Platform Debugger Edge Trace](set-up-analytics.md#experience-cloud-id-validation).
>![View ECID](assets/validate-dev-console-ecid.png)
-->

Meer informatie over hoe [ECIDs wordt gevolgd gebruikend het Web SDK van het Platform](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/overview.html?lang=en).

ECID&#39;s worden ingesteld met behulp van een combinatie van eersteklas cookies en Platform Edge Network. Door gebrek, worden de eerste-partijkoekjes geplaatst door het Web SDK. Als u browserbeperkingen voor de levensduur van cookies wilt compenseren, kunt u ervoor kiezen om uw eigen cookies van de eerste fabrikant in te stellen en te beheren. Deze worden ook wel FPID&#39;s (First-Party Device ID&#39;s) genoemd.

>[!IMPORTANT]
>
>De [Experience Cloud ID Service-extensie](https://exchange.adobe.com/experiencecloud.details.100160.adobe-experience-cloud-id-launch-extension.html) is niet nodig wanneer het uitvoeren van het Web SDK van Adobe Experience Platform, aangezien de functionaliteit van de Dienst van identiteitskaart in het Web SDK van het Platform wordt gebouwd.

## FPID (First Party Device ID)

FPID&#39;s zijn cookies van de eerste fabrikant _u kunt instellen met uw eigen webservers_ welke Adobe dan gebruikt om ECID tot stand te brengen, in plaats van het eerste partijkoekje te gebruiken dat door SDK van het Web wordt geplaatst. Hoewel de browserondersteuning kan variëren, zijn cookies van de eerste partij meestal duurzamer wanneer ze worden ingesteld door een server die gebruikmaakt van een DNS A-record (voor IPv4) of AAAA-record (voor IPv6), in tegenstelling tot wanneer ze worden ingesteld door een DNS CNAME- of JavaScript-code.

Nadat een FPID-cookie is ingesteld, kan de waarde ervan worden opgehaald en naar de Adobe worden verzonden wanneer gebeurtenisgegevens worden verzameld. Verzamelde FPID&#39;s worden gebruikt als zaden om ECID&#39;s te genereren op Platform Edge Network, wat de standaard-id&#39;s blijven in Adobe Experience Cloud-toepassingen.

Hoewel FPIDs niet in dit leerprogramma wordt gebruikt, wordt u aangemoedigd om FPIDs in uw eigen implementatie van SDK van het Web te gebruiken. Meer informatie over [Eerste partij apparaat IDs in het Web SDK van het Platform](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/first-party-device-ids.html?lang=en)

>[!CAUTION]
>
> FPID is een alternatieve manier om de ECID te genereren met behulp van een cookie die door uw webservers is ingesteld. Het wordt niet gebruikt voor het identificeren van geverifieerde gebruikers.

## Geverifieerde id

Zoals hierboven vermeld, wordt aan alle bezoekers van uw digitale eigenschappen een ECID toegewezen door Adobe wanneer het gebruiken van het Web SDK van het Platform. Hierdoor is ECID de standaardidentiteit voor het bijhouden van niet-geverifieerd digitaal gedrag.

U kunt ook een geverifieerde gebruikers-id verzenden, zodat Platform [Identiteitsgrafiek](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/understanding-identity-and-identity-graphs.html?lang=en) en Target kan zijn [Id van derde partij](https://experienceleague.adobe.com/docs/target/using/audiences/visitor-profiles/3rd-party-id.html). Dit wordt gedaan door te gebruiken [!UICONTROL Identiteitskaart] type gegevenselement.

Als u de opdracht [!UICONTROL Identiteitskaart] gegevenselement:

1. Ga naar **[!UICONTROL Gegevenselementen]** en selecteert u **[!UICONTROL Gegevenselement toevoegen]**

1. **[!UICONTROL Naam]** het gegevenselement `identityMap.loginID`

1. Als de **[!UICONTROL Extensie]**, selecteert u `Adobe Experience Platform Web SDK`

1. Als de **[!UICONTROL Type gegevenselement]**, selecteert u `Identity map`

1. Hiermee wordt een schermgebied rechts in het venster **[!UICONTROL Interface voor gegevensverzameling]** voor u om de identiteit te vormen:

   ![Interface voor gegevensverzameling](assets/identity-identityMap-setup.png)

1. Als de  **[!UICONTROL Naamruimte]**, selecteert u de `lumaCrmId` naamruimte die u eerder hebt gemaakt in het dialoogvenster [Identiteiten configureren](configure-identities.md) les.

   >[!NOTE]
   >
   >    Als u uw `lumaCrmId` naamruimte, controleert u of u deze ook hebt gemaakt in uw standaardproductiestandbox. Alleen naamruimten die zijn gemaakt in de standaardproductiefsandbox worden momenteel weergegeven in het vervolgkeuzemenu voor naamruimten.

1. Na de **[!UICONTROL Naamruimte]** is geselecteerd, moet een id worden ingesteld. Selecteer de `user.profile.attributes.username` gegevenselement dat eerder in het dialoogvenster [Gegevenselementen maken](create-data-elements.md#create-data-elements-to-capture-the-data-layer) les, die een identiteitskaart vangt wanneer de gebruikers in de plaats van de Luma worden geregistreerd.

   <!--  >[!TIP]
    >
    >You can verify the **[!UICONTROL Luma CRM ID]** is collected in a data element on the web property by going to the [Luma Demo site](https://luma.enablementadobe.com/content/luma/us/en.html), logging in, [switching the tag environment](validate-with-debugger.md#use-the-experience-platform-debugger-to-map-to-your-tag-property) to your own, and typing `_satellite.getVar("user.profile.attributes.username")` in the web browser developer console.
    >
    >   ![Data Element  ID ](assets/identity-data-element-customer-id.png)
    -->

1. Als de **[!UICONTROL Status voor authentiek]**, selecteert u **[!UICONTROL Geverifieerd]**
1. Selecteren **[!UICONTROL Primair]**

1. Selecteren **[!UICONTROL Opslaan]**

   ![Interface voor gegevensverzameling](assets/identity-id-namespace.png)

>[!TIP]
>
> Adobe beveelt aan identiteiten te verzenden die een persoon vertegenwoordigen, zoals `Luma CRM Id`als de [!UICONTROL primair] identiteit.
>
> Als het identiteitsbewijs de personsidentificatie bevat (bijvoorbeeld `Luma CRM Id`), wordt de persoon-identificator de [!UICONTROL primair] identiteit. Anders, `ECID` wordt de [!UICONTROL primair] identiteit.




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
| `cart.orderId` | `identityMap.loginID` |
| `cart.productInfo` | `xdm.variable.content` |
| `cart.productInfo.purchase` | |
| `page.pageInfo.hierarchie1` | |
| `page.pageInfo.pageName` | |
| `page.pageInfo.server` | |
| `product.category` | |
| `product.productInfo.sku` | |
| `product.productInfo.title` | |
| `user.profile.attributes.loggedIn` | |
| `user.profile.attributes.username` | |

Met deze gegevenselementen op zijn plaats, bent u klaar om gegevens naar het Netwerk van de Rand van het Platform via het voorwerp te verzenden XDM door een regel in markeringen te creëren.

[Volgende: ](create-tag-rule.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over de SDK van Adobe Experience Platform Web. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
