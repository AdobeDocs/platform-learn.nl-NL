---
title: Globale variabelen migreren
description: Leer hoe te om globale variabelen van de de uitbreidingsconfiguratie van Analytics aan Web SDK te migreren
solution: Data Collection, Analytics
feature: Web SDK
jira: KT-17277
exl-id: 0917e951-c7e0-4723-8354-d308890bdaac
source-git-commit: 744b26da58307f0d6f6e8715a534ca814e02371c
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 0%

---

# Globale variabelen migreren

In deze oefening zult u leren hoe te om globale variabelen van de de uitbreidingsconfiguratie van Analytics aan Web SDK te migreren.

## Overzicht

In de extensie Adobe Analytics is er een configuratiesectie met de naam &quot;Algemene variabelen&quot;.

![ Globale het Etiket van Variabelen ](assets/analytics-global-variables-label.jpg)

Algemene variabelen zijn variabelen die in het object Analytics tracking worden ingesteld wanneer dat object op de pagina wordt geïnitialiseerd. Alle variabelen die u hier instelt, worden ingesteld wanneer het volgende object op elke pagina wordt gemaakt.

![ Globale geplaatste variabelen ](assets/analytics-set-global-variables.jpg)

Als u hier variabelen hebt worden geplaatst, moeten wij deze aan het Web SDK eveneens migreren.

## Waar kan ik globale variabelen toevoegen in de Web SDK?

De **bodemlijn** is hier dat er geen gelijkwaardig gebied in de configuratie van de uitbreiding van SDK van het Web is, zodat zal het niet zo gemakkelijk zijn zoals eenvoudig het kopiëren over de variabelen zoals wij in de Standaardoefening van de Regel van de Lading van de Pagina deden.
In plaats daarvan, is het korte antwoord: **creeer een nieuwe regel die vóór de andere regels op elke pagina loopt, en plaats de variabelen daarin.**

Als u geen stappen nodig hebt die voor u zijn gedefinieerd, gaat u dat doen en bent u klaar met deze les. Als u hulp wilt, gaat u verder...

### Stappen voor het migreren van Globale Variabelen aan Web SDK

1. De Adobe Analytics-extensieconfiguratie openen

   ![ de uitbreidingsconfig van aa ](assets/configure-analytics-extension.jpg)

1. Schuif omlaag naar de sectie Algemene variabelen (afbeelding hierboven), open deze en noteer alle variabelen die worden ingesteld. U moet deze variabelen en waarden later kennen.
1. Annuleer de extensie Analytics.
1. Selecteer **Regels** in de linkernavigatie, en de klik **voegt Regel** toe.
1. Noem uw nieuwe regel &quot;Globale Variabelen&quot;.
1. Klik op de knop Toevoegen onder Gebeurtenissen.

   ![ Globale Veranderlijke regel 1 ](assets/global-variable-rule-1.jpg)

1. Vorm uw gebeurtenis om vóór uw andere regels teweeg te brengen. U moet het gebeurtenistype en de volgorde weten die u in andere regels hebt gebruikt. Voorbeelden:
   1. Plaats de **Uitbreiding** aan Kern
   1. **Type van Gebeurtenis** kon klaar DOM, afhankelijk van uw implementatie zijn
   1. Breid **Geavanceerde Opties** uit
   1. Plaats de **Orde** aan een lager aantal dan uw andere regels, zodat het eerst zal uitvoeren.
      ![ vorm Globale Veranderlijke Gebeurtenis ](assets/configure-global-variable-event.jpg)
      >[!NOTE]
      >
      >Het belangrijkste ding hier is dat deze regel vóór de standaardpaginalading regel in brand steekt, zodat om het even welke die variabelen in deze regel worden geplaatst naar Analytics via de sendEvent regel kunnen worden verzonden. Nochtans, stellen wij voor dat deze regel **eerst** in werking stelt algemeen, omdat de variabelen die in de Globale sectie van Variabelen in de uitbreiding van de Analyse worden geplaatst in andere regels konden worden veranderd. Die functionaliteit nastreven we. In het bovenstaande voorbeeld gaan we ervan uit dat &quot;10&quot; een lager bestelnummer is dan een van uw andere regels. Als dat niet juist is, wijzigt u het getal in een lager getal dan de andere regels.
1. Selecteer **houden Veranderingen** om uw werk te bewaren.
1. U te hoeven niet om voorwaarden aan deze regel toe te voegen, zodat kunt u die sectie van regelverwezenlijking alleen verlaten.
1. Klik het plusteken onder **sectie van Acties**
1. De nieuwe handeling configureren
   1. Kies de Extensie van SDK van het Web van Adobe Experience Platform ****
   1. Voor **Type van Actie**, kies de Variabele van de Update
   1. Op het recht, kies uw veranderlijk **Element van Gegevens** (voor dit leerprogramma, werd het genoemd &quot;Element van de Gegevens van de Mening van de Pagina,&quot;maar uw kan variëren)
   1. Selecteer **Analytics** onder het gegevensvoorwerp
   1. Vul de variabelen die u hebt opgeslagen vanuit de sectie Globale variabelen in de extensieconfiguratie Analytics (in het voorbeeld van deze zelfstudie, eVar10 instellen op het gegevenselement Paginatype)

   ![ websdk-global-variables-action ](assets/websdk-global-variables-action.jpg)

1. Wijzigingen behouden
1. Sla de regel op in uw werkbibliotheek en build

Uw globale variabelen worden nu gemigreerd naar Web SDK en zullen op om het even welke paginading in brand steken.
