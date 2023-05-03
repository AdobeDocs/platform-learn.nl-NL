---
title: Experience Platform-API's verifiëren en openen
description: Leer hoe u toegang krijgt tot Adobe Experience Platform-API's.
role: Developer
feature: API
kt: 3688
thumbnail: 28832.jpeg
exl-id: c1774670-436e-46dd-9c9b-177bfee5f749
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 9%

---

# Verifiëren en toegang [!DNL Experience Platform] API&#39;s

Als u Adobe Experience Platform API&#39;s wilt aanroepen, moet u eerst toegang krijgen tot een Experience Platform developer-account.

Voor stapsgewijze instructies waarin wordt uitgelegd hoe u toegang kunt krijgen tot een ontwikkelaarsaccount, gaat u naar de [Zelfstudie over Experience Platform API-verificatie](https://www.adobe.com/go/platform-api-authentication-en).

## Experience Platform-API maken en exporteren naar Postman

[Postman](https://www.getpostman.com/) is een hulpmiddel waarmee ontwikkelaars snel en gemakkelijk kunnen communiceren met Adobe Experience Platform API&#39;s.

Adobe Developer Console **Exportdetails voor Postman** biedt een eenvoudige manier om alle accountgegevens te exporteren die nodig zijn voor toegang tot en interactie met een Experience Platform-API in één Postman-milieubestand. Hierdoor hoeft u geen waarden meer te kopiëren en te plakken van Adobe Developer Console naar Postman.

>[!VIDEO](https://video.tv.adobe.com/v/28832/?quality=12&learn=on)

## Een toegangstoken genereren met Postman

Gebruik de [Adobe Identity Management Service-API&#39;s](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims?lang=nl) een toegangstoken verkrijgen voor toegang tot de Adobe Experience Platform API&#39;s voor niet-productiegebruik

>[!VIDEO](https://video.tv.adobe.com/v/29698/?quality=12&learn=on)

>[!WARNING]
>
> Zoals vermeld in de inzameling van Postman van de Generatie van de Token van de Toegang van de Adobe I/O, zijn de gesignaleerde generatiemethodes geschikt voor niet-productiegebruik. Bij Lokaal ondertekenen wordt een JavaScript-bibliotheek geladen van een host van een andere fabrikant en bij Extern ondertekenen wordt de persoonlijke sleutel naar een webservice verzonden die eigendom is van een Adobe. Hoewel Adobe deze persoonlijke sleutel niet opslaat, mogen productietoetsen nooit met iemand worden gedeeld.

## Interactie met Adobe I/O API&#39;s met Postman

Interactie met Adobe I/O API&#39;s ontdekken via de [Adobe-API voor Experience Platform Postman-verzamelingen](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform), voortbouwend op de [Adobe I/O Omgevingsvariabelen](#export-adobe-io-integration-details-to-postman) en [gegenereerd toegangstoken](#generate-an-access-token-with-postman).

>[!VIDEO](https://video.tv.adobe.com/v/29704/?quality=12&learn=on)

Houd er rekening mee dat door Adobe verschafte Postman-verzamelingen mogelijk niet bestaan voor elke Adobe I/O-API, maar de beschikbare [Experience Platform API Postman-verzamelingen](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform) U kunt dit gebruiken als richtlijn voor het definiëren van uw eigen Postman-verzamelingen voor deze use-cases.

## Aanvullende bronnen

* [Adobe I/O-console](https://console.adobe.io)
* [Adobe Experience Platform Postman-voorbeelden](https://github.com/adobe/experience-platform-postman-samples)
   * [Adobe I/O Access Token Generation Postman Collection](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims?lang=nl)
   * [Adobe Experience Platform API&#39;s Postman Collections](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform)
* [Postman downloaden](https://www.getpostman.com/)
