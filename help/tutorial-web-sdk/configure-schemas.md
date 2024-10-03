---
title: Een XDM-schema voor webgegevens maken
description: Leer hoe te om een schema XDM voor Webgegevens in de interface van de Inzameling van Gegevens tot stand te brengen. Deze les maakt deel uit van de Zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Web SDK,Schemas
jira: KT-15398
exl-id: 2858ce03-4f95-43ac-966c-1b647b33ef16
source-git-commit: 63987fb652a653283a05a5f35f7ce670127ae905
workflow-type: tm+mt
source-wordcount: '1510'
ht-degree: 0%

---

# Een XDM-schema voor webgegevens maken

Leer hoe u een XDM-schema voor webgegevens maakt in de interface van de Adobe Experience Platform-gegevensverzameling.

De schema&#39;s van het Gegevensmodel van de ervaring (XDM) zijn de bouwstenen, de principes, en de beste praktijken voor het verzamelen van gegevens in Adobe Experience Platform.

De SDK van het Web van het platform gebruikt uw schema om uw gegevens van de Webgebeurtenis te standaardiseren, het naar de Edge Network van het Platform te verzenden, en uiteindelijk door:sturen de gegevens aan om het even welke Experience Cloud toepassingen die in de datastream worden gevormd. Deze stap is kritiek aangezien het een standaardgegevensmodel bepaalt dat voor het opnemen van gegevens van de klantenervaring in Experience Platform wordt vereist en stroomafwaartse diensten en toepassingen toelaat die op deze normen worden voortgebouwd.

>[!NOTE]
>
>Een schema XDM wordt _vereist_ niet om Adobe Analytics, Adobe Target, of Adobe Audience Manager met Web SDK uit te voeren (de gegevens kunnen in het `data` voorwerp in plaats van het `xdm` voorwerp worden overgegaan aangezien u later zult zien). Een XDM-schema is vereist voor de krachtigste implementaties van Platform-native toepassingen zoals Journey Optimizer, Real-time Customer Data Platform en Customer Journey Analytics. Terwijl u kunt besluiten om geen schema XDM in uw eigen implementatie te gebruiken, wordt u geacht dit als deel van dit leerprogramma te doen.

## Waarom modelleren de gegevens?

De ondernemingen hebben hun eigen taal voor het communiceren over hun domein. De autohandel handelt merk, modellen, en cilinders. Luchtvaartmaatschappijen hebben te maken met vluchtnummers, dienstencategorieën en zitplaatsen. Sommige van deze termen zijn uniek voor een bepaalde onderneming, sommige worden gedeeld door een verticale industrie, en sommige worden gedeeld door bijna alle ondernemingen. Voor termen die worden gedeeld tussen een verticale of zelfs bredere branche, kunt u krachtige dingen met uw gegevens beginnen te doen wanneer u deze termen op een gemeenschappelijke manier noemt en structureert.

Bijvoorbeeld, behandelen vele ondernemingen bevelen. Wat als deze bedrijven gezamenlijk besloten om een order op dezelfde manier te modelleren? Wat gebeurt er bijvoorbeeld als het gegevensmodel bestond uit een object met een eigenschap `priceTotal` die de totale prijs van de order vertegenwoordigde? Wat gebeurt er als dat object ook eigenschappen met de naam `currencyCode` en `purchaseOrderNumber` had? Misschien bevat het orderobject een eigenschap met de naam `payments` die een array van betalingsobjecten zou zijn. Elk object zou een betaling voor de bestelling zijn. Bijvoorbeeld, misschien betaalde een klant voor een deel van de orde met een geschenkkaart en de rest gebruikend een creditcard. U kunt beginnen een model te construeren dat er ongeveer als volgt uitziet:

```json
{
  "order": {
    "priceTotal": 89.50,
    "currencyCode": "EUR",
    "purchaseOrderNumber": "JWN20192388410012",
    "payments": [
      {
        "paymentType": "gift_card",
        "paymentAmount": 50
      },
      {
        "paymentType": "credit_card",
        "paymentAmount": 39.50
      }
    ]
  }
}
```

Als alle bedrijven die met orders te maken hebben, besloten hebben om hun ordergegevens op consistente wijze te modelleren voor termen die in de sector algemeen zijn, kunnen er magische dingen beginnen te gebeuren. De informatie zou vlotter binnen en buiten uw organisatie kunnen worden uitgewisseld in plaats van constant het interpreteren en vertalen van de gegevens (pro&#39;s en evars, om het even wie?). Het leren van de machine kon gemakkelijker begrijpen wat uw gegevens __ betekent en actionable inzichten verstrekken. Gebruikersinterfaces voor het opzoeken van relevante gegevens kunnen intuïtiever worden. Uw gegevens kunnen naadloos worden geïntegreerd met partners en leveranciers die dezelfde modellering volgen.

Dit is het doel van het Model van de Gegevens van de Ervaring van de Adobe [ ](https://business.adobe.com/products/experience-platform/experience-data-model.html). XDM verstrekt voorschrijvende modellering voor gegevens die in de industrie gemeenschappelijk zijn, terwijl ook het toestaan van u om het model voor uw specifieke behoeften uit te breiden. Adobe Experience Platform is opgebouwd rond XDM en gegevens die naar Experience Platform worden verzonden, moeten daarom in XDM staan. In plaats van na te denken over waar en hoe u uw huidige gegevensmodellen in XDM kunt omzetten alvorens de gegevens naar Experience Platform te verzenden, overweeg doordringend het goedkeuren van XDM over uw organisatie zodat de vertaling zelden moet voorkomen.


>[!NOTE]
>
> Voor demonstratiedoeleinden, bouwen de oefeningen in deze les een voorbeeldschema om inhoud te vangen bekeken en producten die door klanten in de [ Plaats van de Demo van de Luma worden gekocht ](https://luma.enablementadobe.com/content/luma/us/en.html). Terwijl u deze stappen kunt gebruiken om een verschillend schema voor uw eigen doeleinden tot stand te brengen, adviseert men dat u eerst samen met het creëren van het voorbeeldschema volgt om de mogelijkheden van de schemaredacteur te leren.

Om meer over schema&#39;s te leren XDM, op de playlist [ ModelUw Gegevens van de Ervaring van de Klant met XDM ](https://experienceleague.adobe.com/en/playlists/experience-platform-model-your-customer-experience-data-with-xdm) of zie het [ XDM overzicht van het Systeem ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home).

## Leerdoelstellingen

Aan het eind van deze les, zult u kunnen:

* Creeer een schema XDM van binnen de interface van de Inzameling van Gegevens
* Veldgroepen toevoegen aan uw XDM-schema
* XDM-schema&#39;s maken voor webgebeurtenisgegevens met behulp van best practices

## Vereisten

Alle noodzakelijke levering en gebruikerstoestemmingen voor de Inzameling van Gegevens en Adobe Experience Platform beschreven op de [ overzicht ](overview.md) pagina.

## Een XDM-schema maken

De schema&#39;s XDM zijn de standaardmanier om gegevens in Experience Platform te beschrijven, toestaand alle gegevens die aan de schema&#39;s voldoen om over een organisatie zonder conflicten worden opnieuw gebruikt, of zelfs tussen veelvoudige organisaties worden gedeeld. Meer leren, zie de [ grondbeginselen van de samenstelling van het Schema ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition).

In deze oefening, zult u een schema XDM gebruikend de geadviseerde groepen van het basislijngebied voor het vangen van de gegevens van de Webgebeurtenis over de ](https://luma.enablementadobe.com/content/luma/us/en.html) {target="_blank"} Plaats van de Demo van 0} Luma creëren:[

1. Open de [ interface van de Inzameling van Gegevens ](https://launch.adobe.com/) {target="_blank"}
1. Zorg ervoor dat u zich in de juiste sandbox bevindt. De sandbox in de rechterbovenhoek zoeken

   >[!NOTE]
   >
   >Als u de klant bent van een toepassing op basis van een platform, zoals Real-Time CDP of Journey Optimizer, raden we u aan een ontwikkelingssandbox voor deze zelfstudie te gebruiken. Als u dat niet doet, gebruikt u de **[!UICONTROL Prod]** -sandbox.

1. Ga naar **[!UICONTROL Schemas]** in de linkernavigatie
1. Selecteer de knop **[!UICONTROL Create Schema]** rechtsboven

   ![ creeer Schema ](assets/schema-xdm-create-schema.png)
1. Selecteer **[!UICONTROL Experience Event]** in het volgende scherm
1. Selecteren **[!UICONTROL Next]**

   ![ Gebeurtenis van de Ervaring van het Schema ](assets/schema-experience-event.png)

1. Voer in dit geval de naam van het schema in onder het veld **[!UICONTROL Schema display name]** . `Luma Web Event Data`

   >[!TIP]
   >
   >Een gemeenschappelijke noemende overeenkomst voor schema XDM moet het schema na de bron van de gegevens noemen.


1. Voltooien selecteren

   ![ Einde van de Gebeurtenis van de Ervaring van het Schema ](assets/schema-name-schema.png)

## Veldgroepen toevoegen

Zoals eerder vermeld, is XDM het kernkader dat klantenervaringsgegevens door gemeenschappelijke structuren en definities voor gebruik in de stroomafwaartse diensten van Adobe Experience Platform te verstrekken gestandaardiseerd. Door aan normen XDM te houden, _kunnen alle gegevens van de klantenervaring_ in een gemeenschappelijke vertegenwoordiging worden opgenomen. Deze benadering staat u toe om waardevolle inzichten van klantenacties te bereiken, klantenpubliek door segmenten te bepalen, en klantenattributen voor verpersoonlijkingsdoeleinden uit te drukken gebruikend gegevens uit veelvoudige bronnen. Zie [ Beste praktijken voor gegevens modelleren ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/best-practices) voor meer informatie.

Indien mogelijk wordt aangeraden bestaande veldgroepen te gebruiken en zich te houden aan een product-agnostisch model en naamgevingsconventies. Voor alle gegevens die specifiek zijn voor uw organisatie en die niet in de hierboven vooraf gedefinieerde veldgroepen passen, kunt u een aangepaste veldgroep maken. Zie [ Creërend een schema gebruikend de Redacteur van het Schema ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/create-schema-ui#create) voor meer gedetailleerde stappen op douaneschema&#39;s.

>[!TIP]
> 
>In deze exercitie voegt u de aanbevolen vooraf gedefinieerde veldgroepen voor het verzamelen van webgegevens toe: _**[!UICONTROL AEP Web SDK ExperienceEvent]**_en_**[!UICONTROL Consumer Experience Event]**_ .
>


1. Selecteer in de sectie **[!UICONTROL Field groups]** de optie **[!UICONTROL Add]**

   ![ Nieuwe Groep van het Gebied ](assets/schema-new-field-group.png)

1. Zoeken naar [!UICONTROL `AEP Web SDK ExperienceEvent`]
1. Het selectievakje inschakelen
1. Zoeken naar [!UICONTROL `Consumer Experience Event`]
1. Het selectievakje inschakelen
1. Selecteren **[!UICONTROL Add field groups]**

   ![ voeg de Groep van het Gebied ](assets/schema-add-field-group.png) toe

Bij beide veldgroepen zult u zien dat u toegang hebt tot de meestgebruikte sleutelwaardeparen die vereist zijn voor gegevensverzameling op het web. De [!UICONTROL display name] van elk gebied verschijnt aan marketers in de segmentbuilderinterface van op platform-gebaseerde toepassingen en u kunt de vertoningsnaam van standaardgebieden veranderen om uw behoeften aan te passen. U kunt ook velden verwijderen die u niet wilt. Wanneer u op één van beide naam van de gebiedsgroep klikt, benadrukt de interface welke sleutel-waarde paargroeperingen tot het behoren. In het onderstaande voorbeeld ziet u tot welke velden behoren **[!UICONTROL Consumer Experience Event]** .

![ Groepen van het Gebied van het Schema ](assets/schema-consumer-experience-event.png)

Deze les is slechts een uitgangspunt. Wanneer het bouwen van uw eigen schema van Webgebeurtenissen, moet u uw bedrijfsvereisten onderzoeken en documenteren. Dit proces is gelijkaardig aan het creëren van het Document van Bedrijfs a [ Vereisten ](https://experienceleague.adobe.com/en/docs/analytics-learn/tutorials/implementation/implementation-basics/creating-a-business-requirements-document) en [ de Verwijzing van het Ontwerp van de Oplossing ](https://experienceleague.adobe.com/en/docs/analytics-learn/tutorials/implementation/implementation-basics/creating-and-maintaining-an-sdr) voor een implementatie van Adobe Analytics, maar zou vereisten voor _alle stroomafwaartse gegevensontvangers_ zoals Platform, Doel, en gebeurtenis moeten omvatten door:sturen bestemmingen.


### Het object identityMap

Er is een speciaal veld dat wordt gebruikt voor het identificeren van webgebruikers die `[!UICONTROL identityMap]` worden genoemd.

![ Gegevens van de Gebeurtenis van het Web Luma ](assets/schema-identityMap.png)

Het is een verplicht voorwerp voor om het even welke Web-gerelateerde gegevensinzameling, aangezien het Experience Cloud identiteitskaart die voor het identificeren van gebruikers op het Web wordt vereist opslaat. Het is ook de sleutel aan het plaatsen van interne klant IDs voor voor authentiek verklaarde gebruikers. `[!UICONTROL identityMap]` wordt besproken meer in [ vormen de 2} les van Identiteiten {. ](configure-identities.md) Deze wordt automatisch opgenomen in alle schema&#39;s met behulp van de klasse **[!UICONTROL XDM ExperienceEvent]** .


>[!IMPORTANT]
>
> U kunt **[!UICONTROL Profile]** mogelijk inschakelen voor een schema voordat u het schema opslaat. **laat niet** het op dit punt toe. Als een schema eenmaal is ingeschakeld voor Profiel, kan het niet worden uitgeschakeld of verwijderd zonder de volledige sandbox opnieuw in te stellen. De gebieden kunnen niet van schema&#39;s op dit punt of worden verwijderd, hoewel het mogelijk is [ Gebieden in UI ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/field-deprecation-ui#deprecate) te verwerpen. Deze implicaties zijn belangrijk om later in mening te houden wanneer u met uw eigen gegevens in uw milieu van de Productie werkt.
>
>
>Dit het plaatsen wordt besproken meer tijdens de ](setup-experience-platform.md) les van het Experience Platform van de Opstelling 0} {.[
>![Profielschema ](assets/schema-profile.png)

Selecteer **[!UICONTROL Save]** rechtsboven om deze les te voltooien.

![ sparen Schema ](assets/schema-select-save.png)


Nu, kunt u dit schema van verwijzingen voorzien wanneer u de uitbreiding van SDK van het Web aan uw markeringsbezit toevoegt.


[Volgende: ](configure-identities.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over de SDK van Adobe Experience Platform Web. Als u vragen hebt, algemene terugkoppelen wilt delen, of suggesties over toekomstige inhoud hebben, gelieve hen op deze [ Communautaire besprekingspost van de Experience League te delen ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
