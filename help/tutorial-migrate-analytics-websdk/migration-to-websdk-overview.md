---
title: Adobe Analytics migreren naar Web SDK met tags
description: Leer de stappen die u tijdens de migratie naar Web SDK gaat nemen, en de beslissingen die onderweg moeten worden genomen.
solution: Data Collection, Analytics
feature: Web SDK
jira: KT-16755
exl-id: e578b669-42b4-46ae-b6e6-6688e5c5c772
source-git-commit: d6471c8e383e22fed4ad5870952d0d0470f593db
workflow-type: tm+mt
source-wordcount: '1157'
ht-degree: 0%

---

# Adobe Analytics migreren naar Web SDK met tags

Leer de stappen om een implementatie van Adobe Analytics te migreren gebruikend de uitbreiding van Analytics in de Markeringen van het Experience Platform (vroeger die als Lancering wordt bekend) aan Web SDK, die de uitbreiding van SDK van het Web ook in Markeringen gebruikt. Wanneer de extensie Adobe Analytics in Tags wordt gebruikt, wordt achter de schermen de code &quot;AppMeasurement.js&quot; gebruikt. Daarom kunt u aan dit als een leerprogramma denken dat AppMeasurement aan het Web SDK migreert, maar dit leerprogramma is volledig in Markeringen en behandelt NIET het bewegen van naar of van een implementatie van JavaScript (met uitzondering van de code van JavaScript die binnen de Codes UI wordt gebruikt). Voor migratie van de implementaties van JavaScript, gelieve te zien de [ documentatie ](https://experienceleague.adobe.com/en/docs/analytics/implementation/aep-edge/web-sdk/appmeasurement-to-web-sdk).

>[!NOTE]
>
>Soortgelijke migratiezelfstudies zijn beschikbaar voor:
>
> * [ Adobe Target ](../tutorial-migrate-target-websdk/introduction.md)
> * [ Adobe Audience Manager ](https://experienceleague.adobe.com/nl/docs/audience-manager/user-guide/migrate-to-web-sdk/appmeasurement-to-web-sdk)

>[!CAUTION]
>
> Omdat het Web SDK van het Platform veelvoudige Adobe toepassingen steunt, zouden alle bibliotheken van de Adobe op een bepaalde pagina tezelfdertijd moeten worden gemigreerd. Bijvoorbeeld, wordt een gemengde implementatie van Web SDK voor Doel en AppMeasurement voor Analytics op één enkele pagina _niet gesteund_. Nochtans, wordt een gemengde implementatie over verschillende pagina&#39;s gesteund, bijvoorbeeld Web SDK op pagina A, en at.js met AppMeasurement op pagina B.

## Wat u uit deze zelfstudie krijgt

Alvorens wij in de stappen springen om uw implementatie van Analytics te migreren, is het belangrijk dat u precies begrijpt wat u zult doen, die _implementatie_ voor Analytics verandert/bijwerkt. Aan het eind van deze zelfstudie, wanneer je in je rapporten kijkt en alles hetzelfde is, zou je je kunnen afvragen: &quot;Waarom heb ik dat allemaal gedaan?&quot; Er zijn andere documenten om de voordelen te schetsen van het gebruiken van het Web SDK voor uw implementatie van Analytics, maar een paar zijn:

1. Ondersteuning voor apparaat-id van eerste partij
1. Betere prestaties
1. Toekomstige tests van uw implementatie wanneer u de Adobe Experience Platform-toepassingen gaat gebruiken (nieuwe gebruiksscenario&#39;s inschakelen)

Neem contact op met uw Adobe Analytics-vertegenwoordiger voor meer informatie over hoe de Web SDK u kan helpen. Aangezien wij met dit leerprogramma verdergaan, zullen wij zich op _richten hoe_ om de migratie te doen.

>[!IMPORTANT]
>
>Het is belangrijk om op te merken dat een van de belangrijkste redenen dat u deze migratie van uw implementatie uitvoert, is om Adobe Experience Platform-toepassingen voor te bereiden, zoals Customer Journey Analytics, Real-Time CDP of Journey Optimizer (zoals vermeld in #3 hierboven). Het gebruik van uw websitegegevens voor dit doel bevat aanvullende stappen die niet in deze zelfstudie zijn opgenomen, maar deze zelfstudie is zeker een voorwaarde voor die verdere voortgang van uw implementatie. Voltooi deze zelfstudie dan ook en voer de stappen uit die nodig zijn om dezelfde websitegegevens ook naar het Experience Platform te verzenden.

## Migratiemethode

Er zijn waarschijnlijk veel manieren waarop u dit migratieproces kunt uitvoeren, maar we moeten hier over twee dingen spreken:

**Methode 1:** werk uw bestaand bezit van Markeringen aan Web SDK bij, creërend nieuwe gegevenselementen, en aanbrengend veranderingen in de regels die reeds in uw bezit bestaan.

**Methode 2:** u kon een nieuw bezit (door uw bestaande te kopiëren of één gloednieuw te creëren) ook tot stand brengen, en dan dat nieuw bezit met Web SDK in plaats van de uitbreiding van Adobe Analytics vormen.

**voor dit migratieleerprogramma, gaan wij Methode 1 gebruiken.** Op die manier zijn de insluitcodes die aan de eigenschap zijn gekoppeld, al ingesloten op uw ontwikkelings-, staging- en productiesites. Het is dus niet nodig om insluitcodes te wijzigen. Als u besluit om met Methode 2 te gaan, vergeet niet om de nieuwe bed codes voor elk milieu van de **sectie van Milieu&#39;s** van het nieuwe bezit te krijgen en hen in de hoofdsectie van uw plaats te plaatsen.

>[!NOTE]
>
>Hoewel we tijdens deze migratie gewoon onze bestaande eigenschap in Codes gaan bewerken, is het nog steeds een goed idee om voorzichtig te zijn. Daarom wordt u ten zeerste aangeraden een kopie van uw huidige eigenschap te maken voordat u de migratie start. Op die manier kon je altijd in de kopie kijken hoe de dingen waren voordat je ze veranderde, er code uit trok, enzovoort.
>Het is gewoon goed om voorzichtig te zijn, voor het geval dat. Maak een kopie van de eigenschap. Ik zal hier wachten tot je terug bent.

## Stappen voor het migreren van uw analytische implementatie naar Web SDK

Terwijl u de stappen doorloopt, zijn er een aantal punten die belangrijk zijn om te begrijpen:

1. Ten eerste hebt u wellicht al deze stappen nodig. Er is bijvoorbeeld een les over het migreren van aangepaste code. Als u een implementatie van Markeringen hebt die geen douanecode (met inbegrip van het gebruiken van stop-ins) gebruikt, dan zult u deze les niet nodig hebben. We hebben geprobeerd de lessen op te nemen die de meeste gebruikers nodig hebben, dus lees in ieder geval de lessen om te zien of u tijdens uw migratie aanpassingen aan uw site moet aanbrengen.
1. Bovendien is er gewoon geen manier voor ons om een migratiezelfstudie te maken die 100% van de gebruiksgevallen zal bestrijken die iedereen gebruikt. Zoals in het vorige punt vermeld, hebben we geprobeerd de lessen op te nemen die de meeste mensen nodig zullen hebben en die betrekking zullen hebben op de meeste gevallen van gebruik. Er zullen echter ongetwijfeld gebruiksgevallen zijn die niet in deze zelfstudie aan de orde komen. In dit geval, zie of geven de inbegrepen lessen u een goed idee van hoe u voor uw gebruiksgeval zou moeten migreren. U kunt uw edelen in de [ Gemeenschap van het Experience League voor gegevensinzameling ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/ct-p/adobe-launch-community) ook vragen.

Het migratieproces omvat de volgende belangrijke stappen:

1. Maak een rapportenpakket voor migratievalidatie.
1. Maak en configureer een gegevensstroom.
1. Voeg en vorm de uitbreiding van SDK van het Web in Markeringen (vroeger het Lanceren van de Adobe) toe.
1. Creeer een nieuw gegevenselement om gegevens binnen via het Web SDK te verzenden.
1. Migreer uw standaardregel voor het laden van pagina&#39;s om het de gegevenselement en de acties van SDK van het Web te gebruiken.
1. Migreer aangepaste code in regels of voor plug-ins.
1. Publish uw implementatiewijzigingen.
1. Begrijp hoe te om uw veranderingen te zuiveren en te bevestigen, en uw standaardpaginalading en de variabelen te bevestigen verbonden aan het. Deze validatie moet dan tijdens de migratie worden uitgevoerd wanneer u wijzigingen aanbrengt.
1. Migreer extra regels voor het laden van pagina&#39;s.
1. Aangepaste koppelingsregels migreren.
1. Na volledige validatie verwijdert u verwijzingen naar de extensie Analytics en verwijdert u de extensie zelf.
1. Nadat u alle wijzigingen hebt aangebracht, duwt u de bibliotheek door naar de testfase en vervolgens naar de productie.
1. Test opnieuw nadat alles is voltooid. Dit is nodig omdat u wijzigingen hebt aangebracht door de verwijzingen naar oude analytische code te verwijderen en u wilt ervoor zorgen dat alles nog steeds correct werkt.

>[!NOTE]
>
>We helpen u graag succesvol te zijn bij uw migratie van Analytics naar Web SDK. Als u in obstakels met uw migratie loopt of als er kritieke informatie mist in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-adobe-analytics-to-web-sdk-using/m-p/732308#M604) {target="_blank"} te posten.

