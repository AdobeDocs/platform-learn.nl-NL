---
title: Audience Manager instellen met Platform Web SDK
description: Leer hoe te opstelling Adobe Audience Manager gebruikend het Web SDK van het Platform en de implementatie te bevestigen gebruikend een koekjesbestemming. Deze les maakt deel uit van de Zelfstudie Adobe Experience Cloud met Web SDK implementeren.
solution: Data Collection, Audience Manager
exl-id: 45db48e9-73cf-4a9c-88f4-b5872a8224d3
source-git-commit: 15bc08bdbdcb19f5b086267a6d94615cbfe1bac7
workflow-type: tm+mt
source-wordcount: '1276'
ht-degree: 0%

---

# Audience Manager instellen met Platform Web SDK


>[!CAUTION]
>
>We verwachten dat we op dinsdag 23 april 2024 belangrijke wijzigingen in deze zelfstudie zullen publiceren. Na dat punt zullen vele oefeningen veranderen en u kunt het leerprogramma van het begin moeten opnieuw beginnen om alle lessen te voltooien.

Leer hoe te opstelling Adobe Audience Manager gebruikend het Web SDK van het Platform en de implementatie te bevestigen gebruikend een koekjesbestemming.

[Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager.html) is de Adobe Experience Cloud-oplossing die alles biedt wat nodig is om commercieel relevante informatie over sitebezoekers te verzamelen, verhandelbare segmenten te maken en gerichte reclame en inhoud aan het juiste publiek te bezorgen.


## Leerdoelstellingen

Aan het eind van deze les, zult u kunnen:

* Een gegevensstroom configureren om Audience Manager in te schakelen
* Een cookiebestemming in Audience Manager inschakelen
* Valideer de implementatie van de Audience Manager door publiekskwalificatie met Adobe Experience Platform Debugger te bevestigen

## Vereisten

Om deze les te voltooien, moet u eerst:

* Voltooi de vroegere lessen in de Aanvankelijke secties van de Configuratie van de Configuratie en van de Markeringen van dit leerprogramma.
* Heb toegang tot Adobe Audience Manager en de aangewezen toestemmingen om, attributen, segmenten, en bestemmingen tot stand te brengen te lezen en te schrijven. Lees voor meer informatie [Op rol-Gebaseerd Toegangsbeheer van Audience Manager](https://experienceleague.adobe.com/docs/audience-manager-learn/tutorials/setup-and-admin/user-management/setting-permissions-with-role-based-access-control.html?lang=en).

## De gegevensstroom configureren

De implementatie van de Audience Manager die het Web SDK van het Platform gebruikt verschilt van de implementatie die [server-kant door:sturen (SSF)](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/server-side-forwarding/ssf.html). Door:sturen op de server geeft Adobe Analytics-aanvraaggegevens door aan de Audience Manager. Een implementatie van SDK van het Web van het Platform gaat XDM gegevens over die naar de Edge Network van het Platform aan Audience Manager worden verzonden. Audience Manager is ingeschakeld in de gegevensstroom:

1. Ga naar [Gegevensverzameling](https://experience.adobe.com/#/data-collection){target="blank"} interface
1. Selecteer in de linkernavigatie de optie **[!UICONTROL Datastreams]**
1. Selecteer de eerder gemaakte `Luma Web SDK` datastream

   ![Selecteer de Luma Web SDK-gegevensstroom](assets/datastream-luma-web-sdk.png)

1. Selecteren **[!UICONTROL Add Service]**
   ![Een service toevoegen aan de gegevensstroom](assets/aam-datastream-addService.png)
1. Selecteren **[!UICONTROL Adobe Audience Manager]** als de **[!UICONTROL Service]**
1. Bevestig dat **[!UICONTROL Cookie Destinations Enabled]** en **[!UICONTROL URL Destinations Enabled]** zijn geselecteerd
1. Selecteren **[!UICONTROL Save]**
   ![Bevestig de gegevensstroominstellingen van de Audience Manager en sla de gegevens op](assets/aam-datastream-save.png)

## Een gegevensbron maken

Maak vervolgens een [Gegevensbron](https://experienceleague.adobe.com/docs/audience-manager/user-guide/features/data-sources/datasources-list-and-settings.html?lang=en), een fundamenteel instrument voor het ordenen van gegevens binnen de Audience Manager:

1. Ga naar de [Audience Manager](https://experience.adobe.com/#/audience-manager/) interface
1. Selecteren **[!UICONTROL Audience Data]** vanaf de bovenste navigatie
1. Selecteer de **[!UICONTROL Data Sources]** in het keuzemenu
1. Selecteer de **[!UICONTROL Add New]** knoop van de bovenkant van de pagina van Gegevensbronnen

   ![Gegevensbronnen Adobe Experience Platform Audience Manager](assets/data-sources-list.jpg)

1. Geef de gegevensbron een vriendelijke naam en beschrijving. Voor de eerste setup kunt u deze`Platform Web SDK tutorial`.
1. Set **[!UICONTROL ID Type]** tot **[!UICONTROL Cookie]**
1. In de **[!UICONTROL Data Export Controls]** sectie, selecteert u **[!UICONTROL No Restriction]**

   ![Adobe Experience Platform Audience Manager Data Source Setup](assets/data-source-details.png)

1. **[!UICONTROL Save]** de gegevensbron


## Een kenmerk maken

Als de gegevensbron is opgeslagen, stelt u een [eigenschap](https://experienceleague.adobe.com/docs/audience-manager/user-guide/features/traits/traits-overview.html?lang=en). De sporen zijn een combinatie van één of meerdere signalen in Audience Manager. Maak een kenmerk voor bezoekers van de startpagina.

>[!NOTE]
>
>Alle gegevens XDM worden verzonden naar Audience Manager als het in de gegevensstroom wordt toegelaten, nochtans zouden de gegevens 24u kunnen vergen tot het in het Ongebruikte rapport van Signalen beschikbaar is. Maak expliciete kenmerken voor de XDM-gegevens die u direct in de Audience Manager wilt gebruiken, zoals in deze oefening wordt beschreven.

1. Selecteren **[!UICONTROL Audience Data]** >  **[!UICONTROL Traits]**
1. Selecteren **[!UICONTROL Add New]** >  **[!UICONTROL Rule-Based]** eigenschap

   ![Op regel gebaseerde reis van Adobe Experience Platform Audience Manager](assets/rule-based-trait.jpg)

1. Geef uw kenmerk een vriendelijke naam en beschrijving, `Luma homepage view`
1. Selecteer de **[!UICONTROL Data Source]** die u in de vorige sectie hebt gemaakt.
1. **[!UICONTROL Select a Folder]** waarin u de eigenschap wilt opslaan in het deelvenster aan de rechterkant. U kunt een map maken door **het pictogram + selecteren** naast een bestaande bovenliggende map. U kunt deze nieuwe map een naam geven `Platform Web SDK tutorial`.
1. Breid uit **[!UICONTROL Trait Expression]** inlasteken en selecteren **[!UICONTROL Expression Builder]** U moet een sleutelwaardepaar verstrekken dat een homepagebezoek betekent.
1. Open de [Luminantiepage](https://luma.enablementadobe.com/content/luma/us/en.html) (toegewezen aan uw eigenschap tag) en de **Platform Web SDK Debugger** en vernieuw de pagina.
1. Bekijk de Verzoeken van het Netwerk en de gebeurtenisdetails voor het Web SDK van het Platform om de sleutel en naamwaarde voor de homepage te vinden.
   ![Adobe Experience Platform Audience Manager XDM-gegevens](assets/xdm-keyvalue.jpg)
1. Ga terug naar de Bouwer van de Uitdrukking in de UI van de Audience Manager en ga sleutel in als **`web.webPageDetails.name`** en de waarde van **`content:luma:us:en`**. Deze stap zorgt ervoor dat u een eigenschap brandt wanneer u de homepage laadt.
1. **[!UICONTROL Save]** de eigenschap.


## Een segment maken

De volgende stap is het creëren van een **segment** en wijs uw nieuw gedefinieerde kenmerk toe aan dit segment.

1. Selecteren **[!UICONTROL Audience Data]** in de bovenste navigatie en selecteer **[!UICONTROL Segments]**
1. Selecteren **[!UICONTROL Add New]** linksboven op de pagina om de segmentbuilder te openen
1. Geef uw segment een vriendelijke naam en beschrijving, zoals `Platform Web SDK - Homepage visitors`
1. **[!UICONTROL Select a Folder]** waar uw segment in de ruit aan het recht zal worden bewaard. U kunt een map maken door **het pictogram + selecteren** naast een bestaande bovenliggende map. U kunt deze nieuwe map een naam geven `Platform Web SDK tutorial`.
1. Voeg een integratiecode toe, die in dit geval een willekeurige reeks getallen is. 1. In de **[!UICONTROL Data Source]** sectie, selecteert u **[!UICONTROL Audience Manager]** en de eerder gemaakte gegevensbron
1. Breid uit **[!UICONTROL Traits]** sectie en zoek naar het kenmerk dat u hebt gemaakt
1. Selecteer **[!UICONTROL Add Trait]**.
1. Selecteren **[!UICONTROL Save]** onder aan de pagina

   ![Adobe Experience Platform Audience Manager Trait toevoegen](assets/add-trait-segment.jpg)

   ![Adobe Experience Platform Audience Manager Trait toevoegen](assets/saved-segment.jpg)

## Een doel maken

Maak vervolgens een **Op cookie gebaseerd doel** met de **Bestemmingsbouwer**. De Bouwer van de Bestemming laat u koekje, URL, en server-aan-server bestemmingen tot stand brengen en beheren.

1. Open de Bouwer van de Bestemming door te selecteren **[!UICONTROL Destinations]** binnen de **Poortgegevens** menu in de bovenste navigatie
1. Selecteren **[!UICONTROL Create Destination]**
1. Voer een naam en beschrijving in. `Platform Web SDK tutorial`
1. Als de **[!UICONTROL Category]**, selecteert u **[!UICONTROL Custom]**
1. Als de **[!UICONTROL Type]**, selecteert u **[!UICONTROL Cookie]**

   ![Adobe Experience Platform Audience Manager Trait toevoegen](assets/destination-settings.jpg)

1. Open de **[!UICONTROL Configuration]** sectie om de details over uw koekjesbestemming in te gaan
1. Geef uw koekje een vriendschappelijke naam, `platform_web_sdk_tutorial`
1. Als de **[!UICONTROL Cookie Domain]**, voegt u het domein van de site toe waar u de integratie wilt uitvoeren, voor de zelfstudie-invoer in het domein Luma. `luma.enablementadobe.com`
1. Als de **[!UICONTROL Publish data to]** selecteert u **[!UICONTROL Only the Selected domains]**
1. Selecteer uw domein als dit nog niet is toegevoegd
1. Als de **[!UICONTROL Data Format]**, selecteert u **[!UICONTROL Single Key]** en geef je koekje een sleutel. Voor deze zelfstudie `segment` als de sleutelwaarde.
1. Tot slot selecteert u **[!UICONTROL Save]** om de details van de bestemmingsconfiguratie te bewaren.

   ![sectie Configuratie Audience Manager bestemming](assets/aam-destination-config-dw.png)

<!--
   ![Adobe Experience Platform Audience Manager Add Trait](assets/aam-destination-config.jpg)


   ![Adobe Experience Platform Audience Manager Add Trait](assets/cookie-destination-config.jpg)
-->

1. In de **[!UICONTROL Segment Mappings]** de sectie gebruiken **[!UICONTROL Search and Add Segments]** functie om te zoeken naar uw eerder gemaakte `Platform Web SDK - Homepage visitors` en selecteert u **[!UICONTROL Add]**.


1. Nadat u het segment hebt toegevoegd, wordt een pop-upvenster geopend waarin u een verwachte waarde voor de cookie moet opgeven. Voer voor deze oefening de waarde &quot;hpbezoeker&quot; in.

1. Selecteren **[!UICONTROL Save]**

1. Selecteren **[!UICONTROL Done]**
   ![Adobe Experience Platform Audience Manager Trait toevoegen](assets/luma-cookie-segment-dw.png)

De periode van de segmentafbeelding vereist een paar uren om worden geactiveerd. Zodra voltooid, kunt u de interface van de Audience Manager verfrissen en zien dat **Toegewezen segmenten** bijgewerkte lijst.

## Het segment valideren

Een paar uur na de eerste aanmaak van het segment kunt u controleren of het segment goed werkt.

Bevestig eerst dat u in aanmerking kunt komen voor het segment

1. Open de [Homepage van Luma-demo-site](https://luma.enablementadobe.com/content/luma/us/en.html) hiermee wordt de tag toegewezen aan uw eigenschap tag om in aanmerking te komen voor het zojuist gemaakte segment.
1. De browser openen **ontwikkelprogramma&#39;s**  > **Netwerk** tab
1. Filter aan het verzoek van SDK van het Web van het Platform gebruikend `interact` als het tekstfilter
1. Selecteer een vraag en open **Voorvertoning** tabblad om de reactiedetails weer te geven
1. Breid uit **payload** om de verwachte koekjesdetails, zoals eerder gevormd in Audience Manager te bekijken. In dit voorbeeld ziet u de verwachte cookienaam `platform_web_sdk_tutorial`.

   ![Adobe Experience Platform Audience Manager Trait toevoegen](assets/segment-validate-response.jpg)

1. Open de **Toepassing** en openen **Cookies** van de **Opslag** -menu.
1. Selecteer de **`https://luma.enablementadobe.com`** en bevestigen dat uw cookie correct in de lijst is geschreven

   ![Adobe Experience Platform Audience Manager Trait toevoegen](assets/validate-cookie.jpg)


Tot slot zou u het segment in de interface van de Audience Manager moeten openen en ervoor zorgen dat **Segmentpopulaties** is verhoogd:

![Adobe Experience Platform Audience Manager Trait toevoegen](assets/segment-population.jpg)


Nu u deze les hebt voltooid, zou u moeten kunnen zien hoe het Web SDK van het Platform gegevens tot Audience Manager overgaat en een segment-specifieke eerstepartijkoekje met een koekjesbestemming kunnen plaatsen.

[Volgende: ](setup-target.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over de SDK van Adobe Experience Platform Web. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
