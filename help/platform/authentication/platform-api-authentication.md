---
title: Experience Platform-API's verifiëren en openen
description: Leer hoe u toegang krijgt tot Adobe Experience Platform-API's.
role: Developer
feature: API
kt: 3688
thumbnail: 28832.jpeg
last-substantial-update: 2023-06-21T00:00:00Z
exl-id: c1774670-436e-46dd-9c9b-177bfee5f749
source-git-commit: 60f509ef55ce121f572466a8f13953dba982a0ce
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 15%

---

# Verifiëren en toegang [!DNL Experience Platform] API&#39;s

Als u aanvragen wilt indienen bij Adobe Experience Platform API&#39;s, hebt u een Experience Platform-ontwikkelaarsaccount nodig.

## Een project maken in Adobe Developer Console en een Postman-omgeving exporteren

[[!DNL Postman]](https://www.postman.com/) is een hulpmiddel waarmee ontwikkelaars snel en gemakkelijk kunnen communiceren met Adobe Experience Platform API&#39;s.

Adobe Developer Console **Exportdetails voor Postman** biedt een eenvoudige manier om alle accountgegevens te exporteren die nodig zijn voor toegang tot en interactie met een Experience Platform-API in één Postman-milieubestand. Hierdoor hoeft u geen waarden meer te kopiëren en te plakken van Adobe Developer Console naar Postman.

>[!VIDEO](https://video.tv.adobe.com/v/28832/?quality=12&learn=on)

>[!IMPORTANT]
>
>Na het creëren van uw API referentie, moet een Beheerder van het Systeem bij uw bedrijf de referentie met een rol van het Experience Platform associëren.


## Een toegangstoken genereren met Postman

Gebruik de [Adobe Identity Management Service-API&#39;s](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims?lang=nl) om een toegangstoken te verkrijgen voor toegang tot de Adobe Experience Platform API&#39;s.

>[!VIDEO](https://video.tv.adobe.com/v/29698/?quality=12&learn=on)


## Interactie met Experience Platform-API&#39;s met Postman

Ontdek de interactie met Adobe Experience Platform API&#39;s met de [Adobe-API voor Experience Platform Postman-verzamelingen](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform), voortbouwend op de [Adobe Developer Console-omgevingsvariabelen](#export-adobe-io-integration-details-to-postman) en [gegenereerd toegangstoken](#generate-an-access-token-with-postman).

>[!VIDEO](https://video.tv.adobe.com/v/29704/?quality=12&learn=on)


## Aanvullende bronnen

* [Adobe Developer Console](https://developer.adobe.com/console/home)
* [Adobe Experience Platform Postman-voorbeelden](https://github.com/adobe/experience-platform-postman-samples)
   * [Identity Management System Postman Collection voor het genereren van toegangstokens](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims?lang=nl)
   * [Adobe Experience Platform API Postman-verzamelingen](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform)
* [Postman downloaden](https://www.postman.com/)
