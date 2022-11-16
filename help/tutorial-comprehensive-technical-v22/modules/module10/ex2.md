---
title: Adobe Journey Optimizer - Een op batch gebaseerde reis configureren
description: In deze sectie configureert u een batch-e-mailtransport voor het verzenden van een nieuwsbrief
kt: 5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 761da5b4-682f-430b-951c-278302fc4c54
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '787'
ht-degree: 0%

---

# 10.2 Vorm een op partij-gebaseerde nieuwsbrief reis

Aanmelden bij Adobe Journey Optimizer door naar [Adobe Experience Cloud](https://experience.adobe.com). Klikken **Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

U wordt omgeleid naar de **Home**  in Journey Optimizer. Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxId--`. Als u van de ene naar de andere sandbox wilt gaan, klikt u op **PRODUCTIEVOORRAAD (VA7)** en selecteert u de sandbox in de lijst. In dit voorbeeld krijgt de sandbox een naam **AEP-activering FY22**. Dan ben je in de **Home** weergave van de sandbox `--aepSandboxId--`.

![ACOP](../module7/images/acoptriglp.png)

## 10.2.1 Een nieuwsbrief maken

U zult nu een op partij-gebaseerde reis creëren. In tegenstelling tot de op gebeurtenis-gebaseerde reis van de vorige oefening die op inkomende ervaringsgebeurtenissen of segmentingangen of uitgang steunt om een reis voor één specifieke klant teweeg te brengen, richten de op partij-gebaseerde reizen één keer een heel segment met unieke inhoud zoals nieuwsbrieven, eenmalige bevorderingen, of generische informatie of periodiek met gelijkaardige inhoud die op regelmatige basis wordt verzonden zoals bijvoorbeeld verjaardagscampagnes en herinneringen.

Ga in het menu naar **Reizen** en klik op **Reis maken**.

![Journey Optimizer](./images/oc43.png)

Rechts ziet u een formulier waarin u de naam en de beschrijving van het transport moet vermelden. Voer de volgende waarden in:

- **Naam**: `--demoProfileLdap-- - Newsletter Journey`. Bijvoorbeeld: **vangeluw - Newsletter Journey**.
- **Beschrijving**: Maandelijkse nieuwsbrief

Klikken **OK**.

![Journey Optimizer](./images/batchj2.png)

Onder **Orchestratie**, slepen en neerzetten **Segment lezen** op het canvas. Dit betekent dat, zodra de reis wordt gepubliceerd, het hele segmentpubliek zal terugwinnen, dat dan het doelpubliek van de reis en de boodschap wordt. Klikken **Een segment selecteren**.

![Journey Optimizer](./images/batchj3.png)

In de **Een segment kiezen** popup, onderzoek naar uw ldap en selecteer het segment u binnen creeerde [Module 6 - Echte tijd CDP - Bouw een segment en neem actie](../module6/real-time-cdp-build-a-segment-take-action.md) benoemd `--demoProfileLdap-- - Interest in PROTEUS FITNESS JACKSHIRT`. bijvoorbeeld: vangeluw - interesse in PROTEUS FITNESS JACKSHIRT. Klikken **Opslaan**.

![Journey Optimizer](./images/batchj5.png)

Klikken **OK**.

![Journey Optimizer](./images/batchj6.png)

Zoek in het linkermenu de **Handelingen** en sleep een **E-mail** op het canvas.

![Journey Optimizer](./images/batchj7.png)

Stel de **Categorie** tot **Marketing** en selecteer een e-mailoppervlak waarmee u e-mail kunt verzenden. In dit geval is het te selecteren e-mailoppervlak **E-mail**. Zorg ervoor dat de selectievakjes **Klik op e-mail** en **e-mail wordt geopend** zijn beide ingeschakeld.

![ACOP](./images/journeyactions1eee.png)

De volgende stap is uw bericht te creëren. Om dat te doen, klikt u op **Inhoud bewerken**.

![ACOP](./images/journeyactions2.png)

U ziet dit nu. Klik op de knop **Onderwerpregel** tekstveld.

![Journey Optimizer](./images/batch4.png)

Voer deze tekst in voor de onderwerpregel: `Luma Newsletter - your monthly update has arrived.`. Klikken **Opslaan**.

![Journey Optimizer](./images/batch5.png)

Dan ben je hier weer. Klikken **E-mailontwerper** om de e-mailinhoud te maken.

![Journey Optimizer](./images/batch6.png)

Dan zie je dit. Klikken **HTML importeren**.

![Journey Optimizer](./images/batch7.png)

In het pop-upscherm moet u het HTML-bestand van de e-mail slepen en neerzetten. U kunt de sjabloon HTML vinden [hier](../../assets/html/ajo-newsletter.html.zip). Download het ZIP-bestand met de HTML-sjabloon naar uw lokale computer en pak het uit op uw bureaublad.

![Journey Optimizer](./images/html1.png)

Het bestand slepen en neerzetten **ajo-nieuwsbrief.html** om te uploaden naar Journey Optimizer. Klikken **Importeren**.

![Journey Optimizer](./images/batch8.png)

Deze e-mailinhoud is klaar voor gebruik omdat deze alle verwachte personalisatie, afbeeldingen en tekst bevat. Alleen de tijdelijke aanduiding voor het voorstel blijft leeg.

Er kan een foutbericht verschijnen: **Fout tijdens het ophalen van elementen**. Dit is gekoppeld aan de afbeelding in de e-mail.

![Journey Optimizer](./images/errorfetch.png)

Als deze fout optreedt, selecteert u de afbeelding en klikt u op de knop **Afbeelding bewerken** knop.

![Journey Optimizer](./images/errorfetch1.png)

Klikken **Assets Essentials** om terug te gaan naar uw AEM Assets Essentials-bibliotheek.

![Journey Optimizer](./images/errorfetch2.png)

Dan zie je deze popup. Ga naar de map **vermogensbestanddelen** en selecteert u de afbeelding **luma-newsletterContent.png**. Klikken **Selecteren**.

![Journey Optimizer](./images/errorfetch3.png)

Je standaardnieuwsbrief is nu klaar. Klikken **Opslaan**.

![Journey Optimizer](./images/ready.png)

Ga terug naar het berichtdashboard door op het **pijl** naast de tekst van de onderwerpregel in de linkerbovenhoek.

![Journey Optimizer](./images/batch9.png)

Klik op de pijl in de linkerbovenhoek om terug te gaan naar uw reis.

![Journey Optimizer](./images/oc79aeee.png)

Klikken **OK** om uw e-mailactie te sluiten.

![Journey Optimizer](./images/oc79beee.png)

Uw nieuwsbrief kan nu worden gepubliceerd. Voordat u dit doet, moet u de **Schema** waar u deze reis van een eenmalig naar een terugkerende campagne kunt schakelen. Klik op de knop **Schema** knop.

![Journey Optimizer](./images/batchj12.png)

Dan zie je dit. Selecteren **Eenmaal**.

![Journey Optimizer](./images/sch1.png)

Selecteer een datum en tijd binnen het volgende uur zodat u uw reis kunt testen. Klikken **OK**.

>[!NOTE]
>
>De verzenddatum en -tijd van het bericht moeten binnen een uur liggen.

Klikken **Publiceren**.

![Journey Optimizer](./images/batchj13.png)

Klikken **Publiceren** opnieuw.

![Journey Optimizer](./images/batchj14.png)

Uw standaardnieuwsbrief is nu gepubliceerd. Uw e-mailbericht voor nieuwsbrieven wordt verzonden zoals u het in uw planning hebt gedefinieerd. Uw reis wordt beëindigd zodra het laatste e-mailbericht is verzonden.

![Journey Optimizer](./images/batchj14eee.png)

U hebt deze oefening voltooid.

Volgende stap: [10.3 Een personalisatie toepassen in een e-mailbericht](./ex3.md)

[Ga terug naar module 10](./journeyoptimizer.md)

[Terug naar alle modules](../../overview.md)
