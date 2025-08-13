---
title: Wijs een gefederaliseerd publiek aan S3 toe
seo-title: Map a federated audience to S3 | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Wijs een gefederaliseerd publiek aan S3 toe
description: In deze visuele oefening, zullen wij een federated publiek aan een stroomafwaartse bestemming van Real-Time CDP in kaart brengen om een gepersonaliseerde off-line ervaring te steunen.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-create-an-audience.jpg
hide: true
exl-id: a47b8f7b-7bd0-43a0-bc58-8b57d331b444
source-git-commit: a3c8d8b03472d01f491bf787ed647a696d3a5524
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---

# Wijs Federale Publiek aan S3 aan de Attributen van het Publiek van de Hefboomwerking voor Verrijking toe

U kunt publieksattributen in uw gegevenspakhuis hefboomwerking om de ervaring van uw publiek in stroomafwaartse activeringswerkschema&#39;s te verrijken gebruikend de bestemmingen van RTCDP. Voor SecurFinancial, kunnen deze gefederaliseerde attributen worden gebruikt om de het verpersoonlijkingservaring van het klantenpubliek offline te verbeteren. Hieronder wordt het gefedereerde publiek toegewezen aan een vooraf geconfigureerde Amazon S3-bestemming.

## Stappen

1. Navigeer aan het **portaal van Doelen**.

2. Klik het **3 punt menu** knoop naast de pre-gevormde bestemming van Amazon S3, dan klik **actief Soorten publiek**.

   ![ activeer-publiek ](assets/activate-audiences.png)

3. Selecteer de **S3 bestemming**, dan klik **daarna**.

   ![ uitgezocht-s3-bestemming ](assets/select-s3-destination.png)

4. Selecteer het juiste publiek. In ons voorbeeld: **SecureFinancial Klanten - Geen Leningen, het Goede publiek van de Krediet**.

   ![ selecteren-s3-publiek ](assets/select-s3-audience.png)

5. In **plannend** sectie, gebruik de standaardmontages en klik **daarna**.

6. In de **Afbeelding** stap, kies de deduplicatietoets. In ons voorbeeld, `xdm: personalEmail.address` is inbegrepen en geselecteerd als **De-duplicatie Sleutel**. Dan klik **daarna**:

   ![ deduplicatie-sleutel ](assets/deduplication-key.png)

7. In de afbeeldingsstap, uitgezochte verrijkingsattributen die op de afbeeldingen van het publieksgebied in de gefedereerde publiekssamenstelling worden gebaseerd. Klik het **potlood (geef uit)** pictogram om de pre-geselecteerde attributen te bekijken.

   ![ geef-attributen uit ](assets/edit-attributes.png)

   ![ definitief-attributen ](assets/final-attribution.png)

8. Herzie uw publiekstoewijzing en slag **Afwerking**.

>[**SAMENVATTING**]
>
> We hebben met succes een publiek gemaakt en het geactiveerd naar een S3-bestemming. Met de gebruikersvriendelijke interface van het platform kunnen marketingteams snel een publiek maken en activeren, waardoor tijd tot waarde wordt beperkt. Klanten die deze aanpak volgen, zijn in minder dan twee maanden in de eerste gebruikszaak geweest.

Wij zijn bereid om zich op [ te bewegen bouwend een reis ](build-journey-federated-audience.md).
