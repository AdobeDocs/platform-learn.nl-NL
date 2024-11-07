---
title: In real time CDP - Bouw een segment en neem actie - verzend uw segment naar een S3-bestemming
description: In real time CDP - Bouw een segment en neem actie - verzend uw segment naar een S3-bestemming
kt: 5342
doc-type: tutorial
source-git-commit: 2cdc145d7f3933ec593db4e6f67b60961a674405
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 0%

---

# 2.3.4 Actie nemen: verzend uw segment naar een S3-bestemming

Adobe Experience Platform heeft ook de capaciteit om Publiek aan E-mailMarketing Doelen zoals de Marketing Cloud van Salesforce, Oracle Eloqua, Oracle Responsys en Adobe Campaign te delen.

U kunt FTP of SFTP als deel van de specifieke bestemmingen voor elk van deze E-mailMarketing Doelen gebruiken, of u kunt AWS S3 gebruiken om lijsten van klanten tussen Adobe Experience Platform en deze E-mailmarketing Doelen uit te wisselen.

In deze module, zult u zulk een bestemming vormen door gebruik van een emmertje van AWS S3 te maken.

## 2.3.4.1 Maak een S3-emmertje

Ga naar [ https://console.aws.amazon.com ](https://console.aws.amazon.com) en teken binnen met de Amazon-rekening u eerder creeerde.

![ ETL ](./images/awshome.png)

Na het programma openen, zult u aan de **Console van het Beheer van AWS** opnieuw worden gericht.

![ ETL ](./images/awsconsole.png)

In het **menu van de Diensten van de Vondst**, onderzoek naar **s3**. Klik het eerste onderzoeksresultaat: **S3 - Schaalbare Opslag in de Wolk**.

![ ETL ](./images/awsconsoles3.png)

U zult dan de **homepage van Amazon S3** zien. Klik **creëren Emmertje**.

![ ETL ](./images/s3home.png)

In **creeer het 1} scherm van het Emmertje {, moet u twee dingen vormen:**

- Naam: gebruik de naam `aepmodulertcdp--demoProfileLdap--` . Als voorbeeld, in deze oefening is de emmernaam **aepmodulertcdpvangeluw**
- Regio: gebruik de regio **EU (Frankfurt) eu-central-1**

![ ETL ](./images/bucketname.png)

Laat alle andere standaardinstellingen ongewijzigd. De rol neer en klikt **creeert emmer**.

![ ETL ](./images/createbucket.png)

Vervolgens ziet u dat uw emmer is gemaakt en wordt deze omgeleid naar de startpagina van Amazon S3.

![ ETL ](./images/S3homeb.png)

## 2.3.4.2 Recht plaatsen om tot uw S3 emmertje toegang te hebben

De volgende stap is toegang tot uw S3 emmertje te plaatsen.

Om dat te doen, ga naar [ https://console.aws.amazon.com/iam/home ](https://console.aws.amazon.com/iam/home).

De toegang tot AWS-bronnen wordt beheerd door Amazon Identity and Access Management (IAM).

U ziet deze pagina nu.

![ ETL ](./images/iam.png)

In het linkermenu, klik **Gebruikers**. U zult dan het **scherm van Gebruikers** zien. Klik **toevoegen Gebruikers**.

![ ETL ](./images/iammenu.png)

Configureer vervolgens de gebruiker:

- Gebruikersnaam: gebruik `s3_--demoProfileLdap--_rtcdp` als naam, dus in dit voorbeeld is de naam `s3_vangeluw_rtcdp` .
- Het toegangstype van AWS: uitgezochte **sleutel van de Toegang - Programmatische toegang**.

Klik **daarna: Toestemmingen**.

![ ETL ](./images/configuser.png)

U zult dan dit toestemmingenscherm zien. Klik **direct bestaand beleid** verbinden.

![ ETL ](./images/perm1.png)

Ga de onderzoekstermijn **s3** in om al verwant S3 beleid te zien. Selecteer het beleid **AmazonS3FullAccess**. Klik **daarna: Markeringen**.

![ ETL ](./images/perm2.png)

Op het **scherm van Markeringen**, is er geen behoefte om om het even wat te vormen. Klik **daarna: Overzicht**.

![ ETL ](./images/perm3.png)

Controleer uw configuratie. Klik **creëren Gebruiker**.

![ ETL ](./images/review.png)

Uw gebruiker wordt nu gecreeerd en u ziet uw geloofsbrieven om tot uw S3 milieu toegang te hebben. Dit is de enige keer dat u uw referenties ziet, dus schrijf deze naar beneden.

![ ETL ](./images/cred.png)

Klik **tonen** om uw Geheime toegangstoets te zien:

![ ETL ](./images/cred1.png)

>[!IMPORTANT]
>
>Sla uw gegevens op in een tekstbestand op uw computer.
>
> - Toegang sleutel-id: ...
> - Geheime toegangssleutel: ...
>
> Zodra u **dicht** klikt zult u uw geloofsbrieven nooit meer zien!

Klik **dicht**.

![ ETL ](./images/close.png)

U hebt nu een AWS S3 emmertje met succes gecreeerd en u hebt een gebruiker met toestemmingen gecreeerd om tot dit emmertje toegang te hebben.

## 2.3.4.3 Bestemming in Adobe Experience Platform configureren

Ga naar [ Adobe Experience Platform ](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxId--`` . U kunt dit doen door op de tekst **[!UICONTROL Production Prod]** in de blauwe lijn boven op het scherm te klikken. Nadat u de juiste [!UICONTROL sandbox] hebt geselecteerd, ziet u de schermwijziging en nu bevindt u zich in uw toegewezen [!UICONTROL sandbox] .

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/sb1.png)

In het linkermenu, ga naar **Doelen**, dan gaan naar **Catalogus**. U zult dan de **Catalogus van Doelen** zien.

![ RTCDP ](./images/rtcdpmenudest.png)

Klik {de Opslag van de Wolk 1}, dan klik de **Opstelling** knoop (of op **activeer Segmenten**, afhankelijk van uw milieu) op de **S3** kaart van Amazon.****

![ RTCDP ](./images/rtcdp2.png)

Afhankelijk van uw milieu, zou u **kunnen moeten klikken + nieuwe bestemming** vormen beginnen uw bestemming te creëren.

![ RTCDP ](./images/rtcdp2a.png)

Selecteer **Nieuwe Rekening** als Type van Rekening. Gelieve te gebruiken de S3 geloofsbrieven die aan u in de vorige stap werden gegeven:

| Toegangstoets-id | Geheime toegangstoets |
|:-----------------------:| :-----------------------:|
| AKIA... | Cm5Ln.... |

Klik **verbinden met bestemming**.

![ RTCDP ](./images/rtcdpsfs3.png)

Vervolgens ziet u een visuele bevestiging dat deze bestemming nu is verbonden.

![ RTCDP ](./images/rtcdpsfs3connected.png)

U moet een naam en een map opgeven zodat Adobe Experience Platform verbinding kan maken met het S3-emmertje.

Als naamgevingsconventie kunt u het volgende gebruiken:

| Toegangstoets-id | Geheime toegangstoets |
|:-----------------------:| :-----------------------:|
| Naam | `AWS - S3 - --demoProfileLdap--` |
| Beschrijving | `AWS - S3 - --demoProfileLdap--` |
| Naam emmertje | `aepmodulertcdp--demoProfileLdap--` |
| Mappad | / |

Klik **daarna**.

![ RTCDP ](./images/rtcdpsfs3connect2.png)

U kunt nu optioneel een beleid voor gegevensbeheer aan uw nieuwe bestemming koppelen. Klik **daarna**.

![ RTCDP ](./images/rtcdpsfs3connect2gov.png)

Zoek in de lijst met segmenten naar het segment dat u in oefening 1 hebt gemaakt en selecteer het. Klik **daarna**.

![ RTCDP ](./images/s3a.png)

Dan zie je dit. Als u wenst, kunt u het programma uitgeven door het **potlood** pictogram te klikken. **creeer Programma**.

![ RTCDP ](./images/s3bb.png)

Bepaal uw keuzeplanning. Selecteer **de stijgende dossiers van de Uitvoer** en plaats de frequentie aan **Uur** om de **3 uren**. Klik **creëren**.

![ RTCDP ](./images/s3bbc.png)

Dan heb je dit. Klik **daarna**.

![ RTCDP ](./images/s3bbca.png)

U kunt nu kenmerken selecteren voor het exporteren naar AWS S3. Klik **toevoegen nieuw gebied** en zorg ervoor het gebied `--aepTenantId--.identification.core.ecid` wordt toegevoegd en als **Sleutel van de Deduplicatie** duidelijk.

U kunt desgewenst zoveel andere velden toevoegen als u wilt.

Zodra u alle gebieden hebt toegevoegd, klik **daarna**.

![ RTCDP ](./images/s3c.png)

Controleer uw configuratie. Klik **Afwerking** om uw configuratie te beëindigen.

![ RTCDP ](./images/s3g.png)

U zult dan terug bij het scherm van de Activering van de Bestemming zijn en u zult uw segment zien dat aan deze bestemming wordt toegevoegd.

![ RTCDP ](./images/s3j.png)

Als u meer segmentuitvoer zou willen toevoegen, kunt u **klikken activeert Segmenten** om het proces opnieuw te beginnen en meer segmenten toe te voegen.

![ RTCDP ](./images/s3k.png)

Volgende Stap: [ 2.3.5 Actie nemen: verzend uw segment naar Adobe Target ](./ex5.md)

[Terug naar module 2.3](./real-time-cdp-build-a-segment-take-action.md)

[Terug naar alle modules](../../../overview.md)
