---
title: Goedkeuring instellen met Platform Web SDK
description: Leer hoe te om de privacymontages van de de markeringsuitbreiding van SDK van het Web van het Experience Platform te vormen. Deze les maakt deel uit van de Zelfstudie Adobe Experience Cloud met Web SDK implementeren.
exl-id: 502a7467-3699-4b2b-93bf-6b6069ea2090
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '1624'
ht-degree: 0%

---

# Goedkeuring instellen met Platform Web SDK

Leer hoe te om de privacymontages van de de markeringsuitbreiding van SDK van het Web van het Experience Platform te vormen. Stel toestemming in op basis van de interactie van de bezoeker met een banner van een Platform voor beheer van instemming (CMP).

>[!NOTE]
> 
>Ter demonstratie gebruikt deze zelfstudie [Klaro](https://heyklaro.com/) als CMP. U kunt met Klaro of het CMP dat u voor uw website gebruikt doorgaan.


## Leerdoelstellingen

Aan het einde van deze les kunt u het volgende doen:

* Een CMP laden met tags
* Privacy-instellingen configureren in Experience Platform Web SDK-tagextensie
* Toestemming voor het Web SDK van het Experience Platform instellen op basis van de actie van de bezoeker

## Vereisten

U zou met markeringen en de stappen vertrouwd moeten zijn om regels, gegevenselementen tot stand te brengen, bibliotheken aan milieu&#39;s te bouwen, en markeringsbibliotheken te schakelen gebruikend Foutopsporing van het Experience Platform.

Voordat u de privacy-instellingen gaat configureren en de regels voor het instellen van de toestemming gaat maken, moet u controleren of u het script van het toestemmingsbeheerplatform op de website hebt ingespoten en correct werkt. Een CMP kan rechtstreeks in de broncode worden geladen met behulp van siteontwikkelaars of door tags zelf worden geladen. Deze les toont de laatste aanpak aan.
>[!NOTE]
> 
>1. Organisaties gebruiken een Platform voor beheer van toestemming (of CMP) om de toestemmingskeuzes van een bezoeker wettelijk te documenteren en te beheren voordat ze bezoekersgegevens verzamelen, delen of verkopen van online bronnen zoals websites en apps.
>
>2. De aanbevolen methode voor het injecteren van een CMP is rechtstreeks via broncode vóór het script voor tagbeheer.


### Klaro configureren

Voordat u in de tagconfiguraties gaat, leert u meer over het platform voor het beheer van de toestemming dat in deze zelfstudie Klaro wordt gebruikt.

1. Bezoek [Klaro](https://heyklaro.com/) en een account instellen.
1. Ga naar **Privacy Manager** en maak een instantie volgens de instructies.
1. Gebruik de **Integratiecode** om Klaro in uw tag-eigenschap te injecteren (instructies zijn in de volgende oefening).
1. Sla de **Scannen** , omdat hiermee de eigenschap tag wordt gedetecteerd die op de demo-website van Luma is gecodeerd en niet de eigenschap die u voor deze zelfstudie hebt gemaakt.
1. Voeg de geroepen dienst toe `aep web sdk` en schakelt u de **Standaardstatus service**. Wanneer deze optie is ingeschakeld, is de standaardwaarde voor de toestemming `true`anders is het `false`. Deze configuratie is handig wanneer u wilt bepalen wat de status van de standaardtoestemming (vóór toestemming van de bezoeker) is voor uw webtoepassing. Bijvoorbeeld:
   * Voor CCPA wordt de standaardtoestemming algemeen geplaatst aan `true`. U gaat naar dit scenario verwijzen als **Impliciete opt-in** door deze zelfstudie
   * Voor GDPR wordt de standaardtoestemming doorgaans ingesteld op `false`. U gaat naar dit scenario verwijzen als **Impliciete opt-out** in deze zelfstudie.

<!--
    This consent value can be verified by returning the JavaScript object ```klaro.getManager().consents``` in the browser's developer console.
-->
    >[!OPMERKING]
    >
    >In het algemeen worden de bovengenoemde stappen uitgevoerd en verzorgd door het team of de persoon die verantwoordelijk is voor de behandeling van het CMP, zoals OneTrust of TrustArc.

## Injecteer een CMP

>[!WARNING]
>
>De beste praktijken om een Platform van het Beheer van de Toestemming uit te voeren zijn typisch om CMP te laden _voor_ het laden van uw tagbeheer. Om deze zelfstudie te vergemakkelijken, laadt u de CMP _with_ de tagmanager. Deze les wordt ontworpen om u te tonen hoe te om de toestemmingseigenschappen in het Web SDK van het Platform te gebruiken en zou niet als gids moeten worden gebruikt om Klaro of een andere CMP correct te vormen.


Nu, zodra u met de configuraties van Klaro wordt gedaan, creeer een markeringsregel met de volgende configuraties:

* [!UICONTROL Naam]: `all pages - library load - Klaro`
* [!UICONTROL Gebeurtenis]: [!UICONTROL Bibliotheek geladen (pagina boven)] with [!UICONTROL Geavanceerde opties] > [!UICONTROL Volgorde] ingesteld op 1
* [!UICONTROL Handeling]: [!UICONTROL Aangepaste code], [!UICONTROL Taal]: HTML om het CMP-script te laden.

![CMP-regel injecteren](assets/consent-cmp-inject-rule-1.png)

Het aangepaste codeblok moet er ongeveer als volgt uitzien:

![CMP-regel injecteren](assets/consent-cmp-inject-rule-2.png)

Sla deze regel nu op en maak deze regel op in uw ontwikkelingsbibliotheek. valideer de toestemmingsbanner wordt weergegeven door de tagbibliotheek van de Luministensite naar uw eigen bibliotheek te verplaatsen. U ziet hieronder een CMP-banner op de website. En om de toestemming van de huidige bezoeker te controleren kunt u het volgende fragment op de console van browser gebruiken.

```javascript
    klaro.getManager().consents 
```

![Constante banner](assets/consent-cmp-banner.png)

Gebruik het volgende selectievakje in Adobe Experience Platform debugger om naar de foutopsporingsmodus te gaan.

![Foutopsporingsmodus voor tags](assets/consent-rule-debugging.png)

Mogelijk moet u uw cookies en lokale opslag meerdere keren wissen tijdens het doorlopen van deze zelfstudie, aangezien de waarde van de toestemming van de bezoeker daar wordt opgeslagen. Je kunt dat gewoon als volgt doen:

![Opslag wissen](assets/consent-clearning-cookies.png)

## Goedkeuringsscenario&#39;s

Privacyhandelingen zoals GDPR, CCPA en andere spelen een cruciale rol in de manier waarop u de uitvoering van de toestemming ontwikkelt. In deze les, onderzoekt u hoe een bezoeker met de toestemmingsbanner onder twee meest prominente privacyhandelingen zou kunnen in wisselwerking staan.
![Goedkeuringsscenario&#39;s](assets/consent-scenarios.jpeg)


### Scenario 1: Impliciete optie-in

Impliciete opt-in betekent dat het bedrijf de toestemming van de bezoeker (of de &quot;opt-in&quot;) niet hoeft te verkrijgen voordat het zijn gegevens verzamelt, en dat alle bezoekers van de website daarom standaard als gekozen worden behandeld. De bezoeker kan er echter voor kiezen de cookies te negeren via de bevestigingsbanner. Dit gebruik-geval is gelijkaardig aan CCPA.

Nu zult u toestemming voor dit scenario vormen en uitvoeren:

1. In de **[!UICONTROL Privacy]** sectie van de de markeringsuitbreiding van SDK van het Web van het Experience Platform, zorg ervoor  **[!UICONTROL Standaardtoestemming]** is ingesteld op **[!UICONTROL In]** :


   ![Goedkeuring AEP-configuratie voor extensieprivacyconfiguratie](assets/consent-web-sdk-privacy-in.png)

   >[!NOTE]
   > 
   >Voor een dynamische oplossing selecteert u de optie Een gegevenselement opgeven en geeft u een gegevenselement door dat de waarde van ```klaro.getManager().consents```
   >
   >Deze optie wordt gebruikt als het CMP wordt geïnjecteerd in de broncode *voor* De code van de markering inbedt zodat de standaardtoestemming beschikbaar is alvorens de uitbreiding van SDK van het Web van het Experience Platform begint te laden. In ons voorbeeld kunnen we deze optie niet gebruiken omdat het CMP wordt geladen met tags en niet voor tags.



2. Deze wijziging opslaan en samenstellen in uw tagbibliotheek
3. Laad uw tagbibliotheek op de Luma-demo-site
4. Schakel foutopsporing van tags in op de Luministoepassing en laad de pagina opnieuw. In de ontwikkelaarsconsole van uw browser, zou u moeten zien dat defaultConsent gelijk is aan **[!UICONTROL In]**
5. Met deze configuratie, blijft de uitbreiding van SDK van het Web van het Experience Platform netwerkverzoeken indienen, tenzij een bezoeker besluit om de koekjes en opt-out te verwerpen:

   ![Ingeschakelde toestemming](assets/consent-Implied-optin-default.png)



Als een bezoeker besluit om te weigeren (de volgende cookies negeren), moet u de toestemming wijzigen om **[!UICONTROL Uit]**. Wijzig de instelling voor toestemming door de volgende stappen uit te voeren:

<!--
1. Create a data element to store the consent value of the visitor. Let's call it `klaro consent value`. Use the code snippet to create a custom code type data element:
    
    ```javascript
    return klaro.getManager().consents["aep web sdk"]
    ```

    ![Data Element consent value](assets/consent-data-element-value.png)


1. Create another custom code data element, `consent confirmed`, with the following snippet which returns ```true``` only after a visitor confirms consent:

    
    ```javascript
    return klaro.getManager().confirmed
    ```

    ![Data Element consent confirmed](assets/consent-data-element-confirmed.png)
-->

1. Een regel maken die wordt geactiveerd wanneer de bezoeker klikt **Ik weiger**.  Noem deze regel als: `all pages - click consent banner - set consent "out"`

1. Als de **[!UICONTROL Gebeurtenis]**, gebruik **[!UICONTROL Klikken]** op **[!UICONTROL Elementen die overeenkomen met de CSS-kiezer]** `#klaro .cn-decline`

   ![De gebruiker van de Voorwaarde van de regel klikt &quot;ik verwerp&quot;](assets/consent-optOut-clickEvent.png)

1. Nu, gebruik SDK van het Web van het Experience Platform, [!UICONTROL Goedkeuring instellen] [!UICONTROL actietype] om de toestemming als &quot;out&quot; vast te stellen:

   ![Handeling voor Weigeren van regel voor instemming](assets/consent-rule-optout-action.png)

1. Selecteren **[!UICONTROL Opslaan in bibliotheek en samenstellen]**:

   ![Uw bibliotheek opslaan en samenstellen](assets/consent-rule-optout-saveAndBuild.png)

Nu, wanneer een bezoeker uit opteert, zou de regel die op de bovengenoemde manier wordt gevormd in brand steken en de toestemming van SDK van het Web als plaatst **[!UICONTROL Uit]**.

Valideren door naar de Luma-demo-site te gaan, cookies negeren en bevestigen dat geen Web SDK-aanvraag wordt geactiveerd nadat u deze hebt uitgeschakeld.

### Scenario 2: Impliciete optie


Impliciete opt-out houdt in dat bezoekers standaard moeten worden behandeld als opted-out en cookies niet mogen worden ingesteld. Web SDK-aanvragen mogen alleen worden gestart als bezoekers besluiten handmatig aan te melden door de cookies te accepteren via de machtigingsbanner. Misschien moet u een dergelijk gebruiksgeval aanpakken in de regio van de Europese Unie waar de GDPR van toepassing is.

Hier is hoe u opstelling de configuratie voor een impliciet opt-outscenario:

1. Schakel in Klaro de **Standaardstatus service** in uw `aep web sdk` en sla de bijgewerkte configuratie op.

1. In **[!UICONTROL Privacy]** sectie van de uitbreiding van SDK van het Web van het Experience Platform, vastgestelde standaardtoestemming aan **[!UICONTROL Uit]** of **[!UICONTROL In behandeling]** zoals vereist.

   ![Goedkeuring AEP-configuratie voor extensieprivacyconfiguratie](assets/consent-implied-opt-out.png)

1. **Opslaan** de bijgewerkte configuratie aan uw markeringsbibliotheek en herbouwt het.

   Met deze configuratie, zorgt het Web SDK van het Experience Platform ervoor dat geen verzoek brandt tenzij de toestemmingstoestemming verandert in **[!UICONTROL In]**. Dit kan gebeuren als een bezoeker de cookies handmatig accepteert door in te schakelen.

1. Zorg er in Foutopsporing voor dat de Luminantiesite is toegewezen aan uw tageigenschap en dat de logboekregistratie voor de tagconsole is ingeschakeld.
1. Gebruik de ontwikkelaarsconsole van uw browser aan **Sitegegevens wissen** in **Toepassing** > **Opslag**

1. Laad de Luminasite opnieuw en zorg dat `defaultConsent` is ingesteld op **[!UICONTROL Uit]** en er zijn geen Web SDK-verzoeken ingediend

   ![Ingevoerde toestemming om uit te schakelen](assets/consent-implied-out-cmp.png)

Als een bezoeker besluit zich aan te melden (de volgende cookies accepteren), moet u de toestemming wijzigen en instellen op **[!UICONTROL In]**. Hieronder wordt beschreven hoe u dit kunt doen met een regel:

1. Een regel maken die wordt geactiveerd wanneer de bezoeker klikt **Dat is oké**.  Noem deze regel als: `all pages - click consent banner - set consent "in"`

1. Als de **[!UICONTROL Gebeurtenis]**, gebruik **[!UICONTROL Klikken]** op **[!UICONTROL Elementen die overeenkomen met de CSS-kiezer]** `#klaro .cm-btn-success`

   ![De gebruiker van de Voorwaarde van de regel klikt &quot;dat is ok&quot;](assets/consent-optIn-clickEvent.png)

1. Voeg een actie toe gebruikend het Web SDK van het Experience Platform [!UICONTROL Extensie], **[!UICONTROL Type handeling]** van **[!UICONTROL Goedkeuring instellen]**, **[!UICONTROL Algemene instemming]** als **[!UICONTROL In]**.

   ![Handeling voor inschakelen van regel](assets/consent-rule-optin-action.png)

   Eén ding is dat dit [!UICONTROL Goedkeuring instellen] actie zal het eerste verzoek zijn dat uitgaat en de identiteit vaststelt . Daarom kan het belangrijk zijn om identiteiten op het eerste verzoek zelf te synchroniseren. Het identiteitsoverzicht kan worden toegevoegd aan [!UICONTROL Goedkeuring instellen] door een gegevenselement voor het type identiteit door te geven.

1. Selecteren **[!UICONTROL Opslaan in bibliotheek en samenstellen]**:

   ![Weigeren van instemming](assets/consent-rule-optin-saveAndBuild.png)

1. **[!UICONTROL Opslaan]** de regel aan uw bibliotheek en herbouwt het.

Zodra u deze regel op zijn plaats hebt, zou de gebeurtenisinzameling moeten beginnen wanneer een bezoeker opteert-binnen.

![Optie voor verzending van berichten](assets/consent-post-user-optin.png)


Voor meer informatie over toestemming in Web SDK, zie [Voorkeuren voor toestemming van klanten ondersteunen](https://experienceleague.adobe.com/docs/experience-platform/edge/consent/supporting-consent.html?lang=en).


Voor meer informatie over de [!UICONTROL Goedkeuring instellen] actie, zie [Goedkeuring instellen](https://experienceleague.adobe.com/docs/experience-platform/edge/extension/action-types.html?lang=en#set-consent).

[Volgende: ](setup-event-forwarding.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over Adobe Experience Platform Web SDK. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
