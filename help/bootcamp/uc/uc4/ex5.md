---
title: Bootkamp - Customer Journey Analytics - Visualisatie met behulp van Customer Journey Analytics
description: Bootkamp - Customer Journey Analytics - Visualisatie met behulp van Customer Journey Analytics
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
solution: Customer Journey Analytics
feature-set: Customer Journey Analytics
feature: Visualizations
exl-id: 051b5b91-56c4-414e-a4c4-74aa67219551
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '1479'
ht-degree: 0%

---

# 4.5 Visualisatie met Customer Journey Analytics

## Doelstellingen

- Analysis Workspace-gebruikersinterface begrijpen
- Leer een functie die Analysis Workspace zo verschillend maakt.
- Leer hoe u in CJA analyseert met Analysis Workspace

## Context

In deze exercitie gebruikt u Analysis Workspace in CJA om productweergaven, producttrechters, churn enz. te analyseren.

Laten wij het project gebruiken u in [&#x200B; 4.4 Voorbereiding van Gegevens in Analysis Workspace &#x200B;](./ex4.md) creeerde, zo ga [&#x200B; https://analytics.adobe.com &#x200B;](https://analytics.adobe.com).

![&#x200B; demo &#x200B;](./images/prohome.png)

Open uw project `yourLastName - Omnichannel Analysis` .

Als uw project is geopend en de gegevensweergave `CJA Bootcamp - Omnichannel Data View` is geselecteerd, kunt u uw eerste visualisaties gaan maken.

![&#x200B; demo &#x200B;](./images/prodataView1.png)

## Hoeveel productweergaven hebben we dagelijks

Allereerst moeten we de juiste data selecteren om de gegevens te analyseren. Ga naar de kalenderdropdown op de rechterkant van het canvas. Klik erop en selecteer het toepasselijke datumbereik.

>[!IMPORTANT]
>
>De meest recente beschikbare gegevens zijn ingevoerd op 19-09-2022. Selecteer een datumbereik dat deze datum bevat.

![&#x200B; demo &#x200B;](./images/pro1.png)

In het linkerzijmenu (componentengebied), vind de Berekende Metrische **Kijken van het Product**. Selecteer het en sleep het en laat vallen het binnen aan het canvas, op het hoogste recht binnen de vrije vormlijst.

![&#x200B; demo &#x200B;](./images/pro2.png)

Automatisch zal de afmeting **Dag** worden toegevoegd om uw eerste lijst tot stand te brengen. Nu kunt u zien hoe uw vraag direct wordt beantwoord.

![&#x200B; demo &#x200B;](./images/pro3.png)

Klik vervolgens met de rechtermuisknop op het metrische overzicht.

![&#x200B; demo &#x200B;](./images/pro4.png)

Klik op **visualiseren** en selecteer dan **Lijn** als visualisatie.

![&#x200B; demo &#x200B;](./images/pro5.png)

Je ziet je producten dagelijks.

![&#x200B; demo &#x200B;](./images/pro6.png)

U kunt het tijdwerkingsgebied in dag veranderen door op **Montages** binnen visualisatie te klikken.

![&#x200B; demo &#x200B;](./images/pro7.png)

Klik op de punt naast **Lijn** om **de Gegevens Source** te beheren.

![&#x200B; demo &#x200B;](./images/pro7a.png)

Daarna, klik **de Selectie van het Slot** en selecteer **Geselecteerde Punten** om deze visualisatie te sluiten zodat het altijd een chronologie van de Mening van het Product toont.

![&#x200B; demo &#x200B;](./images/pro7b.png)

## Top 4 van producten weergegeven

Wat zijn de vier belangrijkste producten die worden weergegeven?

Vergeet niet om het project nu en dan op te slaan.

| OS | Korte snede |
| ----------------- |-------------| 
| Windows | Control + S |
| Mac | Command + S |

Laten we de beste vier bekeken producten vinden. In het linkerzijmenu, vind de **Naam van het Product** - Dimension.

![&#x200B; demo &#x200B;](./images/pro8.png)

Nu belemmering en laat vallen {de Naam van het 0} Product **om de** 3&rbrace; dimensie van de Dag te vervangen:**&#x200B;**

Dit zal het resultaat zijn

![&#x200B; demo &#x200B;](./images/pro10a.png)

Probeer vervolgens een van de producten te splitsen op merknaam. Onderzoek naar **brandName** en sleep het onder de eerste productnaam.

![&#x200B; demo &#x200B;](./images/pro13.png)

Daarna, doe een verdeling gebruikend het loyaliteitsniveau. Onderzoek naar **Niveau van de Loyaliteit** en sleep het onder de merknaam.

![&#x200B; demo &#x200B;](./images/pro15.png)

U zult dan dit zien:

![&#x200B; demo &#x200B;](./images/pro15a.png)

Tot slot kunt u meer visualisaties toevoegen. Zoek links onder visualisatie naar `Donut` . Neem `Donut`, belemmering-en-daling het op het canvas onder de **visualisatie van de Lijn**.

![&#x200B; demo &#x200B;](./images/pro18.png)

Daarna, in de Lijst, selecteer de 3 **rijen van het Niveau van de Loyalty** van de onderbreking wij onder **het Pixel XL 32GB Zwarte Smartphone van Google** > **het Signaal van Citi** deden. Terwijl het selecteren van de 3 rijen, houd **CTRL** knoop (op Vensters) of **Bevel** knoop (op Mac).

![&#x200B; demo &#x200B;](./images/pro20.png)

Het donutdiagram is gewijzigd:

![&#x200B; demo &#x200B;](./images/pro21.png)

U kunt zelfs het ontwerp aanpassen om beter leesbaar te zijn, door zowel de **grafiek van de Lijn** als de **grafiek van de Donut** kleiner te maken zodat kunnen zij naast elkaar passen:

![&#x200B; demo &#x200B;](./images/pro22.png)

Klik op de punt naast **Donut** om **de Gegevens Source** te beheren.
Daarna, klik **de Selectie van het Slot** om deze visualisatie te sluiten zodat het altijd een chronologie van de Mening van het Product toont.

![&#x200B; demo &#x200B;](./images/pro22b.png)

Meer informatie over visualisaties met Analysis Workspace vindt u hier:

- [&#x200B; https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/freeform-analysis-visualizations.html?lang=nl-NL](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/freeform-analysis-visualizations.html?lang=nl-NL)
- [&#x200B; https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/t-sync-visualization.html?lang=nl-NL](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/t-sync-visualization.html?lang=nl-NL)

## Trechter met productinteracties, van weergave tot aankoop

Er zijn veel manieren om deze kwestie op te lossen. Één van hen moet het Type van Interactie van het Product gebruiken en het op een vrije vormlijst gebruiken. Een andere manier is de Visualisatie van de a **Vallout** te gebruiken. Laten we de laatste gebruiken die we tegelijkertijd willen visualiseren en analyseren.

Sluit het huidige deelvenster door hier te klikken:

![&#x200B; demo &#x200B;](./images/pro23.png)

Voeg nu een nieuw leeg paneel toe door op **+ te klikken voegt Leeg Comité toe**.

![&#x200B; demo &#x200B;](./images/pro24.png)

Klik de visualisatie **Vallout**.

![&#x200B; demo &#x200B;](./images/pro25.png)

Selecteer hetzelfde datumbereik als in de vorige exercitie.

![&#x200B; demo &#x200B;](./images/pro1.png)

Dan zie je dit.

![&#x200B; demo &#x200B;](./images/prodatefa.png)

Vind het Type van de afmeting **Gebeurtenis** onder de componenten op de linkerkant:

![&#x200B; demo &#x200B;](./images/pro26.png)

Klik op de pijl om de dimensie te openen:

![&#x200B; demo &#x200B;](./images/pro27.png)

Alle beschikbare gebeurtenistypen worden weergegeven.

![&#x200B; demo &#x200B;](./images/pro28.png)

Selecteer het punt **commerce.productViews** en sleep en laat vallen het op **toevoegen Touchpoint** gebied binnen de **Visualisatie van de Vallout**.

![&#x200B; demo &#x200B;](./images/pro29.png)

Doe het zelfde met **commerce.productListAdds** en **commerce.purchase** en laat vallen hen op **toevoegen Aanraakpunt** gebied binnen de **Visualisatie van de Vallout**. Uw visualisatie ziet er nu als volgt uit:

![&#x200B; demo &#x200B;](./images/props1.png)

Je kunt hier veel doen. Sommige voorbeelden: vergelijk in de loop der tijd elke stap per apparaat of vergelijk elke stap per loyaliteit. Maar als we interessante dingen willen analyseren zoals waarom klanten geen artikelen kopen nadat ze een artikel aan hun winkelwagentje hebben toegevoegd, kunnen we het beste hulpmiddel in CJA gebruiken: klik met de rechtermuisknop.

Klik met de rechtermuisknop op het aanraakpunt **commerce.productListAdds**. Dan klik op **val van de Onderbreking op dit aanraakpunt**.

![&#x200B; demo &#x200B;](./images/pro32.png)

Er wordt een nieuwe vrije-vormtabel gemaakt om te analyseren wat de mensen deden als ze niets hadden aangeschaft.

![&#x200B; demo &#x200B;](./images/pro33.png)

Verander het **Type van Gebeurtenis** door **Naam van de Pagina**, in de nieuwe vrije lijst, om te zien welke pagina&#39;s zij in plaats van de Pagina van de Bevestiging van de Aankoop gaan.

![&#x200B; demo &#x200B;](./images/pro34.png)

## Wat doen de mensen op de plaats alvorens de Cancel pagina van de Dienst te bereiken?

Nogmaals, er zijn vele manieren om deze analyse uit te voeren. Laten we de flowanalyse gebruiken om het detectieonderdeel te starten.

Sluit het huidige deelvenster door hier te klikken:

![&#x200B; demo &#x200B;](./images/pro0.png)

Voeg nu een nieuw leeg paneel toe door op **+ te klikken voegt Leeg Comité toe**.

![&#x200B; demo &#x200B;](./images/pro0a.png)

Klik de visualisatie **Stroom**.

![&#x200B; demo &#x200B;](./images/pro35.png)

U zult dan dit zien:

![&#x200B; demo &#x200B;](./images/pro351.png)

Selecteer hetzelfde datumbereik als in de vorige exercitie.

![&#x200B; demo &#x200B;](./images/pro1.png)

Vind de afmeting **Naam van de Pagina** onder de componenten op de linkerkant:

![&#x200B; demo &#x200B;](./images/pro36.png)

Klik op de pijl om de dimensie te openen:

![&#x200B; demo &#x200B;](./images/pro37.png)

Alle weergegeven pagina&#39;s worden gevonden. Vind de paginanaam: **annuleert Dienst**.
De belemmering en laat vallen **annuleert Dienst** in de Visualisatie van de Stroom op het middelste gebied:

![&#x200B; demo &#x200B;](./images/pro38.png)

U zult dan dit zien:

![&#x200B; demo &#x200B;](./images/pro40.png)

Laten wij nu analyseren als de klanten die **hebben bezocht annuleer de pagina van de Dienst** op de website ook callcenter riepen, en wat het resultaat was.

Onder de afmetingen, ga terug en vind dan **het Type van Interactie van de Vraag**.
De belemmering en laat vallen **Type van Interactie van de Vraag** om de eerste interactie op het recht binnen de **Visualisatie van de Stroom** te vervangen.

![&#x200B; demo &#x200B;](./images/pro43.png)

U ziet nu het steunkaartje van de klanten die het vraagcentrum na het bezoeken van **roepen annuleert de pagina van de Dienst**.

![&#x200B; demo &#x200B;](./images/pro44.png)

Daarna, onder de dimensies, onderzoek naar **het Etiketteren van de Vraag**.  De belemmering en laat vallen het om de eerste interactie op het recht binnen de **Visualisatie van de Stroom** te vervangen.

![&#x200B; demo &#x200B;](./images/pro46.png)

U zult dan dit zien:

![&#x200B; demo &#x200B;](./images/flow.png)

Zoals u kunt zien, hebben wij een omnichannel analyse in werking gesteld gebruikend de Visualisatie van de Stroom. Daardoor hebben we ontdekt dat sommige klanten die van plan waren hun service te annuleren, een positief gevoel hadden nadat ze het callcenter hadden gebeld. Hebben we misschien hun gedachten veranderd met een promotie?


## Hoe presteert de klanten met een Positief contact Callcenter tegen belangrijkste KPIs?

Laten wij eerst de gegevens segmenteren om slechts gebruikers met **positieve** vraag te krijgen. In CJA, worden de Segmenten genoemd Filters. Ga naar filters binnen het componentengebied (op de linkerkant) en klik **+**.

![&#x200B; demo &#x200B;](./images/pro58.png)

Geef binnen de filterconstructor een naam op voor het filter

| Naam | Beschrijving |
| ----------------- |-------------| 
| Bellen - Positief | Bellen - Positief |

![&#x200B; demo &#x200B;](./images/pro47.png)

Onder de componenten (binnen de Bouwer van de Filter), vind **het Keren van de Vraag** en sleep en laat vallen het in de Definitie van de Bouwer van de Filter.

![&#x200B; demo &#x200B;](./images/pro48.png)

Nu uitgezochte **positief** als waarde voor de filter.

![&#x200B; demo &#x200B;](./images/pro49.png)

Verander het werkingsgebied om **Persoonlijk** niveau te zijn.

![&#x200B; demo &#x200B;](./images/pro50.png)

Om te beëindigen, klik eenvoudig **sparen**.

![&#x200B; demo &#x200B;](./images/pro51.png)

Dan ben je hier weer. Sluit het vorige deelvenster als dat nog niet is gedaan.

![&#x200B; demo &#x200B;](./images/pro0c.png)

Voeg nu een nieuw leeg paneel toe door op **+ te klikken voegt Leeg Comité toe**.

![&#x200B; demo &#x200B;](./images/pro24c.png)

Selecteer hetzelfde datumbereik als in de vorige exercitie.

![&#x200B; demo &#x200B;](./images/pro1.png)

Klik op **Vrije vormlijst**.

![&#x200B; demo &#x200B;](./images/pro52.png)

Sleep nu het filter dat u zojuist hebt gemaakt.

![&#x200B; demo &#x200B;](./images/pro53.png)

Tijd voor het toevoegen van cijfers. Begin met **Weergaven van het Product**. Sleep en zet het neer in de vrije-vormlijst. U kunt ook de **metrische Gebeurtenissen** schrappen.

![&#x200B; demo &#x200B;](./images/pro54.png)

Doe het zelfde met **Mensen**, **toevoegen aan Kaart** en **Aankopen**. Je komt dan met zo&#39;n tafel.

![&#x200B; demo &#x200B;](./images/pro55.png)

Dankzij de eerste stroomanalyse kwam er een nieuwe vraag op. Dus besloten we deze tabel te maken en een aantal KPI&#39;s te controleren op een segment om die vraag te beantwoorden. Zoals u kunt zien, is tijd aan inzicht veel sneller dan het gebruiken van SQL of het gebruiken van andere oplossingen van BI.

## Customer Journey Analytics- en Analysis Workspace-opbergplaats

Zoals u in dit laboratorium hebt geleerd, hecht Analysis Workspace gegevens van alle kanalen samen om de volledige klantenreis te analyseren. Vergeet ook niet dat u gegevens naar dezelfde werkruimte kunt brengen die niet aan de reis is gekoppeld.
Het kan echt nuttig zijn om losgekoppelde gegevens in uw analyse te brengen om context aan de reis te geven. Voorbeelden zijn onder andere NPS-gegevens, enquêtes, Facebook Ads-gebeurtenissen of offline-interacties (niet geïdentificeerd).

Volgende Stap: [&#x200B; 4.6 van inzichten aan actie &#x200B;](./ex6.md)

[Ga terug naar Gebruikersstroom 4](./uc4.md)

[Terug naar alle modules](./../../overview.md)
