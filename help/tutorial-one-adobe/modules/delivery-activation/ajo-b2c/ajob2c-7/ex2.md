---
title: Offer Decisioning - Je voorstellen en beslissing-id configureren
description: Offer Decisioning - Je voorstellen en beslissing-id configureren
kt: 5342
doc-type: tutorial
source-git-commit: 13d790855601fa6f36c1afa0f2d5faad5fc07eb0
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 10%

---

# 3.7.2 Uw aanbiedingen en beslissingen configureren

## 3.7.2.1 Je gepersonaliseerde aanbiedingen maken

In deze oefening, zult u vier **Gepersonaliseerde Aanbiedingen** creëren. Hier volgen de details waarmee u rekening moet houden bij het maken van deze aanbiedingen:

| Naam | Datumbereik | Afbeeldingskoppeling voor e-mail | Afbeeldingskoppeling voor web | Tekst | Prioriteit | Subsidiabiliteit | Taal | Bijschriftfrequentie | Afbeeldingsnaam |
|-----|------------|----------------------|--------------------|------|:--------:|--------------|:-------:|:-------:|:-------:|
| `--aepUserLdap-- - AirPods Max` | vandaag - 1 maand later | https://bit.ly/4a9RJ5d | Kies uit Assets-bibliotheek | `{{ profile.person.name.firstName }}, 10% discount on AirPods Max` | 25 | all - Vrouwelijke klanten | Engels (Verenigde Staten) | 3 | Apple AirPods Max- Vrouwelijk.jpg |
| `--aepUserLdap-- - Galaxy S24` | vandaag - 1 maand later | https://bit.ly/3W8yuDv | Kies uit Assets-bibliotheek | `{{ profile.person.name.firstName }}, 5% discount on Galaxy S24` | 15 | all - Vrouwelijke klanten | Engels (Verenigde Staten) | 3 | Galaxy S24 - Female.jpg |
| `--aepUserLdap-- - Apple Watch` | vandaag - 1 maand later | https://bit.ly/4fGwfxX | https://bit.ly/4fGwfxX | `{{ profile.person.name.firstName }}, 10% discount on Apple Watch` | 25 | all - Mannelijke klanten | Engels (Verenigde Staten) | 3 | Apple Watch - Male.jpg |
| `--aepUserLdap-- - Galaxy Watch 7` | vandaag - 1 maand later | https://bit.ly/4gTrkeo | Kies uit Assets-bibliotheek | `{{ profile.person.name.firstName }}, 5% discount on Galaxy Watch 7` | 15 | all - Mannelijke klanten | Engels (Verenigde Staten) | 3 | Galaxy Watch7 - Male.jpg |

{style="table-layout:auto"}

Login aan Adobe Journey Optimizer door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ ACOP ](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

U zult aan de **1} mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. U zult dan in de **1} mening van het Huis {van uw zandbak** zijn.`--aepSandboxName--`

![ ACOP ](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)

## Volgende stappen

Ga naar [ 3.7.3 de opstelling van SDK van het Web voor Ervaring het Beslissen ](./ex3.md){target="_blank"}

Ga terug naar [ Beslissing van de Ervaring ](ajo-decisioning.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}
