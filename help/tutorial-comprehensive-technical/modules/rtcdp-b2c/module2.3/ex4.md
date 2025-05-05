---
title: CDP in real time - Bouw een publiek en neem actie - verzend uw publiek naar een S3-bestemming
description: CDP in real time - Bouw een publiek en neem actie - verzend uw publiek naar een S3-bestemming
kt: 5342
doc-type: tutorial
exl-id: 656fc93c-74ff-4d8f-8674-6520d2a70b86
source-git-commit: acb941e4ee668248ae0767bb9f4f42e067c181ba
workflow-type: tm+mt
source-wordcount: '830'
ht-degree: 0%

---

# 2.3.4 Actie ondernemen: stuur je publiek naar een S3-bestemming

Adobe Experience Platform heeft ook de capaciteit om publiek aan E-mailMarketing Doelen zoals de Marketing Cloud van Salesforce, Oracle Eloqua, Oracle Responsys en Adobe Campaign te delen.

U kunt FTP of SFTP als deel van de specifieke bestemmingen voor elk van deze E-mailMarketing Doelen gebruiken, of u kunt AWS S3 gebruiken om lijsten van klanten tussen Adobe Experience Platform en deze E-mailmarketing Doelen uit te wisselen.

In deze module, zult u zulk een bestemming vormen door gebruik van een emmertje van AWS S3 te maken.

## Maak uw S3-emmertje

Ga naar [ https://console.aws.amazon.com ](https://console.aws.amazon.com) en teken binnen.

>[!NOTE]
>
>Als je nog geen AWS-account hebt, maak dan een nieuwe AWS-account aan met je persoonlijke e-mailadres.

![ ETL ](./images/awshome.png)

Na het programma openen, zult u aan de **Console van het Beheer van AWS** opnieuw worden gericht.

![ ETL ](./images/awsconsole.png)

In de onderzoeksbar, onderzoek naar **s3**. Klik het eerste onderzoeksresultaat: **S3 - Schaalbare Opslag in de Wolk**.

![ ETL ](./images/awsconsoles3.png)

U zult dan de **homepage van Amazon S3** zien. Klik **creëren Emmertje**.

![ ETL ](./images/s3home.png)

In **creeer het 1&rbrace; scherm van het Emmertje &lbrace;, gebruik de naam `aepmodulertcdp--aepUserLdap--`**

![ ETL ](./images/bucketname.png)

Laat alle andere standaardinstellingen ongewijzigd. De rol neer en klikt **creeert emmer**.

![ ETL ](./images/createbucket.png)

Vervolgens ziet u dat uw emmer is gemaakt en wordt deze omgeleid naar de startpagina van Amazon S3.

![ ETL ](./images/S3homeb.png)

## Toestemmingen plaatsen om tot uw S3 emmertje toegang te hebben

De volgende stap is toegang tot uw S3 emmertje te plaatsen.

Om dat te doen, ga naar [ https://console.aws.amazon.com/iam/home ](https://console.aws.amazon.com/iam/home).

De toegang tot AWS-bronnen wordt beheerd door Amazon Identity and Access Management (IAM).

U ziet deze pagina nu.

![ ETL ](./images/iam.png)

In het linkermenu, klik **Gebruikers**. U zult dan het **scherm van Gebruikers** zien. Klik **creëren gebruiker**.

![ ETL ](./images/iammenu.png)

Configureer vervolgens de gebruiker:

- Gebruikersnaam: gebruik `s3_--aepUserLdap--_rtcdp`

Klik **daarna**.

![ ETL ](./images/configuser.png)

U zult dan dit toestemmingenscherm zien. Klik **beleid van de Band direct**.

![ ETL ](./images/perm1.png)

Ga de onderzoekstermijn **s3** in om al verwant S3 beleid te zien. Selecteer het beleid **AmazonS3FullAccess**. De rol neer en klikt **daarna**.

![ ETL ](./images/perm2.png)

Controleer uw configuratie. Klik **creëren Gebruiker**.

![ ETL ](./images/review.png)

Dan zie je dit. Klik **Gebruiker van de Mening**.

![ ETL ](./images/review1.png)

Klik **geloofsbrieven van de Veiligheid** en klik dan **creeer toegangssleutel**.

![ ETL ](./images/cred.png)

Selecteer **Toepassing die buiten AWS** loopt. De rol neer en klikt **daarna**.

![ ETL ](./images/creda.png)

Klik **creëren toegangssleutel**

![ ETL ](./images/credb.png)

Dan zie je dit. Klik **tonen** om uw Geheime toegangstoets te zien:

![ ETL ](./images/cred1.png)

Uw **Geheime toegangssleutel** wordt nu getoond.

>[!IMPORTANT]
>
>Sla uw gegevens op in een tekstbestand op uw computer.
>
> - Toegang sleutel-id: ...
> - Geheime toegangssleutel: ...
>
> Zodra u **Gedaan** klikt zult u uw geloofsbrieven nooit meer zien!

Klik **Gedaan**.

![ ETL ](./images/cred2.png)

U hebt nu een AWS S3 emmertje met succes gecreeerd en u hebt een gebruiker met toestemmingen gecreeerd om tot dit emmertje toegang te hebben.

## Doel configureren in Adobe Experience Platform

Ga naar [ Adobe Experience Platform ](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``--aepSandboxName--`` . Nadat u de juiste [!UICONTROL sandbox] hebt geselecteerd, ziet u de schermwijziging en nu bevindt u zich in uw toegewezen [!UICONTROL sandbox] .

![ Ingestie van Gegevens ](./../../../modules/datacollection/module1.2/images/sb1.png)

In het linkermenu, ga naar **Doelen**, dan gaan naar **Catalogus**. U zult dan de **Catalogus van Doelen** zien.

![ RTCDP ](./images/rtcdpmenudest1.png)

Klik {de Opslag van de Wolk 1}, dan klik de **Opstelling** knoop (of op **activeer Soorten publiek**, afhankelijk van uw milieu) op **Amazon S3** kaart.**&#x200B;**

![ RTCDP ](./images/rtcdp2.png)

Selecteer **Sleutel van de Toegang** als Type van Rekening. Gelieve te gebruiken de S3 geloofsbrieven die aan u in de vorige stap werden gegeven:

| Toegangstoets-id | Geheime toegangstoets |
|:-----------------------:| :-----------------------:|
| AKIA... | 7 cm... |

Klik **verbinden met bestemming**.

![ RTCDP ](./images/rtcdpsfs3.png)

Vervolgens ziet u een visuele bevestiging dat deze bestemming nu is verbonden.

![ RTCDP ](./images/rtcdpsfs3connected.png)

U moet S3 emmerdetails verstrekken zodat Adobe Experience Platform met het S3 emmertje kan verbinden.

Als naamgevingsconventie kunt u het volgende gebruiken:

| Toegangstoets-id | Geheime toegangstoets |
|:-----------------------:| :-----------------------:|
| Naam | `AWS - S3 - --aepUserLdap--` |
| Beschrijving | `AWS - S3 - --aepUserLdap--` |
| Naam emmertje | `aepmodulertcdp--aepUserLdap--` |
| Mappad | /now |

Selecteer **Soorten publiek**.

Voor **Type van Dossier**, uitgezochte **CSV** en verlaat onveranderd de standaardmontages.

![ RTCDP ](./images/rtcdpsfs3connect2.png)

Omlaag schuiven. Voor **formaat van de Compressie**, uitgezochte **niets**. Klik **daarna**.

![ RTCDP ](./images/rtcdpsfs3connect3.png)

U kunt nu optioneel een beleid voor gegevensbeheer aan uw nieuwe bestemming koppelen. Klik **daarna**.

![ RTCDP ](./images/rtcdpsfs3connect2gov.png)

Zoek in de lijst met soorten publiek naar het publiek dat u in de vorige oefening hebt gemaakt `--aepUserLdap-- - Interest in Galaxy S24` en selecteer dit. Klik **daarna**.

![ RTCDP ](./images/s3a.png)

Dan zie je dit. Als u wenst, kunt u het programma en filename uitgeven door het **potlood** pictogram te klikken. Klik **daarna**.

![ RTCDP ](./images/s3bb.png)

U kunt nu profielkenmerken selecteren voor het exporteren naar AWS S3. Klik **toevoegen nieuw gebied** en zorg ervoor het gebied `--aepTenantId--.identification.core.ecid` wordt toegevoegd en als **Sleutel van de Deduplicatie** duidelijk.

U kunt desgewenst zoveel andere profielkenmerken toevoegen als u wilt.

Zodra u alle gebieden hebt toegevoegd, klik **daarna**.

![ RTCDP ](./images/s3c.png)

Controleer uw configuratie. Klik **Afwerking** om uw configuratie te beëindigen.

![ RTCDP ](./images/s3g.png)

U zult dan terug bij het scherm van de Activering van de Bestemming zijn en u zult uw publiek zien aan deze bestemming worden toegevoegd.

Als u meer publieksuitvoer zou willen toevoegen, kunt u **klikken activeert Soorten publiek** om het proces opnieuw te beginnen en meer publiek toe te voegen.

![ RTCDP ](./images/s3j.png)

Volgende Stap: [ 2.3.5 Actie nemen: verzend uw publiek naar Adobe Target ](./ex5.md)

[Terug naar module 2.3](./real-time-cdp-build-a-segment-take-action.md)

[Terug naar alle modules](../../../overview.md)
