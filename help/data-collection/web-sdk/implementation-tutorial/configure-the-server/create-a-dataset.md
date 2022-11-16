---
title: Een gegevensset maken
description: Een gegevensset maken
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
kt: 10447
hide: true
hidefromtoc: true
exl-id: 7705d292-a29c-4977-bcc6-f088a51713ea
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 3%

---

# Een gegevensset maken

Naast het beschrijven van de gegevens die u naar Adobe Experience Platform verzendt, hebt u een plaats nodig om de gegevens te handhaven. In Adobe Experience Platform worden deze emmers waar u gegevens kunt plaatsen, gegevenssets genoemd.

Om een dataset tot stand te brengen, navigeer aan [!UICONTROL Gegevenssets] bekijken in Adobe Experience Platform.

![Gegevens, weergave](../../../assets/implementation-strategy/datasets-view.png)

Klikken [!UICONTROL Gegevensset maken] in de rechterbovenhoek.

Tijdens het proces voor het maken van de gegevensset selecteert u [!UICONTROL Gegevensset maken van schema] en selecteert u [het schema dat u eerder hebt gemaakt](create-a-schema.md).

![Schema selecteren](../../../assets/implementation-strategy/schema-selection.png)

Klikken [!UICONTROL Volgende] en geef een naam en een beschrijving.

![Naam en beschrijving van gegevensset](../../../assets/implementation-strategy/dataset-name-description.png)

Klikken [!UICONTROL Voltooien]. Uw dataset is gecreeerd en is klaar om gegevens te ontvangen.

Terwijl u gegevens naar een gegevensset gaat verzenden, zal Adobe Experience Platform valideren dat de gegevens die u in de gegevensset wilt plaatsen, overeenkomen met het toegepaste schema. Als de gegevens niet met het schema in overeenstemming zijn, worden de gegevens verworpen en niet geplaatst in de dataset. Als gevolg van deze valideringsstap kunnen de gebruikers van de gegevensset (Adobe-producten, derden of uw eigen bedrijf) enige mate van zekerheid hebben met betrekking tot de structuur en de zuiverheid van de gegevens in de gegevensset.

Voor meer informatie over het creëren van datasets, zie [UI-gids voor gegevensbestanden](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/user-guide.html?lang=nl).
