---
title: Naamruimte configureren
description: Leer hoe u naamruimten configureert voor gebruik met Adobe Experience Platform Web SDK. Deze les maakt deel uit van de zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Web SDK,Identities
jira: KT-15400
exl-id: 7719dff4-6b30-4fa0-acae-7491c3208f15
source-git-commit: d73f9b3eafb327783d6bfacaf4d57cf8881479f7
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# Naamruimte configureren

Leer hoe u naamruimten configureert voor gebruik met Adobe Experience Platform Web SDK.

De [ Dienst van de Identiteit van Adobe Experience Cloud ](https://experienceleague.adobe.com/nl/docs/id-service/using/home) plaatst een gemeenschappelijke bezoekersidentiteitskaart (ECID) over op SDK-Gebaseerde toepassingen van Adobe aan macht Experience Cloud mogelijkheden zoals publiek-deel tussen toepassingen. U kunt ook uw eigen klant-id&#39;s naar de service sturen, zodat u toepassingen op verschillende apparaten kunt zoeken en kunt integreren met andere systemen, zoals uw CRM-systeem (Customer Relationship Management).

De [ Dienst van de Identiteit van Adobe Experience Platform ](https://experienceleague.adobe.com/nl/docs/experience-platform/identity/home) (ja, zijn er twee!) gebruikt ECIDs en klant IDs om identiteitsgrafieken te produceren, toestaand u om attributen en gedrag in de Profielen van de Klant in real time samen te voegen.

>[!NOTE]
>
>Een douaneidentiteit namespace wordt _vereist_ niet om Adobe Analytics, Adobe Target, of Adobe Audience Manager met het Web SDK uit te voeren (de voor authentiek verklaarde identiteiten kunnen in het `data` voorwerp in plaats van het `xdm` voorwerp worden overgegaan aangezien u later zult zien). Identiteitsnaamruimten zijn vereist voor platformonafhankelijke toepassingen zoals Journey Optimizer, Real-Time Customer Data Platform en Customer Journey Analytics. Terwijl u kunt besluiten om een identiteitsnamespace in uw eigen implementatie niet te gebruiken, wordt u geacht dit als deel van dit leerprogramma te doen.

>[!NOTE]
>
> Voor demonstratiedoeleinden, hebben de oefeningen in deze les u de identiteitsdetails van een fictieve klant vangen die in de [ Plaats van de Demo van de Luma ](https://luma.enablementadobe.com/content/luma/us/en.html) wordt geregistreerd gebruikend de geloofsbrieven, **gebruiker: `test@test.com` / wachtwoord: test**.

## Leerdoelstellingen

Aan het eind van deze les, zult u kunnen:

* Naamruimten voor identiteiten begrijpen
* Een aangepaste naamruimte voor identiteit maken om een interne CRM-id vast te leggen


## Vereisten

U moet de vorige lessen reeds hebben voltooid:

* [Schema&#39;s configureren](configure-schemas.md)

>[!IMPORTANT]
>
>De [ Uitbreiding van identiteitskaart van Experience Cloud ](https://exchange.adobe.com/apps/ec/100160/adobe-experience-cloud-id-launch-extension) is niet nodig wanneer het uitvoeren van SDK van het Web van Adobe Experience Platform, aangezien de bibliotheek van JavaScript van het Web de dienstfunctionaliteit van identiteitskaart van de Bezoeker bevat.
>
> Als uw website de Experience Cloud-id-service al op uw website gebruikt (via de Bezoeker-API of de extensie voor de Experience Cloud-id-service) en u wilt deze blijven gebruiken wanneer u naar Adobe Experience Platform Web SDK migreert, moet u de nieuwste versie van de Bezoeker-API of de Experience Cloud ID Service-tagextensie gebruiken. Zie [ Migratie van identiteitskaart ](https://experienceleague.adobe.com/nl/docs/experience-platform/edge/identity/overview) voor meer informatie.

## Naamruimte maken

In deze oefening, creeert u een identiteitsnaamruimte voor het gebied van de douaneIdentiteit van Luma, `lumaCrmId`. Identiteitsnaamruimten spelen een kritieke rol in de bouw van klantenprofielen in real time, aangezien twee passende waarden in zelfde namespace twee gegevensbronnen toestaan om een identiteitsgrafiek te vormen.

Voordat u de oefeningen start, bekijkt u deze korte video voor meer informatie over identiteit in Adobe Experience Platform:

>[!VIDEO](https://video.tv.adobe.com/v/27841?learn=on&enablevpops)

Maak nu een naamruimte voor de Luma CRM-id:

1. Open de [ interface van de Inzameling van Gegevens ](https://experience.adobe.com/data-collection/){target="_blank"}
1. Selecteer de sandbox die u gebruikt voor de zelfstudie

   >[!NOTE]
   >
   >Als u de klant bent van een toepassing op basis van een platform, zoals Real-Time CDP of Journey Optimizer, raden we u aan een ontwikkelingssandbox voor deze zelfstudie te gebruiken. Als u dat niet doet, gebruikt u de **[!UICONTROL Prod]** -sandbox.

1. Selecteren **[!UICONTROL Identities]** in de linkernavigatie
1. Selecteren **[!UICONTROL Browse]**

   In de hoofdinterface van de pagina wordt een lijst met naamruimten weergegeven met de namen, identiteitssymbolen, de datum die als laatste is bijgewerkt en of het standaardnaamruimten of aangepaste naamruimten zijn. De rechtertrack bevat informatie over [!UICONTROL Identity graph strength] .

1. Selecteren **[!UICONTROL Create identity namespace]**

   ![ Identiteiten van de Mening ](assets/configure-identities-screen.png)

1. Geef de volgende gegevens op en selecteer **[!UICONTROL Create]** .

   | Veld | Waarde |
   |---------------|-----------|
   | Weergavenaam | Luma CRM-id |
   | Identiteitssymbool | lumaCrmId |
   | Type | Individuele apparaat-id |


   ![ creeer Namespaces ](assets/identities-create-namespace.png)


   De naamruimte Identiteit wordt in het scherm **[!UICONTROL Identities]** gevuld.

   ![ creeer Namespaces ](assets/configure-identities-namespace-lumaCrmId.png)


>[!NOTE]
>
> In [ creeer Identiteiten ](create-identities.md) les, zult u leren hoe te om dit te gebruiken namespace wanneer het verzenden van identiteiten naar Platform Edge Network.

Nu de identiteiten op zijn plaats zijn, kan de gegevensstroom worden gevormd.

[Volgende: ](configure-datastream.md)

>[!NOTE]
>
>Bedankt dat je tijd hebt geïnvesteerd in het leren over Adobe Experience Platform Web SDK. Als u vragen hebt, algemene terugkoppelen wilt delen, of suggesties over toekomstige inhoud hebben, gelieve hen op deze [ Communautaire besprekingspost van Experience League te delen ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-data/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
