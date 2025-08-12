---
title: Een publiek maken
seo-title: Create an audience | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Een publiek maken
description: In deze les, vormen wij een verbinding tussen Adobe Experience Platform en uw onderneming Data Warehouse om Federated Audience Composition toe te laten.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-create-an-audience.jpg
hide: true
source-git-commit: a5ae2695763bc3d6dce786861dcbc15f3422c035
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---


# Audience Creation Exercition

Deze oefening leidt u door het creëren van een publiek van uw Data Warehouse gebruikend de Samenstelling van het Federale publiek. We bouwen een publiek om SecurFinancial-klanten te kwalificeren die een creditscore van 650 of hoger hebben en momenteel geen lening in hun SecurFinancial-portfolio hebben.

## Stappen

1. In de **Klant > Publiek** portaal, klik de **Federated samenstellingen** tabel.
2. Klik **creeer samenstelling**.

   ![ creeer-samenstelling ](assets/create-composition.png)

3. Label uw compositie als `SecurFinancial Customers - No Loans, Good Credit + [your lab user ID]`. Klik **creëren**.

4. Klik **+** knoop in het canvas en selecteer **het publiek van de Bouwstijl**. De rechterspoorlijn moet worden weergegeven.

5. Klik **Uitgezocht een schema** en selecteer het **FSI_CRM** schema, dan klik **bevestigen**.

6. Klik **verdergaan**. In het venster van de vraagbouwer, klik **+** knoop en dan **de Voorwaarde van de Douane**. Maak de volgende voorwaarden:
   - `CURRENTPRODUCTS does not contain loan`
   - `AND`
   - `CREDITSCORE greater than or equal to 650`
   - We gebruiken voorkeursgegevens voor marketing om klanten te segmenteren die voor e-mail hebben gekozen als hun voorkeurscommunicatiekanaal:
   - `AND`
   - `CONSENTSMARKETINGPREFERRED equal to email`

   **Nota:** het waardegebied is case-sensitive.

   Uw query moet er nu als volgt uitzien:

   ![ vraag-bouwer ](assets/query-builder.png)

7. Klik volgende **+** knoop, dan klik **sparen publiek**.

   Label deze stap als `SecurFinancial Customers - No Loans, Good Credit + [your lab user ID]`. Gebruik dezelfde waarde als het label voor het publiek.

8. Voeg de volgende publieksafbeeldingen toe:
   - **het Gebied van het publiek van Source:** EMAIL
   - **het Gebied van het publiek van Source:** CURRENTPRODUCTS
   - **het Gebied van het publiek van Source:** EERSTE NAAM

9. Selecteer de primaire identiteit en naamruimte die voor profielen moeten worden gebruikt:
   - **Primair identiteitsgebied:** E-mail
   - **Identiteitsnaamruimte:** E-mail

10. Klik **sparen** en klik dan **Begin** om de vraag van de samenstelling in werking te stellen u enkel bouwde.

**Nota:** wij gebruikten product en kredietinformatie om ons publiek te bouwen dat geen gevoelige gegevens, zoals creditscore, aan stroomafwaartse platforms voor activering verplaatste.

Voor meer informatie over publiekssamenstelling, bezoek [ Experience League ](https://experienceleague.adobe.com/en/docs/federated-audience-composition/using/compositions/create-composition/create-composition){target="_blank"}.

Nu ons gefedereerd publiek is gecreeerd, zullen wij met [ voorwaartse afbeelding het aan een S3 rekening ](map-federated-audience-to-s3.md) bewegen.
