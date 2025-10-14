---
title: GenStudio for Performance Marketing maakt uw Amazon AWS S3-emmertje
description: GenStudio for Performance Marketing maakt uw Amazon AWS S3-emmertje
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 044677e4-7ca3-4dfe-9067-640983681ea7
source-git-commit: 1f9a868c5e4ef4aa0e09d7f5d73a951006ee6c5a
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# 1.6.2 Een AWS S3-emmertje maken

## 1.6.2.1 Een S3-emmertje maken

Ga naar [&#x200B; https://console.aws.amazon.com &#x200B;](https://console.aws.amazon.com) en teken binnen.

>[!NOTE]
>
>Als je nog geen AWS-account hebt, maak dan een nieuwe AWS-account aan met je persoonlijke e-mailadres.

![&#x200B; ETL &#x200B;](./images/awshome.png)

Na het programma openen, zult u aan de **Console van het Beheer van AWS** opnieuw worden gericht.

![&#x200B; ETL &#x200B;](./images/awsconsole.png)

In de onderzoeksbar, onderzoek naar **s3**. Klik het eerste onderzoeksresultaat: **S3 - Schaalbare Opslag in de Wolk**.

![&#x200B; ETL &#x200B;](./images/awsconsoles3.png)

U zult dan de **homepage van Amazon S3** zien. Klik **creëren Emmertje**.

![&#x200B; ETL &#x200B;](./images/s3home.png)

In **creeer het 1&rbrace; scherm van het Emmertje &lbrace;, gebruik de naam**.`--aepUserLdap---gspem-dam`

![&#x200B; ETL &#x200B;](./images/bucketname.png)

Laat alle andere standaardinstellingen ongewijzigd. De rol neer en klikt **creeert emmer**.

![&#x200B; ETL &#x200B;](./images/createbucket.png)

Vervolgens ziet u dat uw emmer is gemaakt en wordt deze omgeleid naar de startpagina van Amazon S3.

![&#x200B; ETL &#x200B;](./images/S3homeb.png)

## Toestemmingen plaatsen om tot uw S3 emmertje toegang te hebben

De volgende stap is toegang tot uw S3 emmertje te plaatsen.

Om dat te doen, ga naar [&#x200B; https://console.aws.amazon.com/iam/home &#x200B;](https://console.aws.amazon.com/iam/home).

De toegang tot AWS-bronnen wordt beheerd door Amazon Identity and Access Management (IAM).

U ziet deze pagina nu.

![&#x200B; ETL &#x200B;](./images/iam.png)

In het linkermenu, klik **Gebruikers**. U zult dan het **scherm van Gebruikers** zien. Klik **creëren gebruiker**.

![&#x200B; ETL &#x200B;](./images/iammenu.png)

Configureer vervolgens de gebruiker:

- Gebruikersnaam: gebruik `s3_--aepUserLdap--_gspem_dam`

Klik **daarna**.

![&#x200B; ETL &#x200B;](./images/configuser.png)

U zult dan dit toestemmingenscherm zien. Klik **beleid van de Band direct**.

![&#x200B; ETL &#x200B;](./images/perm1.png)

Ga de onderzoekstermijn **s3** in om al verwant S3 beleid te zien. Selecteer het beleid **AmazonS3FullAccess**. De rol neer en klikt **daarna**.

![&#x200B; ETL &#x200B;](./images/perm2.png)

Controleer uw configuratie. Klik **creëren Gebruiker**.

![&#x200B; ETL &#x200B;](./images/review.png)

Dan zie je dit. Klik **Gebruiker van de Mening**.

![&#x200B; ETL &#x200B;](./images/review1.png)

Klik **geloofsbrieven van de Veiligheid** en klik dan **creeer toegangssleutel**.

![&#x200B; ETL &#x200B;](./images/cred.png)

Selecteer **Toepassing die buiten AWS** loopt. De rol neer en klikt **daarna**.

![&#x200B; ETL &#x200B;](./images/creda.png)

Klik **creëren toegangssleutel**

![&#x200B; ETL &#x200B;](./images/credb.png)

Dan zie je dit. Klik **tonen** om uw Geheime toegangstoets te zien:

![&#x200B; ETL &#x200B;](./images/cred1.png)

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

![&#x200B; ETL &#x200B;](./images/cred2.png)

U hebt nu een AWS S3 emmertje met succes gecreeerd en u hebt een gebruiker met toestemmingen gecreeerd om tot dit emmertje toegang te hebben.

## 1.6.2.2 Assets uploaden naar uw S3-emmertje

In de onderzoeksbar, onderzoek naar **s3**. Klik het eerste onderzoeksresultaat: **S3 - Schaalbare Opslag in de Wolk**.

![&#x200B; ETL &#x200B;](./images/bucket1.png)

Klik om het nieuwe S3 emmertje te openen, dat `--aepUserLdap---gspem-dam` zou moeten worden genoemd.

![&#x200B; ETL &#x200B;](./images/bucket2.png)

Klik **uploaden**.

![&#x200B; ETL &#x200B;](./images/bucket3.png)

Dan moet je dit zien.

![&#x200B; ETL &#x200B;](./images/bucket4.png)

U kunt CitiSignal beelddossiers [&#x200B; hier downloaden &#x200B;](./images/package.zip){target="_blank"}.

Exporteer de bestanden naar uw bureaublad.

![&#x200B; ETL &#x200B;](./images/bucket5.png)

Klik **toevoegen Omslag**.

![&#x200B; ETL &#x200B;](./images/bucket6.png)

Selecteer de omslag **activa** van het pakket van de downloadomslag **&#x200B;**. Klik **uploaden**.

![&#x200B; ETL &#x200B;](./images/bucket7.png)

Dan moet je dit zien. Klik **voeg opnieuw Omslag** toe.

![&#x200B; ETL &#x200B;](./images/bucket8.png)

Selecteer de omslag **duimnagels** van het pakket van de downloadomslag **&#x200B;**. Klik **uploaden**.

![&#x200B; ETL &#x200B;](./images/bucket9.png)

Dan moet je dit zien. Klik **uploaden**.

![&#x200B; ETL &#x200B;](./images/bucket10.png)

Het uploaden is nu voltooid. Klik **dicht**.

![&#x200B; ETL &#x200B;](./images/bucket11.png)

U zou deze omslagstructuur in uw S3 emmertje nu moeten hebben.

![&#x200B; ETL &#x200B;](./images/bucket12.png)

## Volgende stappen

Ga naar [&#x200B; creeer uw externe toepassing DAM &#x200B;](./ex3.md){target="_blank"}

Ga terug naar [&#x200B; GenStudio for Performance Marketing - Uitbreidbaarheid &#x200B;](./genstudioext.md){target="_blank"}

Ga terug naar [&#x200B; Alle Modules &#x200B;](./../../../overview.md){target="_blank"}
