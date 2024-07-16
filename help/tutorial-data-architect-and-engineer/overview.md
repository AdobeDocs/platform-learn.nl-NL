---
title: Aan de slag met Adobe Experience Platform voor Data Architects en Data Engineers
description: Ga aan de slag met Adobe Experience Platform voor Data Architects en Data Engineers.
breadcrumb-title: Overzicht
role: Data Architect, Data Engineer
jira: KT-4348
thumbnail: 4348-overview.jpg
recommendations: catalog, noDisplay
last-substantial-update: 2023-06-21T00:00:00Z
exl-id: fabbc591-840b-40dc-89af-305626a16338
source-git-commit: efef0389cedfec7dfa19d876df96c58b7463ee12
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 0%

---

# Aan de slag met Adobe Experience Platform voor Data Architects en Data Engineers

<!--5min-->

_Begonnen het Worden met Adobe Experience Platform voor de Architecten van Gegevens en de Ingenieurs van Gegevens_ is het perfecte uitgangspunt om hands-on met Experience Platform te krijgen.


<!--How do we address ETL-->

## Leerdoelen

De Architecten van gegevens en de Ingenieurs van Gegevens moeten nauw samenwerken voor een succesvolle plaatsing van het Experience Platform. Dit hands-on leerprogramma leert u de belangrijkste taken die door _worden uitgevoerd beide rollen_ zodat weet u hoe te beginnen Platform voor uw eigen zaken uit te voeren. U zult door oefeningen worden geleid die u aan de belangrijkste terminologie, eigenschappen, interface, en APIs van Experience Platform zullen introduceren. Klanten van Adobe Experience Cloud-toepassingen zoals Real-time Customer Data Platform, Customer Journey Analytics en Journey Optimizer zullen deze inhoud ook nuttig vinden, omdat de platformservices essentiële fundamenten van deze toepassingen vormen.

![ de marktectuur die van Adobe Experience Cloud de diensten van het Platform benadrukt in dit leerprogramma-identiteit, Profiel, Segmentatie, Opname, Vraag, en Governance ](assets/marketecture.png) worden behandeld

Onderwerpen zijn onder meer:

* Gebruikersmachtigingen configureren
* Sandboxen maken
* Een Developer Console-project instellen en de platform-API gebruiken
* Gegevensbeheer—inclusief het maken van schema&#39;s, gegevenssets, identiteiten, samenvoegbeleid en gegevensbeheer
* Gegevensinvoer met batch- en streaming-modi
* Webgegevens vastleggen met Adobe Experience Platform Web SDK
* Klantprofielen voor realtime samenstellen
* De Dienst van de Vraag gebruiken om gegevens te bevestigen en gegevens te halen
* Segmenten samenstellen

## Bedrijfscenario

Adobe Experience Platform is een technisch platform dat u helpt marketingdoelstellingen te bereiken. De zaken van het bedrijfsgebruik zouden moeten drijven hoe u ontwerpt en de technologie uitvoert. Deze zelfstudie richt zich op een fictief handelsmerk, Luma genaamd. Luma is actief in baksteen- en mortierwinkels in meerdere landen en heeft ook een online aanwezigheid met een website en mobiele apps. Ze investeren in Adobe Experience Platform om loyaliteitsgegevens, CRM-, web- en offlineaankoopgegevens te combineren in realtime klantprofielen en activeren deze profielen om hun marketing naar het volgende niveau te tillen. De bedrijfsdoelstellingen van Luma kunnen of niet met de doelstellingen van uw bedrijf richten, maar u zou de hands-on stappen in dit leerprogramma aan uw eigen bedrijfsdoelstellingen moeten kunnen verbinden.

## Voorwaarden

* U hebt de [ Inleiding aan de cursus van Adobe Experience Platform ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-U-1-2020.1) op Experience League voltooid en bent vertrouwd met de mogelijkheden van het Platform
* U hebt toegang tot een account die is ingericht voor Adobe Experience Platform (of een op een platform gebaseerde toepassing zoals Real-Time CDP of Journey Optimizer) en gegevensverzameling (voorheen Starten).
* U bent een Beheerder van het Systeem van die rekening of kan één [ hebben gebruikerstoestemmingen ](configure-permissions.md) voor u vormen.

## Deze zelfstudie gebruiken

Deze zelfstudie combineert taken voor zowel gegevensengineers als gegevensarchitecten. Aangezien het een inleidende-vlakke zelfstudie is, zou u de taken voor beide rollen moeten kunnen voltooien. Omdat veel van de lessen voortbouwen op wat in vroegere lessen werd uitgevoerd, zou u door de lessen in orde moeten bewegen. Ik zal u vragen welke lessen kunnen worden overgeslagen.

Terwijl u tijdens deze zelfstudie verschillende platformelementen maakt, kunt u proberen om de namen die ik aanbeveel zoveel mogelijk te gebruiken. Nochtans, zijn er een paar high-level elementennamen die u kunt willen aanpassen voor het geval dat er veelvoudige mensen bij uw organisatie zijn die deze zelfstudie gelijktijdig nemen. U kunt bijvoorbeeld de sandbox Platform de naam geven van &#39;&#39;Luma Tutorial Platform - Ignatius J Reilly&#39;&#39; in plaats van alleen &#39;&#39;Luma Tutorial Platform&#39;&#39;.

Als u geplakt wordt, probeer eerst de instructies opnieuw te lezen, en dan het ![ Logboek en de kwestie ](https://experienceleague.adobe.com/assets/img/feedback.svg) verbinding op sidebar van elke pagina te gebruiken om me te contacteren.

## Technische noten

### Sandboxomgevingen

In de zelfstudie maakt u een sandboxomgeving en gebruikt u deze om de oefeningen te voltooien. De zandbakomgeving maakt het voor u veilig om de oefeningen te voltooien en te experimenteren zonder zich zorgen te maken over het in gevaar brengen van uw productiegegevens.

### API

Platform is in eerste instantie een API. Hoewel de interfacewerkschema&#39;s voor alle belangrijke werkschema&#39;s van het Platform bestaan en hoofdzakelijk zullen worden gebruikt, bevat het leerprogramma sommige API-georiënteerde oefeningen. Ik zal u door de basisprojectopstelling in Adobe Developer Console begeleiden en u van [!DNL Postman] milieu&#39;s en inzamelingen voorzien om met Platform API te beginnen. Nadat u de zelfstudie hebt voltooid, vindt u het misschien handig om bekend te zijn met de platform-API en deze te gebruiken in uw eigen implementatie.

### Technologieën van derden

Hoewel u in deze zelfstudie meerdere technologieën gebruikt, blijft u vrijwel volledig binnen het ecosysteem van de Adobe. In uw eigen implementatie van het Platform zult u Platform met specifieke derdetechnologieën waarschijnlijk integreren. Om dit leerprogramma relevant voor alle klanten te houden, zullen wij een generischere implementatie gebruiken.

## Updates van zelfstudie

* Juni 2023: Bijgewerkt om nieuw werkschema van de Toestemming te omvatten en de referentie van Server-aan-Server API van OAuth te gebruiken


Nu beweging op de eerste les - [ vormt toestemmingen ](configure-permissions.md).
