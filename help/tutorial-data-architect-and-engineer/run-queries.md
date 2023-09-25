---
title: Zoekopdrachten uitvoeren
seo-title: Run queries | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Zoekopdrachten uitvoeren
description: In deze les zult u leren om, vragen te plaatsen te schrijven en uit te voeren om de gegevens te bevestigen u hebt opgenomen.
role: Data Architect, Data Engineer
feature: Queries
jira: KT-4348
thumbnail: 4348-run-queries.jpg
exl-id: a37531cb-96ad-4547-86af-84f7ed65f019
source-git-commit: 00ef0f40fb3d82f0c06428a35c0e402f46ab6774
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 2%

---

# Zoekopdrachten uitvoeren

<!-- 15 min-->
In deze les, zult u leren om, vragen te plaatsen te schrijven en uit te voeren om de gegevens te bevestigen u hebt opgenomen.

Met de Adobe Experience Platform Query Service kunt u uw gegevens begrijpen door standaard SQL te gebruiken voor query&#39;s op gegevens in het Platform. Gebruikend de Dienst van de Vraag, kunt u zich bij om het even welke dataset in het meer van Gegevens aansluiten en de vraagresultaten vangen als nieuwe dataset voor gebruik in rapportering, machine het leren, of voor opname in het Profiel van de Klant in real time.

**Gegevensarchitecten** en **Gegevensengineers** zal de vraagdienst buiten dit leerprogramma moeten gebruiken.

Alvorens u met de oefeningen begint, bekijk deze korte video om meer over de Dienst van de Vraag te leren:
>[!VIDEO](https://video.tv.adobe.com/v/29795?learn=on)

## Vereiste machtigingen

In de [Machtigingen configureren](configure-permissions.md) les, plaatst u opstelling alle toegangscontroles die worden vereist om deze les te voltooien.

<!-- Settings > **[!UICONTROL Services]** > **[!UICONTROL Query Service]**
* Permission items Data Management > **[!UICONTROL View Datasets]** and  **[!UICONTROL Manage Datasets]**
* Permission item Sandboxes > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` product profile
-->

## Eenvoudige query&#39;s

Laten we beginnen met enkele eenvoudige vragen:

1. Ga in de gebruikersinterface van het Platform naar **Zoekopdrachten** in de linkernavigatie
1. Selecteer de **Query maken** knop rechtsboven om een tekstvak te openen voor het uitvoeren en uitvoeren van query&#39;s
1. Voer de volgende query in de editor in en druk op Shift+Enter of Shift+Return om de query uit te voeren.

   ```
   SHOW TABLES
   ```

1. Hier wordt de lijst met beschikbare tabellen weergegeven

   ![TABELquery TONEN](assets/queries-showTables.png)


1. Probeer deze query nu uit en vervang `_techmarketingdemos` met uw eigen huurder namespace, die, als u zich herinnert, in uw schema&#39;s zichtbaar is.

   ```
   SELECT person.name.lastName,loyalty.tier
   FROM luma_loyalty_dataset
   WHERE loyalty.tier ='gold'
   ```

   ![Gegevens SELECTEREN uit de gegevensset loyaliteit](assets/queries-loyaltySelect.png)

1. Als er een fout optreedt, worden gedetailleerde berichten weergegeven in het dialoogvenster **[!UICONTROL Console]** tab, zoals hieronder afgebeeld
   ![Fout in de query](assets/queries-error.png)

1. Met uw succesvolle vraag, **[!UICONTROL Naam]** het `Luma Gold Level Customers`
1. Selecteer de **[!UICONTROL Opslaan]** knop
   ![De query opslaan](assets/queries-loyaltySelect-save.png)


<!--SELECT COUNT(DISTINCT (_techmarketingdemos.systemIdentifier.loyaltyId)) FROM luma_loyalty_dataset 


SELECT _techmarketingdemos.systemIdentifier.loyaltyId, COUNT(_techmarketingdemos.systemIdentifier.loyaltyId)
FROM luma_loyalty_dataset 
GROUP BY _techmarketingdemos.systemIdentifier.loyaltyId
HAVING COUNT(_techmarketingdemos.systemIdentifier.loyaltyId) > 1;-->

## Aanvullende oefeningen

De extra oefeningen van de Dienst van de Vraag zullen aan het leerprogramma op een recentere datum worden toegevoegd.
<!--
## Join Datasets

In this exercise, we will join two datasets `Luma Loyalty Dataset` and `Luma Offline Purchase` to get list of gold customers who have spend over $500 dollars in one purchase.

1. Create a new query
1. Copy and paste following query in query editor and execute, again replacing `_techmarketingdemos` with your own tenant namespace
    
    ```
    SELECT DISTINCT lopd.commerce.order.purchaseID as PurchaseId ,
        lld.person.name.firstName as LastName ,
        lld.person.name.lastName as LastName ,
        lopd.personalEmail.address as email,
        lopd.commerce.order.priceTotal as Total

    FROM luma_loyalty_dataset lld
    JOIN luma_offline_purchase_event_dataset lopd
    ON lopd._techmarketingdemos.systemIdentifier.loyaltyId = lld._techmarketingdemos.systemIdentifier.loyaltyId

    WHERE lld._techmarketingdemos.loyalty.level ='gold' AND lopd.commerce.order.priceTotal >500;
    ```

1. You should get list of Gold Customers who have spend over $500 in single purchase.

## Output datasets

1. Select on Output Dataset button
1. Provide name and description to the dataset
1. Save.
1. Go to **Datasets** under **Data Management** to find new dataset created.

-->
<!--Add content for Adobe Defined Functions-->

## Aanvullende bronnen

* [Documentatie bij Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=nl)
* [API-naslagservice](https://www.adobe.io/experience-platform-apis/references/query-service/)

En nu voor de laatste praktische les, [segmenten maken](build-segments.md)!
