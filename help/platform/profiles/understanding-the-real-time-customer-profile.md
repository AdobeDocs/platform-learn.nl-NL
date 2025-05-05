---
title: Klantprofiel in realtime
description: In deze video wordt uitgelegd hoe Adobe Experience Platform realtime profielen van klanten samenstelt en bijwerkt en hoe u deze profielen kunt openen en gebruiken.
feature: Profiles
role: Data Engineer, Data Architect, Developer
level: Beginner
jira: KT-2701
thumbnail: 27251.jpg
exl-id: 6ef5b589-f874-4687-bee3-9650c993f383
source-git-commit: 112e092df6d486d8b9103013bec57d820b8ae6d7
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# Overzicht van het realtime klantprofiel

In deze video wordt uitgelegd hoe Adobe Experience Platform realtime profielen van klanten samenstelt en bijwerkt en hoe u deze profielen kunt openen en gebruiken. Voor meer informatie, gelieve de [ documentatie van het Profiel van de Klant in real time ](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=nl) te bezoeken.

>[!VIDEO](https://video.tv.adobe.com/v/27251?learn=on&enablevpops)

## Architectuur en functies

<!-- CARDS
* overview-diagram.md
* create-merge-policies.md
* union-schemas-overview.md
* create-a-computed-attribute-for-sum-of-purchases.md
-->
<!-- START CARDS HTML - DO NOT MODIFY BY HAND -->
<div class="columns">
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Overview Diagram of Real-Time Customer Profile">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="overview-diagram.md" title="Overzicht Diagram van het Profiel van de Klant in real time" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="https://video.tv.adobe.com/v/33600?format=jpeg&nocache=1740415066741" alt="Overzicht Diagram van het Profiel van de Klant in real time"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="overview-diagram.md" target="_blank" rel="referrer" title="Overzicht Diagram van het Profiel van de Klant in real time"> Diagram van het Overzicht van het Profiel van de Klant in real time </a>
                    </p>
                    <p class="is-size-6">Deze video bespreekt u een overzichtsdiagram dat het vermogen van het Profiel van de Klant in real time van Adobe Experience Platform illustreert.</p>
                </div>
                <a href="overview-diagram.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold"> Leer meer </span>
                </a>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Create merge policies">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="create-merge-policies.md" title="Samenvoegbeleid maken" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="https://video.tv.adobe.com/v/330433?format=jpeg&nocache=1740415066765" alt="Samenvoegbeleid maken"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="create-merge-policies.md" target="_blank" rel="referrer" title="Samenvoegbeleid maken"> creeer fusiebeleid </a>
                    </p>
                    <p class="is-size-6">In deze video wordt getoond hoe u in Adobe Experience Platform beleid voor samenvoegen kunt maken. Het beleid van de fusie is de regels die het Platform gebruikt om te bepalen welke gegevens zullen worden gebruikt en aan prioriteit worden gegeven wanneer het combineren van datasets van ongelijksoortige bronnen, om klantenprofielen tot stand te brengen.</p>
                </div>
                <a href="create-merge-policies.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold"> Leer meer </span>
                </a>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Union schemas overview">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="union-schemas-overview.md" title="Overzicht van uniale schema&apos;s" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="https://video.tv.adobe.com/v/329940?format=jpeg&nocache=1740415066755" alt="Overzicht van uniale schema&apos;s"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="union-schemas-overview.md" target="_blank" rel="referrer" title="Overzicht van uniale schema&apos;s"> schema's van de Unie overzicht </a>
                    </p>
                    <p class="is-size-6">Het profiel van de Klant in real time machtigt kanaalpersonalisatie door schaal door elke fase van de klantenreis. Batch- of streaming-gegevens kunnen worden ingeschakeld voor het realtime klantprofiel door zowel het schema als de bijbehorende gegevensset in te schakelen.</p>
                </div>
                <a href="union-schemas-overview.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold"> Leer meer </span>
                </a>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Create a computed attribute for the sum of purchases">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="create-a-computed-attribute-for-sum-of-purchases.md" title="Een berekend kenmerk maken voor de som van aankopen" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="https://video.tv.adobe.com/v/3443557?format=jpeg&nocache=1740415066775&captions=dut" alt="Een berekend kenmerk maken voor de som van aankopen"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="create-a-computed-attribute-for-sum-of-purchases.md" target="_blank" rel="referrer" title="Een berekend kenmerk maken voor de som van aankopen"> creeer een gegevens verwerkt attribuut voor de som aankopen </a>
                    </p>
                    <p class="is-size-6">Leer hoe u berekende kenmerken kunt gebruiken om de aankoopbedragen van een gebruiker in meerdere verkoopkanalen op te tellen.</p>
                </div>
                <a href="create-a-computed-attribute-for-sum-of-purchases.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold"> Leer meer </span>
                </a>
            </div>
        </div>
    </div>
</div>
<!-- END CARDS HTML - DO NOT MODIFY BY HAND -->

## Profielgegevens invoegen en beheren

<!-- CARDS
* bring-data-into-the-real-time-customer-profile.md
* delete-profiles.md
* update-a-specific-attribute-with-upsert.md
-->
<!-- START CARDS HTML - DO NOT MODIFY BY HAND -->
<div class="columns">
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Bring Data into Real-Time Customer Profile">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="bring-data-into-the-real-time-customer-profile.md" title="Gegevens in realtime-klantprofiel plaatsen" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="https://video.tv.adobe.com/v/27301?format=jpeg&nocache=1740415067018" alt="Gegevens in realtime-klantprofiel plaatsen"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="bring-data-into-the-real-time-customer-profile.md" target="_blank" rel="referrer" title="Gegevens in realtime-klantprofiel plaatsen"> breng Gegevens in Echt - het Profiel van de Klant - tijd </a>
                    </p>
                    <p class="is-size-6">Het profiel van de Klant in real time machtigt kanaalpersonalisatie door schaal door elke fase van de klantenreis. Batch- of streaming-gegevens kunnen worden ingeschakeld voor het realtime klantprofiel door zowel het schema als de bijbehorende gegevensset in te schakelen.</p>
                </div>
                <a href="bring-data-into-the-real-time-customer-profile.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold"> Leer meer </span>
                </a>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Delete profiles">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="delete-profiles.md" title="Profielen verwijderen" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="https://video.tv.adobe.com/v/3429807/?format=jpeg&nocache=1740415067005" alt="Profielen verwijderen"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="delete-profiles.md" target="_blank" rel="referrer" title="Profielen verwijderen"> de profielen van de Schrapping </a>
                    </p>
                    <p class="is-size-6">Leer hoe u gegevens uit het profielarchief kunt verwijderen met de realtime-API voor klantprofiel. Met de profiel-API kunt u gegevens verwijderen uit het profielarchief zonder dat dit van invloed is op het datumpigment of de identiteitsgrafiek. Dit kan nuttig zijn wanneer het oplossen van problemen van de identiteitsgrafiek en het verbeteren van occasionele fouten in gegevensopname die slechts een paar profielen beïnvloeden.</p>
                </div>
                <a href="delete-profiles.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold"> Controle </span>
                </a>
            </div>
        </div>
    </div>
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="Update specific profile attributes using `upsert`">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="update-a-specific-attribute-with-upsert.md" title="Specifieke profielkenmerken bijwerken met behulp van &quot;upsert&quot;" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="https://video.tv.adobe.com/v/3443447/?format=jpeg&nocache=1740415067029&captions=dut" alt="Specifieke profielkenmerken bijwerken met behulp van &quot;upsert&quot;"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="update-a-specific-attribute-with-upsert.md" target="_blank" rel="referrer" title="Specifieke profielkenmerken bijwerken met behulp van &quot;upsert&quot;"> werk specifieke profielattributen bij gebruikend "upsert &grave; </a>
                    </p>
                    <p class="is-size-6">Leer hoe u een specifiek kenmerk van een profiel kunt bijwerken met de functie 'upsert' van Adobe Experience Platform.</p>
                </div>
                <a href="update-a-specific-attribute-with-upsert.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold"> Controle </span>
                </a>
            </div>
        </div>
    </div>
</div>
<!-- END CARDS HTML - DO NOT MODIFY BY HAND -->

## Accountprofielen

<!-- CARDS
* view-account-profiles.md
-->
<!-- START CARDS HTML - DO NOT MODIFY BY HAND -->
<div class="columns">
    <div class="column is-half-tablet is-half-desktop is-one-third-widescreen" aria-label="View account profiles">
        <div class="card" style="height: 100%; display: flex; flex-direction: column; height: 100%;">
            <div class="card-image">
                <figure class="image x-is-16by9">
                    <a href="view-account-profiles.md" title="Accountprofielen weergeven" target="_blank" rel="referrer">
                        <img class="is-bordered-r-small" src="https://video.tv.adobe.com/v/3446583?format=jpeg&nocache=1740415067214&captions=dut" alt="Accountprofielen weergeven"
                             style="width: 100%; aspect-ratio: 16 / 9; object-fit: cover; overflow: hidden; display: block; margin: auto;">
                    </a>
                </figure>
            </div>
            <div class="card-content is-padded-small" style="display: flex; flex-direction: column; flex-grow: 1; justify-content: space-between;">
                <div class="top-card-content">
                    <p class="headline is-size-6 has-text-weight-bold">
                        <a href="view-account-profiles.md" target="_blank" rel="referrer" title="Accountprofielen weergeven"> de rekeningsprofielen van de Mening </a>
                    </p>
                    <p class="is-size-6">Leer hoe u accountprofielen kunt weergeven in Real-Time CDP B2B edition.</p>
                </div>
                <a href="view-account-profiles.md" target="_blank" rel="referrer" class="spectrum-Button spectrum-Button--outline spectrum-Button--primary spectrum-Button--sizeM" style="align-self: flex-start; margin-top: 1rem;">
                    <span class="spectrum-Button-label has-no-wrap has-text-weight-bold"> Leer meer </span>
                </a>
            </div>
        </div>
    </div>
</div>
<!-- END CARDS HTML - DO NOT MODIFY BY HAND -->