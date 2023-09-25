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
source-git-commit: 00ef0f40fb3d82f0c06428a35c0e402f46ab6774
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 11%

---

# Verifiëren en toegang [!DNL Experience Platform] API&#39;s

Leer hoe u aan de slag gaat met Adobe Experience Platform API&#39;s. Deze zelfstudie begeleidt u door het proces om verificatiereferenties te maken en Experience Platform API-aanvragen te maken.

## Een project maken in Adobe Developer Console en een Postman-omgeving exporteren{#export-integration-details-to-postman}

[[!DNL Postman]](https://www.postman.com/) is een externe toepassing waarmee ontwikkelaars snel en gemakkelijk kunnen communiceren met Adobe Experience Platform API&#39;s.

[Adobe Developer Console](https://developer.adobe.com/console/home) **Exportdetails voor Postman** biedt een eenvoudige manier om de accountgegevens te exporteren die nodig zijn voor toegang tot en interactie met een Experience Platform-API&#39;s in één Postman-milieubestand. Hierdoor hoeven waarden niet meer van Adobe Developer Console naar Postman te worden gekopieerd en geplakt.

>[!IMPORTANT]
>
>Als u toegang wilt krijgen tot [Adobe Developer Console](https://developer.adobe.com/console/home)u moet een van de [Systeembeheerder](https://helpx.adobe.com/enterprise/using/admin-roles.html) of [Ontwikkelaar](https://helpx.adobe.com/enterprise/using/manage-developers.html#:~:text=Add%20developers%20to%20a%20single%20product%20profile&amp;text=In%20the%20Admin%20Console%2C%20navigate,in%20the%20upper%2Dright%20corner.) in de [Adobe Admin Console](https://adminconsole.adobe.com).
>
> Nadat u de API-referentie hebt gemaakt, moet een systeembeheerder de referentie aan een rol in het Experience Platform koppelen.

>[!VIDEO](https://video.tv.adobe.com/v/28832/?learn=on)

## Een toegangstoken genereren met Postman{#generate-an-access-token-with-postman}

Gebruik de [Adobe Identity Management Service-API&#39;s](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims?lang=nl) om een toegangstoken te verkrijgen voor toegang tot de Adobe Experience Platform API&#39;s.

>[!VIDEO](https://video.tv.adobe.com/v/29698/?learn=on)


## Interactie met Experience Platform-API&#39;s met Postman

Ontdek de interactie met Adobe Experience Platform API&#39;s met de [Door Adobe verschafte Experience Platform API Postman-verzamelingen](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform), voortbouwend op de [Adobe Developer Console-omgevingsvariabelen](#export-integration-details-to-postman) en [gegenereerd toegangstoken](#generate-an-access-token-with-postman).

>[!VIDEO](https://video.tv.adobe.com/v/29704/?learn=on)


## Bronnen waarnaar in deze video&#39;s wordt verwezen

* [Adobe Developer Console](https://developer.adobe.com/console/home)
* [Adobe Experience Platform Postman-voorbeelden](https://github.com/adobe/experience-platform-postman-samples)
   * [Identity Management System Postman Collection voor het genereren van toegangstokens](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/ims?lang=nl)
   * [Adobe Experience Platform API Postman-verzamelingen](https://github.com/adobe/experience-platform-postman-samples/tree/master/apis/experience-platform)
* [Postman downloaden](https://www.postman.com/)
