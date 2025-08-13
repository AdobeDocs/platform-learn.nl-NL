---
title: Een publiek maken
seo-title: Create an audience | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Een publiek maken
description: In deze visuele oefening, vormen wij een verbinding tussen Adobe Experience Platform en uw onderneming Data Warehouse om Federated Audience Composition toe te laten.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-create-an-audience.jpg
hide: true
exl-id: a507cab5-dba9-4bf7-a043-d7c967e9e07d
source-git-commit: a3c8d8b03472d01f491bf787ed647a696d3a5524
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Audience Creation Exercition

Vervolgens begeleiden we u door een publiek te maken vanuit onze Data Warehouse met Federated Audience Composition. Het publiek bestaat uit SecurFinancial-klanten met een kredietscore van 650 of hoger en die momenteel geen lening in hun SecurFinancial-portefeuille hebben.

## Stappen

1. In de **Klant > Publiek** portaal, klik de **Federated samenstellingen** tabel.
2. Klik **creeer samenstelling**.

   ![ creeer-samenstelling ](assets/create-composition.png)

3. Label uw compositie. In ons voorbeeld: `SecurFinancial Customers - No Loans, Good Credit`. Klik **creëren**.

4. Klik **+** knoop in het canvas en selecteer **het publiek van de Bouwstijl**. Het rechterspoor verschijnt.

5. Klik **Uitgezocht een schema**, selecteer het aangewezen schema, dan klik **bevestigen**.

6. Klik **verdergaan**. In het venster van de vraagbouwer, klik **+** knoop en dan **de Voorwaarde van de Douane**. Schrijf de voorwaarden. In ons voorbeeld wordt het volgende gebruikt:

   `CURRENTPRODUCTS does not contain loan`
   `AND`
   `CREDITSCORE greater than or equal to 650`
   `AND`
   `CONSENTSMARKETINGPREFERRED equal to email`

   *de laatste voorwaarde verzekert marketing voorkeursgegevens worden gebruikt om klanten te segmenteren die voor e-mail als hun aangewezen kanaal van mededeling* hebben gekozen.

   **Nota:** het waardegebied is case-sensitive.

   ![ vraag-bouwer ](assets/query-builder.png)

7. Klik volgende **+** knoop, dan klik **sparen publiek**. Label deze stap. In ons voorbeeld geven we het label `SecurFinancial Customers - No Loans, Good Credit` .

8. Voeg de relevante publiekstoewijzingen toe. In dit voorbeeld:

   - **het Gebied van het publiek van Source:** EMAIL
   - **het Gebied van het publiek van Source:** CURRENTPRODUCTS
   - **het Gebied van het publiek van Source:** EERSTE NAAM

9. Selecteer de primaire identiteit en naamruimte die voor profielen moeten worden gebruikt. Dit zijn de identiteiten en de gebieden die voor onze gegevens worden gebruikt:

   - **Primair identiteitsgebied:** E-mail
   - **Identiteitsnaamruimte:** E-mail

10. Klik **sparen** en klik dan **Begin** om de vraag van de samenstelling in werking te stellen.

>[**SAMENVATTING**]
>
> In dit voorbeeld werd product- en kredietinformatie gebruikt om ons publiek te maken via directe toegang tot bedrijfsgegevens van Snowflake, zonder een kopie ervan te maken Adobe Experience Platform. Nadat het externe systeem de query heeft verwerkt, worden alleen de relevante e-mail, huidige producten en voornaamwaarden naar de publieksdefinitie overgebracht voor downstreamactivering. Dit geldt voor alle bestemmingen die RTCDP ondersteunt.

Voor meer informatie over publiekssamenstelling, bezoek [ Experience League ](https://experienceleague.adobe.com/en/docs/federated-audience-composition/using/compositions/create-composition/create-composition){target="_blank"}.

Nu ons gefedereerde publiek is gecreeerd, zullen wij [ het aan een S3 rekening ](map-federated-audience-to-s3.md) in kaart brengen.
