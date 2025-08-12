---
title: Een reis maken met gegevens over gefederaliseerde doelgroepen
seo-title: Build a journey with federated audience data | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Een reis maken met gegevens over gefederaliseerde doelgroepen
description: In deze les gebruiken we een gefedereerd publiek in een Journey Optimizer-reis.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-build-a-journey-with-federated-audience-data.jpg
hide: true
source-git-commit: fcfadca95c12d0123cfb221e44909f7e0fa8abab
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---


# Bouw een Reis met de Federatieve Gegevens van het Publiek

In deze les leert u hoe u een gefedereerd publiek kunt gebruiken tijdens reizen binnen Adobe Journey Optimizer (AJO). Dit omvat het gebruiken van vragen attributen van de Federatieve Samenstelling van het Publiek om overseinen te personaliseren. Om met het verhaal van de klant SecurFinancial verder te gaan en de klant te richten en de kwestie van het verpersoonlijkingsgebruik te richten, organiseren wij een reis voor pregekwalificeerde klanten. Het doel is om een gepersonaliseerde e-mail te verzenden die op attributen wordt gebaseerd die van de Data Warehouse van SecurFinancial worden gefedereerd.

## Stappen

### Een reis maken met een leespubliek

1. Navigeer aan het **portaal van de Reizen** en klik **creeer de 3} knoop van de Reis {.**

   ![ creeer-a-reis ](assets/create-journey.png)

2. Werk de eigenschappen van de Reis bij met een nieuwe naam: `SecurFinancial - Home Loan Offer - [your lab user ID]`.

3. Klik op **Orchestration**, dan belemmering en laat vallen de **Gelezen publiek** tegel aan het canvas.

4. Klik op het **potloodpictogram** naast de doos van het Publiek op de rechterkant van het scherm.

5. In de onderzoeksbar, onderzoek naar `SecureFinancial Customers - No Loans, Good Credit`, dan klik **sparen**.

   ![ creeer-a-reis ](assets/select-audience.png)

6. Verlaat alle montages als gebrek in het juiste zijmenu en klik dan **sparen**.

   ![ sparen-publiek-montages ](assets/save-audience-settings.png)

### E-mail personaliseren

1. Klik op **Acties**, dan klik en sleep de **E-mail** tegel aan het canvas.

2. Op het rechterzijmenu, klik op **E-mailconfiguratie** en selecteer **EmailMarketing**. Dan klik op **geef inhoud** uit.

3. Voeg in de onderwerpregel het volgende toe: `Learn more about SecurFinancial Home Loan` . Dan klik op **uitgeeft e-maillichaam**.

4. Klik het **malplaatje van de Inhoud** knoop in de hoogste juiste hoek. Vind en selecteer `SecureFinancial Template`, dan klik **bevestigen**.

   ![ reis-e-mail-config ](assets/journey-email-config.png)

   ![ reis-e-mail-bevestig ](assets/journey-email-confirm.png)

5. Herzie het malplaatje en klik **Malplaatje van het Gebruik**.

6. Je bent nu in de e-mail-Designer. Beweeg over de `{profile.person.name.firstName}` macro en klik **verpersoonlijkingsavatar**.

7. Blader in het venster Verpersoonlijken naar het volgende mappad: `[sandbox] > audienceEnrichment > CustomerAudienceUpload`

8. Klik in de **gelezen publiek** omslag. De verrijkingskenmerken van uw gefedereerde publiek kunt u hier vinden.

9. Selecteer het **Eerste** attribuut van de Naam aan de uitdrukkingsbouwer. In de e-mail wordt dynamisch de waarde van de voornaam van de klant uitgedrukt om het e-mailadres aan te passen.

10. Klik **sparen**.

11. Nu de voornaampersonalisatie is toegevoegd, voegt u `Hi, ` toe vóór de personalisatievariabele. Dan klik **sparen**.

   ![ reis-e-mail-sparen ](assets/journey-email-save.png)

12. Klik op de **Achtergrond** knoop tweemaal om aan het wegcanvas terug te keren. Dan in de **Actie: E-mail** menu aan het recht, klik **sparen**.

   ![ sparen-definitief-reis ](assets/save-final-journey.png)

Gefeliciteerd! U hebt een reis gemaakt in AJO met behulp van een gefederaliseerd publiek en gefederaliseerde verrijkingskenmerken.

Nu zullen wij bekijken hoe te [ bestaande publiek ](audience-enrichment-demo.md) in Experience Platform met gefederaliseerde gegevens van het gegevenspakhuis verrijken.
