---
title: Adobe Journey Optimizer - Pas personalisatie toe in een e-mailbericht
description: Deze oefening verklaart hoe te om segmentverpersoonlijking binnen een e-mailinhoud te gebruiken
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 573ecfba-4f1d-4242-8358-1d33109aaea3
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 0%

---

# 10.3 Een personalisatie toepassen in een e-mailbericht

Aanmelden bij Adobe Experience Cloud door naar [Adobe Experience Cloud](https://experience.adobe.com). Klikken **Adobe Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

U wordt omgeleid naar de **Home** in Journey Optimizer. Voordat u verdergaat, moet u een **sandbox**. De sandbox die moet worden geselecteerd, krijgt een naam ``--aepTenantId--``. U kunt dit doen door op de tekst te klikken **[!UICONTROL Productieproduct]** in de blauwe lijn boven op het scherm.

![ACOP](../module7/images/acoptriglp.png)

## 10.3.1 personalisatie op basis van segmenten

In deze oefening zult u uw nieuwsbrief e-mailbericht met een gepersonaliseerde tekst verbeteren die op segmentlidmaatschap wordt gebaseerd.

Ga naar **Reizen**. Vind de nieuwsbrief die u in de vorige oefening hebt gecreeerd. Zoeken naar `--demoProfileLdap-- - Newsletter`. Klik op uw reis om deze te openen.

![Journey Optimizer](./images/sbp1.png)

Dan zie je dit. Klikken **Dupliceren**.

![Journey Optimizer](./images/sbp2.png)

Klik op ** Dupliceren**.

![Journey Optimizer](./images/sbp3.png)

Selecteer uw **E-mail** handeling en klik op **Inhoud bewerken**.

![Journey Optimizer](./images/sbp3a.png)

Klikken **E-mailontwerper**.

![Journey Optimizer](./images/sbp4.png)

Dan zie je dit.

![Journey Optimizer](./images/sbp5.png)

Openen **Inhoudscomponenten** en sleep een **Tekst** onder de huidige inhoud van de nieuwsbrief.

![Journey Optimizer](./images/sbp6.png)

Selecteer de hele standaardtekst en verwijder deze. Klik vervolgens op de knop **Aanpassing toevoegen** in de werkbalk.

![Journey Optimizer](./images/sbp7.png)

U zult dan dit zien:

![Journey Optimizer](./images/seg1.png)

Klik in het linkermenu op **Segmentlidmaatschap**.

![Journey Optimizer](./images/seg2.png)

>[!NOTE]
>
>Als u uw segment niet in deze lijst kunt vinden, scrol neer een beetje om instructies op te zoeken hoe te om segmentidentiteitskaart manueel terug te winnen.

Selecteer het segment `Luma - Women's Category Interest` en klik op de knop **+** pictogram, dat er als volgt uitziet:

![Journey Optimizer](./images/seg3.png)

Vervolgens laat u de eerste regel ongewijzigd en vervangt u regel 2 en 3 door de volgende code:

``
Psssst... a private sale in the women category will launch soon, we will keep you posted
{%else%}
Thanks for taking the time to read our newsletter. Here is a 10% promo code to use on the website: READER10
{%/if%}
``

Dan heb je het volgende:

![Journey Optimizer](./images/seg4.png)

Klikken **Valideren** om te controleren of de code correct is. Klikken **Opslaan**.

![Journey Optimizer](./images/sbp8.png)

U kunt dit bericht nu opslaan door op de knop **Opslaan** in de rechterbovenhoek. Klik vervolgens op **Inhoud simuleren**.

![Journey Optimizer](./images/sbp9.png)

Selecteer een van de profielen die u als onderdeel van deze zelfstudie hebt gemaakt en klik op **Voorvertoning**. U zult dan het resultaat van uw configuratie zien.

![Journey Optimizer](./images/sbp10.png)

Dan zie je dit. Klik vervolgens op **Sluiten**.

![Journey Optimizer](./images/sbp10fff.png)

Ga terug naar het berichtdashboard door op het **pijl** naast de tekst van de onderwerpregel in de linkerbovenhoek.

![Journey Optimizer](./images/sbp11.png)

Klik op de pijl in de linkerbovenhoek om terug te gaan naar uw reis.

![Journey Optimizer](./images/oc79afff.png)

Klikken **OK** om uw e-mailactie te sluiten.

![Journey Optimizer](./images/oc79bfff.png)

Wijzig uw **Schema** tot **Eenmaal** en een **Datum/tijd**. Klikken **OK**.

>[!NOTE]
>
>De verzenddatum en -tijd van het bericht moeten binnen een uur liggen.

![Journey Optimizer](./images/sbp18.png)

Klik op de knop **Publiceren** op de reis.

![Journey Optimizer](./images/sbp19.png)

Klik in het pop-upvenster op **Publiceren** opnieuw.

![Journey Optimizer](./images/sbp20.png)

Uw standaardnieuwsbrief is nu gepubliceerd. Uw e-mailbericht voor nieuwsbrieven wordt op basis van uw planning verzonden en uw reis wordt beëindigd zodra het laatste e-mailbericht is verzonden.

![Journey Optimizer](./images/sbp20fff.png)

U hebt deze oefening voltooid.

Volgende stap: [10.4 Pushmeldingen instellen en gebruiken voor iOS](./ex4.md)

[Ga terug naar module 10](./journeyoptimizer.md)

[Terug naar alle modules](../../overview.md)
