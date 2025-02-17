---
title: Adobe Journey Optimizer - Een op batch gebaseerde reis configureren
description: In deze sectie configureert u een batch-e-mailtransport voor het verzenden van een nieuwsbrief
kt: 5342
doc-type: tutorial
exl-id: 40ca710d-63c8-41bd-bd4e-f02186509345
source-git-commit: 3d61d91111d8693ab031fbd7b26706c02818108c
workflow-type: tm+mt
source-wordcount: '881'
ht-degree: 0%

---

# 3.4.2 Een campagne configureren

Login aan Adobe Journey Optimizer door naar [ Adobe Experience Cloud ](https://experience.adobe.com) te gaan. Klik **Journey Optimizer**.

![ ACOP ](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acophome.png)

U zult aan de **1} mening van het Huis {in Journey Optimizer worden opnieuw gericht.** Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxName--` genoemd. U zult dan in de **1} mening van het Huis {van uw zandbak `--aepSandboxName--` zijn.**

![ ACOP ](./../../../../modules/delivery-activation/ajo-b2c/ajob2c-1/images/acoptriglp.png)


## 3.4.2.1 Het publiek maken

Voordat u uw campagne maakt, moet u het publiek definiëren dat de campagne moet ontvangen. Om een publiek tot stand te brengen, ga naar **Soorten publiek** in het linkermenu. Je ziet hier al eerder gecreëerd publiek.

Klik op **+ Publiek maken** .

![ Journey Optimizer ](./images/audcampaign1.png)

Selecteer **bouwt regel** en klik **creëren**.

![ Journey Optimizer ](./images/audcampaign2.png)

Selecteer het gebied **Individueel Profiel XDM > Persoonlijke E-mail > Adres** en voeg het aan het canvas toe. Plaats de regelvoorwaarde aan **bestaat**.

Om het verzenden van e-mails naar andere gebruikers in uw gedeelde opleidingsmilieu te vermijden, kunt u een filter zoals **ook toevoegen Voornaam evenaart - uw voornaam -**.

Plaats de naam van uw publiek aan `--aepUserLdap-- - All customers with email` en klik **publiceren**.

![ Journey Optimizer ](./images/audcampaign3.png)

Uw publiek wordt nu gepubliceerd en kan in een campagne worden gebruikt.

## 3.4.2.2 Een nieuwsbrief maken

U maakt nu een campagne. In tegenstelling tot de op een gebeurtenis gebaseerde reis van de vorige oefening die op inkomende ervaringsgebeurtenissen of publieksingangen of uitgang baseert om een reis voor één specifieke klant teweeg te brengen, richten de campagnes één keer een heel publiek met unieke inhoud zoals nieuwsbrieven, eenmalige bevorderingen, of generische informatie of periodiek met gelijkaardige inhoud die op een regelmatige basis wordt verzonden zoals bijvoorbeeld verjaardagscampagnes en herinneringen.

In het menu, ga naar **Campagnes** en klik **creeer campagne**.

![ Journey Optimizer ](./images/oc43.png)

Selecteer **Gepland - Op de markt brengend** en klik **creeer**.

![ Journey Optimizer ](./images/campaign1.png)

Voor het scherm van de campagneverwezenlijking, vorm het volgende:

- **Naam**: `--aepUserLdap-- - CitiSignal Newsletter`.
- **Beschrijving**: Maandelijkse Nieuwsbrief
- **Type van Identiteit**: verandering in E-mail

Klik **Uitgezochte publiek**.

![ Journey Optimizer ](./images/campaign2.png)

Voor het **publiek**, selecteer het publiek u in de vorige stap, `--aepUserLdap-- - All customers with email` creeerde. Klik **sparen**.

![ Journey Optimizer ](./images/campaign2a.png)

Voor de **Actie**, selecteer **E-mail** en selecteer een bestaande **E-mailconfiguratie**. U gaat de inhoud over een paar minuten bewerken.

![ Journey Optimizer ](./images/campaign3.png)

Voor het **Programma**, kies **op een specifieke datum en een tijd** en plaats een tijd van keus.

![ Journey Optimizer ](./images/campaign4.png)

U kunt nu het e-mailbericht zelf maken. De rol omhoog een beetje, en klikt **geeft inhoud** uit.

![ Journey Optimizer ](./images/campaign5.png)

Dan zie je dit. Voor de **lijn van het Onderwerp**, gebruik dit: `Your monthly CitiSignal update has arrived.`. Daarna, klik **uitgeeft e-maillichaam**.

![ Journey Optimizer ](./images/campaign6.png)

Kies **Ontwerp van kras**.

![ Journey Optimizer ](./images/campaign7.png)

Dan zie je dit. In het linkermenu vindt u de structuurcomponenten die u kunt gebruiken om de structuur van de e-mail (rijen en kolommen) te definiëren.

De belemmering en laat vallen 3 keer a **1:1 kolom** op het canvas, 1 keer een 1:2 kolom verlaten en 1 keer een 2:1 kolom recht die u deze structuur zou moeten geven:

![ Journey Optimizer ](./images/campaign8.png)

In het linkermenu, ga naar **Fragments**. Sleep de kopbal u vroeger in [ oefening 3.1.2.1 ](./../ajob2c-1/ex2.md) op de eerste component in het canvas creeerde. Sleep de footer u vroeger in [ oefening 3.1.2.2 ](./../ajob2c-1/ex2.md) op de laatste component in het canvas creeerde.

![ Journey Optimizer ](./images/campaign9.png)

Klik op het pictogram **+** in het linkermenu. Ga naar **Inhoud** beginnen inhoud op het canvas toe te voegen.

![ Journey Optimizer ](./images/campaign10.png)

De belemmering en laat vallen component van de a **Tekst** op de tweede rij.

![ Journey Optimizer ](./images/campaign11.png)

Selecteer de standaardtekst in die component **gelieve te typen hier uw tekst.** en vervangt deze door de onderstaande tekst. Verander de groepering aan **groepering van het Centrum**.

```javascript
Hi {{profile.person.name.firstName}}

As a CitiSignal member, you're part of a dynamic community that's constantly evolving to meet your needs. We're committed to delivering innovative solutions that enhance your digital lifestyle and keep you ahead of the curve.

Stay connected.
```

![ Journey Optimizer ](./images/campaign12.png)

De belemmering en laat vallen een **component van het Beeld** op de 3de en 4de rij. Klik **doorbladeren** op de 3de rij.

![ Journey Optimizer ](./images/campaign13.png)

Open de omslag **citi-signaal-beelden**, klik om het beeld **Offer_AirPods.jpg** te selecteren, en **Uitgezocht** te klikken.

![ Journey Optimizer ](./images/campaign14.png)

Klik **doorbladeren** op beeldplaceholder op de 4de rij.

![ Journey Optimizer ](./images/campaign15.png)

Open de omslag **citi-signaal-beelden**, klik om het beeld **Offer_Phone.jpg** te selecteren, en **Uitgezocht** te klikken.

![ Journey Optimizer ](./images/campaign16.png)

De belemmering en laat vallen a **component van de Tekst van 0} {op de 3de en 4de rij.**

![ Journey Optimizer ](./images/campaign17.png)

Selecteer de standaardtekst in de component op de 3de rij **Gelieve te typen hier uw tekst.** en vervangt deze door de onderstaande tekst.

```javascript
Get AirPods for free:

Experience seamless connectivity like never before with CitiSignal. Sign up for select premium plans and receive a complimentary pair of Apple AirPods. Stay connected in style with our unbeatable offer.
```

Selecteer de standaardtekst in de component op de 4de rij **Gelieve te typen hier uw tekst.** en vervangt deze door de onderstaande tekst.

```javascript
We'll pay off your phone:

Make the switch to CitiSignal and say goodbye to phone payments! Switching to CitiSignal has never been more rewarding. Say farewell to hefty phone bills as we help pay off your phone, up to 800$!
```

![ Journey Optimizer ](./images/campaign18.png)

Je standaardnieuwsbrief is nu klaar. Klik **sparen**.

![ Journey Optimizer ](./images/ready.png)

Ga terug naar het campagnesdashboard door de **pijl** naast de onderwerpregel tekst in de top-left hoek te klikken.

![ Journey Optimizer ](./images/campaign19.png)

Klik **Overzicht om** te activeren.

![ Journey Optimizer ](./images/campaign20.png)

Deze fout kan dan optreden. Als dat het geval is, dan kunt u tot 24 uur moeten wachten tot het publiek is geëvalueerd, en dan proberen om uw campagne opnieuw te activeren. Mogelijk moet u ook het programma van uw campagne bijwerken zodat deze later kan worden uitgevoerd.

Klik **activeren**.

![ Journey Optimizer ](./images/campaign21.png)

Nadat de campagne is geactiveerd, wordt deze gepland.

![ Journey Optimizer ](./images/campaign22.png)

Uw campagne is nu geactiveerd. Uw e-mailbericht voor de nieuwsbrief wordt verzonden zoals u het in uw programma hebt gedefinieerd. Uw campagne wordt beëindigd zodra het laatste e-mailbericht is verzonden.

U ontvangt de e-mail ook op het e-mailadres dat u hebt gebruikt voor het demoprofiel dat u eerder hebt gemaakt.

![ Journey Optimizer ](./images/campaign23.png)

U hebt deze oefening voltooid.

## Volgende stappen

Ga naar [ 3.4.3 toepassen op segment-gebaseerde verpersoonlijking in een e-mailbericht ](./ex3.md){target="_blank"}

Ga terug naar [ Adobe Journey Optimizer ](journeyoptimizer.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../../overview.md){target="_blank"}
