---
title: Gegevens structureren
description: Gegevens structureren
exl-id: 8d176389-25a4-4718-afff-efd2f87204ed
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# Gegevens structureren

De ondernemingen hebben hun eigen taal voor het communiceren over hun domein. De autohandel handelt merk, modellen, en cilinders. Luchtvaartmaatschappijen hebben te maken met vluchtnummers, dienstencategorieën en zitplaatsen. Sommige van deze termen zijn uniek voor een bepaalde onderneming, sommige worden gedeeld door een verticale industrie, en sommige worden gedeeld door bijna alle ondernemingen. Voor termen die worden gedeeld tussen een verticale of zelfs bredere branche, kunt u krachtige dingen met uw gegevens beginnen te doen wanneer u deze termen op een gemeenschappelijke manier noemt en structureert.

Bijvoorbeeld, behandelen vele ondernemingen bevelen. Wat als deze bedrijven gezamenlijk besloten om een order op dezelfde manier te modelleren? Bijvoorbeeld, wat als het gegevensmodel uit een voorwerp met a bestond `priceTotal` eigendom die de totale prijs van de order vertegenwoordigde? Wat als dat object ook eigenschappen had met een naam `currencyCode` en `purchaseOrderNumber`? Misschien bevat het object order een eigenschap met de naam `payments` dat zou een array van betalingsobjecten zijn . Elk object zou een betaling voor de bestelling zijn. Een klant heeft bijvoorbeeld een deel van de bestelling betaald met een cadeaukaart en de rest betaald met een creditcard. U kunt beginnen een model te construeren dat er ongeveer als volgt uitziet:

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

Als alle bedrijven die met orders te maken hebben, besloten hebben om hun ordergegevens op consistente wijze te modelleren voor termen die in de sector algemeen zijn, kunnen er magische dingen beginnen te gebeuren. De informatie zou vlotter binnen en buiten uw organisatie kunnen worden uitgewisseld in plaats van constant het interpreteren en vertalen van de gegevens (pro&#39;s en evars, iedereen?). Het leren van machines kan eenvoudiger begrijpen wat uw gegevens zijn _middelen_ en activeerbare inzichten te bieden. Gebruikersinterfaces voor het opzoeken van relevante gegevens kunnen intuïtiever worden. Uw gegevens kunnen naadloos worden geïntegreerd met partners en leveranciers die dezelfde modellering volgen.

## XDM

Dit is het doel van Adobe [Experience Data Model](https://business.adobe.com/products/experience-platform/experience-data-model.html). XDM verstrekt voorschrijvende modellering voor gegevens die in de industrie gemeenschappelijk zijn, terwijl ook het toestaan van u om het model voor uw specifieke behoeften uit te breiden. Adobe Experience Platform is opgebouwd rond XDM en gegevens die naar Experience Platform worden verzonden, moeten daarom in XDM staan. In plaats van na te denken over waar en hoe u uw huidige gegevensmodellen in XDM kunt omzetten alvorens de gegevens naar Experience Platform te verzenden, overweeg doordringend het goedkeuren van XDM over uw organisatie zodat de vertaling zelden moet voorkomen.

[Volgende: ](configure-the-server/create-a-schema.md)

>[!NOTE]
>
>Dank u voor het investeren van uw tijd in het leren over de Inzameling van Gegevens. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud hebt, kunt u deze delen over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-use-adobe-experience-platform-data/m-p/543877)
