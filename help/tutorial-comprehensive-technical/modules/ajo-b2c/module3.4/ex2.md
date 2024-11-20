---
title: Adobe Journey Optimizer - Een op batch gebaseerde reis configureren
description: In deze sectie configureert u een batch-e-mailtransport voor het verzenden van een nieuwsbrief
kt: 5342
doc-type: tutorial
exl-id: 52b2e019-e408-4160-87b7-2aabd0f3c68f
source-git-commit: acb941e4ee668248ae0767bb9f4f42e067c181ba
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 0%

---

# 3.4.2 Een op batch gebaseerde nieuwsbrief-reis configureren

Login aan Adobe Journey Optimizer door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ ACOP ](./../../../modules/ajo-b2c/module3.2/images/acophome.png)

U zult aan de **1} mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. Om van één zandbak in een andere te veranderen, klik op **Prod van de PRODUCTIE (VA7)** en selecteer de zandbak van de lijst. In dit voorbeeld, wordt de zandbak genoemd **AEP Enablement FY22**. U zult dan in de **1} mening van het Huis {van uw zandbak `--aepSandboxName--` zijn.**

![ ACOP ](./../../../modules/ajo-b2c/module3.2/images/acoptriglp.png)

## 3.4.2.1 Een nieuwsbrief maken

U zult nu een op partij-gebaseerde reis creëren. In tegenstelling tot de op gebeurtenissen gebaseerde reis van de vorige oefening die op inkomende ervaringsgebeurtenissen of publieksingangen of uitgang steunt om een reis voor één specifieke klant teweeg te brengen, richten de op partij-gebaseerde reizen één keer een heel publiek met unieke inhoud zoals nieuwsbrieven, eenmalige bevorderingen, of generische informatie of periodiek met gelijkaardige inhoud die op regelmatige basis wordt verzonden zoals bijvoorbeeld verjaardagscampagnes en herinneringen.

In het menu, ga naar **Reizen** en klik **creeer Reizen**.

![ Journey Optimizer ](./images/oc43.png)

Rechts ziet u een formulier waarin u de naam en de beschrijving van het transport moet vermelden. Voer de volgende waarden in:

- **Naam**: `--aepUserLdap-- - Newsletter Journey`. Bijvoorbeeld: **vangeluw - de Reizen van de Bulletin**.
- **Beschrijving**: Maandelijkse Nieuwsbrief

Klik **OK**.

![ Journey Optimizer ](./images/batchj2.png)

Onder **Orchestratie**, belemmering en laat vallen **Gelezen Publiek** op het canvas. Dit betekent dat, zodra de reis gepubliceerd wordt, het hele publiek zal terugwinnen, dat dan het doelpubliek van de reis en de boodschap wordt. Klik **Uitgezocht een publiek**.

![ Journey Optimizer ](./images/batchj3.png)

In **kies een publiek** popup, onderzoek naar uw ldap en selecteer het publiek u in [ Module 2.3 - In real time CDP creeerde - Bouw een publiek en neem actie ](./../../../modules/rtcdp-b2c/module2.3/real-time-cdp-build-a-segment-take-action.md) genoemd `--aepUserLdap-- - Interest in Galaxy S24`. Klik **sparen**.

![ Journey Optimizer ](./images/batchj5.png)

Klik **OK**.

![ Journey Optimizer ](./images/batchj6.png)

In het linkermenu, vind de **sectie van Acties** en sleep en laat vallen een **E-mail** actie op het canvas.

![ Journey Optimizer ](./images/batchj7.png)

Plaats de **Categorie** aan **Marketing** en selecteer een e-mailoppervlakte die u toelaat om e-mail te verzenden. In dit geval, is de e-mailoppervlakte om te selecteren **E-mail**. Zorg ervoor dat checkboxes voor **klikt op e-mail** en **e-mail opent** allebei worden toegelaten.

![ ACOP ](./images/journeyactions1eee.png)

De volgende stap is uw bericht te creëren. Om dat te doen, klik **geef inhoud** uit.

![ ACOP ](./images/journeyactions2.png)

U ziet dit nu. Klik het **Onderwerplijn** tekstgebied.

![ Journey Optimizer ](./images/batch4.png)

Voer deze tekst voor de onderwerpregel in: `Luma Newsletter - your monthly update has arrived.`. Klik **sparen**.

![ Journey Optimizer ](./images/batch5.png)

Dan ben je hier weer. Klik **E-mail Designer** beginnen de e-mailinhoud tot stand te brengen.

![ Journey Optimizer ](./images/batch6.png)

Dan zie je dit. Klik **de HTML van de Invoer**.

![ Journey Optimizer ](./images/batch7.png)

In het pop-upscherm moet u het HTML-bestand van de e-mail slepen en neerzetten. U kunt het malplaatje van de HTML [ hier ](./../../../assets/html/ajo-newsletter.html.zip) vinden. Download het ZIP-bestand met de HTML-sjabloon naar uw lokale computer en pak het uit op uw bureaublad.

![ Journey Optimizer ](./images/html1.png)

De belemmering en laat vallen het dossier **ajo-newsletter.html** om het in Journey Optimizer te uploaden. Klik **Invoer**.

![ Journey Optimizer ](./images/batch8.png)

Deze e-mailinhoud is klaar voor gebruik omdat deze alle verwachte personalisatie, afbeeldingen en tekst bevat. Alleen de tijdelijke aanduiding voor het aanbod blijft leeg.

U zou een foutenmelding kunnen krijgen: **Fout wanneer het proberen om activa** te halen. Dit is gekoppeld aan de afbeelding in de e-mail.

![ Journey Optimizer ](./images/errorfetch.png)

Als u deze fout krijgt, selecteer het beeld en klik **geef beeld** knoop uit.

![ Journey Optimizer ](./images/errorfetch1.png)

Klik **Assets Essentials** om terug naar uw bibliotheek van de Hoofdzaak van AEM Assets te gaan.

![ Journey Optimizer ](./images/errorfetch2.png)

Dan zie je deze popup. Navigeer aan de omslag **enablement-activa** en selecteer het beeld **luma-newsletterContent.png**. Klik **Uitgezocht**.

![ Journey Optimizer ](./images/errorfetch3.png)

Je standaardnieuwsbrief is nu klaar. Klik **sparen**.

![ Journey Optimizer ](./images/ready.png)

Ga terug naar het berichtdashboard door de **pijl** naast de onderwerplijntekst in de top-left hoek te klikken.

![ Journey Optimizer ](./images/batch9.png)

Klik op de pijl in de linkerbovenhoek om terug te gaan naar uw reis.

![ Journey Optimizer ](./images/oc79aeee.png)

Klik **O.K.** om uw e-mailactie te sluiten.

![ Journey Optimizer ](./images/oc79beee.png)

Uw nieuwsbrief is nu klaar om te worden gepubliceerd. Alvorens u dit doet, zie de **sectie van het Programma** waar u deze reis van het zijn van één-off aan een terugkomende campagne kunt schakelen. Klik de **knoop van het Programma**.

![ Journey Optimizer ](./images/batchj12.png)

Dan zie je dit. Selecteer **eens**.

![ Journey Optimizer ](./images/sch1.png)

Selecteer een datum en tijd binnen het volgende uur zodat u uw reis kunt testen. Klik **OK**.

>[!NOTE]
>
>De verzenddatum en -tijd van het bericht moeten binnen een uur liggen.

Klik **Publish**.

![ Journey Optimizer ](./images/batchj13.png)

Klik **opnieuw Publish**.

![ Journey Optimizer ](./images/batchj14.png)

Uw standaardnieuwsbrief is nu gepubliceerd. Uw e-mailbericht voor nieuwsbrieven wordt verzonden zoals u het in uw planning hebt gedefinieerd. Uw reis wordt beëindigd zodra het laatste e-mailbericht is verzonden.

![ Journey Optimizer ](./images/batchj14eee.png)

U hebt deze oefening voltooid.

Volgende Stap: [ 3.4.3 is verpersoonlijking in een e-mailbericht ](./ex3.md) van toepassing

[Terug naar module 3.4](./journeyoptimizer.md)

[Terug naar alle modules](../../../overview.md)
