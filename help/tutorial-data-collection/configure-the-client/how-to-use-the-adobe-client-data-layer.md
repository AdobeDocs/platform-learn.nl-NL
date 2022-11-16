---
title: Hoe te om de Laag van Gegevens van de Cliënt van Adobe te gebruiken
description: Hoe te om de Laag van Gegevens van de Cliënt van Adobe te gebruiken
exl-id: b5af9e72-aa6c-4cd7-80dd-b2de762a7523
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 0%

---

# Hoe te om de Laag van Gegevens van de Cliënt van Adobe te gebruiken

In [Wat is een gegevenslaag?](whats-a-data-layer.md)hebt u geleerd dat er twee onderdelen zijn waarmee u rekening moet houden wanneer u gegevenslagen bespreekt: de container en de inhoud. De [Gegevenslaag Adobe-client](https://github.com/adobe/adobe-client-data-layer) is de container. Het maakt niet uit hoe je [uw gegevens structureren](../structuring-your-data.md) of welke gegevens u wilt invoeren. De gegevens kunnen worden gestructureerd als [XDM](../structuring-your-data.md#xdm), zoals hieronder wordt getoond, of u kunt uw eigen structuur volledig bouwen.

Ideaal gezien, is het de ingenieursteam van uw bedrijf verantwoordelijk voor het duwen van om het even welke noodzakelijke gegevens in de gegevenslaag door on-page code. Het marketing team wint dan gegevens van de gegevenslaag terug, bij voorkeur gebruikend de eigenschap van Markeringen van Adobe Experience Platform, vroeger genoemd Lancering.

## Gegevens naar de gegevenslaag duwen

De gegevenslaag van de Cliënt van Adobe is een serie JavaScript. Wanneer u de Laag van Gegevens van de Cliënt van Adobe creeert, begint het leeg:

```js
window.adobeDataLayer = window.adobeDataLayer || [];
```

Om gegevens in de gegevenslaag te plaatsen, roep `push` methode op de array van gegevenslagen:

```js
window.adobeDataLayer.push({
  "claims": {
    "ID": "CL10991306",
    "policyID": "IXP28113",
    "type": "automobile"
  }
});
```

U kunt op elk gewenst moment aanvullende gegevens in de gegevenslaag duwen door `push` opnieuw.

```js
window.adobeDataLayer.push({
  "claims": {
    "status": "approved",
    "benefitAmount": {
      "amount": 1827.90,
      "currencyCode": "USD"
    }
  }
});
```

## Betekenis van geduwde gegevens

Als u de twee vorige `push` vraag, zou u omhoog met twee ingangen in de serie van de gegevenslaag eindigen. De gegevenslaag is niet nuttig in deze staat. Normaal, wilt u tot de samengevoegde staat van de gegevenslaag toegang hebben of, met andere woorden, één enkel voorwerp dat het gecombineerde resultaat van alle gegevens is u in de gegevenslaag hebt geduwd. In de zelfstudie leert u hoe u deze samengevoegde staat kunt openen. Vooralsnog is het voldoende om te begrijpen dat de berekende status van de gegevenslaag na onze twee lagen `push` de uitnodigingen luiden als volgt :

```json
{
  "claims": {
    "ID": "CL10991306",
    "policyID": "IXP28113",
    "type": "automobile",
    "status": "approved",
    "benefitAmount": {
      "amount": 1827.90,
      "currencyCode": "USD"
    }
  }
}
```

## Gegevens verwijderen

Soms moet u gegevens uit de gegevenslaag verwijderen. Dit komt vaak voor in toepassingen van één pagina wanneer de gebruiker van de ene weergave naar de volgende navigeert. Bijvoorbeeld, als de gebruiker van een productmening aan een contactmening navigeert, kan het steek zijn om het even welke productgegevens op de gegevenslaag te ontruimen aangezien het niet meer relevant voor de actieve mening is.

U kunt gegevens verwijderen door een waarde van `undefined` voor de sleutel die u wilt verwijderen. Voortbouwend op onze vorige voorbeelden, als u wilt verwijderen `status` vanaf de gegevenslaag ziet uw code er als volgt uit:

```js
window.adobeDataLayer.push({
  "claims": {
    "status": undefined
  }
});
```

De berekende status van de gegevenslaag wordt niet langer opgenomen `status`:

```json
{
  "claims": {
    "ID": "CL10991306",
    "policyID": "IXP28113",
    "type": "automobile",
    "benefitAmount": {
      "amount": 1827.90,
      "currencyCode": "USD"
    }
  }
}
```

## Gebeurtenissen naar de gegevenslaag verplaatsen

De gegevenslaag van de Cliënt van Adobe wordt niet alleen gebruikt voor het opslaan van gegevens, maar ook voor het meedelen van welke gebeurtenissen op de pagina voorkomen. In feite duw u typisch gegevens in de gegevenslaag _als gevolg_ van een gebeurtenis die op de pagina plaatsvindt. Deze gebeurtenissen zijn onder andere (1) interactiegebeurtenissen, zoals het openen van een chatsessie of het typen van een zoekterm in een zoekbalk of (2) niet-interactiegebeurtenissen, zoals de indruk van een advertentie of het voltooien van prestatieberekeningen op de webpagina.

Neem een `event` in het object dat u naar de gegevenslaag duwt. U kunt bijvoorbeeld opgeven dat een gebruiker een zoekquery in een zoekveld heeft ingevoerd.

```js
window.adobeDataLayer.push({
  "event": "searchQueryEntered"
});
```

<!--Later, you'll learn how to trigger rules within Adobe Experience Platform Tags when a particular event is pushed to the data layer.--> Also note that the `event` key is not included in the computed state. It receives special treatment by the data layer.


## Gebeurtenissen en gegevens naar de gegevenslaag verplaatsen

Het is handig om listeners te laten weten dat de gebruiker een zoekquery heeft ingevoerd, maar wat als u aanvullende informatie over de gebeurtenis wilt geven? Misschien wilt u bijvoorbeeld de zoekquery van de gebruiker opnemen. U kunt deze gegevens op twee manieren opgeven:

1. Gegevens opgeven zodat deze **wordt behouden** in de gegevenslaag als deel van de gegevens verwerkte staat van de laag.
1. Gegevens opgeven zodat deze **niet behouden** in de gegevenslaag als deel van de gegevens verwerkte staat van de laag.

Of u de gegevens in de gegevenslaag wilt behouden hangt gewoonlijk van af als u van plan bent om die gegevens door de duur van de gebruiker van verwijzingen te voorzien die op de pagina is. Als niet, dan het behouden van de gegevens binnen de gegevenslaag resulteert in een gegroepeerde gegevenslaag.

Hier is een voorbeeld van het duwen van een gebeurtenis met extra gegevens die **wordt behouden** in de gegevenslaag:

```js
window.adobeDataLayer.push({
  "event": "searchQueryEntered",
  "siteKnowledge": {
    "supportSiteSearch": {
      "term": "roller",
      "locationInPage": "topSearchBar"
    }
  }
});
```

Na deze `push` plaatsvindt, `siteKnowledge` wordt altijd weergegeven in de computerstatus van de gegevenslaag totdat de pagina wordt verwijderd (tenzij u deze handmatig verwijdert of overschrijft `siteKnowledge`).

Hier ziet u daarentegen een voorbeeld van het duwen van een gebeurtenis met aanvullende gegevens die **niet behouden** in de gegevenslaag:

```js
window.adobeDataLayer.push({
  "event": "searchQueryEntered",
  "eventInfo": {
    "siteKnowledge": {
      "supportSiteSearch": {
        "term": "roller",
        "locationInPage": "topSearchBar"
      }
    }
  }
});
```

In dit voorbeeld wordt opgemerkt dat `siteKnowledge` is ingepakt `eventInfo`. De `eventInfo` key ontvangt een speciale behandeling door de gegevenslaag. De gegevenslaag krijgt de melding dat deze gegevens _moet_ moet worden opgenomen in de gebeurtenis die naar listeners wordt verzonden, maar _mogen_ worden bewaard binnen de gegevenslaag. Nadat listeners (zoals een tagmanager) op de hoogte zijn gesteld van de gebeurtenis, worden deze gegevens genegeerd. De `siteKnowledge` key wordt nooit weergegeven in de berekende status van de gegevenslaag.

Elke keer dat u belt `push`, brengt de Laag van Gegevens van de Cliënt van Adobe op de hoogte om het even welke luisteraars. Later leert u hoe u naar deze meldingen kunt luisteren <!--from Adobe Experience Platform Tags--> en stelt dienovereenkomstig regels in werking.

[Volgende: ](implement-product-page-data-layer.md)

>[!NOTE]
>
>Dank u voor het investeren van uw tijd in het leren over de Inzameling van Gegevens. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)
