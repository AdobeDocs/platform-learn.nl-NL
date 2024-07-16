---
title: CSC Bootkamp - Webpagina-banner voor product maken
description: CSC Bootkamp - Webpagina-banner voor product maken
doc-type: multipage-overview
exl-id: c78b6ba2-1a1a-4e95-a8ab-1b572fa2d8b1
source-git-commit: 143da6340b932563a3309bb46c1c7091e0ab2ee2
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 0%

---

# Homepatiebanner voor producten maken

## Productie van de banner

Dankzij de automatisering van content beschikt Adobe Creative Cloud over de kracht van Experience Manager Assets. Zo kunnen marketers de productie van bedrijfsmiddelen op grote schaal automatiseren, waardoor het creëren van variaties aanzienlijk wordt versneld. Laten we deze functies gebruiken om een banner te genereren die op de startpagina moet worden gebruikt!

- Ga naar de AEM auteur op [ https://author-p105462-e991028.adobeaemcloud.com/ ](https://author-p105462-e991028.adobeaemcloud.com/) en login met de geloofsbrieven die wij verstrekten.

- Navigeer vanaf de startpagina naar Gereedschappen \> Assets \> Profielen verwerken.

![ Hulpmiddelen > Assets > de Profielen van de Verwerking ](./images/prod-processing-profiles.png)

- In de interface ziet u alle bestaande verwerkingsprofielen. Deze kunnen worden gebruikt tot om bepaalde automatiseringen toe te laten.

![ lijst van verwerkingsprofielen ](./images/prod-profile-list.png)


- De volgende zijn van belang voor u:
   - Adobe Drive Banner Donker: maakt een Adobe-banner met een donkere bedekking op basis van het geselecteerde element
     ![ donkere banner ](./images/prod-banner-dark.jpg)
   - Adobe fietbannerlicht: maakt een Adobe-banner met een lichtbedekking op basis van het geselecteerde element
     ![ lichte banner ](./images/prod-banner-light.jpg)
   - Adobe fietbanner Green: maakt een Adobe-banner met een groene overlay op basis van het geselecteerde middel
     ![ groene banner ](./images/prod-banner-green.jpg)

- Nadat u het type banner hebt gekozen dat u wilt maken, selecteert u dat verwerkingsprofiel en selecteert u vervolgens Profiel toepassen op map(pen).

![ pas profiel op omslag ](./images/prod-apply-profile.png) toe

- Blader op het volgende scherm naar de map van uw team in AEM Assets. Selecteer vervolgens linksboven de knop &quot;Maken&quot; om een nieuwe map te maken en geef deze een betekenisvolle naam, bijvoorbeeld &quot;Donkere banner maken&quot;.

![ creeer omslag ](./images/prod-create-profile-folder.png)

![ creeer omslagdetails ](./images/prod-profile-folder-details.png)

- Nadat u de map hebt gemaakt, schakelt u het vakje naast de naam in en klikt u op de knop Toepassen aan de rechterkant.

![ is op gecreeerde omslag ](./images/prod-select-profile-folder.png) van toepassing

Nu we de noodzakelijke configuratie hebben gedaan, laten we onze banner genereren.

- Klik op AEM logo in de linkerbovenhoek om de navigatie te openen en navigeer vervolgens naar Navigatie \> Assets \> Bestanden.

![ noem huisscherm ](./images/prod-select-assets.png)
![ de activa van de naam het scherm ](./images/prod-select-assets-2.png)

- Zoek de map &quot;Gegenereerde Adobe Assets&quot; en open deze door op de kaart te klikken. Hier worden de gegenereerde banners weergegeven.

![ geproduceerde adocycle activa ](./images/prod-generated-banners.png)

- Open een nieuw tabblad en navigeer opnieuw naar AEM Assets. Navigeer vervolgens naar de map waarop we het verwerkingsprofiel hebben toegepast.

- Upload in de map de afbeelding waarvoor u een banner wilt maken door deze naar de browser te slepen of door op Maken te klikken. Kies in de rechterbovenhoek van de interface de optie Bestanden maken.

![ upload door belemmering in daling ](./images/prod-drag-drop-banner.png)

![ uploadt gebruikend creeer dossier ](./images/prod-create-file.png)


- Wacht een minuut tot uw element is verwerkt en laad vervolgens het scherm opnieuw. Als u uw middel in staat &quot;Nieuw&quot;ziet, weet u dat het klaar is verwerking.

![ activa in nieuwe staat ](./images/prod-asset-processed.png)

- Navigeer terug naar de vorige tab en laad ook hier het scherm opnieuw. Een nieuw element met de status &quot;Nieuw&quot; wordt weergegeven. Dit is onze gegenereerde banner, allemaal van de DAM! Zie je het nog niet? Wacht nog een minuut en laad het scherm opnieuw.

![ geproduceerde banner ](./images/prod-new-banner.png)

>[!NOTE]
>
> Niet tevreden met het resultaat? U kunt een ander verwerkingsprofiel toepassen op uw map en uw element opnieuw uploaden om een andere banner te genereren (of natuurlijk een ander middel te uploaden). Tijdens het opnieuw uploaden wordt u door het systeem gevraagd wat u met het bestaande element wilt doen. Selecteer &quot;Vervangen&quot;.
> ![bestaande vervangen ](./images/prod-replace-asset.png)

We hebben nu onze gegenereerde banner die we later kunnen gebruiken tijdens de uitvoering van onze campagne. Vergeet niet de banner te publiceren door deze te selecteren en vervolgens op de knop &quot;Quick Publish&quot; op het lint te klikken.

![ publiceer activa ](./images/prod-publish-banner.png)

## Follow-up in Workfront

Als je een formele en controleerbare beoordeling en goedkeuringsprocedure van je Assets nodig hebt, is Workfront de plaats om te zijn.

>[!NOTE]
>
> Hoewel we het hier expliciet noemen, is het de bedoeling om de taken in Workfront bij te werken nadat u ze hebt voltooid. U moet altijd streven naar een stroom Maken > Revisie > Goedkeuren.

- Laten we teruggaan naar ons project en de &#39;Go/No Go Banner Review&#39;-accordeon uitvouwen om de taak te openen door erop te klikken:

![ banner gaat/niet-gaat ](./images/banner-gonogo.png)

- Klik op de documentensectie van de taak (linkerkolom) en klik vervolgens op de aan AEM Assets gekoppelde map &#39;Final&#39;. Selecteer ons element door op de desbetreffende zone te klikken en op Proef maken te klikken. Een bewijs hiervan is de mogelijkheid om inhoud, bijvoorbeeld beeld, tekst, video, website, enz., op een gestructureerde en gezamenlijke manier te controleren, waarbij opmerkingen, correcties, wijzigingen van de betrokken belanghebbenden worden verzameld, versies en resultaten kunnen worden vergeleken en de definitieve versie met één klik kan worden goedgekeurd.

![ creeer proef ](./images/wf-create-proof.png)

- Als u een uitgebreid goedkeuringsproces wilt, selecteert u &quot;Geavanceerd bewijs&quot;.

![ geavanceerde proef ](./images/wf-advanced-proof.png)

>[!NOTE]
>
> We zullen handmatig beslissen wie ons bewijs in dit bootkamp zal bekijken en/of goedkeuren. In de meeste echte gebruiksgevallen gebruiken we een vooraf ingesteld model van goedkeuringsstroom(en) die al voor elk type bewijs is gedefinieerd.

- Standaard bevinden we ons in het workflowtype &#39;basic&#39; en we gaan uw Workfront Bootcampingspecialist selecteren als revisor en fiatteur. Typ de naam van de Workfront Specialist van Bootkamp waar staat: &#39;Typ de naam of het e-mailadres van de contactpersoon om een ontvanger toe te voegen:

![ wijs bewijs ](./images/wf-proof-assign.png) toe

![ wijs bewijs ](./images/wf-assign-proof-2.png) toe

- Stel deze in als Reviewer en fiatteur:

![ recensent en fiatteur ](./images/wf-review-approve.png)

- Klik op Proefdruk maken. Workfront zal enkele ogenblikken duren om de bewijzen te genereren:

![ producerend bewijs ](./images/wf-generating-proof.png)

- Je Workfront Specialist heeft nu een nieuwe kennisgeving ontvangen waarin ze weten dat ze een bewijs hebben om te beoordelen en/of goed te keuren:

![ werkfront taak ](./images/wf-proof-task.png)

- Nadat ze op de melding hebben geklikt, kunnen ze uw proefdruk bekijken en opmerkingen maken en/of deze proefdruk goedkeuren.

   - Als ze opmerkingen hebben, kunnen ze op Opmerking toevoegen boven aan het scherm klikken:

  ![ voeg commentaar ](./images/wf-proof-add-comment.png) toe

   - Vervolgens kunnen ze niet alleen opmerkingen toevoegen, maar ook de kleine pointerwerkbalk gebruiken om duidelijk te definiëren welk gebied moet worden gewijzigd.

  ![ PuntCommentaar van het Punt van het Punt ](./images/wf-proof-comment.png)

   - Door de opmerking toe te voegen, kunnen ze u laten weten dat u extra werk moet doen aan een nieuwe versie van de proefdruk. Vernieuw je Workfront tab en je krijgt een nieuwe melding met dit bericht. Als u eenmaal weet welke wijzigingen u moet aanbrengen, brengt u uw wijzigingen aan in AEM en uploadt u hier de nieuwe versie:

  ![ upload nieuwe versie ](./images/wf-upload-version.png)

   - Selecteer uw bijgewerkte element (als er geen wijzigingen nodig zijn in het opstartscenario, uploadt u gewoon hetzelfde element nogmaals) en klik op &#39;Koppelen&#39;:

  ![ verbindingsactiva ](./images/wf-link-new-asset.png)

   - Klik vervolgens aan de rechterkant op &#39;proefdruk maken&#39;.

  ![ creeer proef ](./images/create-new-proof.png)

   - Zodra de proefdruk is gegenereerd (dit kan even duren), ontvangt uw Workfront-specialist een melding en kan deze nieuwe versie bekijken en hopelijk goedkeuren.  Met de knop Vergelijking proef zien ze bijvoorbeeld een vergelijking naast elkaar van V1 en V2 met alle opmerkingen die zijn gemaakt.

  ![ proef vergelijk ](./images/wf-proof-compare.png)

  ![ maak besluit ](./images/make-decision-proof.png)

  ![ goedgekeurd ](./images/approved.png)

We hebben nu een formele goedkeuring voor het gebruik van onze banner. Het is gemakkelijk om te volgen waar in het proces wij zijn, en de updates u automatisch berichten teweegbrengt, zodat kunt u op een zo efficiënt mogelijke manier werken.

Volgende Stap: [ Fase 2 - Productie: Creeer sociale media en ](./social.md)

[Ga terug naar Fase 1 - Planning: Andere pre-work](../planning/prework.md)

[Terug naar alle modules](../../overview.md)
