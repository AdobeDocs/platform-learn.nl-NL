---
title: Naamruimte configureren
description: Leer hoe u naamruimten configureert voor gebruik met Adobe Experience Platform Web SDK. Deze les maakt deel uit van de Zelfstudie Adobe Experience Cloud met Web SDK implementeren.
feature: Web SDK,Tags,Identities
exl-id: 7719dff4-6b30-4fa0-acae-7491c3208f15
source-git-commit: 4a12f8261cf1fb071bc70b6a04c34f6c16bcce64
workflow-type: tm+mt
source-wordcount: '692'
ht-degree: 1%

---

# Naamruimte configureren

Leer hoe u naamruimten configureert voor gebruik met Adobe Experience Platform Web SDK.

De [Adobe Experience Platform Identity Service](https://experienceleague.adobe.com/docs/id-service/using/home.html) Hiermee stelt u een gemeenschappelijke bezoeker-id in voor alle Adobe-oplossingen om de mogelijkheden van het Experience Cloud, zoals het delen van het publiek tussen oplossingen, te versterken. U kunt ook uw eigen klant-id&#39;s naar de service sturen, zodat u toepassingen op verschillende apparaten kunt zoeken en kunt integreren met andere systemen, zoals uw CRM-systeem (Customer Relationship Management).

Als uw website de Experience Cloud-id Service al op uw website gebruikt—via de Bezoeker-API of de de etiketuitbreiding van de Dienst van identiteitskaart van het Experience Cloud - en u zou het willen blijven gebruiken terwijl het migreren aan de SDK van het Web van Adobe Experience Platform, moet u de recentste versie van Bezoeker API of de de marktextensie van de Dienst van identiteitskaart van het Experience Cloud gebruiken. Zie [ID-migratie](https://experienceleague.adobe.com/docs/experience-platform/edge/identity/overview.html?lang=en) voor meer informatie .

>[!NOTE]
>
> Voor demonstratiedoeleinden, hebben de oefeningen in deze les u de identiteitsdetails van een fictieve klant vangen die in wordt geregistreerd [Luma-demo-site](https://luma.enablementadobe.com/content/luma/us/en.html) de referenties gebruiken, **gebruiker: test@adobe.com / password: test**. Terwijl u deze stappen kunt gebruiken om een verschillende identiteit voor uw eigen doeleinden tot stand te brengen, om de mogelijkheden van de Kaart van de Identiteit in de interface van de Inzameling van Gegevens te leren, wordt het geadviseerd eerst te volgen om de voorbeeldidentiteit te vangen.

## Leerdoelstellingen

Aan het eind van deze les, zult u kunnen:

* Naamruimten voor identiteiten begrijpen
* Een aangepaste naamruimte voor identiteit maken om een interne CRM-id vast te leggen


## Vereisten

U moet de vorige lessen reeds hebben voltooid:

* [Machtigingen configureren](configure-permissions.md)
* [Schema&#39;s configureren](configure-schemas.md)

>[!IMPORTANT]
>
>De [Extensie Experience Cloud-id](https://exchange.adobe.com/experiencecloud.details.100160.adobe-experience-cloud-id-launch-extension.html) is niet nodig bij het implementeren van Adobe Experience Platform Web SDK, aangezien de Web SDK JavaScript-bibliotheek van de Bezoeker ID-service functionaliteit bevat.

## Naamruimte maken

In deze oefening, creeert u een identiteitsnamespace voor het gebied van de douaneidentiteit van Luma, `lumaCrmId`. Identiteitsnaamruimten spelen een kritieke rol in de bouw van klantenprofielen in real time, aangezien twee passende waarden in zelfde namespace twee gegevensbronnen toestaan om een identiteitsgrafiek te vormen.

Voordat u de oefeningen start, bekijkt u deze korte video voor meer informatie over identiteit in Adobe Experience Platform:
>[!VIDEO](https://video.tv.adobe.com/v/27841?learn=on)

Maak nu een naamruimte voor de Luma CRM-id:

1. Open de [Interface voor gegevensverzameling](https://launch.adobe.com/){target="_blank"}
1. Selecteer de sandbox die u gebruikt voor de zelfstudie

   >[!NOTE]
   >
   >Als u de klant bent van een toepassing op basis van een platform, zoals Real-Time CDP, raden wij u aan een ontwikkelingssandbox voor deze zelfstudie te gebruiken. Als dat niet het geval is, gebruikt u de **[!UICONTROL Prod]** sandbox.

1. Selecteren **[!UICONTROL Identiteiten]** in de linkernavigatie
1. Selecteren **[!UICONTROL Bladeren]**

   In de hoofdinterface van de pagina wordt een lijst met naamruimten weergegeven met de namen, identiteitssymbolen, de datum die als laatste is bijgewerkt en of het standaardnaamruimten of aangepaste naamruimten zijn. De rechterspoorstaaf bevat informatie over de sterkte van de identiteitsgrafiek.

1. Selecteren **[!UICONTROL Naamruimte maken]**

   ![Identiteiten weergeven](assets/configure-identities-screen.png)

1. Geef de volgende gegevens op en selecteer **[!UICONTROL Maken]**.

   | Veld | Waarde |
   |---------------|-----------|
   | Weergavenaam | Luma CRM-id |
   | Identiteitssymbool | lumaCrmId |
   | Type | Apparaatoverschrijdende id |


   ![Naamruimten maken](assets/identities-create-namespace.png)


   De naamruimte Identiteit wordt gevuld in het dialoogvenster **[!UICONTROL Identiteiten]** scherm.

   ![Naamruimten maken](assets/configure-identities-namespace-lumaCrmId.png)


>[!INFO]
>
> In de [Gegevenselementen maken](create-data-elements.md) les, zult u leren hoe te om deze namespace te gebruiken wanneer het verzenden van identiteiten naar het Netwerk van de Rand van het Platform.

## Naamruimte maken in uw productiesandbox

Wegens een huidige beperking in de uitbreiding van SDK van het Web, moeten de identiteitsnamespaces ook in de productiesandbox worden gecreeerd om namespace te gebruiken om gegevens naar een ontwikkelingszandbak te verzenden. Als u dus een ontwikkelingssandbox hebt gebruikt voor deze zelfstudie, moet u ook de `Luma CRM ID` naamruimte in uw productiesandbox.

## Aanvullende bronnen

* [Identiteitsdocumentatie](https://experienceleague.adobe.com/docs/experience-platform/identity/home.html?lang=nl)
* [Identity Service API](https://www.adobe.io/experience-platform-apis/references/identity-service/)

Nu de identiteiten op zijn plaats zijn, kan de gegevensstroom worden gevormd.

[Volgende: ](configure-datastream.md)

>[!NOTE]
>
>Bedankt dat u tijd hebt geïnvesteerd in het leren over de SDK van Adobe Experience Platform Web. Als u vragen hebt, algemene feedback wilt delen of suggesties voor toekomstige inhoud wilt hebben, deelt u deze over deze [Experience League Communautaire discussiestuk](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-with-web/td-p/444996)
