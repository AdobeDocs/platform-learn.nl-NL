---
title: Wijs een Federale Publiek aan een S3 Bestemming toe
seo-title: Map a Federated Audience to an S3 Destination | Engage with audiences directly from your data warehouse using Federated Audience Composition
breadcrumb-title: Wijs een Federaal publiek aan S3 toe
description: In deze oefening, zullen wij een federated publiek aan een stroomafwaartse bestemming van Real-Time CDP in kaart brengen om een gepersonaliseerde off-line ervaring te steunen.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-create-an-audience.jpg
exl-id: a47b8f7b-7bd0-43a0-bc58-8b57d331b444
source-git-commit: 41298ea7c79a5b540c546be93dcb14201ce27ce3
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# Wijs een Federaal publiek aan een S3 bestemming aan hefboompublieksattributen voor verrijking toe

U kunt publieksattributen in uw gegevenspakhuis hefboomwerking om de ervaring van uw publiek in stroomafwaartse activeringswerkschema&#39;s te verrijken gebruikend de bestemmingen van RTCDP. Voor SecurFinancial, kunnen deze gefederaliseerde attributen worden gebruikt om de het verpersoonlijkingservaring van het klantenpubliek offline te verbeteren. Hieronder wordt het gefedereerde publiek toegewezen aan een vooraf geconfigureerde Amazon S3-bestemming.

## Stappen

1. Navigeer aan het **portaal van Doelen**.

2. Klik het **3 punt menu** knoop naast de pre-gevormde bestemming van Amazon S3, dan klik **actief Soorten publiek**.

   ![&#x200B; activeer-publiek &#x200B;](assets/activate-audiences.png)

3. Selecteer de **S3 bestemming**, dan klik **daarna**.

   ![&#x200B; uitgezocht-s3-bestemming &#x200B;](assets/select-s3-destination.png)

4. Selecteer het juiste publiek. In ons voorbeeld: **SecureFinancial Klanten - Geen Leningen, het Goede publiek van de Krediet**.

   ![&#x200B; selecteren-s3-publiek &#x200B;](assets/select-s3-audience.png)

5. In **plannend** sectie, gebruik de standaardmontages en klik **daarna**.

6. In de **Afbeelding** stap, kies de deduplicatietoets. In ons voorbeeld, `xdm: personalEmail.address` is inbegrepen en geselecteerd als **De-duplicatie Sleutel**. Dan klik **daarna**:

   ![&#x200B; deduplicatie-sleutel &#x200B;](assets/deduplication-key.png)

7. In de afbeeldingsstap, uitgezochte verrijkingsattributen die op de afbeeldingen van het publieksgebied in de gefedereerde publiekssamenstelling worden gebaseerd. Klik het **potlood (geef uit)** pictogram om de pre-geselecteerde attributen te bekijken.

   ![&#x200B; geef-attributen uit &#x200B;](assets/edit-attributes.png)

   ![&#x200B; definitief-attributen &#x200B;](assets/final-attribution.png)

8. Herzie uw publiekstoewijzing en slag **Afwerking**.

### OVERZICHT

We hebben met succes een publiek gemaakt en het geactiveerd naar een S3-bestemming. Elke andere oplossing kan dit publiek oppakken en onmiddellijk gebruiken. Met de gebruikersvriendelijke interface kunnen marketingteams snel een publiek maken en activeren zonder onderliggende gegevens te verplaatsen. Klanten die deze aanpak volgen, zijn in ongeveer een maand LIVE gaan met hun eerste gebruiksgeval.


Nu zullen wij [&#x200B; een reis &#x200B;](build-journey-federated-audience.md) bouwen.
