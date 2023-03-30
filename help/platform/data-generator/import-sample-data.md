---
title: Voorbeeldgegevens importeren naar Adobe Experience Platform
description: Leer hoe u een Experience Platform-sandboxomgeving instelt met voorbeeldgegevens.
role: Developer
feature: API
kt: 7349
thumbnail: 7349.jpg
exl-id: da94f4bd-0686-4d6a-a158-506f2e401b4e
source-git-commit: a04bd682ff8d16981700598d9eef8db94c0ea568
workflow-type: tm+mt
source-wordcount: '1752'
ht-degree: 0%

---

# Voorbeeldgegevens importeren naar Adobe Experience Platform

Leer hoe u een Experience Platform-sandboxomgeving instelt met voorbeeldgegevens. Met behulp van een Postman-verzameling kunt u veldgroepen, schema&#39;s, gegevenssets maken en vervolgens voorbeeldgegevens importeren in Experience Platform.

## Voorbeeld van gebruik van gegevens

Zakelijke gebruikers van Experience Platforms moeten vaak een reeks stappen doorlopen die het identificeren van veldgroepen, het creëren van schema&#39;s, het voorbereiden van gegevens, het creëren van datasets, en dan het opnemen van gegevens omvatten alvorens zij de marketing mogelijkheden kunnen onderzoeken die door Experience Platform worden aangeboden. In deze zelfstudie worden enkele stappen geautomatiseerd, zodat u gegevens zo snel mogelijk in een sandbox met Platforms kunt ophalen.

Deze zelfstudie richt zich op een fictief, handelsmerk genaamd Luma. Zij investeren in Adobe Experience Platform om loyaliteit, CRM, productcatalogus en offline aankoopgegevens te combineren in realtime klantprofielen en activeren deze profielen om hun marketing naar het volgende niveau te brengen. We hebben voorbeeldgegevens gegenereerd voor Luma en in de rest van deze zelfstudie importeert u deze gegevens in een van uw Experience Platform-sandboxomgevingen.

>[!NOTE]
>
>Het eindresultaat van deze zelfstudie is een sandbox met vergelijkbare gegevens als de [Aan de slag met Adobe Experience Platform voor Data Architects en Data Engineers - zelfstudie](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html). Het is in april 2023 bijgewerkt om de [Journey Optimizer-uitdagingen](https://experienceleague.adobe.com/docs/journey-optimizer-learn/challenges/introduction-and-prerequisites.html).


## Vereisten

* U hebt toegang tot Experience Platform APIs en weet hoe te voor authentiek te verklaren. Zo niet, bekijk dit [zelfstudie](https://experienceleague.adobe.com/docs/platform-learn/tutorials/platform-api-authentication.html?lang=nl).
* U hebt toegang tot een sandbox voor het ontwikkelen van Experience Platforms.
* Je kent je Experience Platform huurder-id. U kunt het verkrijgen door voor authentiek te maken [API-verzoek](https://experienceleague.adobe.com/docs/experience-platform/xdm/api/getting-started.html?lang=en#know-your-tenant_id)
of door deze uit de URL te halen wanneer u zich aanmeldt bij uw Platform-account. In de volgende URL is de huurder bijvoorbeeld &quot;
`techmarketingdemos`&quot; `https://experience.adobe.com/#/@techmarketingdemos/sname:prod/platform/home`.

## Postman gebruiken {#postman}

### Omgevingsvariabelen instellen

Voordat u de stappen uitvoert, moet u ervoor zorgen dat u de [Postman](https://www.postman.com/downloads/) toepassing.  Laten we beginnen!

1. Download de [platform-utils-main.zip](../assets/data-generator/platform-utils-main.zip) bestand, dat alle bestanden bevat die voor deze zelfstudie zijn vereist.

   >[!NOTE]
   >
   >Gebruikersgegevens in de [platform-utils-main.zip](../assets/data-generator/platform-utils-main.zip) het bestand is fictief en mag alleen voor demonstratiedoeleinden worden gebruikt.

1. Verplaats vanuit de downloadmap de `platform-utils-main.zip` naar de gewenste locatie op de computer en decomprimeer het bestand.
1. In de `luma-data` map, alle `json` bestanden in een teksteditor en vervang alle instanties van `_yourOrganizationID` met je eigen huurder-id, voorafgegaan door een onderstrepingsteken.
1. Openen `luma-offline-purchases.json` en `luma-web-events.json` in een teksteditor en werk alle tijdstempels bij, zodat de gebeurtenissen in de laatste maand plaatsvinden (bijvoorbeeld om `"timestamp":"2022-11` en vervang het jaar en de maand)
1. Noteer de locatie van de uitgevouwen map, zoals u deze later nodig hebt bij het instellen van de `FILE_PATH` Postman-omgevingsvariabele:

   >[!NOTE]
   > Als u een bestandspad op uw Mac wilt verkrijgen, navigeert u naar de `platform-utils-main` map, klikt u met de rechtermuisknop op de map en selecteert u **Info ophalen** optie.
   >
   > ![Mac-bestandspad](../assets/data-generator/images/mac-file-path.png)

   >[!NOTE]
   > U verkrijgt dossierweg op uw vensters, klik om de plaats van de gewenste omslag te openen, en dan met de rechtermuisknop aan het recht van de weg in de adresbar te klikken. Kopieer het adres om het bestandspad te verkrijgen.
   > 
   > ![Windows-bestandspad](../assets/data-generator/images/windows-file-path.png)

1. Open Postman en maak een nieuwe werkruimte via de **Werkruimten** vervolgkeuzemenu:\
   ![Werkruimte maken](../assets/data-generator/images/create-workspace.png)
1. Voer een **Naam** en optioneel **Samenvatting** voor uw werkruimte en klik op **Werkruimte maken**. Postman schakelt over naar de nieuwe werkruimte wanneer u deze maakt.
   ![Werkruimte opslaan](../assets/data-generator/images/save-workspace.png)
1. Pas nu enkele instellingen aan om de Postman-verzamelingen in deze werkruimte uit te voeren. Klik in de koptekst van Postman op het tandwielpictogram en selecteer **Instellingen** om de instellingen modaal te openen. U kunt ook de sneltoets (CMD/CTRL + ,) gebruiken om het modaal te openen.
1. Onder de `General` tabblad, de time-out van de aanvraag in ms bijwerken naar `5000 ms` en `allow reading file outside this directory`
   ![Instellingen](../assets/data-generator/images/settings.png)

   >[!NOTE]
   > Als bestanden vanuit de werkmap worden geladen, worden ze op alle apparaten probleemloos uitgevoerd als dezelfde bestanden op de andere apparaten worden opgeslagen. Als u echter bestanden van buiten de werkmap wilt uitvoeren, moet een instelling worden ingeschakeld om dezelfde intentie aan te geven. Als uw `FILE_PATH` is niet hetzelfde als het pad naar de Postman-werkmap. Schakel deze optie in.

1. Sluit de **Instellingen** deelvenster.
1. Selecteer **Omgevingen** en selecteer vervolgens **Importeren**:
   ![Omgevingsimport](../assets/data-generator/images/env-import.png)
1. Importeer het gedownloade JSON-omgevingsbestand. `DataInExperiencePlatform.postman_environment`
1. Selecteer in Postman de omgeving in het vervolgkeuzemenu rechtsboven en klik op het oogpictogram om de omgevingsvariabelen weer te geven:
   ![Omgevingsselectie](../assets/data-generator/images/env-selection.png)

1. Controleer of de volgende omgevingsvariabelen zijn gevuld. Als u wilt weten hoe u de waarde van de omgevingsvariabelen ophaalt, raadpleegt u de [Verifiëren voor Experience Platform-API&#39;s](/help/platform/authentication/platform-api-authentication.md) zelfstudie voor stapsgewijze instructies.

   * `CLIENT_SECRET`
   * `API_KEY`—`Client ID` in Adobe Developer Console
   * `TECHNICAL_ACCOUNT_ID`
   * `META_SCOPE`
   * `IMS`
   * `IMS_ORG`—`Organization ID` in Adobe Developer Console
   * `PRIVATE_KEY`
   * `SANDBOX_NAME`
   * `CONTAINER_ID`
   * `TENANT_ID`—moet met een onderstrepingsteken bijvoorbeeld beginnen `_techmarketingdemos`
   * `platform_end_point`
   * `FILE_PATH`—gebruik het lokale omslagweg waar u uitgepakt `platform-utils-main.zip` bestand. Zorg ervoor dat de map bijvoorbeeld de mapnaam bevat `/Users/dwright/Desktop/platform-utils-main`

1. **Opslaan** de bijgewerkte omgeving

### Postman-verzamelingen importeren

Vervolgens moet u de verzamelingen importeren in Postman.

1. Selecteren **Verzamelingen** en kies vervolgens de importoptie:

   ![Verzamelingen](../assets/data-generator/images/collections.png)

1. Importeer de volgende verzamelingen:

   * `0-Authentication.postman_collection.json`
   * `1-Luma-Loyalty-Data.postman_collection.json`
   * `2-Luma-CRM-Data.postman_collection.json`
   * `3-Luma-Product-Catalog.postman_collection.json`
   * `4-Luma-Offline-Purchase-Events.postman_collection.json`
   * `5-Luma-Product-Inventory-Events.postman_collection.json`
   * `6-Luma-Test-Profiles.postman_collection.json`
   * `7-Luma-Web-Events.postman_collection.json`

   ![Verzamelingen importeren](../assets/data-generator/images/collection-files.png)

### Verifiëren

Vervolgens moet u een gebruikerstoken verifiëren en genereren. Houd er rekening mee dat de methoden voor het genereren van tokens die in deze zelfstudie worden gebruikt, alleen geschikt zijn voor niet-productiedoeleinden. Bij Lokaal ondertekenen wordt een JavaScript-bibliotheek geladen van een host van een andere fabrikant en bij Extern ondertekenen wordt de persoonlijke sleutel naar een webservice verzonden die eigendom is van een Adobe. Hoewel Adobe deze persoonlijke sleutel niet opslaat, mogen productietoetsen nooit met iemand worden gedeeld.

1. Open de `Authentication` verzameling, selecteer de `IMS: JWT Generate + Auth via User Token` POST verzoek, en klik `SEND` om het toegangstoken voor authentiek te verklaren en te verkrijgen.

   ![Verzamelingen importeren](../assets/data-generator/images/authentication.png)

1. Controleer de omgevingsvariabelen en merk op dat de `JWT_TOKEN` en `ACCESS_TOKEN` zijn nu gevuld.

### Gegevens importeren

Nu kunt u de gegevens voorbereiden en importeren in de sandbox van het Platform. De Postman-verzamelingen die u hebt geïmporteerd, maken het hele heft!

1. Open de `1-Luma-Loyalty-Data` verzameling en klik op **Uitvoeren** op het overzichtslusje om een Runner van de Inzameling te beginnen.

   ![Verzamelingen importeren](../assets/data-generator/images/loyalty.png)

1. Zorg ervoor dat in het venster van de verzamelingsrunner de omgeving in het vervolgkeuzemenu is geselecteerd en werk de **Vertraging** tot `4000ms`, controleert u de **Reacties opslaan** en zorgt u ervoor dat de uitvoervolgorde correct is. Klik op de knop **Loyaliteitsgegevens uitvoeren** knop

   ![Verzamelingen importeren](../assets/data-generator/images/loyalty-run.png)

   >[!NOTE]
   >
   >**1-Luma-Loyalty-Data** leidt tot een schema voor de gegevens van de klantenloyaliteit. Het schema is gebaseerd op de individuele klasse van het Profiel XDM, standaardgebiedsgroep, en een groep en een gegevenstype van het douanegebied. De inzameling leidt tot een dataset gebruikend het schema en uploadt de gegevens van de steekproefklantenloyaliteit aan Adobe Experience Platform.

   >[!NOTE]
   >
   >Als om het even welke inzamelingsverzoeken tijdens de de inzamelingsloopler van Postman ontbreken, houd de uitvoering tegen en stel de inzamelingsverzoeken één voor één in werking.

1. Als alles goed gaat, alle verzoeken in de `Luma-Loyalty-Data` de verzameling moet slagen .

   ![Loyalty Result](../assets/data-generator/images/loyalty-result.png)

1. Nu aanmelden bij [Adobe Experience Platform-interface](https://platform.adobe.com/) en navigeer naar gegevenssets.
1. Open de `Luma Loyalty Dataset` dataset, en onder het venster van de gegevenssetactiviteit, kunt u een succesvolle partijlooppas bekijken die 1000 verslagen ingebed. U kunt ook op de optie van de voorproefdataset klikken om de opgenomen verslagen te verifiëren. Mogelijk moet u enkele minuten wachten om te bevestigen dat 1000 [!UICONTROL Nieuwe profielfragmenten] zijn gemaakt.
   ![Loyalty Dataset](../assets/data-generator/images/loyalty-dataset.png)
1. Herhaal stap 1-3 om de andere verzamelingen uit te voeren:
   * `2-Luma-CRM-Data.postman_collection.json` leidt tot een schema en bevolkte dataset voor de gegevens van CRM van klanten. Het schema is gebaseerd op de klasse van het Profiel van Individuele XDM die Demografische Details, Persoonlijke Details van het Contact, de Details van de Voorkeur en een groep van het het gebiedsveld van de douaneidentiteit omvat.
   * `3-Luma-Product-Catalog.postman_collection.json` leidt tot een schema en een bevolkte dataset voor de informatie van de productcatalogus. Het schema is gebaseerd op een aangepaste productcatalogusklasse en gebruikt een aangepaste productcatalogusveldgroep.
   * `4-Luma-Offline-Purchase-Events.postman_collection.json` leidt tot een schema en een bevolkte dataset voor off-line gegevens van de koopgebeurtenis van klanten. Het schema is gebaseerd op de klasse XDM ExperienceEvent en omvat een aangepaste identiteit en de de gebiedsgroepen van de Details van de Handel.

   * `5-Luma-Product-Inventory-Events.postman_collection.json` leidt tot een schema en bevolkte dataset voor gebeurtenissen met betrekking tot producten die in en uit voorraad gaan. Het schema is gebaseerd op een aangepaste bedrijfsgebeurtenisklasse en een aangepaste veldgroep.
   * `6-Luma-Test-Profiles.postman_collection.json` leidt tot een schema en bevolkte dataset met testprofielen in Adobe Journey Optimizer te gebruiken
   * `7-Luma-Web-Events.postman_collection.json` leidt tot een schema en bevolkte dataset met eenvoudige historische Webgegevens.


## Validatie

De voorbeeldgegevens zijn zodanig ontworpen dat, wanneer de verzamelingen zijn uitgevoerd, realtime profielen van klanten worden gemaakt waarin gegevens van meerdere systemen worden gecombineerd. Een goed voorbeeld hiervan is de eerste record van de gegevens over loyaliteit, CRM en offline aankopen. Zoek dat profiel op om te bevestigen dat de gegevens zijn opgenomen. In de [Adobe Experience Platform-interface](https://platform.adobe.com/):

1. Ga naar **[!UICONTROL Profielen]** > **[!UICONTROL Bladeren]**
1. Selecteren `Luma Loyalty Id` als de **[!UICONTROL Naamruimte identiteit]**
1. Zoeken naar `5625458` als de **[!UICONTROL Identiteitswaarde]**
1. Open de `Danny Wright` profiel

![Een profiel openen](../assets/data-generator/images/validation-profile-open.png)

Door de gegevens in het dialoogvenster **[!UICONTROL Attributen]** en **[!UICONTROL Gebeurtenissen]** tabbladen, ziet u dat het profiel gegevens bevat uit de verschillende gegevensbestanden:
![Gebeurtenisgegevens uit het offlinebestand Purchase-gebeurtenissen](../assets/data-generator/images/validation-profile-events.png)

## Volgende stappen

Als u meer wilt weten over Adobe Journey Optimizer, bevat deze sandbox alles wat u nodig hebt om de [Journey Optimizer-uitdagingen](https://experienceleague.adobe.com/docs/journey-optimizer-learn/challenges/introduction-and-prerequisites.html)

Als u over samenvoegingsbeleid, gegevensbeheer, vraagdienst, en de segmentbouwer zou willen leren, over aan [les 11 in het Getting Started for Data Architects and Data Engineers lesbestand](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/create-merge-policies.html?lang=en). De vroegere lessen van dit andere leerprogramma hebben u manueel alles bouwen dat enkel door deze inzameling van Postman bevolkt was—geniet van het hoofdbegin!

Als u een voorbeeldimplementatie van SDK van het Web aan verbinding aan deze zandbak wilt bouwen, ga door
[Zelfstudie Adobe Experience Cloud implementeren met Web SDK](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/overview.html). Nadat u de lessen &quot;Eerste configuratie&quot;, &quot;Configuratie van tags&quot; en &quot;Experience Platform instellen&quot; van de zelfstudie van de SDK van Web hebt ingesteld, meldt u zich aan bij de Luma-website met de eerste tien e-mailadressen in het dialoogvenster `luma-crm.json` bestand met het wachtwoord `test` om te zien hoe de profielfragmenten worden samengevoegd met gegevens die in deze zelfstudie zijn geüpload.

Als u een voorbeeld van een mobiele SDK-implementatie wilt maken om een koppeling naar deze sandbox te maken, doorloopt u het dialoogvenster
[Zelfstudie Adobe Experience Cloud implementeren in mobiele apps](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/overview.html). Nadat u de lessen &quot;Eerste configuratie&quot;, &quot;App-implementatie&quot; en &quot;Experience Platform&quot; van de zelfstudie van de Web SDK hebt ingesteld, meldt u zich aan bij de Luma-website met de eerste e-mailadressen in het dialoogvenster `luma-crm.json` bestand om een profielfragment samen te voegen met gegevens die in deze zelfstudie zijn geüpload.

## Sandbox-omgeving opnieuw instellen {#reset-sandbox}

Als u een niet-productiesandbox opnieuw instelt, worden alle bronnen verwijderd die aan die sandbox zijn gekoppeld (schema&#39;s, gegevenssets, enzovoort), terwijl de naam van de sandbox en de bijbehorende machtigingen behouden blijven. Deze &#39;schone&#39; sandbox blijft onder dezelfde naam beschikbaar voor gebruikers die er toegang toe hebben.

Voer de stappen uit [hier](https://experienceleague.adobe.com/docs/experience-platform/sandbox/ui/user-guide.html?lang=en#reset-a-sandbox) om een sandboxomgeving opnieuw in te stellen.
