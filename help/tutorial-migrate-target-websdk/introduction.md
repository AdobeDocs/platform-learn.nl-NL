---
title: Doel migreren van at.js 2.x naar Web SDK
description: Leer hoe u een Adobe Target-implementatie migreert van at.js 2.x naar Adobe Experience Platform Web SDK. De onderwerpen omvatten het laden van de bibliotheek van JavaScript, het verzenden van parameters, het teruggeven activiteiten, en andere opmerkelijke callouts.
last-substantial-update: 2023-02-23T00:00:00Z
exl-id: c8920fde-ad6b-4f2d-a35f-ce865b35bba0
source-git-commit: d6471c8e383e22fed4ad5870952d0d0470f593db
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 0%

---

# Doel migreren van at.js 2.x naar Platform Web SDK

Deze gids is voor ervaren implementatoren van Adobe Target leren hoe te om een implementatie at.js aan het Web SDK van Adobe Experience Platform te migreren.

Adobe Experience Platform Web SDK is een client-side JavaScript-bibliotheek waarmee klanten van Adobe Experience Cloud via de Adobe Experience Platform-Edge Network kunnen communiceren met services van Experiencen Cloud. Deze nieuwe bibliotheek combineert de mogelijkheden van de afzonderlijke toepassingsbibliotheken van de Adobe tot één lichtgewichtpakket dat de nieuwe Adobe Experience Platform-functies ten volle kan benutten.


>[!NOTE]
>
>Soortgelijke migratiezelfstudies zijn beschikbaar voor:
>
> * [ Adobe Analytics ](../tutorial-migrate-analytics-websdk/migration-to-websdk-overview.md)
> * [ Adobe Audience Manager ](https://experienceleague.adobe.com/nl/docs/audience-manager/user-guide/migrate-to-web-sdk/appmeasurement-to-web-sdk)

>[!CAUTION]
>
> Omdat het Web SDK van het Platform veelvoudige Adobe toepassingen steunt, zouden alle bibliotheken van de Adobe op een bepaalde pagina tezelfdertijd moeten worden gemigreerd. Bijvoorbeeld, wordt een gemengde implementatie van Web SDK voor Doel en AppMeasurement voor Analytics op één enkele pagina _niet gesteund_. Nochtans, wordt een gemengde implementatie over verschillende pagina&#39;s gesteund, bijvoorbeeld Web SDK op pagina A, en at.js met AppMeasurement op pagina B.



## Belangrijkste voordelen

Enkele voordelen van het Web SDK van het Platform in vergelijking met de standalone bibliotheek at.js omvatten:

* Sneller het delen van publiek van [ Real-time Customer Data Platform ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html)
* Het integreren Doel met Journey Optimizer om [ levering van de Offer decisioning te steunen ](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html)
* Capaciteit om [ eerste-partijids ](https://experienceleague.adobe.com/docs/platform-learn/data-collection/edge-network/generate-first-party-device-ids.html) te gebruiken om ECID voor langere duur bezoekersidentificatie te produceren
* Een kleinere voetafdruk voor verbeterde afmetingen voor de paginasnelheid
* Extra implementatieflexibiliteit voor ontwikkelaars

Het grootste voordeel van migratie voor klanten van Target is waarschijnlijk de integratie met Real-time Customer Data Platform. Real-Time CDP biedt enorme mogelijkheden voor publieksopbouw op basis van het volledige scala aan gegevens die in het Experience Platform worden opgenomen en de mogelijkheid om in realtime een klantprofiel te maken. Een ingebouwd kader voor gegevensbeheer automatiseert verantwoord gebruik van die gegevens. Met AI van de klant kunt u eenvoudig modellen voor machinaal leren gebruiken voor het samenstellen van eigenschappen en churn-modellen waarvan de uitvoer naar Adobe Target kan worden gedeeld. Tot slot kunnen klanten van de optionele toevoegingen aan de gezondheidszorg en het privacyschild de functie voor het afdwingen van toestemming gebruiken om de voorkeuren voor toestemming van individuele klanten eenvoudig af te dwingen. Platform Web SDK is een vereiste om deze Real-Time CDP-functies in uw webkanaal te kunnen gebruiken.

## Leerdoelstellingen

Aan het einde van deze zelfstudie kunt u het volgende doen:

* Begrijp de de implementatieverschillen van het Doel tussen at.js en Platform Web SDK
* De eerste configuratie voor de doelfunctionaliteit instellen
* Upgrade de at.js-bibliotheek naar Platform Web SDK
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
* Verzeker u een [ Redacteur of rol van de Uitgever ](https://experienceleague.adobe.com/docs/target/using/administer/manage-users/enterprise/properties-overview.html#section_8C425E43E5DD4111BBFC734A2B7ABC80) voor uw instantie van het Doel hebt zodat kunt u voorbeelden op uw eigen proberen
* Weet hoe u activiteiten kunt opzetten in Adobe Target. Als u een herhaling nodig hebt, zijn de volgende zelfstudies en hulplijnen handig voor deze les:
   * [ Gebruik Composer van de Visuele Ervaring ](https://experienceleague.adobe.com/docs/target-learn/tutorials/experiences/use-the-visual-experience-composer.html)
   * [ gebruik de op vorm-Gebaseerde Composer van de Ervaring ](https://experienceleague.adobe.com/docs/target-learn/tutorials/experiences/use-the-form-based-experience-composer.html)
   * [ creeer ervaring richtend Activiteiten ](https://experienceleague.adobe.com/docs/target-learn/tutorials/activities/create-experience-targeting-activities.html)

Zodra u klaar bent, moet de eerste stap aan een succesvolle migratie [ over het migratieproces ](migration-overview.md) leren en hoe at.js en het Web SDK van het Platform verschillen.

>[!NOTE]
>
>We helpen u graag succesvol te zijn met uw doelmigratie van at.js naar Web SDK. Als u in obstakels met uw migratie loopt of als er kritieke informatie ontbreekt in deze gids voelt, gelieve ons te vertellen door in [ deze communautaire bespreking ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-migrate-target-from-at-js-to-web-sdk/m-p/575587#M463) te posten.
