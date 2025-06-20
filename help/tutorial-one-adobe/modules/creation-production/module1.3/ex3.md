---
title: GenStudio for Performance Marketing Campagne activeren naar Meta
description: GenStudio for Performance Marketing Campagne activeren naar Meta
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 2c7ef715-b8af-4a5b-8873-5409b43d7cb0
source-git-commit: b8f7b370a5aba82a0dcd6e7f4f0222fe209976f7
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 0%

---

# 1.3.3 Campagne activeren naar Meta

>[!IMPORTANT]
>
>Als u deze bewerking wilt voltooien, hebt u toegang nodig tot een werkende AEM Assets CS Author-omgeving met AEM Content Hub ingeschakeld. Als u oefening [ Adobe Experience Manager Cloud Service &amp; Edge Delivery Services ](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"} volgt zult u toegang tot zulk een milieu hebben.

>[!IMPORTANT]
>
>Als u eerder een AEM Assets CS-programma hebt geconfigureerd met een auteur- en AEM Assets-omgeving, kan het zijn dat de AEM CS-sandbox is geminimaliseerd. Gezien het feit dat het vernietigen van zo&#39;n zandbak 10 tot 15 minuten duurt, zou het een goed idee zijn om het ontruimingsproces nu te beginnen zodat u niet op een later tijdstip hoeft te wachten.

## 1.3.3.1 Campagne maken

In **GenStudio for Performance Marketing**, ga naar **Campagnes** in het linkermenu. Klik **+ toevoegen campagne**.

![ GSPeM ](./images/gscampaign1.png)

Dan zou u een leeg campagneoverzicht moeten zien.

![ GSPeM ](./images/gscampaign2.png)

Gebruik `--aepUserLdap-- - CitiSignal Fiber Launch Campaign` voor de veldnaam.

Voor het gebied **Beschrijving**, gebruik de hieronder tekst.

```
The CitiSignal Fiber Launch campaign introduces CitiSignal’s flagship fiber internet service—CitiSignal Fiber Max—to key residential markets. This campaign is designed to build awareness, drive sign-ups, and establish CitiSignal as the go-to provider for ultra-fast, reliable, and future-ready internet. The campaign will highlight the product’s benefits for remote professionals, online gamers, and smart home families, using persona-driven messaging across digital and physical channels.
```

Voor het gebied **Doelstelling**, gebruik de hieronder tekst.

```
Generate brand awareness in target regions
Drive early sign-ups and pre-orders for CitiSignal Fiber Max
Position CitiSignal as a premium, customer-first fiber internet provider
Educate consumers on the benefits of fiber over cable or DSL
```

Voor het gebied **Zeer belangrijke Overseinen**, gebruik de hieronder tekst.

```
Supporting Points:
Symmetrical speeds up to 2 Gbps
Whole-home Wi-Fi 6E coverage
99.99% uptime guarantee
24/7 concierge support
No data caps or throttling
 Channels:
Digital Advertising: Google Display, YouTube pre-roll, Meta (Facebook/Instagram), TikTok (for gamers)
Email Marketing: Persona-segmented drip campaigns
Social Media: Organic and paid posts with testimonials, speed demos, and influencer partnerships
Out-of-Home (OOH): Billboards, transit ads in suburban commuter corridors
Local Events: Pop-up booths at tech expos, family festivals, and gaming tournaments
Direct Mail: Personalized flyers with QR codes for early sign-up discounts
 
Target Regions:
Primary Launch Markets:
Denver Metro Area, CO
Austin, TX
Raleigh-Durham, NC
Salt Lake City, UT
Demographic Focus:
Suburban neighborhoods with high remote work density
Areas with high smart home adoption
Zip codes with underserved or dissatisfied cable customers
```

Dan zou u het volgende moeten hebben:

![ GSPeM ](./images/gscampaign3.png)

Schuif omlaag om meer velden weer te geven:

![ GSPeM ](./images/gscampaign4.png)

Voor het gebied **Begin**, plaats het aan de datum van vandaag.

Voor het gebied **Eind**, plaats het aan een datum 1 maand van nu.

Voor het gebied **Status**, plaats het aan **Actief**.

Voor het gebied **Kanalen**, plaats het aan **Meta**, **E-mail**, **Betaalde Media**, **Vertoning**.

Voor het gebied **Gebieden**, selecteer een gebied van keus.

Voor het gebied voor het gebied **Verwijzingen** > **Producten**: kies het product `--aepUserLdap-- - CitiSignal Fiber Max`.

**Verwijzingen** > **Personas**: kies de persona&#39;s `--aepUserLdap-- - Remote Professionals`, `--aepUserLdap-- - Online Gamers`, `--aepUserLdap-- - Smart Home Families`

U zou dan dit moeten zien:

![ GSPeM ](./images/gscampaign5.png)

Uw campagne is nu klaar. Klik de **pijl** om terug te gaan.

![ GSPeM ](./images/gscampaign6.png)

Dan zie je je campagne in de lijst. Klik op het pictogram van de kalenderweergave om de weergave in de campagnecalender te wijzigen.

![ GSPeM ](./images/gscampaign7.png)

Dan zou u een campagnemalender moeten zien die een visueel idee geeft van welke campagnes op dat moment actief zijn.

![ GSPeM ](./images/gscampaign8.png)

## 1.3.3.2 Verbinding met Meta instellen

>[!IMPORTANT]
>
>Als u uw verbinding met Meta wilt instellen, hebt u een Meta-gebruikersaccount nodig en moet die gebruikersaccount worden toegevoegd aan een Meta Business-account.

Om de verbinding aan Meta te plaatsen, klik de 3 punten **...** en selecteer **Montages**.

![ GSPeM ](./images/gsconnection1.png)

Klik **verbinden** voor **Meta Adds**.

![ GSPeM ](./images/gsconnection2.png)

Meld u aan met uw Meta-account. Klik **verdergaan**.

![ GSPeM ](./images/gsconnection3.png)

Als uw account is gekoppeld aan een Meta Business-account, kunt u de bedrijfsportefeuille selecteren die in Meta is geconfigureerd.

![ GSPeM ](./images/gsconnection5.png)

Zodra de verbinding met succes is gevestigd, klik de lijn die **X verbonden rekening(en)** zegt.

![ GSPeM ](./images/gsconnection4.png)

U moet dan de gegevens bekijken van de Meta Business Account die is verbonden met GenStudio for Performance Marketing.

![ GSPeM ](./images/gsconnection6.png)

## 1.3.3.3 Nieuw element maken

Ga naar [ https://firefly.adobe.com/ ](https://firefly.adobe.com/){target="_blank"}. Ga de herinnering `a neon rabbit running very fast through space` in en klik **produceert**.

![ GSPeM ](./images/gsasset1.png)

Er worden dan verschillende afbeeldingen gegenereerd. Kies het beeld u van de meesten houdt, klik het **pictogram van het Aandeel** op het beeld en selecteer dan **Open in Adobe Express**.

![ GSPeM ](./images/gsasset2.png)

Vervolgens ziet u dat de afbeelding die u zojuist hebt gegenereerd, beschikbaar is in Adobe Express voor bewerking. U moet nu het CitiSignal-logo aan de afbeelding toevoegen. Om dat te doen, ga naar **Banden**.

![ GSPeM ](./images/gsasset3.png)

Vervolgens wordt de sjabloon van het CitiSignal-merk die u in GenStudio for Performance Marketing hebt gemaakt, weergegeven in Adobe Express. Klik om uw merksjabloon te selecteren met de naam `--aepUserLdap-- - CitiSignal` .

![ GSPeM ](./images/gsasset4.png)

Ga naar **Logo&#39;s** en klik het **witte** embleem van het Citisignaal om het op het beeld te laten vallen.

![ GSPeM ](./images/gsasset5.png)

Plaats het CitiSignal-logo in de linkerbovenhoek.

![ GSPeM ](./images/gsasset6.png)

Daarna, klik **Aandeel**.

![ GSPeM ](./images/gsasset7.png)

Selecteer **AEM Assets**.

![ GSPeM ](./images/gsasset8.png)

Klik **Uitgezochte omslag**.

![ GSPeM ](./images/gsasset9.png)

Selecteer uw AEM Assets CS-opslagplaats met de naam `--aepUserLdap-- - CitiSignal` en selecteer vervolgens de map `--aepUserLdap-- - CitiSignal Fiber Campaign` . Klik **Uitgezocht**.

![ GSPeM ](./images/gsasset11.png)

Dan moet je dit zien. Klik **uploaden 1 activa**. Uw afbeelding wordt nu geüpload naar AEM Assets CS.

![ GSPeM ](./images/gsasset12.png)

Ga naar [ https://experience.adobe.com/ ](https://experience.adobe.com/){target="_blank"}. Open **Experience Manager Assets**.

![ GSPeM ](./images/gsasset13.png)

Selecteer de AEM Assets CS-omgeving met de naam `--aepUserLdap-- - CitiSignal dev` .

![ GSPeM ](./images/gsasset14.png)

Ga naar **Assets** en klik dan de omslag `--aepUserLdap-- - CitiSignal Fiber Campaign` tweemaal.

![ GSPeM ](./images/gsasset15.png)

Dan zou je iets gelijkaardigs moeten zien. Dubbelklik op de afbeelding `--aepUserLdap-- - neon rabbit` .

![ GSPeM ](./images/gsasset16.png)

De afbeelding `--aepUserLdap-- - neon rabbit` wordt dan weergegeven. Verandering de **Status** aan **Goedgekeurd** en klik dan **sparen**

>[!IMPORTANT]
>
>Als het statuut van een beeld niet aan **Goedgekeurd** wordt geplaatst, dan zal het beeld niet in GenStudio for Performance Marketing zichtbaar zijn. Alleen goedgekeurde middelen zijn toegankelijk in GenStudio for Performance Marketing.

![ GSPeM ](./images/gsasset17.png)

Ga terug naar GenStudio for Performance Marketing. In het linkermenu, ga naar **Assets** en selecteer uw bewaarplaats van AEM Assets CS, die zou moeten worden genoemd `--aepUserLdap-- - CitiSignal`. Vervolgens ziet u dat de afbeelding die u zojuist hebt gemaakt en goedgekeurd, beschikbaar wordt in GenStudio for Performance Marketing.

![ GSPeM ](./images/gsasset18.png)

## 1.3.3.4 Meta-advertentie maken en goedkeuren

## 1.3.3.5 Advertentie publiceren naar Meta

## Volgende stappen

Ga naar [ Samenvatting &amp; voordelen ](./summary.md){target="_blank"}

Ga terug naar [ GenStudio for Performance Marketing ](./genstudio.md){target="_blank"}

Ga terug naar [ Alle Modules ](./../../../overview.md){target="_blank"}
