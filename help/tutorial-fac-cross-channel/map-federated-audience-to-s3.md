---
title: Wijs een gefederaliseerd publiek aan S3 toe
seo-title: Map a federated audience to S3 | Unlock cross-channel insights with Federated Audience Composition
breadcrumb-title: Wijs een gefederaliseerd publiek aan S3 toe
description: In deze les, zullen wij een federated publiek aan een stroomafwaartse bestemming van Real-Time CDP in kaart brengen om een gepersonaliseerde off-line ervaring te steunen.
role: Data Architect, Data Engineer
jira: KT-18743
thumbnail: 18743-create-an-audience.jpg
hide: true
source-git-commit: b5611dccdba66d31f7dfcd96506e06d1bdd5fb3d
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---


# Wijs Federale Publiek aan S3 aan de Attributen van het Publiek van de Hefboomwerking voor Verrijking toe

In deze oefening, zult u leren hoe te hefboomwerkings publieksattributen in uw gegevenspakhuis om de ervaring van uw publiek in stroomafwaartse activeringswerkschema&#39;s te verrijken gebruikend de bestemmingen van RTCDP. Voor SecurFinancial, kunnen deze gefederaliseerde attributen worden gebruikt om de het verpersoonlijkingservaring van het klantenpubliek offline te verbeteren. In dit voorbeeld, zullen wij het gefedereerde publiek aan een pre-gevormde bestemming van Amazon S3 in kaart brengen.

## Stappen

1. Navigeer aan het **portaal van Doelen**.

2. Klik het **3 punt menu** knoop naast de pre-gevormde bestemming van Amazon S3, dan klik **actief Soorten publiek**.

   ![ activeer-publiek ](assets/activate-audiences.png)

3. Selecteer de **S3 bestemming**, dan klik **daarna**.

   ![ uitgezocht-s3-bestemming ](assets/select-s3-destination.png)

4. Selecteer de **klanten SecureFinancial - Geen Leningen, het Goede publiek van de Krediet**.

   ![ selecteren-s3-publiek ](assets/select-s3-audience.png)

5. In de **Plannende** sectie, verlaat alle standaardmontages en klik **daarna**.

6. In de **Afbeelding** stap, zorg ervoor `xdm: personalEmail.address` inbegrepen en geselecteerd als **Sleutel van de Deduplicatie** is. Dan klik **daarna**:

   ![ deduplicatie-sleutel ](assets/deduplication-key.png)

7. In de volgende toewijzingsstap kunt u verrijkingskenmerken selecteren op basis van toewijzingen van het doelveld in de gefederaliseerde publiekscompositie. Klik het **potlood (geef uit)** pictogram om de pre-geselecteerde attributen te bekijken.

   ![ geef-attributen uit ](assets/edit-attributes.png)

   ![ definitief-attributen ](assets/final-attribution.png)

8. Herzie uw publiekstoewijzing en slag **Afwerking**.

Wij zijn bereid om zich op [ te bewegen bouwend een reis ](build-journey-federated-audience.md).
