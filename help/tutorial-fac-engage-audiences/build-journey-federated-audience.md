---
title: Een reis maken met een federaal publiek
seo-title: Build a journey with a Federated Audience | Engage with audiences directly from your data warehouse using Federated Audience Composition
breadcrumb-title: Een reis maken met een federaal publiek
description: In deze oefening wordt een gefedereerd publiek gebruikt in een Journey Optimizer reis.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-build-a-journey-with-federated-audience-data.jpg
exl-id: a153667a-9b3a-4db7-9f58-b83e695009e0
source-git-commit: 7e2f7bbb392eba51c0d6b9ccc8224c2081a01c7c
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# Een reis maken met een federaal publiek

Federaal publiek kan worden gebruikt voor reizen binnen Adobe Journey Optimizer (AJO). Dit omvat het gebruiken van vragen attributen van de Federatieve Samenstelling van het Publiek om overseinen te personaliseren.

Om verder te gaan met het verhaal SecurFinancial, met name de klant die en de kwestie van het verpersoonlijkingsgebruik opnieuw richt, organiseren wij een reis voor pre-gekwalificeerde klanten. Het doel is een gepersonaliseerde e-mail te verzenden die op attributen wordt gebaseerd van het gegevenspakhuis van SecurFinancial worden gefedereerd.

## Stappen

### Een reis maken met een leespubliek

1. Navigeer aan het **portaal van de Reizen** en klik **creeer de 3&rbrace; knoop van de Reis &lbrace;.**

   ![&#x200B; creeer-a-reis &#x200B;](assets/create-journey.png)

2. Werk de eigenschappen van de Reis met een nieuwe naam bij. In ons voorbeeld: **`SecurFinancial - Home Loan Offer`** .

3. Klik op **Orchestration**, dan belemmering en laat vallen de **Gelezen publiek** tegel aan het canvas.

4. Klik op het **potloodpictogram** naast de doos van het Publiek op de rechterkant van het scherm.

5. Zoek in de zoekbalk naar het publiek. In ons voorbeeld: **`SecureFinancial Customers - No Loans, Good Credit`**. Klik **sparen**.

   ![&#x200B; creeer-a-reis &#x200B;](assets/select-audience.png)

6. Verlaat alle montages als gebrek in het juiste zijmenu en klik dan **sparen**.

   ![&#x200B; sparen-publiek-montages &#x200B;](assets/save-audience-settings.png)

### E-mail personaliseren

1. Klik op **Acties**, dan klik en sleep de **E-mail** tegel aan het canvas.

2. Op het rechterzijmenu, klik op **E-mailconfiguratie** en selecteer **EmailMarketing**. Dan klik op **geef inhoud** uit.

3. Voeg een onderwerpregel toe. In ons voorbeeld: **`Learn more about SecurFinancial Home Loan`**. Dan klik op **uitgeeft e-maillichaam**.

4. Klik het **malplaatje van de Inhoud** knoop in de hoogste juiste hoek. Zoek en selecteer de gewenste sjabloon. In ons voorbeeld wordt `SecureFinancial Template` gebruikt. Dan klik **bevestigen**.

   ![&#x200B; reis-e-mail-config &#x200B;](assets/journey-email-config.png)

   ![&#x200B; reis-e-mail-bevestig &#x200B;](assets/journey-email-confirm.png)

5. Herzie het malplaatje en klik **Malplaatje van het Gebruik**.

6. Je bent nu in de e-mail-Designer. Beweeg over de `{profile.person.name.firstName}` macro en klik **verpersoonlijkingsavatar**.

7. Blader in het verpersoonlijkingsvenster omlaag naar het mappad met het geüploade gefederaliseerde publiek. In ons voorbeeld: **`[sandbox] > audienceEnrichment > CustomerAudienceUpload`**

8. Klik in de **gelezen publiek** omslag. De verrijkingskenmerken van uw gefedereerde publiek kunt u hier vinden.

9. Selecteer het **Eerste** attribuut van de Naam aan de uitdrukkingsbouwer. In de e-mail wordt dynamisch de waarde van de voornaam van de klant uitgedrukt om het e-mailadres aan te passen.

10. Klik **sparen**.

11. Nu de voornaampersonalisatie is toegevoegd, voegt u `Hi, ` toe vóór de personalisatievariabele. Dan klik **sparen**.

    ![&#x200B; reis-e-mail-sparen &#x200B;](assets/journey-email-save.png)

12. Klik op de **Achtergrond** knoop tweemaal om aan het wegcanvas terug te keren. Dan in de **Actie: E-mail** menu aan het recht, klik **sparen**.

   ![&#x200B; sparen-definitief-reis &#x200B;](assets/save-final-journey.png)

We creëerden een reis in AJO met behulp van een gefederaliseerd publiek en gefederaliseerde verrijkingskenmerken.

Nu zullen wij bekijken hoe te [&#x200B; een publiek &#x200B;](federated-audience-composition.md) in Experience Platform met gegevens van het gegevenspakhuis verrijken.
