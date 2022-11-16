---
title: Regels maken voor het bijhouden van paginaweergaven en commerciële gebeurtenissen
description: Regels maken voor het bijhouden van paginaweergaven en commerciële gebeurtenissen
exl-id: 00bf3374-9319-47ce-a75a-2b94f793c938
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 0%

---

# Regels maken voor het bijhouden van paginaweergaven en commerciële gebeurtenissen

Als u wilt controleren of de gebruiker de productpagina heeft bekeken, maakt u een regel in Adobe Experience Platform [!DNL Tags].

1. Klikken op **[!UICONTROL Regels]** in de linkerzijnavigatie, dan klik **[!UICONTROL Nieuwe regel maken]**.

1. Voor de regelnaam voert u **_Pagina weergegeven_**.

## Een gebeurtenis toevoegen

1. Klik op de knop **[!UICONTROL Toevoegen]** knop onder [!UICONTROL Gebeurtenissen]. U kunt nu tonen dat deze zich in de gebeurtenisweergave bevindt. Voor de [!UICONTROL Extensie] veld, selecteren **[!UICONTROL Gegevenslaag Adobe-client]**. Voor de [!UICONTROL Type gebeurtenis] veld, selecteren **[!UICONTROL Gegevens geplakt]**.
1. Omdat u deze regel alleen wilt activeren als de `pageViewed` -gebeurtenis naar de gegevenslaag wordt geduwd, selecteert u **[!UICONTROL Specifieke gebeurtenis]** krachtens [!UICONTROL Luisteren naar] en type **_pageViewed_** in de [!UICONTROL Gebeurtenis/sleutel waarvoor u zich wilt registreren] tekstveld.
1. Klikken **[!UICONTROL Wijzigingen behouden]**.
   ![Gebeurtenis Pagina weergegeven](../assets/page-viewed-event.png)

## Een handeling toevoegen

Nu u weer bij de regelweergave bent:

1. Klik op de knop **[!UICONTROL Toevoegen]** knop onder [!UICONTROL Handelingen]. U moet nu in de actieweergave zijn. Voor de [!UICONTROL Extensie] veld, selecteren **[!UICONTROL Adobe Experience Platform Web SDK]**. Voor de [!UICONTROL Type handeling] veld, selecteren **[!UICONTROL Gebeurtenis Send]**. Met deze actie kunt u een ervaringsgebeurtenis naar Adobe Experience Platform Edge Network sturen.
1. In het midden van het scherm, vind [!UICONTROL Type] veld en selecteer **`web.webpagedetails.pageViews`**. Dit is een van de canonieke gebeurtenistypen van de Ervaring die Adobe Experience Platform uit de doos verstrekt. Deze vertegenwoordigt een paginaweergave.
1. Voor de [!UICONTROL XDM-gegevens] veld, Enter **`%event.fullState%`**. Dit wijst erop dat de gegevens verwerkte staat (die ook als volledige staat wordt bekend) van de gegevenslaag, die op het tijdstip wordt gevangen de regel werd teweeggebracht. Dit moet als onderdeel van de ervaringsgebeurtenis worden verzonden.
1. Klik op de knop **[!UICONTROL Wijzigingen behouden]** knop.
   ![Handeling Pagina weergegeven](../assets/page-viewed-action.png)

Als de gegevens die u van uw website in de gegevenslaag hebt geduwd niet met uw XDM-schema in overeenstemming waren, of als u slechts een gedeelte van de gegevens wilt verzenden verwerkte staat van de gegevenslaag, gebruik [!UICONTROL XDM-object] het type gegevenselement (verstrekt door de uitbreiding van SDK van het Web van Adobe Experience Platform) om een aangewezen voorwerp te bouwen dat uw schema aanpast.

## De regel opslaan

1. Sla de regel op door op **[!UICONTROL Opslaan]**.
   ![Regel voor weergegeven pagina](../assets/page-viewed-rule.png)

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

Daarna, behandelen wij het volgen klikken op [!UICONTROL De app downloaden] koppeling.

[Volgende: ](create-a-data-element-and-rule-for-tracking-app-downloads.md)

>[!NOTE]
>
>Dank u voor het investeren van uw tijd in het leren over de Inzameling van Gegevens. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)
