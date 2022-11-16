---
title: Een schema maken
description: Een schema maken
role: Developer
level: Intermediate
recommendations: noDisplay,noCatalog
kt: 10447
hide: true
hidefromtoc: true
exl-id: 25d77367-046d-46bd-9640-60fbcea263da
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 1%

---

# Een schema maken

Zoals besproken in [Gegevens structureren](../structuring-your-data.md)Gegevens die naar Adobe Experience Platform worden verzonden, moeten in XDM staan. Meer specifiek moeten uw gegevens overeenkomen met een _schema_. Een schema is in feite een beschrijving van hoe de gegevens eruit moeten zien. Hierin worden de namen van de velden beschreven en wordt aangegeven waar deze zich in de gegevens moeten bevinden. Het beschrijft ook het type waarde dat elk veld moet hebben (bijvoorbeeld een booleaanse waarde, een tekenreeks met een lengte van 12 tekens, een array van getallen).

Adobe Experience Platform biedt een aantal bouwstenen die buiten de doos liggen en die bekend staan als veldgroepen die in de branche veel voorkomen. Voor de financiële dienstensector zijn er bijvoorbeeld veldgroepen voor saldooverdrachten en kredietaanvragen. Voor de reis- en gastindustrie zijn er veldgroepen voor vluchten en reserveringen.

Wij adviseren u de ingebouwde gebiedsgroepen waar mogelijk te gebruiken wanneer het creëren van uw schema. We begrijpen ook dat u velden nodig hebt die specifiek zijn voor uw eigen bedrijf. Daarom kunt u uw eigen aangepaste veldgroepen maken die u kunt gebruiken binnen de schema&#39;s die u maakt.

Laten we doorlopen met het maken van een schema voor een typische e-commercewebsite.

Ga eerst naar de [!UICONTROL Schemas] bekijken in Adobe Experience Platform.

![Schemaweergave](../../../assets/implementation-strategy/schemas-view.png)

Selecteren [!UICONTROL Schema maken] in de rechterbovenhoek. Er wordt een menu weergegeven. Selecteren [!UICONTROL XDM ExperienceEvent].

Op dit punt, zou een dialoog moeten worden getoond vragend u welke gebiedsgroepen u aan uw schema wilt toevoegen. De eerste veldgroep die u moet selecteren, is de veldgroep met de naam [!UICONTROL AEP Web SDK ExperienceEvent]. Deze veldgroep voegt een set velden toe waarin automatisch gegevens worden opgenomen die door Adobe Experience Platform Web SDK worden verzameld.

![Mengsel van AEP Web SDK](../../../assets/implementation-strategy/aep-web-sdk-mixin.png)

Omdat de website voor deze zelfstudie een e-commercewebsite is, moet u ook de optie [!UICONTROL Handelsgegevens] veldgroep. Met deze groep kunt u typische handelsgegevens verzenden, zoals welke producten worden weergegeven, aan de winkelwagen worden toegevoegd en aangeschaft.

![Mengsel van handelsdetails](../../../assets/implementation-strategy/commerce-details-mixin.png)

Klik op de knop [!UICONTROL Veldgroepen toevoegen] rechtsboven in het dialoogvenster. Op dit punt, zou u de structuur van uw schema moeten zien.

![Schema met mengsels](../../../assets/implementation-strategy/schema-with-mixins.png)

De veldgroepen die u hebt toegevoegd, worden links weergegeven. Als u een veldgroep selecteert, worden aan de rechterkant de velden gemarkeerd die door die veldgroep zijn verschaft. Neem even de tijd om de beschikbare velden te verkennen.

Tot slot selecteert u [!UICONTROL Naamloos schema] links van het scherm geeft u een naam en een beschrijving rechts van het scherm op en klikt u op [!UICONTROL Opslaan].

![Schema met naam en beschrijving](../../../assets/implementation-strategy/schema-name-description.png)

Uw schema is gemaakt. Daarna, leren hoe te om een dataset tot stand te brengen om uw gegevens te houden.

Voor meer informatie over het creëren van schema&#39;s, zie [Een schema maken (UI)](https://experienceleague.adobe.com/docs/experience-platform/xdm/tutorials/create-schema-ui.html).
