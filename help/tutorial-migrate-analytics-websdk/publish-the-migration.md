---
title: 'Publish: migratie naar staging en productie'
description: Wanneer alle ontwikkeling voor de migratie is voltooid en gevalideerd, kunt u opbouwen tot een gefaseerde installatie en vervolgens publiceren naar de productie wanneer u klaar bent.
solution: Data Collection, Analytics
feature: Web SDK
jira: KT-16767
source-git-commit: 15f2122c53a3b2f3dc1942502e908403e55519ab
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 0%

---


# Publish: migratie naar staging en productie

Wanneer alle ontwikkeling voor de migratie is voltooid en gevalideerd, kunt u opbouwen tot een gefaseerde installatie en vervolgens publiceren naar de productie wanneer u klaar bent.

## Overzicht

Dit is echt de laatste belangrijkste stap van uw migratie, en het is om de bibliotheek te verplaatsen die u hebt gebruikt om uw migratie te ontwikkelen en te testen samen aan uw het opvoeren milieu voor het definitieve testen daar, en dan op het productiemilieu.

Als u terug naar [ gaat creeer en vorm een datastream ](create-and-configure-the-analytics-datastream.md) les, zult u aan het eind van het zien dat wij op de het opvoeren gegevensstroom hebben gericht om de analysegegevens naar de zelfde reeks van het ontwikkelingsrapport (of alternatief aan een nieuwe het opvoeren rapportreeks) te verzenden. U wordt er ook aan herinnerd dat we de productiedatabase hebben aangeroepen om gegevens te verzenden naar de bestaande productierapportsuite die u hebt gebruikt.
Dit is slechts goede informatie om te hebben aangezien wij nu de gemigreerde bibliotheek langs de het publiceren weg aan opvoeren en productie bewegen.

## Overstappen op staging- en productieomgevingen

Hier volgen de stappen waarmee onze bibliotheek wordt verplaatst naar een testomgeving en productieomgeving:

1. Selecteer in de interface Codes de optie Stroom publiceren links in de navigatie
1. U zou uw migratiebibliotheek onder Ontwikkeling moeten zien (naam die is wat u aan het begin van dit migratieproces hebt gekozen)

   ![ bibliotheek van de Migratie in Dev ](assets/migration-lib-in-dev.jpg)

1. Als u zeker weet dat u al elke wijziging in de bibliotheek hebt toegevoegd, kunt u de bibliotheek onder de drie punten naar voren verplaatsen en de volgende stappen overslaan. Als u niet zeker bent, volg de volgende vijf stappen.
1. Klik op de naam van de bibliotheek om de bibliotheekdetails in te vullen
1. Controleer of u zich in de juiste bibliotheek bevindt via de naam
1. Selecteer Alle gewijzigde bronnen onder aan de pagina toevoegen
1. Klik vervolgens op Opslaan en bouwen naar ontwikkeling om alle wijzigingen in de wachtrij toe te voegen aan de bibliotheek

   ![ voeg alle veranderde middelen ](assets/add-all-changed-resources.jpg) toe

1. Hierdoor gaat u terug naar de interface van de publicatiestroom. Als de build met succes wordt voltooid, wordt er een groene stip weergegeven naast de bibliotheek.
1. Vervolgens kunt u uw bibliotheek naar wens verplaatsen in het publicatieproces. U kunt het voor goedkeuringen plaatsen, het verplaatsen naar het opvoeren om daar te testen en goed te keuren, of zelfs het voor goedkeuring verplaatsen of direct publiceren op productie. Dit hangt weer af van de publicatiebehoeften van uw organisatie.

   ![ het Publiceren proces ](assets/publishing-process.jpg)

Gefeliciteerd! Op dit punt, is uw implementatie van Analytics volledig op het Web SDK!

Ik wil hier een belangrijke opmerking toevoegen die we aan het begin van deze zelfstudie hadden:

>[!IMPORTANT]
>
>Het is belangrijk om op te merken dat een van de belangrijkste redenen dat u deze migratie van uw implementatie uitvoert, is om Adobe Experience Platform-toepassingen voor te bereiden, zoals Customer Journey Analytics, Real-Time CDP of Journey Optimizer (zoals vermeld in #3 hierboven). Het gebruik van uw websitegegevens voor dit doel bevat aanvullende stappen die niet in deze zelfstudie zijn opgenomen, maar deze zelfstudie is zeker een voorwaarde voor die verdere voortgang van uw implementatie. Voltooi deze zelfstudie dan ook en voer de stappen uit die nodig zijn om dezelfde websitegegevens ook naar het Experience Platform te verzenden.

Veel succes op uw reis met analyses en andere content en marketinginspanningen!
