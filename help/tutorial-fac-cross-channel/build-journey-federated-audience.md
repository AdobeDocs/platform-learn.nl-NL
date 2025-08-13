---
title: Een reis maken met gegevens over gefederaliseerde doelgroepen
seo-title: Build a journey with federated audience data | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Een reis maken met gegevens over gefederaliseerde doelgroepen
description: In deze visuele oefening wordt een gefedereerd publiek gebruikt in een Journey Optimizer-reis.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-build-a-journey-with-federated-audience-data.jpg
hide: true
exl-id: a153667a-9b3a-4db7-9f58-b83e695009e0
source-git-commit: a3c8d8b03472d01f491bf787ed647a696d3a5524
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# Bouw een Reis met de Federatieve Gegevens van het Publiek

Federaal publiek kan worden gebruikt voor reizen binnen Adobe Journey Optimizer (AJO). Dit omvat het gebruiken van vragen attributen van de Federatieve Samenstelling van het Publiek om overseinen te personaliseren.

Om verder te gaan met het verhaal SecurFinancial, met name de klant die en de kwestie van het verpersoonlijkingsgebruik opnieuw richt, organiseren wij een reis voor pre-gekwalificeerde klanten. Het doel is om een gepersonaliseerde e-mail te verzenden die op attributen wordt gebaseerd die van de Data Warehouse van SecurFinancial worden gefedereerd.

## Stappen

### Een reis maken met een leespubliek

1. Navigeer aan het **portaal van de Reizen** en klik **creeer de 3} knoop van de Reis {.**

   ![ creeer-a-reis ](assets/create-journey.png)

2. Werk de eigenschappen van de Reis met een nieuwe naam bij. In ons voorbeeld: **`SecurFinancial - Home Loan Offer`** .

3. Klik op **Orchestration**, dan belemmering en laat vallen de **Gelezen publiek** tegel aan het canvas.

4. Klik op het **potloodpictogram** naast de doos van het Publiek op de rechterkant van het scherm.

5. Zoek in de zoekbalk naar het publiek. In ons voorbeeld: **`SecureFinancial Customers - No Loans, Good Credit`**. Klik **sparen**.

   ![ creeer-a-reis ](assets/select-audience.png)

6. Verlaat alle montages als gebrek in het juiste zijmenu en klik dan **sparen**.

   ![ sparen-publiek-montages ](assets/save-audience-settings.png)

### E-mail personaliseren

1. Klik op **Acties**, dan klik en sleep de **E-mail** tegel aan het canvas.

2. Op het rechterzijmenu, klik op **E-mailconfiguratie** en selecteer **EmailMarketing**. Dan klik op **geef inhoud** uit.

3. Voeg een onderwerpregel toe. In ons voorbeeld: **`Learn more about SecurFinancial Home Loan`**. Dan klik op **uitgeeft e-maillichaam**.

4. Klik het **malplaatje van de Inhoud** knoop in de hoogste juiste hoek. Zoek en selecteer de gewenste sjabloon. In ons voorbeeld wordt `SecureFinancial Template` gebruikt. Dan klik **bevestigen**.

   ![ reis-e-mail-config ](assets/journey-email-config.png)

   ![ reis-e-mail-bevestig ](assets/journey-email-confirm.png)

5. Herzie het malplaatje en klik **Malplaatje van het Gebruik**.

6. Je bent nu in de e-mail-Designer. Beweeg over de `{profile.person.name.firstName}` macro en klik **verpersoonlijkingsavatar**.

7. Blader in het verpersoonlijkingsvenster omlaag naar het mappad met het geüploade gefederaliseerde publiek. In ons voorbeeld: **`[sandbox] > audienceEnrichment > CustomerAudienceUpload`**

8. Klik in de **gelezen publiek** omslag. De verrijkingskenmerken van uw gefedereerde publiek kunt u hier vinden.

9. Selecteer het **Eerste** attribuut van de Naam aan de uitdrukkingsbouwer. In de e-mail wordt dynamisch de waarde van de voornaam van de klant uitgedrukt om het e-mailadres aan te passen.

10. Klik **sparen**.

11. Nu de voornaampersonalisatie is toegevoegd, voegt u `Hi, ` toe vóór de personalisatievariabele. Dan klik **sparen**.

   ![ reis-e-mail-sparen ](assets/journey-email-save.png)

12. Klik op de **Achtergrond** knoop tweemaal om aan het wegcanvas terug te keren. Dan in de **Actie: E-mail** menu aan het recht, klik **sparen**.

   ![ sparen-definitief-reis ](assets/save-final-journey.png)

We creëerden een reis in AJO met behulp van een gefederaliseerd publiek en gefederaliseerde verrijkingskenmerken.

Nu zullen wij bekijken hoe te [ bestaande publiek ](federated-audience-composition.md) in Experience Platform met gefederaliseerde gegevens van het gegevenspakhuis verrijken.
