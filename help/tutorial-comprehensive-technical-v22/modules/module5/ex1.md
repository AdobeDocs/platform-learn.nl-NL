---
title: Intelligente services - Voorbereiding van AI-gegevens van klanten (Ingest)
description: AI van klant - Gegevensvoorbereiding (overzicht)
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 60996e70-b033-4932-b614-b37014232f6e
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 0%

---

# 5.1 AI van klant - Gegevensvoorbereiding (Ingest)

Om de Intelligente Diensten inzichten van uw marketing gebeurtenisgegevens te ontdekken, moeten de gegevens semantisch worden verrijkt en in een standaardstructuur worden gehandhaafd. Intelligent Services leverages Adobe Experience Model (XDM) schema&#39;s om dit te bereiken.
Specifiek, moeten alle datasets die in de Intelligente Diensten worden gebruikt met in overeenstemming zijn **Consumentenervaringsgebeurtenis** XDM-schema.

## 5.1.1 Schema maken

In deze oefening, zult u een schema creëren dat bevat **Consumer Experience Event-mix**, die vereist zijn door de **Customer AI** Intelligente service.

Meld u aan bij Adobe Experience Platform door naar deze URL te gaan: [https://experience.adobe.com/platform](https://experience.adobe.com/platform).

Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![Gegevensinname](../module2/images/home.png)

Voordat u verdergaat, moet u een **sandbox**. De sandbox die moet worden geselecteerd, krijgt een naam ``--module10sandbox--``. U kunt dit doen door op de tekst te klikken **[!UICONTROL Productieproduct]** in de blauwe lijn boven op het scherm. Na het selecteren van de aangewezen zandbak, zult u de het schermverandering zien en nu bent u in uw specifieke zandbak.

![Gegevensinname](../module2/images/sb1.png)

Klik in het linkermenu op **Schemas** en ga naar **Bladeren**. Klikken **Schema maken**.

![Nieuw schema maken](./images/create-schema-button.png)

Selecteer **XDM ExperienceEvent**.

![Nieuw schema maken](./images/xdmee.png)

Dan zie je dit.

![Nieuw schema maken](./images/xdmee1.png)

Zoek en selecteer het volgende **Mixins** om aan dit Schema toe te voegen:

- Consumentenervaringsgebeurtenis

   ![Nieuw CEE-schema](./images/cee.png)

- Gegevens van eindgebruiker

   ![Nieuw CEE-schema](./images/identitymap.png)

Klikken **Veldgroepen toevoegen**.

![Definitie van identiteitssleutel](./images/addmixin.png)

Dan zie je dit. De mix selecteren **Gegevens van eindgebruiker**.

![Nieuw schema maken](./images/eui1.png)

Naar het veld navigeren **endUserIDs._experience.emailid.id**.

![Nieuw schema maken](./images/eui2.png)

In het rechtermenu van het veld **endUserIDs._experience.emailid.id**, omlaag schuiven en het selectievakje inschakelen voor **Identiteit**, schakel het selectievakje in voor **Primaire identiteit** en selecteert u de **Naamruimte identiteit** van **E-mail**.

![Nieuw schema maken](./images/eui3.png)

Naar het veld navigeren **endUserIDs._experience.mcid.id**. Schakel het selectievakje in voor **Identiteit** en selecteert u de **Naamruimte identiteit** van **ECID**. Klikken **Toepassen**.

![Nieuw schema maken](./images/eui4.png)

Geef uw schema nu een naam.

Als naam voor ons schema, zult u dit gebruiken:

- `--demoProfileLdap-- - Demo System - Customer Experience Event`

Als voorbeeld voor LDAP **vangeluw** Dit moet de naam van het schema zijn:

- **vangeluw - demosysteem - Customer Experience Event**

Dat zou je iets dergelijks moeten geven. Klik op de knop **+ Toevoegen** knop om nieuwe toe te voegen **Mixins**.

![Nieuw schema maken](./images/xdmee2.png)

Selecteer de naam van het schema. U moet nu uw schema inschakelen voor **Profiel** door op de knop **Profiel** schakelen.

![Nieuw schema maken](./images/xdmee3.png)

Dan zie je dit. Klikken **Inschakelen**.

![Nieuw schema maken](./images/xdmee4.png)

Dat zou u nu moeten doen. Klikken **Opslaan** om uw schema op te slaan.

![Nieuw schema maken](./images/xdmee5.png)

## 5.1.2 Gegevensset maken

Klik in het linkermenu op **Gegevenssets** en ga naar **Bladeren**. Klikken **Gegevensset maken**.

![Gegevensset](./images/createds.png)

Klikken **Gegevensset maken van schema**.

![Gegevensset](./images/createdatasetfromschema.png)

In het volgende scherm, selecteer de dataset u in de vorige oefening creeerde, die wordt genoemd **[!UICONTROL LDAP - demosysteem - Customer Experience Event]**. Klik op **Next**.

![Gegevensset](./images/createds1.png)

Als naam voor uw dataset, gebruik `--demoProfileLdap-- - Demo System - Customer Experience Event Dataset`. Klikken **Voltooien**.

![Gegevensset](./images/createds2.png)

Uw dataset wordt nu gecreeerd. De optie **Profiel** schakelen.

![Gegevensset](./images/createds3.png)

Klikken **Inschakelen**.

![Gegevensset](./images/createds4.png)

U zou nu het volgende moeten hebben:

![Gegevensset](./images/createds5.png)

U bent nu klaar om gegevens van de Gebeurtenis van de Ervaring van de Consumenten te beginnen en de dienst van AI van de Klant te gebruiken.

## 5.1.3 Testgegevens downloadervaring

Wanneer de **Schema** en **Gegevensset** zijn gevormd, bent u nu klaar om de gegevens van de Gebeurtenis van de Ervaring in te voeren. Aangezien AI van de Klant gegevens vereist over **2 kwarten of ten minste**, moet u extern voorbereide gegevens opnemen.

De gegevens die worden voorbereid voor de ervaringsgebeurtenissen moeten voldoen aan de vereisten en het schema van het [Consumer Experience Event XDM Mixer](https://github.com/adobe/xdm/blob/797cf4930d5a80799a095256302675b1362c9a15/docs/reference/context/experienceevent-consumer.schema.md).

Download het bestand met voorbeeldgegevens van deze locatie: [https://dashboard.adobedemo.com/data](https://dashboard.adobedemo.com/data). Klik op de knop **Downloaden** knop.

![Gegevensset](./images/dsn1.png)

U hebt nu een bestand gedownload met de naam **retail-v1-dec2020-xl.json.zip**. Plaats het bestand op het bureaublad van de computer en decomprimeer het, waarna u een bestand ziet met de naam **retail-v1.json**. U hebt dit bestand nodig in de volgende oefening.

![Gegevensset](./images/ingest.png)

## 5.1.4 Testgegevens over gebeurtenissen met de grootste ervaring

Ga in Adobe Experience Platform naar **Gegevenssets** en open uw dataset, die wordt genoemd **[!UICONTROL ldap - demosysteem - Gegevensset van gebeurtenis Klantervaring]**.

![Gegevensset](./images/ingest1.png)

Klik in de gegevensset op **Bestanden kiezen** om gegevens toe te voegen.

![Gegevensset](./images/ingest2.png)

Selecteer het bestand in de pop-up **retail-v1.json** en klik op **Openen**.

![Gegevensset](./images/ingest3.png)

U zult dan de gegevens zien die worden ingevoerd, en een nieuwe partij wordt gecreeerd in **Laden** status. Navigeer niet van deze pagina weg tot het dossier wordt geupload.

![Gegevensset](./images/ingest4.png)

Zodra het bestand is geüpload, ziet u de wijziging in de batchstatus van **Laden** tot **Verwerking**.

![Gegevensset](./images/ingest5.png)

Het installeren en verwerken van de gegevens kan 10 tot 20 minuten duren.

Als de gegevens eenmaal zijn ingevoerd, verandert de batchstatus in **Succes**.

![Gegevensset](./images/ingest7.png)

![Gegevensset](./images/ingest8.png)

Volgende stap: [5.2 AI van de Klant - creeer een Nieuwe Instantie (vorm)](./ex2.md)

[Ga terug naar module 5](./intelligent-services.md)

[Terug naar alle modules](./../../overview.md)
