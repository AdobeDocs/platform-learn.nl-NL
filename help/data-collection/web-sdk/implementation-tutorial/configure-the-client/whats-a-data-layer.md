---
title: Wat is een gegevenslaag?
description: Wat is een gegevenslaag?
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
kt: 10447
hide: true
hidefromtoc: true
exl-id: 747f2e60-646e-4324-993c-88568415ea59
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---

# Wat is een gegevenslaag?

Wanneer het uitvoeren van marketing technologieën op uw plaats, is het waarschijnlijk u belangrijke stukken gegevens hebt die door uw UI worden verspreid. De naam van een product kan bijvoorbeeld in een kop op de pagina staan en de prijs kan lager zijn op de pagina onder de productafbeelding. Als u die gegevens naar Adobe of één of andere andere verkoper wilt verzenden, kunt u zeker de elementen vinden van de HTML die de gegevens bevatten door naar bepaalde HTML markeringen of attributen te zoeken, de gegevens van die elementen te trekken, en hen weg te verzenden. Maar wat gebeurt er als uw technische team besluit de productnaam van de koptekst naar een zijbalk te verplaatsen? Uw implementatie wordt onderbroken. Uw implementatie kan de kop niet meer vinden of, erger nog, de kop opzoeken en irrelevante gegevens naar de server verzenden.

Één belangrijk doel van een gegevenslaag is dit probleem op te lossen. In zijn eenvoudigste, is een gegevenslaag een voorwerp JavaScript (of, zoals wij later, een serie zullen zien) dat gegevens over het product op de pagina of om het even welke andere relevante gegevens bevat uw marketing technologieën baseren zich om uw doelstellingen te ontmoeten. Door niet op de elementen van de gebruikersinterface te vertrouwen om deze gegevens te verstrekken, wordt onze implementatie robuuster. De gegevenslaag bevat de gegevens en moet als een contract worden beschouwd. Dit contract is typisch tussen het technische team, dat gegevens in de gegevenslaag plaatst, en het marketing team, dat gegevens van de gegevenslaag terugwint.

Als een ingenieur op het punt staat de structuur van de gegevenslaag te veranderen, zijn zij veel waarschijnlijker om het werken met het marketing team te overwegen zodat de aangewezen veranderingen in de marketing implementatie kunnen worden aangebracht. Deze mededeling en samenwerking _moet_ in uw organisatie worden ingesteld om een robuuste implementatie te garanderen.

## Container vs. inhoud

In de industrie, wordt de term &quot;gegevenslaag&quot;geworpen rond een beetje losjes en kan vaak tot verwarring en wanmededeling leiden. Kijk eens naar een doos marbles. Er zijn twee onderdelen: de container (de doos) en de inhoud (de marbles). Op dezelfde manier wordt een gegevenslaag vaak beschouwd als twee delen: de container (het JavaScript-object of -array) en de inhoud (de gegevens zoals `priceTotal`, `currencyCode`, en `purchaseOrderNumber` ).

Aangezien dit leerprogramma naar de Laag van Gegevens van de Cliënt van Adobe verwijst, verwijst het naar de container en niet de inhoud. Wanneer het naar XDM verwijst, verwijst het naar de inhoud en niet naar de container. In het geval van de Laag van Gegevens van de Cliënt van Adobe, maakt het niet uit als de inhoud XDM of uw eigen gegevensmodel is. De gegevenslaag van de Cliënt van Adobe geeft niet om. Het is gewoon een doos. Maar het _is_ een doos met speciale bevoegdheden...

## Wijzigingen communiceren

Wanneer u een gegevenslaag gebruikt, kunt u de inhoud op elk gewenst moment wijzigen. Dat is een handige functie, omdat gegevens op verschillende momenten beschikbaar kunnen worden. U kunt bijvoorbeeld gegevens over de gebruiker direct beschikbaar hebben, maar u moet mogelijk een asynchrone aanvraag indienen bij een derde voor aanvullende informatie. Dit vereist speciale aandacht. Als u deze asynchrone gegevens naar Adobe Experience Platform op een gegeven moment moet verzenden, hoe weet uw marketing technologieën wanneer bepaalde gegevens aan de gegevenslaag zijn toegevoegd en klaar zijn om te worden verzonden? U hebt een slimmere gegevenslaag nodig, een gebeurtenisgestuurde gegevenslaag.

Een gebeurtenis-gedreven gegevenslaag kan meedelen dat zijn inhoud is veranderd zodat de marketing technologieën op de verandering kunnen reageren. Op de juiste manier gebruikt, kunt u timingproblemen voorkomen die zich vaak voordoen bij gegevenslagen die geen communicatiemiddel hebben wanneer er wijzigingen optreden.

De gegevenslaag van de Gegevens van de Cliënt van Adobe is een gebeurtenis-gedreven gegevenslaag.
