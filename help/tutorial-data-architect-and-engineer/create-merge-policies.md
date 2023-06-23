---
title: Samenvoegbeleid maken
seo-title: Create merge policies | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Samenvoegbeleid maken
description: In deze les, zult u samenvoegbeleid creëren om te bepalen hoe de gegevens in profielen samenvoegen.
role: Data Architect, Data Engineer
feature: Profiles
jira: KT-4348
audience: data architect
doc-type: tutorial
activity: implement
thumbnail: 4348-create-merge-policies.jpg
exl-id: ec862bb2-7aa2-4157-94eb-f5af3a94295f
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '996'
ht-degree: 0%

---

# Samenvoegbeleid maken

<!--20 min-->

In deze les, zult u samenvoegbeleid tot stand brengen om voorrang te geven aan hoe de veelvoudige gegevensbronnen in profielen samenvoegen.

Met Adobe Experience Platform kunt u gegevens uit meerdere bronnen samenbrengen en combineren om een volledig beeld van elke afzonderlijke klant te krijgen. Bij het samenbrengen van deze gegevens, bepaalt het samenvoegbeleid hoe aan de gegevens prioriteit wordt gegeven en welke gegevens worden gecombineerd om die verenigde mening tot stand te brengen.

We blijven bij de gebruikersinterface voor deze les, maar API-opties bestaan ook voor het maken van samenvoegbeleid.

**Gegevensarchitecten** moet een samenvoegbeleid maken buiten deze zelfstudie.

Voordat u met de oefeningen begint, bekijkt u deze korte video voor meer informatie over het samenvoegbeleid:
>[!VIDEO](https://video.tv.adobe.com/v/330433?quality=12&learn=on)

## Vereiste machtigingen

In de [Machtigingen configureren](configure-permissions.md) les, plaatst u opstelling alle toegangscontroles die worden vereist om deze les te voltooien.

<!--* Permission items **[!UICONTROL Profile Management]** > **[!UICONTROL View Merge Policies]** and **[!UICONTROL Manage Merge Policies]**
* Permission item **[!UICONTROL Profile Management]** > **[!UICONTROL View Profiles]** and **[!UICONTROL Manage Profiles]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
-->

## Over het samenvoegingsbeleid en Unieschema

U kunt zich herinneren, in de les over partijopname, uploadden wij twee verslagen met lichtjes verschillende informatie voor de zelfde klant. In de [!DNL Loyalty] gegevens, de voornaam van de klant was `Daniel` en hij leefde in `New York City`, maar in de CRM-gegevens was de voornaam van de klant `Danny` en hij leefde in `Portland`. Wijzigingen in klantgegevens in de loop der tijd. Misschien is hij van `Portland` tot `New York City`. Ook andere dingen veranderen, zoals telefoonnummers en e-mailadressen. Met samenvoegingsbeleid kunt u bepalen hoe deze soorten conflicten moeten worden afgehandeld wanneer twee gegevensbronnen verschillende informatie voor dezelfde gebruiker geven.

Waarom? `Danny` win out as the first name ? Laten we eens kijken:

1. Selecteer in de gebruikersinterface van het Platform de optie **[!UICONTROL Profielen]** in de linkernavigatie
1. Ga naar de **[!UICONTROL Beleid samenvoegen]** tab
1. Het standaardbeleid voor samenvoegen is geordende tijdstempel. Omdat u de CRM-gegevens na de Loyalty-gegevens hebt geüpload, `Danny` wordt weergegeven als voornaam in het profiel:

![Scherm Beleid samenvoegen](assets/mergepolicies-default.png)

Wanneer meerdere schema&#39;s zijn ingeschakeld voor het profiel, wordt een [!UICONTROL Unieschema] wordt automatisch gemaakt voor alle voor profielen ingeschakelde recordschema&#39;s die een basisklasse delen. U kunt de [!UICONTROL Unieregelingen] door naar de **[!UICONTROL Unieschema]** tab.

![Scherm Beleid samenvoegen](assets/mergepolicies-unionSchema.png)

Merk op dat er geen verenigingsschema voor de klasse ExperienceEvent is. ExperienceEvent-gegevens blijven in het profiel staan, omdat het tijdreeksen zijn, elke gebeurtenis een tijdstempel en id bevat en botsingen geen probleem zijn.

Wat gebeurt er als dat standaardsamenvoegbeleid u niet bevalt? Wat als Luma beslist hun CRM-systeem de bron van de waarheid zou moeten zijn als er een conflict is? Daarvoor zullen we een fusiebeleid ontwikkelen.

## Een samenvoegbeleid maken in de gebruikersinterface

1. Selecteer in het scherm Beleid samenvoegen de optie **[!UICONTROL Samenvoegbeleid maken]** knop rechtsboven
1. Als de **[!UICONTROL Naam]**, enter `Loyalty Prioritized`
1. Als de **[!UICONTROL Schema]**, selecteert u **[!UICONTROL XDM-profiel]** (aangezien de aangepaste klasse recordgegevens bevat, is de aangepaste klasse ook beschikbaar voor samenvoegbeleidsregels)
1. Voor **[!UICONTROL Id-instelling]**, selecteert u **[!UICONTROL Privégrafiek]**
1. Voor **[!UICONTROL Kenmerksamenvoeging]**, selecteert u **[!UICONTROL Dataset-prioriteit]**
1. Slepen en neerzetten `Luma Loyalty Dataset` en `Luma CRM Dataset` aan de **[!UICONTROL Gegevensset]** deelvenster.
1. Controleer of `Luma Loyalty Dataset` is bovenaan door te slepen en neer te zetten boven de `Luma CRM Dataset`
1. Selecteer **[!UICONTROL Opslaan]** knop
   <!--do i need to explain Private Graph? Is that GA?-->
   ![Samenvoegingsbeleid](assets/mergepolicies-newPolicy.png)

## Het samenvoegingsbeleid valideren

Laten we eens kijken of het fusiebeleid doet wat we zouden verwachten:

1. Ga naar de **[!UICONTROL Bladeren]** tab
1. Wijzig de **[!UICONTROL Samenvoegbeleid]** aan uw nieuwe `Loyalty Prioritized` beleid
1. Als de **[!UICONTROL Naamruimte identiteit]**, gebruik uw `Luma CRM Id`
1. Als de **[!UICONTROL Identiteitswaarde]** gebruiken `112ca06ed53d3db37e4cea49cc45b71e`
1. Selecteer **[!UICONTROL Profiel weergeven]** knop
1. `Daniel` is terug!

![Een profiel weergeven met een ander samenvoegbeleid](assets/mergepolicies-lookupProfileWithMergePolicy.png)

## Een samenvoegbeleid met beperkte gegevenssets maken

Wanneer het creëren van beleid van de Fusie gebruikend datasetbelangrijkheid, slechts zijn de datasets van de zelfde basisklasse die u in het recht omvat inbegrepen in het profiel. Laten we een ander samenvoegingsbeleid instellen

1. Selecteer in het scherm Beleid samenvoegen de optie **[!UICONTROL Samenvoegbeleid maken]** knop rechtsboven
1. Als de **[!UICONTROL Naam]**, enter  `Loyalty Only`
1. Als de **[!UICONTROL Schema]**, selecteert u **[!UICONTROL XDM-profiel]**
1. Voor **[!UICONTROL Id-instelling]**, selecteert u **[!UICONTROL Geen]**
1. Voor **[!UICONTROL Kenmerksamenvoeging]**, selecteert u **[!UICONTROL Dataset-prioriteit]**
1. Alleen slepen en neerzetten `Luma Loyalty Dataset` tot **[!UICONTROL Geselecteerde gegevensset]** deelvenster.
1. Selecteer **[!UICONTROL Opslaan]** knop

![Beleid voor alleen-geldigheids samenvoegen](assets/mergepolicies-loyaltyOnly.png)

## Het samenvoegingsbeleid valideren

Laten we nu eens kijken wat dit samenvoegbeleid doet:

1. Ga naar de **[!UICONTROL Bladeren]** tab
1. Wijzig de **[!UICONTROL Samenvoegbeleid]** aan uw nieuwe `Loyalty Only` beleid
1. Als de **[!UICONTROL Naamruimte identiteit]**, gebruik uw `Luma CRM Id`
1. Als de **[!UICONTROL Identiteitswaarde]** gebruiken `112ca06ed53d3db37e4cea49cc45b71e`
1. Selecteer **[!UICONTROL Profiel weergeven]** knop
1. Bevestig dat er geen profielen zijn gevonden:
   ![Alleen Loyalty is geen CRM-id-opzoekopdracht.](assets/mergepolicies-loyaltyOnly-noCrmLookup.png)

CRM-id is een identiteitsveld in het dialoogvenster `Luma Loyalty Dataset`, maar alleen primaire identiteiten kunnen worden gebruikt om profielen op te zoeken. Laten we dus het profiel opzoeken met de primaire identiteit. `Luma Loyalty Id`&quot;

1. Wijzig de **[!UICONTROL Naamruimte van identiteit]** tot `Luma Loyalty Id`
1. Als de **[!UICONTROL Identiteitswaarde]** gebruiken `5625458`
1. Selecteer **[!UICONTROL Profiel weergeven]** knop
1. Selecteer profiel-id om het profiel te openen
1. Ga naar de **[!UICONTROL Attributen]** tab
1. Andere profieldetails van de dataset van CRM, zoals het mobiele telefoonaantal en e-mailadres niet beschikbaar zijn omdat wij slechts
   ![CRM-gegevens kunnen niet worden weergegeven in het alleen-geldigheidbeleid](assets/mergepolicies-loyaltyOnly-attributes.png)
1. Ga naar de **[!UICONTROL Gebeurtenissen]** tab
1. De gegevens van ExperienceEvent zijn beschikbaar ondanks niet uitdrukkelijk het opnemen in de datasets van het fusiebeleid:
   ![Gebeurtenissen kunnen worden weergegeven in het beleid Alleen logo](assets/mergepolicies-loyaltyOnly-events.png)

## Meer informatie over samenvoegingsbeleid

Wijzig in de profielzoekopdracht het samenvoegbeleid waarnaar u teruggaat `Default Timebased` en selecteert u de **[!UICONTROL Profiel weergeven]** knop. Danny is terug!

![Een profiel weergeven met een ander samenvoegbeleid](assets/mergepolicies-backToDanny.png)

Wat is hier aan de hand? Welnu, het samenvoegen van profielen is niet één keer. De de klantenprofielen van de in real time worden verzameld op de vlucht, die op diverse factoren wordt gebaseerd, met inbegrip van welk fusieprincipe wordt gebruikt. U kunt meerdere samenvoegbeleidsregels maken om in verschillende contexten te gebruiken, afhankelijk van de weergave van de klant die u wilt gebruiken.

Een belangrijke reden voor samenvoegbeleid is gegevensbeheer. Stel bijvoorbeeld dat u gegevens van derden in een Platform invoert die niet kunnen worden gebruikt voor gevallen van verpersoonlijkingsgebruik, maar _kan_ worden gebruikt voor reclamedoeleinden. U kunt een fusiebeleid tot stand brengen dat deze derde dataset sluit en dit fusiebeleid gebruiken om segmenten voor uw het advertentiegebruikgevallen te bouwen.

## Aanvullende bronnen

* [Documentatie voor samenvoegingsbeleid](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/overview.html)
* [API voor samenvoegingsbeleid (onderdeel van Real-Time Customer Profile API)](https://www.adobe.io/experience-platform-apis/references/profile/#tag/Merge-policies)

Laten we nu verder gaan naar de [gegevensbeheerkader](apply-data-governance-framework.md).
