---
title: Aan de slag met Workfront Planning
description: Aan de slag met Workfront Planning
kt: 5342
doc-type: tutorial
exl-id: 26fa872b-c872-46b6-8f56-fa41696100da
source-git-commit: 42c9c3bbf0958794d5a65c37d4771345c6ff584c
workflow-type: tm+mt
source-wordcount: '1258'
ht-degree: 0%

---

# 1.1.1 Aan de slag met Workfront Planning

## 1.1.1.1 Beknopte CitiSignal-campagne

Om de context van CitiSignal en wat te begrijpen zij proberen te bereiken, download en lees hier de Brief van de Campagne van CitiSignal: [ CitiSignal-Fibre-Launch-Winter-2026.pdf ](./../../../assets/brief/CitiSignal-Fiber-Launch-Winter-2026.pdf).

## 1.1.1.2 Terminologie voor Workfront-planning

Hieronder vindt u de belangrijkste Workfront-planningsobjecten en -concepten:

| Term | Toelichting |
| --- | ---|
| **Workspace** | Een verzameling recordtypen die de operationele levenscyclus van een bepaalde organisatie definiëren. Een werkruimte is het werkkader van een organisatorische eenheid. |
| **Type van Verslag** | De naam van objecttypen in Workfront Planning. Met recordtypen worden werkruimten gevuld. In tegenstelling tot Workfront Workflow, waar de objecttypen vooraf zijn gedefinieerd, kunt u in Workfront Planning uw eigen objecttypen maken. |
| **Verslag** | Een instantie van een recordtype. |
| **malplaatje van Workspace** | U kunt een werkruimte maken met vooraf gedefinieerde sjablonen. U kunt de vooraf gedefinieerde recordtypen en -velden gebruiken die in een sjabloon voorkomen, of u kunt uw eigen recordtypen toevoegen. |
| **Velden** | Velden zijn kenmerken die u kunt toevoegen aan recordtypen. Velden bevatten informatie over het recordtype. |

>[!NOTE]
>
>Er gelden beperkingen voor het aantal Workfront Planning-objecten dat u kunt maken. Zie Overzicht van objectbeperkingen voor Adobe Workfront Planning voor meer informatie.

U gaat nu de handen in elkaar slaan en zelf een aantal van deze objecten maken.

## 1.1.1.3 Workspace, Recordtype, Velden

Ga naar [ https://experience.adobe.com/ ](https://experience.adobe.com/){target="_blank"}. Klik om **Workfront** te openen.

![ Planning van Workfront ](./images/wfpl1.png)

In Workfront, klik om het menu te openen en dan **Planning** te selecteren.

![ Planning van Workfront ](./images/wfpl2.png)

Dan moet je dit zien. Klik **creëren Workspace**.

![ Planning van Workfront ](./images/wfpl3.png)

Klik **malplaatje van het Gebruik** voor het malplaatje **Basis Marketing Beheer**.

![ Planning van Workfront ](./images/wfpl4.png)

Er wordt nu een nieuwe werkruimte gemaakt. Voordat u verdergaat, moet u de naam van de werkruimte wijzigen. Klik de 3 punten **..** en selecteer dan **uitgeven**.

![ Planning van Workfront ](./images/wfpl5.png)

Wijzig de naam in `--aepUserLdap-- - Basic: Marketing Management` . Klik **sparen**.

![ Planning van Workfront ](./images/wfpl6.png)

Dan moet je dit hebben.

![ Planning van Workfront ](./images/wfpl7a.png)

## 1.1.1.4 Taxonomies: Recordtype en velden

Onder **Taxonomies**, klik **+ voeg het Type van Verslag** toe en selecteer dan **voeg manueel** toe.

![ Planning van Workfront ](./images/wfpl7.png)

U zou dan **recordtype** popup moeten zien toevoegen.

![ Planning van Workfront ](./images/wfpl8.png)

Werk de volgende informatie op het **Verschijning** lusje bij:

- Vervang **Naamloos verslagtype** door `Business Unit`.
- Beschrijving: `Defines which BU is leading campaign planning.`.
- Een kleur en vorm selecteren voor het pictogram van uw keuze

Klik **sparen**.

![ Planning van Workfront ](./images/wfpl9.png)

Klik om het pas gecreëerde **BedrijfsEenheid** verslagtype te openen.

![ Planning van Workfront ](./images/wfpl10.png)

Er wordt nu een lege tabelweergave weergegeven, omdat er voor het nieuwe recordtype nog geen records van de Business Unit zijn gedefinieerd.

![ Planning van Workfront ](./images/wfpl11.png)

Klik de dropdown knoop op het gebied **Datum van het Begin** en selecteer dan **Schrapping**.

![ Planning van Workfront ](./images/wfpl12.png)

Selecteer **Schrapping**.

![ Planning van Workfront ](./images/wfpl13.png)

Klik de dropdown knoop op het gebied **Datum van het Eind** en selecteer dan **Schrapping**.

![ Planning van Workfront ](./images/wfpl14.png)

Selecteer **Schrapping**.

![ Planning van Workfront ](./images/wfpl15.png)

Klik vervolgens op het pictogram **+** om een nieuw veld toe te voegen. De rol neer in de lijst van beschikbare gebiedstypes en selecteert **Mensen**.

![ Planning van Workfront ](./images/wfpl16.png)

Plaats de **Naam** van het gebied aan `Business Unit Lead` en plaats de beschrijving van het gebied aan `Business Unit Lead responsible for budget and resources (VP, Head).`

Klik **sparen**.

![ Planning van Workfront ](./images/wfpl17.png)

Klik de 3 punten **...** op het eerste verslag en selecteer **Mening**.

![ Planning van Workfront ](./images/wfpla1.png)

Plaats de **Naam** aan `Consumer Services`.

Plaats de **Beschrijving** aan `Handles residential offerings like mobile plans, internet packages, and customer support.`.

Plaats de **Lood van de BedrijfsEenheid** aan zich.

Klik eenmaal op de pijl om terug te gaan naar het vorige scherm.

![ Planning van Workfront ](./images/wfpla2.png)

Klik de 3 punten **...** op het tweede verslag en selecteer **Mening**.

![ Planning van Workfront ](./images/wfpla3.png)

Plaats de **Naam** aan `Enterprise & Business Solutions`

Plaats de **Beschrijving** aan `Provides connectivity, cloud, and managed services to corporate clients and government entities.`

Plaats de **Lood van de BedrijfsEenheid** aan zich.

Klik eenmaal op de pijl om terug te gaan naar het vorige scherm.

![ Planning van Workfront ](./images/wfpla4.png)

Klik de 3 punten **...** op het derde verslag en selecteer **Mening**.

![ Planning van Workfront ](./images/wfpla5.png)

Plaats de **Naam** aan `Sales & Marketing`

Plaats de **Beschrijving** aan `Drives customer acquisition, brand strategy, advertising, and market segmentation.`

Plaats de **Lood van de BedrijfsEenheid** aan zich.

Klik eenmaal op de pijl om terug te gaan naar het vorige scherm.

![ Planning van Workfront ](./images/wfpla6.png)

U hebt nu een nieuw recordtype gemaakt, u hebt zowel velden verwijderd als gemaakt en u hebt drie bedrijfseenheden gemaakt. Ga terug naar het Workspace-overzichtsscherm door op de pijl in de linkerbovenhoek te klikken.

![ Planning van Workfront ](./images/wfpl18.png)

Dan moet je dit zien.

![ Planning van Workfront ](./images/wfpl19.png)

## 1.1.1.5 Typen operationele records: velden

Klik om **Campagnes** te openen.

![ Planning van Workfront ](./images/wfpl20.png)

Klik op het pictogram **+** om een nieuw veld te maken. Selecteer **Nieuwe verbinding** en selecteer dan **BedrijfsEenheid**.

![ Planning van Workfront ](./images/wfpl21.png)

Laat de standaardinstellingen staan. Klik **creëren**.

![ Planning van Workfront ](./images/wfpl22.png)

Selecteer **Overslaan**.

![ Planning van Workfront ](./images/wfpl23.png)

Het nieuwe veld wordt vervolgens weergegeven in de tabelweergave.

![ Planning van Workfront ](./images/wfpl24.png)

## 1.1.1.6 Een aanvraagformulier maken

Op het het overzichtsscherm van Campagnes, klik de 3 punten **...** en selecteer dan **de verzoekvorm van de creatie**.

![ Planning van Workfront ](./images/wfpl25.png)

Wijzig de naam in `Campaign Request Form` . Klik **creëren**.

![ Planning van Workfront ](./images/wfpl26.png)

Op dit moment hoeft u het formulier niet te wijzigen. U gebruikt deze zonder wijzigingen. Eerst, klik **sparen** en klik dan **publiceren**.

![ Planning van Workfront ](./images/wfpl27.png)

Klik op de pijl in de linkerbovenhoek om terug te keren naar het overzichtsscherm Request Forms.

![ Planning van Workfront ](./images/wfpl28.png)

Klik op de pijl in de linkerbovenhoek om terug te keren naar het scherm Campagnes overview.

![ Planning van Workfront ](./images/wfpl29.png)

## 1.1.1.7 Een nieuwe record verzenden met het aanvraagformulier

Voor het het overzichtsscherm van Campagnes, klik **+ Nieuw Verslag**.

![ Planning van Workfront ](./images/wfpl31.png)

Selecteer **voorleggen een verzoek** en klik **verdergaan**.

![ Planning van Workfront ](./images/wfpl32.png)

Plaats het **Onderwerp** aan `--aepUserLdap-- - New Campaign Creation Request`.

Plaats de **naam van de Campagne** aan `--aepUserLdap-- - CitiSignal Fiber Launch`.

Plaats de **samenvatting van de Campagne** aan:

```
The CitiSignal Fiber Launch campaign introduces CitiSignal’s flagship fiber internet service—CitiSignal Fiber Max—to key residential markets. This campaign is designed to build awareness, drive sign-ups, and establish CitiSignal as the go-to provider for ultra-fast, reliable, and future-ready internet. The campaign will highlight the product’s benefits for remote professionals, online gamers, and smart home families, using persona-driven messaging across digital and physical channels.
```

Vul de overige velden naar wens in.

Klik **voorleggen verzoek**.

![ Planning van Workfront ](./images/wfpl33.png)

Klik **X** om popup te sluiten.

![ Planning van Workfront ](./images/wfpl34.png)

Dan zou u de nieuw gecreëerde campagne in het overzicht moeten zien.

![ Planning van Workfront ](./images/wfpl35.png)

## 1.1.1.8 Portfolio en aangepast formulier maken

In de volgende stap gaat u een automatisering maken die informatie neemt uit de campagne die u hebt gemaakt in Workfront Planning en die die informatie gebruikt in Workfront om een programma te maken. Voordat u de automatisering kunt maken, moet u eerst twee dingen configureren in Workfront: een portfolio en een aangepast formulier.

Om de portefeuille tot stand te brengen, open het menu en klik **Portfolio&#39;s**.

![ Planning van Workfront ](./images/wfplss1.png)

Klik **+ Nieuwe Portfolio**.

![ Planning van Workfront ](./images/wfplss2.png)

Stel de naam van het portfolio in op `--aepUserLdap-- - Marketing` .

![ Planning van Workfront ](./images/wfplss3.png)

Daarna, open het menu en klik **Opstelling** om de douanevorm tot stand te brengen.

![ Planning van Workfront ](./images/wfplss4.png)

In het linkermenu, ga naar **Douane Forms**, **Forms** en klik dan **+ Nieuwe douanevorm**.

![ Planning van Workfront ](./images/wfplss5.png)

Selecteer **Programma** en klik **verdergaan**.

![ Planning van Workfront ](./images/wfplss6.png)

Wijzig de naam van het formulier in `--aepUserLdap-- - Program Information` .

![ Planning van Workfront ](./images/wfplss7.png)

Daarna, ga naar **Bibliotheek van het Gebied** en onderzoek naar `budget`. De belemmering en laat vallen het bestaande gebied **Begroting** op de vorm.

Klik **toepassen**.

![ Planning van Workfront ](./images/wfplss8.png)

Uw aangepaste formulierconfiguratie is nu opgeslagen.

![ Planning van Workfront ](./images/wfplss9.png)

## 1.1.1.8 Een automatisering maken

Met het portfolio en het aangepaste formulier dat u hebt gemaakt, kunt u de automatisering nu maken.

Klik om het menu te openen en dan **Planning** te selecteren.

![ Planning van Workfront ](./images/wfpl36.png)

Klik om de werkruimte te openen die u eerder hebt gemaakt, met de naam `--aepUserLdap-- - Basic: Marketing Management` .

![ Planning van Workfront ](./images/wfpl37.png)

Klik om **Campagnes** te openen.

![ Planning van Workfront ](./images/wfpl38.png)

Op het het overzichtsscherm van Campagnes, klik de 3 punten **...** en selecteer dan **Automatiseringen beheren**.

![ Planning van Workfront ](./images/wfpl40.png)

Klik **Nieuwe automatisering**.

![ Planning van Workfront ](./images/wfpl41.png)

Stel de naam van de automatisering in op `Campaign to Program` .

De beschrijving instellen op `This automation will convert a Planning Campaign record to a Workfront Program.`

Klik **sparen**.

![ Planning van Workfront ](./images/wfpl42.png)

Plaats de **Actie** aan **creeer programma**. Klik op **+ Verbonden veld toevoegen** .

![ Planning van Workfront ](./images/wfpl43.png)

Selecteer de **portefeuille van het Programma**: `--aepUserLdap-- - Marketing`.

Selecteer deze **Vorm van de Douane**: `--aepUserLdap-- Program information`.

Klik **sparen**.

![ Planning van Workfront ](./images/wfpl44.png)

Dan moet je dit zien. Klik op de pijl om terug te gaan naar het scherm Campagnes overview.

![ Planning van Workfront ](./images/wfpl45.png)

Schakel het selectievakje in voor de campagne die u eerder hebt gemaakt. Dan, klik de **Campagne aan de automatisering van het Programma**.

![ Planning van Workfront ](./images/wfpl46.png)

Na een paar seconden ziet u een bevestiging dat de automatisering met succes is voltooid. Dit betekent dat op het voorwerp van de Campagne in de Planning van Workfront, een Programma werd gecreeerd in Workfront.

![ Planning van Workfront ](./images/wfpl47.png)

Om het Programma in Workfront te controleren, scrol aan het recht en klik het programma in de **Verbonden kolom van het Programma**.

![ Planning van Workfront ](./images/wfpl48.png)

U zou dan het programma moeten zien dat enkel door de automatisering werd gecreeerd u vormde.

![ Planning van Workfront ](./images/wfpl50.png)

Volgende Stap: [ Samenvatting &amp; Voordelen ](./summary.md){target="_blank"}

Ga terug naar [ Inleiding aan de Planning van Workfront ](./wfplanning.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}
