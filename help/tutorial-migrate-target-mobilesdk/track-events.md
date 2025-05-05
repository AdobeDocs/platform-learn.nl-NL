---
title: Conversiegebeurtenissen volgen - De Adobe Target-implementatie in uw mobiele app migreren naar de Adobe Journey Optimizer - De beslissingsextensie bepalen
description: Leer hoe u Adobe Target-conversiegebeurtenissen kunt bijhouden met de Adobe Journey Optimizer - Mobiele extensie bepalen
exl-id: 7b53aab1-0922-4d9f-8bf0-f5cf98ac04c4
source-git-commit: d2da62ed2d36f73af1c8053be5af27feea32cb14
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# De omzettingsgebeurtenissen van het Doel van het spoor gebruikend de mobiele uitbreiding van het Beslissen

Het doel van de meeste doelactiviteiten is het aansturen van waardevolle gebruikersacties in uw toepassing, zoals aankopen, registratie, klikken en meer. De implementaties van het doel gebruiken over het algemeen de gebeurtenissen van de douaneomzetting om deze acties te volgen, die vaak extra details over de omzetting bevatten. Conversiegebeurtenissen voor Target kunnen worden bijgehouden met Optimize SDK, vergelijkbaar met Target SDK. Specifieke API&#39;s moeten worden aangeroepen om conversiegebeurtenissen bij te houden, zoals in de onderstaande tabel wordt getoond:

| Activiteitsdoelstelling | Doelextensie | Extensie voor beslissing |
|---|---|---|
| Een weergaveconversiegebeurtenis voor een mbox-locatie bijhouden (bereik) | Vraag [ displayedLocations ](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank}  API wanneer de mbox plaats wordt bekeken | Vraag [ getoonde ](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank}  API wanneer de Aanbieding voor de mbox plaats wordt bekeken. Dit verzendt een gebeurtenis met gebeurtenistype decisions.propositionDisplay naar het netwerk van de Ervaring Edge. **dit is essentieel om bezoekers in uw activiteiten van het Doel te verhogen en moet worden gedaan wanneer het leveren van zowel regelmatige als standaardaanbiedingen van het Doel.** |
| Houd een klikomzettingsgebeurtenis voor een mbox plaats (werkingsgebied) bij | Roep [ clickedLocations ](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank}  API binnen wanneer de mbox plaats wordt geklikt | Roep [ in kaart gebrachte ](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-direct-offer-class-methods){target=_blank}  API wanneer de Aanbieding voor de mbox plaats wordt geklikt. Dit verzendt een gebeurtenis met gebeurtenistype decisions.propositionInteract naar het netwerk van de Ervaring Edge. |
| Een aangepaste conversiegebeurtenis bijhouden die mogelijk ook aanvullende gegevens bevat, zoals parameters voor het doelprofiel en orderdetails | Geef de extra gegevens op het gebied TargetParameters door [ wordt verstrekt displayedLocations ](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank}  en [ clickedLocations ](https://developer.adobe.com/client-sdks/solution/adobe-target/api-reference/#displayedlocations){target=_blank}  APIs die | Gebruik de openbare methodes [ generateDisplayInteractionXdm ](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-edge-extension-api){target=_blank}  en [ generateTapInteractionXdm ](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/#proposition-tracking-using-edge-extension-api){target=_blank}  APIs beschikbaar in de Aanbieding voor de mboxplaats om de XDM geformatteerde gegevens voor mening te produceren en te klikken respectievelijk. Dan vraag Edge SDK [ sendEvent ](https://developer.adobe.com/client-sdks/edge/edge-network/api-reference/#sendevent){target=_blank}  API om dit het volgen XDM gegevens samen met om het even welke extra XDM en vrije vormgegevens naar het netwerk van de Ervaring Edge te verzenden. |


Daarna, leer hoe te om [ publiek en profielmanuscripten ](update-audiences.md) bij te werken om verenigbaarheid met de Decisioning uitbreiding te verzekeren.

>[!NOTE]
>
>Wij zijn geëngageerd om u te helpen met uw mobiele migratie van het Doel van de uitbreiding van het Doel aan de uitbreiding van het Beslissen succesvol te zijn. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.
