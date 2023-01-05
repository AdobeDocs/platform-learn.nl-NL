---
title: Inleiding | Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe u een Adobe Target-implementatie migreert van at.js 2.x naar Adobe Experience Platform Web SDK. De onderwerpen omvatten het laden van de bibliotheek JavaScript, het verzenden van parameters, het teruggeven activiteiten, en andere opmerkelijke callouts.
recommendations: catalog,noDisplay
source-git-commit: dad7a1b01c4313d6409ce07d01a6520ed83f5e89
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# Doel migreren van at.js 2.x aan het Web SDK van het Platform

Deze gids is voor ervaren implementatoren van Adobe Target leren hoe te om een implementatie at.js aan het Web SDK van Adobe Experience Platform te migreren.

Adobe Experience Platform Web SDK is een JavaScript-bibliotheek aan de clientzijde waarmee Adobe Experience Cloud-klanten via het Adobe Experience Platform Edge Network kunnen communiceren met Experience Cloud-services. Deze nieuwe bibliotheek combineert de mogelijkheden van de afzonderlijke Adobe-toepassingsbibliotheken tot één lichtgewichtpakket dat de nieuwe Adobe Experience Platform-functies ten volle kan benutten.

## Belangrijkste voordelen

Enkele voordelen van het Web SDK van het Platform in vergelijking met de standalone bibliotheek at.js omvatten:

* Sneller delen van publiek van [Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html)
* Doel integreren met Journey Optimizer ter ondersteuning [Levering offer decisioning](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html)
* Gebruiksmogelijkheden [eersteklas id&#39;s](https://experienceleague.adobe.com/docs/platform-learn/data-collection/edge-network/generate-first-party-device-ids.html) om de ECID te genereren voor bezoekersidentificatie van langere duur
* Consolidatie van netwerkaanroepen in Adobe-toepassingen
* Een kleinere voetafdruk voor verbeterde afmetingen voor de paginasnelheid
* Een nauwere integratie met Adobe Analytics die niet afhankelijk is van het koppelen van informatie van afzonderlijke netwerkoproepen
* Extra implementatieflexibiliteit voor ontwikkelaars

Het grootste voordeel van migreren is waarschijnlijk voor klanten van Real-time Customer Data Platform. Real-Time CDP biedt enorme mogelijkheden voor publieksopbouw op basis van het volledige scala aan gegevens die in het Experience Platform worden opgenomen en de mogelijkheid om in realtime klantprofielen te maken. Een ingebouwd kader voor gegevensbeheer automatiseert verantwoord gebruik van die gegevens. Met AI van de klant kunt u eenvoudig modellen voor machinaal leren gebruiken voor het samenstellen van eigenschappen en churn-modellen waarvan de uitvoer naar Adobe Target kan worden gedeeld. Tot slot kunnen klanten van de optionele toevoegingen aan de gezondheidszorg en het privacyschild de functie voor het afdwingen van toestemming gebruiken om de voorkeuren voor toestemming van individuele klanten eenvoudig af te dwingen. De SDK van het Web van het Platform is een vereiste om deze eigenschappen RTCDP in uw Webkanaal te gebruiken.

## Leerdoelstellingen

Aan het einde van deze zelfstudie kunt u het volgende doen:

* Begrijp de de implementatieverschillen van het Doel tussen at.js en het Web SDK van het Platform
* De eerste configuratie voor de doelfunctionaliteit instellen
* Upgrade de bibliotheek at.js naar Platform Web SDK
* Composeractiviteiten op basis van formulieren en visuele ervaringen renderen
* Parameters doorgeven aan doel
* Conversiegebeurtenissen bijhouden
* Ondersteuning voor verschillende domeinen inschakelen
* Soorten publiek en profielscripts bijwerken
* De implementatie valideren
* Debug Target Experience levering


## Vereisten

Als u deze zelfstudie wilt voltooien, moet u eerst:

* Heb een technisch inzicht in uw huidige implementatie van Target at.js
* Zorg ervoor dat u beschikt over een [De rol Editor of Uitgever](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html#section_8C425E43E5DD4111BBFC734A2B7ABC80) voor uw doelinstantie zodat u zelf voorbeelden kunt proberen
* Installeer de [Adobe Experience Cloud Visual Editing Helper-browserextensie](https://experienceleague.adobe.com/docs/target/using/experiences/vec/troubleshoot-composer/visual-editing-helper-extension.html) voor Google Chrome
* Weet hoe u activiteiten kunt opzetten in Adobe Target. Als u een herhaling nodig hebt, zijn de volgende zelfstudies en hulplijnen handig voor deze les:
   * [De composer voor visuele ervaring gebruiken](https://experienceleague.adobe.com/docs/target-learn/tutorials/experiences/use-the-visual-experience-composer.html)
   * [De Form-Based Experience Composer gebruiken](https://experienceleague.adobe.com/docs/target-learn/tutorials/experiences/use-the-form-based-experience-composer.html)
   * [Gericht op ervaring maken](https://experienceleague.adobe.com/docs/target-learn/tutorials/activities/create-experience-targeting-activities.html)

Wanneer u klaar bent, is de eerste stap naar een geslaagde migratie: [meer informatie over het migratieproces](migration-overview.md) en hoe te.js en het Web SDK van het Platform verschillen.

>[!NOTE]
>
>Wij zijn geëngageerd om u met uw migratie van het Doel van at.js aan Web SDK te helpen succesvol zijn. Als u problemen ondervindt met uw migratie of als u denkt dat er essentiële informatie ontbreekt in deze handleiding, kunt u het ons laten weten door te posten in [deze communautaire discussie](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996).