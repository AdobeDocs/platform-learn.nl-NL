---
title: Bootkamp - Overvloeien fysiek en digitaal - Journey Optimizer Maak een reis en duw - Brazilnotification
description: Bootkamp - Overvloeien fysiek en digitaal - Journey Optimizer Maak een reis en duw - Brazilnotification
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
source-git-commit: 75a878ba596078e6d013b65062606931402302dd
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 0%

---

# 3.3 Maak uw reis en pushmelding

In deze oefening, zult u de reis en het bericht vormen die moeten worden teweeggebracht wanneer iemand een baken gebruikend mobiele app ingaat.

Aanmelden bij Adobe Journey Optimizer door naar [Adobe Experience Cloud](https://experience.adobe.com). Klikken **Journey Optimizer**.

![ACOP](./images/acophome.png)

U wordt omgeleid naar de **Home**  in Journey Optimizer. Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `Bootcamp`. Als u van de ene naar de andere sandbox wilt gaan, klikt u op **Prod** en selecteert u de sandbox in de lijst. In dit voorbeeld krijgt de sandbox een naam **Bootkamp**. Dan ben je in de **Home** weergave van de sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

## 3.3.1 Uw reis maken

Klik in het linkermenu op **Reizen**. Klik op Volgende **Reis maken** om een nieuwe reis te maken.

![ACOP](./images/createjourney.png)

Dan zie je een leeg reisscherm.

![ACOP](./images/journeyempty.png)

In de vorige oefening creeerde u een nieuw **Gebeurtenis**. U noemde het zo `yourLastNameBeaconEntryEvent` en vervangen `yourLastName` met uw achternaam. Dit was het resultaat van het maken van de gebeurtenis:

![ACOP](./images/eventdone.png)

U moet deze gebeurtenis nu als begin van deze reis nemen. U kunt dit doen door naar de linkerkant van het scherm te gaan en naar uw gebeurtenis in de lijst met gebeurtenissen te zoeken.

![ACOP](./images/eventlist.png)

Selecteer de gebeurtenis, sleep deze naar het canvas van de reis. Je reis ziet er nu zo uit. Klikken **OK** om uw wijzigingen op te slaan.

![ACOP](./images/journeyevent.png)

Als tweede stap in de reis, moet u toevoegen **Push** handeling. Naar de linkerkant van het scherm gaan **Handelingen**, selecteert u de **Push** actie, dan belemmering en laat vallen het op de tweede knoop in uw reis.

![ACOP](./images/journeyactions.png)

Rechts in het scherm moet u nu een pushmelding maken.

Stel de **Categorie** tot **Marketing** en selecteer een drukknop waarmee u pushmeldingen kunt verzenden. In dit geval moet het te selecteren drukknop **mmeewis-app-mobile-bootkamp**.

![ACOP](./images/journeyactions1.png)

## 3.3.2 Uw bericht maken

Klikken **Inhoud bewerken**.

![ACOP](./images/emptymsg.png)

U zult dan dit zien:

![ACOP](./images/emailmsglist.png)

Laten we de inhoud van de pushmelding definiëren.

Klik op de knop **Titel** tekstveld.

![Journey Optimizer](./images/msg5.png)

Begin met schrijven in het tekstgebied **Hallo**. Klik op het verpersoonlijkingspictogram.

![Journey Optimizer](./images/msg6.png)

U moet nu het personalisatietoken voor het veld introduceren **Voornaam** dat is opgeslagen onder `profile.person.name.firstName`. Selecteer in het linkermenu de optie **Profielkenmerken**, schuift u omlaag of navigeert u naar de **Persoon** -element en klik op de pijl om een niveau dieper te gaan totdat u het veld bereikt `profile.person.name.firstName`. Klik op de knop **+** pictogram om het veld aan het canvas toe te voegen. Klikken **Opslaan**.

![Journey Optimizer](./images/msg7.png)

Dan ben je hier weer. Klik op het pictogram voor aanpassen naast het veld **Lichaam**.

![Journey Optimizer](./images/msg11.png)

In het tekstgebied schrijft u `Welcome at the `.

![Journey Optimizer](./images/msg12.png)

Klik op Volgende **Contextafhankelijke kenmerken** en vervolgens **Journey Orchestration**.

![ACOP](./images/jomsg3.png)

Klikken **Gebeurtenissen**.

![ACOP](./images/jomsg4.png)

Klik op de naam van de gebeurtenis, die er als volgt moet uitzien: **yourLastNameBeaconEntryEvent**.

![ACOP](./images/jomsg5.png)

Klikken **Context plaatsen**.

![ACOP](./images/jomsg6.png)

Klikken **Interactie tussen POI**.

![ACOP](./images/jomsg7.png)

Klikken **POI-details**.

![ACOP](./images/jomsg8.png)

Klik op de knop **+** pictogram op **POI-naam**.
Dan zie je dit. Klikken **Opslaan**.

![ACOP](./images/jomsg9.png)

Uw bericht is nu klaar. Klik op de pijl in de linkerbovenhoek om terug te gaan naar uw reis.

![ACOP](./images/jomsg11.png)

Klikken **OK**.

![ACOP](./images/jomsg14.png)

## 3.3.2 Een bericht naar het scherm verzenden

Als derde stap in de reis, moet u toevoegen **sendMessageToScreen** handeling. Naar de linkerkant van het scherm gaan **Handelingen**, selecteert u de **sendMessageToScreen** actie, dan belemmering en laat vallen het op de derde knoop in uw reis. Dan zie je dit.

![ACOP](./images/jomsg15.png)

De **sendMessageToScreen** De actie is een douaneactie die een bericht aan het eindpunt zal publiceren dat door de in-opslagvertoning wordt gebruikt. De **sendMessageToScreen** handeling verwacht dat een aantal variabelen wordt gedefinieerd. U kunt deze variabelen zien door omlaag te schuiven totdat u ze ziet **Handelingsparameters**.

![ACOP](./images/jomsg16.png)

U moet nu de waarden voor elke handelingsparameter instellen. Volg deze tabel om te begrijpen welke waarden vereist zijn.

| Parameter | value |
|:-------------:| :---------------:|
| LEVERING | `'image'` |
| ECID | `@{yourLastNameBeaconEntryEvent._experienceplatform.identification.core.ecid}` |
| EERSTE NAAM | `#{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName}` |
| EVENTSUBJECT | `#{ExperiencePlatform.ProductListItems.experienceevent.first(currentDataPackField.eventType == "commerce.productViews").productListItems.first().name}` |
| EVENTSUBJECTURL | `#{ExperiencePlatform.ProductListItems.experienceevent.first(currentDataPackField.eventType == "commerce.productViews").productListItems.first()._experienceplatform.core.imageURL}` |
| SANDBOX | `'bootcamp'` |
| CONTAINERID | `''` |
| ACTIVITYID | `''` |
| PLACEMENTID | `''` |

{style=&quot;table-layout:auto&quot;}

Als u deze waarden wilt instellen, klikt u op de knop **Bewerken** pictogram.

![ACOP](./images/jomsg17.png)

Selecteer vervolgens **Geavanceerde modus**.

![ACOP](./images/jomsg18.png)

Plak vervolgens de waarde op basis van de bovenstaande tabel. Klikken **OK**.

![ACOP](./images/jomsg19.png)

Herhaal dit proces om waarden toe te voegen voor elk veld.

>[!IMPORTANT]
>
>Voor het veld ECID is er een verwijzing naar de gebeurtenis `yourLastNameBeaconEntryEvent`. Vervang `yourLastName` op uw achternaam.

Het eindresultaat moet er als volgt uitzien:

![ACOP](./images/jomsg20.png)

Omhoog schuiven en klikken **OK**.

![ACOP](./images/jomsg21.png)

Je moet je reis nog steeds een naam geven. U kunt dat doen door op de knop **Eigenschappen** in de rechterbovenhoek van het scherm.

![ACOP](./images/journeyname.png)

Je kunt hier de naam van de reis invoeren. Gebruik `yourLastName - Beacon Entry Journey`. Klikken **OK** om uw wijzigingen op te slaan.

![ACOP](./images/journeyname1.png)

U kunt uw reis nu publiceren door te klikken **Publiceren**.

![ACOP](./images/publishjourney.png)

Klikken **Publiceren** opnieuw.

![ACOP](./images/publish1.png)

Vervolgens ziet u een groene bevestigingsbalk met de mededeling dat uw reis nu is gepubliceerd.

![ACOP](./images/published.png)

Je reis is nu live en kan worden geïnitieerd.

Je hebt deze oefening nu afgerond.

Volgende stap: [3.4 Test uw reis](./ex4.md)

[Ga terug naar gebruikersstroom 3](./uc3.md)

[Terug naar alle modules](../../overview.md)
