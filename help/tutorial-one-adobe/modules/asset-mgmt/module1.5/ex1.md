---
title: Aan de slag met Adobe Commerce as a Cloud Service
description: Aan de slag met Adobe Commerce as a Cloud Service
kt: 5342
doc-type: tutorial
exl-id: 8603c8e2-c3ba-4976-9703-cef9e63924b8
source-git-commit: 7280f6b7d3579226f2d8c7f94e75ca8d3f2941cc
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 1.5.1 Aan de slag met Adobe Commerce as a Cloud Service

Ga naar [ https://experience.adobe.com/ ](https://experience.adobe.com/){target="_blank"}. Zorg ervoor dat u zich in de juiste omgeving bevindt, die u `--aepImsOrgName--` moet noemen. Klik **Commerce**.

![AEM Assets](./images/accs1.png)

## 1.5.1.1 Een ACCS-instantie maken

Dan moet je dit zien. Klik op **+ Exemplaar toevoegen** .

![AEM Assets](./images/accs2.png)

Vul de velden als volgt in:

- **Naam van de Instantie**: `--aepUserLdap-- - ACCS`
- **Milieu**: `Sandbox`
- **Gebied**: `North America`

Klik **toevoegen instantie**.

![AEM Assets](./images/accs3.png)

U wordt nu gemaakt. Dit kan 5-10 minuten duren.

![AEM Assets](./images/accs4.png)

Wanneer de instantie gereed is, klikt u op de instantie om deze te openen.

![AEM Assets](./images/accs5.png)

## 1.5.1.2 Uw CitiSignal-winkel instellen

Dan moet je dit zien. Klik **binnen Teken met Adobe ID** en dan login.

![AEM Assets](./images/accs6.png)

Nadat u zich hebt aangemeld, kunt u deze startpagina beter zien. De eerste stap is het opzetten van uw CitiSignal-winkel in Commerce. Klik **Opslag**.

![AEM Assets](./images/accs7.png)

Klik **Alle opslag**.

![AEM Assets](./images/accs8.png)

Klik **creëren Website**.

![AEM Assets](./images/accs9.png)

Vul de velden als volgt in:

- **Naam**: `CitiSignal`
- **Code**: `citisignal`

Klik **sparen Website**.

![AEM Assets](./images/accs10.png)

Dan moet je hier weer zijn. Klik **creeer Opslag**.

![AEM Assets](./images/accs11.png)

Vul de velden als volgt in:

- **Website**: `CitiSignal`
- **Naam**: `CitiSignal`
- **Code**: `citisignal`
- **Categorie van de Wortel**: `Default Category`

Klik **sparen Opslag**.

![AEM Assets](./images/accs12.png)

Dan moet je hier weer zijn. Klik **creëren de Mening van de Opslag**.

![AEM Assets](./images/accs13.png)

Vul de velden als volgt in:

- **Opslag**: `CitiSignal`
- **Naam**: `CitiSignal`
- **Code**: `citisignal`
- **Status**: `Enabled`

Klik **sparen Mening van de Opslag**.

![AEM Assets](./images/accs14.png)

Dan zie je dit bericht. Klik **OK**.

![AEM Assets](./images/accs15.png)

Dan moet je hier weer zijn. Klik de **CitiSignal** website om het te openen.

![AEM Assets](./images/accs16.png)

Schakel het selectievakje in om deze website in te stellen als de standaardwebsite.

Klik **sparen Website**.

![AEM Assets](./images/accs16a.png)

Dan moet je hier weer zijn.

![AEM Assets](./images/accs16.png)

## 1.5.1.3 Categorieën en producten configureren

Ga naar **Catalogus** en selecteer dan **Categorieën**.

![AEM Assets](./images/accs17.png)

Selecteer **StandaardCategorie** en klik dan **Subcategorie** toevoegen.

![AEM Assets](./images/accs18.png)

Ga de naam `Phones` in en klik dan **sparen**.

![AEM Assets](./images/accs19.png)

Selecteer **StandaardCategorie** en klik dan **Subcategorie** opnieuw toevoegen.

![AEM Assets](./images/accs20.png)

Ga de naam `Watches` in en klik dan **sparen**.

![AEM Assets](./images/accs21.png)

Er moeten dan twee rubrieken worden gemaakt.

![AEM Assets](./images/accs22.png)

Daarna, ga naar **Catalogus** en selecteer dan **Producten**.

![AEM Assets](./images/accs23.png)

Dan moet je dit zien. Klik **toevoegen Product**.

![AEM Assets](./images/accs24.png)

Configureer uw product als volgt:

- **Naam van het Product**: `iPhone Air`
- **SKU**: `iPhone-Air`
- **Prijs**: `999`
- **Hoeveelheid**: `10000`
- **Categorieën**: uitgezochte `Phones`

Klik **sparen**.

![AEM Assets](./images/accs25.png)

De rol neer aan **Configuraties** en klikt **leidt Configuraties**.

![AEM Assets](./images/accs26.png)

Dan moet je dit zien. Klik **creëren Nieuw Attribuut**.

![AEM Assets](./images/accs27.png)

Plaats het **StandaardEtiket** aan `Storage` en klik dan **Optie** toevoegen onder **beheert Opties**.

![AEM Assets](./images/accs28.png)

Vorm de eerste optie gebruikend de naam `256GB` in alle 3 kolommen, en klik dan **voeg Optie** opnieuw toe.

![AEM Assets](./images/accs29.png)

Vorm de tweede optie gebruikend de naam `512GB` in alle 3 kolommen, en klik dan **voeg Optie** opnieuw toe.

![AEM Assets](./images/accs30.png)

Configureer de derde optie met de naam `1TB` in alle 3 kolommen.

![AEM Assets](./images/accs31.png)

De rol neer aan **Eigenschappen Storefront**. Plaats de volgende opties aan **ja**:

- **Gebruik in Onderzoek**
- **staat de Markeringen van HTML op Storefront toe**
- **Zichtbaar op de Pagina&#39;s van de Catalogus op Storefront**
- **Gebruik in de Lijst van het Product**

![AEM Assets](./images/accs32.png)

De rol omhoog en klikt **sparen Attribuut**.

![AEM Assets](./images/accs33.png)

Dan moet je dit zien. Selecteer beide attributen voor **kleur** en **opslag** en klik **daarna**.

![AEM Assets](./images/accs34.png)

Dan moet je dit zien. U moet nu de beschikbare kleuropties toevoegen. Om dat te doen, creeer **Nieuwe Waarde**.

![AEM Assets](./images/accs35.png)

Ga de waarde `Sky-Blue` in en klik **creeer Nieuwe Waarde**.

![AEM Assets](./images/accs36.png)

Ga de waarde `Light-Gold` in en klik **creeer Nieuwe Waarde**.

![AEM Assets](./images/accs37.png)

Ga de waarde `Cloud-White` in en klik **creeer Nieuwe Waarde**.

![AEM Assets](./images/accs38.png)

Voer de waarde `Space-Black` in. Klik **Uitgezocht allen**

![AEM Assets](./images/accs39.png)

Selecteer alle 3 opties onder **Opslag** en klik **daarna**.

![AEM Assets](./images/accs40.png)

Verlaat de standaardmontages en klik **daarna**.

![AEM Assets](./images/accs41.png)

Dan moet je dit zien. Klik **produceren Producten**.

![AEM Assets](./images/accs42.png)

Plaats de **Hoeveelheid** van elk product aan `10000`. Klik **sparen**.

![AEM Assets](./images/accs43.png)

De rol neer aan **Product in Websites** en controleert checkbox voor **CitiSignal**.

Klik **sparen**.

![AEM Assets](./images/accs44.png)

Klik **bevestigen**.

![AEM Assets](./images/accs45.png)

Dan moet je dit zien. Klik **terug**.

![AEM Assets](./images/accs46.png)

U ziet nu het product **iPhone Air** en zijn variaties in de Catalogus van het Product.

![AEM Assets](./images/accs47.png)

Volgende Stap: [ verbind ACCS met de Storefront van AEM Sites CS/EDS ](./ex2.md){target="_blank"}

Ga terug naar [ Adobe Commerce as a Cloud Service ](./accs.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}
