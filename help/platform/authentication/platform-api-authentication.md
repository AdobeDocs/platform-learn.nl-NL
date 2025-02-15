---
title: Experience Platform-API's verifiëren en openen
description: Leer hoe u toegang krijgt tot Adobe Experience Platform-API's.
feature: API
role: Developer
level: Beginner
jira: KT-3688
thumbnail: 28832.jpeg
last-substantial-update: 2023-06-21T00:00:00Z
exl-id: c1774670-436e-46dd-9c9b-177bfee5f749
source-git-commit: 286c85aa88d44574f00ded67f0de8e0c945a153e
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 8%

---

# [!DNL Experience Platform] API&#39;s verifiëren en openen

Leer hoe u aan de slag gaat met Adobe Experience Platform API&#39;s. Deze zelfstudie begeleidt u door het proces om verificatiereferenties te maken en Experience Platform API-aanvragen in te dienen.

## Een project maken in Adobe Developer Console en een Postman-omgeving exporteren{#export-integration-details-to-postman}

[[!DNL Postman] ](https://www.postman.com/) is een derdetoepassing die ontwikkelaars snel en gemakkelijk met Adobe Experience Platform APIs helpt in wisselwerking te staan.

[ Adobe Developer Console ](https://developer.adobe.com/console/home) **de Details van de Uitvoer voor Postman** vermogen verstrekt een gemakkelijke manier om de rekeningsdetails uit te voeren die worden vereist om tot en met Experience Platform APIs in één enkel dossier van het Milieu van Postman toegang te hebben, verwijderend de behoefte om waarden van Adobe Developer Console in Postman te kopiëren en te kleven.

>[!IMPORTANT]
>
>Om tot [ Adobe Developer Console ](https://developer.adobe.com/console/home) toegang te hebben, moet u a of a [ Beheerder van het Systeem ](https://helpx.adobe.com/enterprise/using/admin-roles.html) of a [ Ontwikkelaar ](https://helpx.adobe.com/enterprise/using/manage-developers.html#:~:text=Add%20developers%20to%20a%20single%20product%20profile&amp;text=In%20the%20Admin%20Console%2C%20navigate,in%20the%20upper%2Dright%20corner.) in [ Adobe Admin Console ](https://adminconsole.adobe.com) zijn.
>
> Nadat u de API-referentie hebt gemaakt, moet een systeembeheerder de referentie koppelen aan een rol in de Experience Platform.

>[!VIDEO](https://video.tv.adobe.com/v/28832/?learn=on&enablevpops)

## Een toegangstoken genereren met Postman{#generate-an-access-token-with-postman}

Gebruik [ de Dienst APIs van Identity Management van Adobe ](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims?lang=nl) om een Token van de Toegang te verkrijgen om tot Adobe Experience Platform APIs toegang te hebben.

>[!VIDEO](https://video.tv.adobe.com/v/29698/?learn=on&enablevpops)


## Interactie met Experience Platform API&#39;s met Postman

Onderzoek het in wisselwerking staan met Adobe Experience Platform APIs die [ Adobe-Geleverde Experience Platform API Postman inzamelingen ](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform) gebruiken, voortbouwend op de [ Variabelen van het Milieu van Adobe Developer Console ](#export-integration-details-to-postman) en [ geproduceerd toegangstoken ](#generate-an-access-token-with-postman).

>[!VIDEO](https://video.tv.adobe.com/v/29704/?learn=on&enablevpops)


## Bronnen waarnaar in deze video&#39;s wordt verwezen

* [Adobe Developer Console](https://developer.adobe.com/console/home)
* [ de Steekproeven van Postman van Adobe Experience Platform ](https://github.com/adobe/experience-platform-postman-samples)
   * [ de Inzameling van Postman van het Systeem van Identity Management voor het produceren van toegangstokens ](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims?lang=nl)
   * [ Adobe Experience Platform API Postman Collections ](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform)
* [ Download Postman ](https://www.postman.com/)
