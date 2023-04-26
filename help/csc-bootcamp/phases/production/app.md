---
title: CSC Bootkamp - Mobiele app-inhoud maken
description: CSC Bootkamp - Mobiele app-inhoud maken
doc-type: multipage-overview
source-git-commit: 989e4e2add1d45571462eccaeebcbe66a77291db
workflow-type: tm+mt
source-wordcount: '1156'
ht-degree: 0%

---

# Mobiele app-inhoud maken

## Wat is de levering van inhoud zonder kop?

Met een systeem voor inhoudsbeheer zonder kop zijn de back-end en frontend nu ontkoppeld. Het onderdeel zonder kop is de achterkant van de inhoud, omdat een CMS zonder kop een back-end alleen inhoudsbeheersysteem is, dat expliciet is ontworpen en gebouwd als een opslagplaats voor inhoud die inhoud toegankelijk maakt via een API, voor weergave op elk apparaat.

De front-end, die onafhankelijk van elkaar wordt ontwikkeld en onderhouden, haalt inhoud van de headless backend op met behulp van een Content Delivery API, typisch in formaat JSON. Dit kan bijvoorbeeld een webtoepassing zijn of in ons geval een mobiele toepassing.

Voor een CMS-achtergrond zonder kop is meestal de structuur van de inhoud vereist op basis van een model of schema. Hierdoor kunnen clienttoepassingen de juiste inhoud aanvragen voor het renderen van een ervaring. Sommige CMS kunnen, net als AEM, zowel gestructureerde als niet-gestructureerde inhoud in JSON-indeling toegankelijk maken.

Een zeer belangrijk kenmerk van deze topologie is dat de inhoud die door het hoofd CMS in formaat JSON wordt gediend zuivere inhoud, zonder ontwerp of lay-outinformatie is. In een CMS-implementatie zonder kop blijft alle opmaak en lay-out behouden door de ontkoppelde frontendtoepassing.

Een zeer belangrijk voordeel van een koploze topologie CMS is de capaciteit om inhoud over veelvoudige kanalen opnieuw te gebruiken, die verschillende cliënt-zij frontend implementaties kunnen gebruiken. Dit kan het vooruitstrevende ontwikkelingsproces efficiënter maken. Maar het betekent ook dat het ontwikkelingsproces van de frontendervaring zeer code en IT-centric kan worden, waarbij IT in wezen de ervaring bezit.

## Hoe werkt de levering van inhoud zonder kop in AEM?

AEM as a Cloud Service is een flexibel hulpmiddel voor het implementatiemodel zonder kop door drie krachtige functies te bieden:

![Levering van inhoud zonder kop](./images/prod-app-headless.png)

1. Inhoudsmodellen
   - Inhoudsmodellen zijn een gestructureerde weergave van inhoud.
   - Inhoudsmodellen worden gedefinieerd door informatiearchitecten in de AEM Content Fragment Model-editor.
   - Inhoudsmodellen dienen als basis voor inhoudsfragmenten.
1. Inhoudsfragmenten
   - Inhoudsfragmenten worden gemaakt op basis van een inhoudsmodel.
   - Gemaakt door auteurs van inhoud met de AEM Content Fragment-editor.
   - Inhoudsfragmenten worden opgeslagen in AEM Assets en beheerd in de interface voor middelenbeheer.
1. Inhoud-API voor levering
   - De AEM GraphQL API ondersteunt de levering van inhoudsfragmenten.
   - De AEM Assets REST-API ondersteunt CRUD-bewerkingen voor inhoudsfragmenten.
   - Directe levering van inhoud is ook mogelijk met de [JSON-export van de Content Fragment Core-component](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=en).

## Uitoefening

Voor dit bootkamp richten we ons op het &quot;content&quot;-gedeelte - het is immers de toeleveringsketen van content die we nastreven. We hebben al een inhoudsmodel en de vereiste API&#39;s voor levering voorzien, zodat u zich kunt richten op wat belangrijk is.

Laten we eerst ons inhoudsmodel bekijken: het is het &#39;contract&#39; dat we hebben met het &#39;headless CMS&#39;, dus we weten welke inhoud ons kan bereiken en in welke vorm.

- Ga naar de AEM auteur op [https://author-p105462-e991028.adobeaemcloud.com/](https://author-p105462-e991028.adobeaemcloud.com/) en meld u aan met de gegevens die we hebben verstrekt.

- Selecteer in het menu AEM Start de optie Gereedschappen \> Algemeen \> Modellen van inhoudsfragmenten

![menu met inhoudsfragmentmodellen](./images/prod-app-cfm.png)

- Op het volgende scherm krijgt u een overzicht van alle sites die inhoud zonder kop gebruiken. Dit staat u toe om bestuur over veelvoudige hoofdloze plaatsen te houden, zonder het moeten vrezen zij zich met elkaar zullen mengen. In ons geval werken we met onze website van Adobe, dus selecteer dat model.

![verschillende headless plaatsen](./images/prod-app-cfm-folder.png)

- In deze map kunnen we technische inhoud zonder kop zien die we gebruiken op de website van Adobe. Wil je meer weten? Voel je vrij om uit te reiken. Laten we ons nu concentreren op de taak voordat we de handen ineenslaan: de mobiele app. Houd de muisaanwijzer boven de Homepage van de Mobile App en klik op het potloodpictogram om het inhoudsmodel te openen.

![homepage-inhoudsmodel mobiele app](./images/prod-app-created-cfm.png)

- In de Editor van het inhoudsfragmentmodel ziet u de details van een bepaald inhoudsmodel. In ons geval zien we de homepage van onze mobiele app: het Adobe-logo, een kop, een optionele, gratis tekst en een optioneel product. Al deze punten zijn gemakkelijk te vormen en bij te werken, zodat als uw inhoudsmodel extra elementen nodig heeft, dit zonder ontwikkelaarsinterferentie op CMS kant kan worden gedaan.

![detailinhoudsmodel](./images/prod-app-cfm-details.png)

>[!WARNING]
>
> **Houd er rekening mee dat het wijzigen van het inhoudsmodel implicaties heeft die verder omlaag gaan**, omdat de mobiele toepassing bepaalde informatie moet ontvangen om de juiste elementen te kunnen weergeven. Wees extra voorzichtig wanneer u velden bijwerkt of verwijdert, maar het toevoegen van velden heeft geen effect.

Nu we een idee hebben van waar onze inhoud van moet bestaan, kunnen we ons inhoudfragment maken.

- Klik op AEM logo in de linkerbovenhoek om de navigatie te openen en navigeer vervolgens naar Navigatie \> Inhoudsfragmenten.

![inhoudsfragmenten, menuoptie](./images/prod-cf-ui.png)

- In de volgende interface krijgt u een overzicht van alle bestaande inhoud binnen AEM. De filters aan de linkerkant kunnen worden gebruikt om omlaag te versmallen als u naar een specifiek inhoudsfragment zoekt. Als u een nieuw inhoudsfragment wilt maken, klikt u rechtsboven op de knop Maken.

![knop Inhoudsfragment maken](./images/prod-app-create-cf.png)

- In de modus die wordt geopend, ziet u dat sommige velden nog niet bewerkbaar zijn. Dit is logisch: verschillende modellen zijn beschikbaar op basis van waar we het fragment maken .
   ![inhoudsfragment maken](./images/prod-app-create-cf-details.png)
   - Selecteer eerst waar het fragment wordt gemaakt door op het mappictogram naast het veld Locatie te klikken. Vouw de structuur van de inhoud uit door op de mappen &quot;adocycle&quot; \> &quot;en&quot; \> &quot;mobile-app&quot; te klikken en vervolgens uw selectie te bevestigen door op de knop &quot;Choose&quot; te klikken.
      ![de juiste locatie selecteren](./images/prod-app-folder.png)
   - Het veld &quot;Inhoudsfragmentmodel&quot; kan nu worden bewerkt. Klik op de pijl naast het veld om het vervolgkeuzemenu te openen en selecteer het inhoudsmodel dat we eerder hebben bekeken: &quot;startpagina van mobiele toepassing&quot;.
   - Geef uw inhoudsfragment vervolgens een betekenisvolle titel (tip: neemt uw teamnummer op om uw inhoud gemakkelijk terug te vinden). U zult merken dat het veld Naam automatisch wordt ingevuld. Dit is om uw leven makkelijker te maken: het is de naam die het systeem gebruikt om uw fragment te identificeren en mag niet worden aangeraakt.
   - Klik ten slotte op de knop &quot;Maken en openen&quot;. Deze knop geeft aan dat het inhoudsfragment wordt gemaakt en wordt geopend zodat u het direct kunt bewerken.

- Hier kan uw team bepalen welke inhoud u wilt weergeven in de mobiele app. ![details inhoudsfragment](./images/prod-cf-details.png)
   - Selecteer uw team nr., zodat u uw inhoud later in de mobiele app kunt controleren.
   - Als u afbeeldingselementen wilt selecteren, klikt u op het mappictogram om in AEM Assets naar de juiste afbeelding te bladeren.
   - Voor het aanbevolen product klikt u op het pictogram voor productopzoeking zodat u eenvoudig ons &quot;Adobe-product 1&quot; kunt selecteren, zodat de gegevens over de handel in de app worden geladen.
   - Klik op de knop Opslaan als u klaar bent om alle geschreven inhoud op te slaan en uw wijzigingen te publiceren.
      ![publicatiewijzigingen](./images/prod-app-publish.png)

Nu we de mobiele app met wat inhoud hebben voorzien, zijn we klaar om onze campagne te leveren.


Volgende stap: [Fase 3 - Levering: Mobiele app verifiëren](../delivery/app.md)

[Ga terug naar Fase 2 - Productie: Een advertentie voor sociale media maken](./social.md)

[Terug naar alle modules](../../overview.md)
