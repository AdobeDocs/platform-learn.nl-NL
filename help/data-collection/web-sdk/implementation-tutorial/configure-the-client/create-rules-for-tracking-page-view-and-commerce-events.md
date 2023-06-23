---
title: Regels maken voor het bijhouden van paginaweergaven en commerciële gebeurtenissen
description: Regels maken voor het bijhouden van paginaweergaven en commerciële gebeurtenissen
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
jira: KT-10447
hide: true
hidefromtoc: true
exl-id: 2dd02462-ddb5-4f67-8b0f-4a5bf5f7d655
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# Regels maken voor het bijhouden van paginaweergaven en commerciële gebeurtenissen

Als u wilt controleren of de gebruiker de productpagina heeft weergegeven, maakt u een regel binnen Adobe Experience Platform-tags. Doe dit door op [!UICONTROL Regels] in het linkermenu klikt u op [!UICONTROL Regel toevoegen].

Voor de regelnaam voert u _Pagina weergegeven_.

## Een gebeurtenis toevoegen

Klik op de knop [!UICONTROL Toevoegen] knop onder [!UICONTROL Gebeurtenissen]. U kunt nu tonen dat deze zich in de gebeurtenisweergave bevindt. Voor de [!UICONTROL Extensie] veld, selecteren [!UICONTROL Gegevenslaag Adobe-client]. Voor de [!UICONTROL Type gebeurtenis] veld, selecteren [!UICONTROL Gegevens geplakt].

Omdat u deze regel alleen wilt activeren als de `pageViewed` -gebeurtenis naar de gegevenslaag wordt geduwd, selecteert u [!UICONTROL Specifieke gebeurtenis] krachtens [!UICONTROL Luisteren naar] en type _pageViewed_ in de [!UICONTROL Gebeurtenis/sleutel waarvoor u zich wilt registreren] tekstveld.

![Gebeurtenis Pagina weergegeven](../../../assets/implementation-strategy/page-viewed-event.png)

Klikken [!UICONTROL Wijzigingen behouden].

## Een handeling toevoegen

Nu u bij de regelweergave bent, klikt u op de knop [!UICONTROL Toevoegen] knop onder [!UICONTROL Handelingen]. U moet nu in de actieweergave zijn. Voor de [!UICONTROL Extensie] veld, selecteren [!UICONTROL Adobe Experience Platform Web SDK]. Voor de [!UICONTROL Type handeling] veld, selecteren [!UICONTROL Gebeurtenis Send]. Met deze actie kunt u een ervaringsgebeurtenis naar Adobe Experience Platform Edge Network sturen.

Zoek aan de rechterkant van het scherm de [!UICONTROL Type] veld en selecteer `web.webpagedetails.pageViews`. Dit is een van de canonieke gebeurtenistypen van de Ervaring die Adobe Experience Platform uit de doos verstrekt. Deze vertegenwoordigt een paginaweergave.

Voor de [!UICONTROL XDM-gegevens] veld, Enter `%event.fullState%`. Dit wijst erop dat de gegevens verwerkte staat (die ook als volledige staat wordt bekend) van de gegevenslaag, die op het tijdstip wordt gevangen de regel werd teweeggebracht, als deel van de ervaringsgebeurtenis zou moeten worden verzonden.

![Handeling Pagina weergegeven](../../../assets/implementation-strategy/page-viewed-action.png)

Als de gegevens die u van uw website in de gegevenslaag hebt geduwd niet met uw XDM-schema in overeenstemming waren, of als u slechts een gedeelte van de gegevens wilt verzenden verwerkte staat van de gegevenslaag, gebruik [!UICONTROL XDM-object] het type gegevenselement (verstrekt door de uitbreiding van SDK van het Web van Adobe Experience Platform) om een aangewezen voorwerp te bouwen dat uw schema aanpast.

Klik op de knop [!UICONTROL Wijzigingen behouden] knop.

## De regel opslaan

Uw regel moet nu volledig zijn.

![Regel voor weergegeven pagina](../../../assets/implementation-strategy/page-viewed-rule.png)

Sla de regel op door op [!UICONTROL Opslaan].

## Het proces herhalen

Herhaal het hierboven beschreven proces om regels te maken voor het bekijken van een product, het openen van een winkelwagentje en het toevoegen van een product aan het winkelwagentje. De enige verschillen tussen de regels zijn de regelnaam, de waarde die in de [!UICONTROL Gebeurtenis/sleutel waarvoor u zich wilt registreren] in het [!UICONTROL Gegevens geplakt] en de [!UICONTROL Type] in het [!UICONTROL Gebeurtenis Send] handeling. Hier volgen de waarden voor elke regel:

Regel voor productweergave:

* **Naam van regel**: _Weergegeven product_
* **Gebeurtenis/sleutel waarvoor u zich wilt registreren** binnen [!UICONTROL Gegevens geplakt] gebeurtenis: `productViewed`
* **Type** binnen [!UICONTROL Gebeurtenis Send] handeling: `commerce.productViews`

Regel voor openen van winkelwagentje:

* **Naam van regel**: _Winkelwagentje geopend_
* **Gebeurtenis/sleutel waarvoor u zich wilt registreren** binnen [!UICONTROL Gegevens geplakt] gebeurtenis: `cartOpened`
* **Type** binnen [!UICONTROL Gebeurtenis Send] handeling: `commerce.productListOpens`

Product toegevoegd aan de kartelregel:

* **Naam van regel**: _Product toegevoegd aan winkelwagentje_
* **Gebeurtenis/sleutel waarvoor u zich wilt registreren** binnen [!UICONTROL Gegevens geplakt] gebeurtenis: `productAddedToCart`
* **Type** binnen [!UICONTROL Gebeurtenis Send] handeling: `commerce.productListAdds`

Hierna volgen we de muisklikken op het tabblad [!UICONTROL De app downloaden] koppeling.
