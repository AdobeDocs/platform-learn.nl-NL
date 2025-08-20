---
title: GenStudio for Performance Marketing maakt uw Amazon AWS S3-emmertje
description: GenStudio for Performance Marketing maakt uw Amazon AWS S3-emmertje
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
source-git-commit: 1dd8b487cbd16e438e9c006c34e458ddb82cce64
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# 1.6.2 Een AWS S3-emmertje maken

## 1.6.2.1 Een S3-emmertje maken

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

In **creeer het 1} scherm van het Emmertje {, gebruik de naam**.`--aepUserLdap---gspem-dam`

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

- Gebruikersnaam: gebruik `s3_--aepUserLdap--_gspem_dam`

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

## 1.6.2.2 Assets uploaden naar uw S3-emmertje

In de onderzoeksbar, onderzoek naar **s3**. Klik het eerste onderzoeksresultaat: **S3 - Schaalbare Opslag in de Wolk**.

![ ETL ](./images/bucket1.png)

Klik om het nieuwe S3 emmertje te openen, dat `--aepUserLdap---gspem-dam` zou moeten worden genoemd.

![ ETL ](./images/bucket2.png)

Klik **uploaden**.

![ ETL ](./images/bucket3.png)

Dan moet je dit zien.

![ ETL ](./images/bucket4.png)

U kunt CitiSignal beelddossiers [ hier downloaden ](./../../asset-mgmt/module2.2/images/CitiSignal_Neon_Rabbit.zip){target="_blank"}.

Exporteer de bestanden naar uw bureaublad.

![ ETL ](./images/bucket5.png)

Neem de twee beelddossiers in die omslag en zet hen in het S3 emmeruploadvenster neer. Klik **uploaden**.

![ ETL ](./images/bucket6.png)

Dan moet je dit zien. Uw S3-emmertje, afbeeldingsbestanden en uw IAM-gebruiker zijn nu klaar om te worden gebruikt door uw externe DAM-app.

![ ETL ](./images/bucket7.png)

## Volgende stappen

Ga naar [ creeer uw externe toepassing DAM ](./ex3.md){target="_blank"}

Ga terug naar [ GenStudio for Performance Marketing - Uitbreidbaarheid ](./genstudioext.md){target="_blank"}

Ga terug naar [ Alle Modules ](./../../../overview.md){target="_blank"}
