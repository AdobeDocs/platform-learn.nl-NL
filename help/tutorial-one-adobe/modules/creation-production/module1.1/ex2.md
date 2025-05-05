---
title: Uw Firefly-proces optimaliseren met Microsoft Azure en Presigned URL's
description: Leer hoe u uw Firefly-proces kunt optimaliseren met Microsoft Azure en vooraf ondertekende URL's
role: Developer
level: Beginner
jira: KT-5342
doc-type: tutorial
exl-id: 5f9803a4-135c-4470-bfbb-a298ab1fee33
source-git-commit: 45f6f9db7d5b3e79e10d508a44a532261bd9cdb3
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 0%

---

# 1.1.2 Optimaliseer uw Firefly-proces met Microsoft Azure en vooraf ondertekende URL&#39;s

Leer hoe u uw Firefly-proces kunt optimaliseren met Microsoft Azure en vooraf ondertekende URL&#39;s.

## 1.1.2.1 Een Azure-abonnement maken

>[!NOTE]
>
>Als u al een bestaand Azure-abonnement hebt, kunt u deze stap overslaan. Ga in dat geval verder met de volgende exercitie.

Ga naar [ https://portal.azure.com ](https://portal.azure.com){target="_blank"} en login met uw Azure rekening. Als je er geen hebt, gebruik dan je persoonlijke e-mailadres om je Azure-account te maken.

![ Azure Opslag ](./images/02azureportalemail.png){zoomable="yes"}

Na succesvolle login zou u het volgende scherm moeten zien:

![ Azure Opslag ](./images/03azureloggedin.png){zoomable="yes"}

Op het linkermenu uitgezocht **Alle Middelen**, verschijnt het Azure abonnementsscherm als u nog niet wordt ingetekend.

Als u niet wordt geabonneerd, uitgezochte **Begin met een Azure vrije Proef**.

![ Azure Opslag ](./images/04azurestartsubscribe.png){zoomable="yes"}

Vul het Azure-abonnementsformulier in en geef uw mobiele telefoon en creditcard op voor activering (u hebt 30 dagen een gratis label en u wordt geen kosten in rekening gebracht, tenzij u een upgrade uitvoert).

Als het abonnementsproces is voltooid, kunt u het beste gaan.

![ Azure Opslag ](./images/06azuresubscriptionok.png){zoomable="yes"}

## 1.1.2.2 Azure Storage Account maken

Onderzoek naar `storage account` en selecteer dan **rekeningen van de Opslag**.

![ Azure Opslag ](./images/azs1.png){zoomable="yes"}

Selecteer **+ creëren**.

![ Azure Opslag ](./images/azs2.png){zoomable="yes"}

Selecteer uw **Abonnement** en selecteer (of creeer) de groep van het Middel van a **&#x200B;**.

Onder **naam van de de rekeningsrekening van de Opslag** gebruik `--aepUserLdap--`.

Selecteer **Overzicht + creeer**.

![ Azure Opslag ](./images/azs3.png){zoomable="yes"}

Selecteer **creeer**.

![ Azure Opslag ](./images/azs4.png){zoomable="yes"}

Na bevestiging selecteert **ga naar middel**.

![ Azure Opslag ](./images/azs5.png){zoomable="yes"}

Uw Azure-opslagaccount is nu klaar om te worden gebruikt.

![ Azure Opslag ](./images/azs6.png){zoomable="yes"}

Selecteer **Opslag van Gegevens**, en ga dan naar **Containers**. Selecteer **+ Container**.

![ Azure Opslag ](./images/azs7.png){zoomable="yes"}

Het gebruik `--aepUserLdap--` voor de naam en selecteert **creeert**.

![ Azure Opslag ](./images/azs8.png){zoomable="yes"}

Uw container is nu klaar om te worden gebruikt.

![ Azure Opslag ](./images/azs9.png){zoomable="yes"}

## 1.1.2.3 Azure Storage Explorer installeren

[ Download Microsoft Azure Storage Explorer om uw dossiers ](https://azure.microsoft.com/en-us/products/storage/storage-explorer#Download-4){target="_blank"} te beheren. Selecteer de juiste versie voor uw specifieke besturingssysteem, download en installeer deze.

![ Azure Opslag ](./images/az10.png){zoomable="yes"}

Open de toepassing en selecteer **Teken binnen met Azure**.

![ Azure Opslag ](./images/az11.png){zoomable="yes"}

Selecteer **Abonnement**.

![ Azure Opslag ](./images/az12.png){zoomable="yes"}

Selecteer **Azure** en dan **daarna**.

![ Azure Opslag ](./images/az13.png){zoomable="yes"}

Selecteer uw Microsoft Azure-account en voltooi het verificatieproces.

![ Azure Opslag ](./images/az14.png){zoomable="yes"}

Na de verificatie wordt dit bericht weergegeven.

![ Azure Opslag ](./images/az15.png){zoomable="yes"}

Terug in Microsoft Azure de app van de Ontdekkingsreiziger van de Opslag, selecteer uw abonnement en kies **Open Ontdekkingsreiziger**.

>[!NOTE]
>
>Als uw rekening niet wordt getoond, klik het **versnelling** pictogram naast uw e-mailadres en selecteer **niet-filter**.

![ Azure Opslag ](./images/az16.png){zoomable="yes"}

Uw opslagrekening verschijnt onder **Rekeningen van de Opslag**.

![ Azure Opslag ](./images/az17.png){zoomable="yes"}

Open **Containers van de Klodder** en selecteer dan de container u in de vorige oefening creeerde.

![ Azure Opslag ](./images/az18.png){zoomable="yes"}

## 1.1.2.4 Handmatig bestanden uploaden en een afbeeldingsbestand gebruiken als stijlverwijzing

Upload een beelddossier van uw keus of [ dit dossier ](./images/gradient.jpg){target="_blank"} in de container.

![ Azure Opslag ](./images/gradient.jpg)

Na het uploaden kunt u het zien in uw container:

![ Azure Opslag ](./images/az19.png){zoomable="yes"}

Klik op `gradient.jpg` met de rechtermuisknop aan en selecteer dan **krijgen de Gedeelde Handtekening van de Toegang**.

![ Azure Opslag ](./images/az20.png){zoomable="yes"}

Onder **Toestemmingen**, slechts **Gelezen** wordt vereist. Selecteer **creeer**.

![ Azure Opslag ](./images/az21.png){zoomable="yes"}

Kopieer uw vooraf ondertekende URL voor dit afbeeldingsbestand voor de volgende API-aanvraag naar Firefly.

![ Azure Opslag ](./images/az22.png){zoomable="yes"}

Terug in Postman open het verzoek **POST - Firefly - T2I (styleref) V3**.
Dit verschijnt in **Lichaam**.

![ Azure Opslag ](./images/az23.png){zoomable="yes"}

Vervang placeholder URL met presigned URL voor uw beelddossier en selecteer **verzend**.

![ Azure Opslag ](./images/az24.png){zoomable="yes"}

Open de reactie Firefly Services nieuwe afbeelding in uw browser.

![ Azure Opslag ](./images/az25.png){zoomable="yes"}

Er wordt een andere afbeelding weergegeven bij `horses in a field` , maar deze keer lijkt de stijl op het afbeeldingsbestand dat u als stijlverwijzing hebt opgegeven.

![ Azure Opslag ](./images/az26.png){zoomable="yes"}

## 1.1.2.5 Programmatische bestandsupload

Om programmatic dossierupload met de Rekeningen van de Opslag te gebruiken Azure, moet u een nieuw **Gedeelde handtekening van de Toegang (SAS)** met toestemmingen tot stand brengen die u toestaan om een dossier te schrijven.

In de Verkenner van de Opslag van Azure, klik uw container met de rechtermuisknop aan, en selecteer **krijgen de Gedeelde Ondertekening van de Toegang**.

![ Azure Opslag ](./images/az27.png){zoomable="yes"}

Onder **Toestemmingen**, selecteer de volgende vereiste toestemmingen:

- **Gelezen**
- **voeg toe**
- **creeer**
- **schrijf**
- **Lijst**

Selecteer **creeer**.

![ Azure Opslag ](./images/az28.png){zoomable="yes"}

Na het ontvangen van uw **SAS-teken**, uitgezochte **Exemplaar**.

![ Azure Opslag ](./images/az29.png){zoomable="yes"}

Gebruik **SAS-teken** om een dossier in uw Azure Rekening van de Opslag te uploaden.

Terug in Postman, selecteer de omslag **FF - de Tech Insiders van Firefly Services**, dan uitgezocht **..** op de **Firefly** omslag, en selecteer dan **verzoek** toevoegen.

![ Azure Opslag ](./images/az30.png){zoomable="yes"}

Verander de naam van het lege verzoek aan **uploadt dossier aan de Rekening van de Opslag Azure**, verander het **Type van Verzoek** in **PUT** en kleef SAS-token URL in de sectie URL, dan uitgezochte **Lichaam**.

![ Azure Opslag ](./images/az31.png){zoomable="yes"}

Daarna, selecteer een dossier van uw lokale machine of gebruik een ander beelddossier dat [ hier ](./images/gradient2-p.jpg){target="_blank"} wordt gevestigd.

![ dossier van de Gradiënt ](./images/gradient2-p.jpg)

In **Lichaam**, selecteer **binair** toen **Uitgezochte dossier**, dan uitgezocht **+ Nieuw dossier van lokale machine**.

![ Azure Opslag ](./images/az32.png){zoomable="yes"}

Selecteer uw dossier van keus en selecteer **Open**.

![ Azure Opslag ](./images/az33.png){zoomable="yes"}

Geef vervolgens de bestandsnaam op die in uw Azure Storage Account moet worden gebruikt door de cursor vóór het vraagteken **te plaatsen?** in de URL als volgt:

![ Azure Opslag ](./images/az34.png){zoomable="yes"}

De URL ziet er momenteel als volgt uit, maar moet worden gewijzigd.

`https://vangeluw.blob.core.windows.net/vangeluw?sv=2023-01-03...`

Wijzig de bestandsnaam in `gradient2-p.jpg` en wijzig de URL zo en voeg de bestandsnaam als volgt toe:

`https://vangeluw.blob.core.windows.net/vangeluw/gradient2-p.jpg?sv=2023-01-03...`

![ Azure Opslag ](./images/az34a.png){zoomable="yes"}

Daarna, ga aan **Kopballen** om een nieuwe kopbal manueel als dit toe te voegen:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| `x-ms-blob-type` | `BlockBlob` |


![ Azure Opslag ](./images/az35.png){zoomable="yes"}

Ga naar **Vergunning** en plaats het **Type van Auth** aan **Geen Auth**, en selecteer **verzenden**.

![ Azure Opslag ](./images/az36.png){zoomable="yes"}

Vervolgens wordt deze lege reactie weergegeven in Postman, wat betekent dat het uploaden van het bestand is voltooid.

![ Azure Opslag ](./images/az37.png){zoomable="yes"}

In Azure Storage Explorer vernieuwt u de inhoud van uw map en wordt het nieuwe geüploade bestand weergegeven.

![ Azure Opslag ](./images/az38.png){zoomable="yes"}

## 1.1.2.6 Programmatisch bestandsgebruik

Om dossiers van de Rekeningen van de Opslag van Azure op lange termijn programmatically te lezen, moet u een nieuw **Gedeelde handtekening van de Toegang (SAS)** teken, met toestemmingen tot stand brengen die u toestaan om een dossier te lezen. Technisch kon u het SAS-teken gebruiken dat in de vorige oefening wordt gecreeerd, maar het is beste praktijken om een afzonderlijk teken met slechts **te hebben gelezen** toestemmingen en afzonderlijk teken met slechts **schrijft** toestemmingen.

### Leesbaar SAS-token op lange termijn

Ga terug naar Azure de Ontdekkingsreiziger van de Opslag, klik uw container met de rechtermuisknop aan en selecteer dan **krijgen de Gedeelde Ondertekening van de Toegang**.

![ Azure Opslag ](./images/az27.png){zoomable="yes"}

Onder **Toestemmingen**, selecteer de volgende vereiste toestemmingen:

- **Gelezen**
- **Lijst**

Plaats **Vervaltijd** aan 1 jaar van nu.

Selecteer **creeer**.

![ Azure Opslag ](./images/az100.png){zoomable="yes"}

Kopieer de URL en noteer deze in een bestand op uw computer om uw SAS-token voor de lange termijn met leesmachtigingen op te halen.

![ Azure Opslag ](./images/az101.png){zoomable="yes"}

Uw URL moet er als volgt uitzien:

`https://vangeluw.blob.core.windows.net/vangeluw?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`

U kunt enkele waarden afleiden van de bovenstaande URL:

- `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
- `AZURE_STORAGE_CONTAINER`: `vangeluw`
- `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`

### SAS-token voor schrijven op lange termijn

Ga terug naar Azure de Ontdekkingsreiziger van de Opslag, klik uw container met de rechtermuisknop aan en selecteer **krijgen de Gedeelde Ondertekening van de Toegang**.

![ Azure Opslag ](./images/az27.png){zoomable="yes"}

Onder **Toestemmingen**, selecteer de volgende vereiste toestemmingen:

- **Gelezen**
- **Lijst**
- **voeg toe**
- **creeer**
- **schrijf**

Plaats de **Vervaltijd** aan 1 jaar van nu.

Selecteer **creeer**.

![ Azure Opslag ](./images/az102.png){zoomable="yes"}

Kopieer de URL en noteer deze in een bestand op uw computer om uw SAS-token voor de lange termijn met leesmachtigingen op te halen.

![ Azure Opslag ](./images/az103.png){zoomable="yes"}

Uw URL moet er als volgt uitzien:

`https://vangeluw.blob.core.windows.net/vangeluw?sv=2023-01-03&st=2025-01-13T07%3A38%3A59Z&se=2026-01-14T07%3A38%3A00Z&sr=c&sp=acw&sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovExAdOCOCUdMk%3D`

U kunt enkele waarden afleiden van de bovenstaande URL:

- `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
- `AZURE_STORAGE_CONTAINER`: `vangeluw`
- `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`
- `AZURE_STORAGE_SAS_WRITE`: `?sv=2023-01-03&st=2025-01-13T07%3A38%3A59Z&se=2026-01-14T07%3A38%3A00Z&sr=c&sp=acw&sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovExAdOCOCUdMk%3D`

### Variabelen in Postman

Zoals u in de bovengenoemde sectie kunt zien, zijn er sommige gemeenschappelijke variabelen in zowel Gelezen als het Schrijven teken.

Vervolgens moet u in Postman variabelen maken die de verschillende elementen van de bovenstaande SAS-tokens opslaan. Er zijn enkele waarden die hetzelfde zijn in beide URL&#39;s:

- `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
- `AZURE_STORAGE_CONTAINER`: `vangeluw`
- `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`
- `AZURE_STORAGE_SAS_WRITE`: `?sv=2023-01-03&st=2025-01-13T07%3A38%3A59Z&se=2026-01-14T07%3A38%3A00Z&sr=c&sp=acw&sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovExAdOCOCUdMk%3D`

Voor toekomstige API-interacties is de elementnaam het belangrijkste wat verandert, terwijl de bovenstaande variabelen ongewijzigd blijven. In dat geval is het handig om variabelen te maken in Postman, zodat u ze niet telkens handmatig hoeft op te geven.

In Postman, uitgezochte **Milieu**, open **Alle variabelen** en selecteer **Milieu**.

![ Azure Opslag ](./images/az104.png){zoomable="yes"}

Creeer deze 4 variabelen in de lijst die wordt getoond en voor de kolommen **Aanvankelijke waarde** en **Huidige waarde**, ga uw specifieke persoonlijke waarden in.

- `AZURE_STORAGE_URL`: uw URL
- `AZURE_STORAGE_CONTAINER`: de naam van uw container
- `AZURE_STORAGE_SAS_READ`: uw SAS-leestoken
- `AZURE_STORAGE_SAS_WRITE`: uw SAS-schrijftoken

Selecteer **sparen**.

![ Azure Opslag ](./images/az105.png){zoomable="yes"}

### Variabelen in PostBuster

Zoals u in de bovengenoemde sectie kunt zien, zijn er sommige gemeenschappelijke variabelen in zowel Gelezen als het Schrijven teken.

Vervolgens moet u variabelen maken in PostBuster waarin de verschillende elementen van de bovenstaande SAS-tokens worden opgeslagen. Er zijn enkele waarden die hetzelfde zijn in beide URL&#39;s:

- `AZURE_STORAGE_URL`: `https://vangeluw.blob.core.windows.net`
- `AZURE_STORAGE_CONTAINER`: `vangeluw`
- `AZURE_STORAGE_SAS_READ`: `?sv=2023-01-03&st=2025-01-13T07%3A36%3A35Z&se=2026-01-14T07%3A36%3A00Z&sr=c&sp=rl&sig=4r%2FcSJLlt%2BSt9HdFdN0VzWURxRK6UqhB8TEvbWkmAag%3D`
- `AZURE_STORAGE_SAS_WRITE`: `?sv=2023-01-03&st=2025-01-13T07%3A38%3A59Z&se=2026-01-14T07%3A38%3A00Z&sr=c&sp=acw&sig=lR9%2FMUfyYLcBK7W9Kv7YJdYz5HEEEovExAdOCOCUdMk%3D`

Open Postbus. Selecteer **Milieu van de Basis** en klik dan **uitgeven** pictogram om het Milieu van de Basis te openen.

![ Azure Opslag ](./images/pbbe1.png)

Dan zie je 4 lege variabelen. Voer hier uw Azure Storage Account-gegevens in.

![ Azure Opslag ](./images/pbbe2.png)

Het bestand voor de basisomgeving moet er nu zo uitzien. Klik **dicht**.

![ Azure Opslag ](./images/pbbe3.png)

### Uw configuratie testen

In één van de vorige oefeningen, zag het **Lichaam** van uw verzoek **Firefly - T2I (styleref) V3** als dit:

`"url": "https://vangeluw.blob.core.windows.net/vangeluw/gradient.jpg?sv=2023-01-03&st=2025-01-13T07%3A16%3A52Z&se=2026-01-14T07%3A16%3A00Z&sr=b&sp=r&sig=x4B1XZuAx%2F6yUfhb28hF0wppCOMeH7Ip2iBjNK5A%2BFw%3D"`

![ Azure Opslag ](./images/az24.png){zoomable="yes"}

Wijzig de URL in:

`"url": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/gradient.jpg{{AZURE_STORAGE_SAS_READ}}"`

Selecteer **verzenden** om de veranderingen te testen u aanbracht.

![ Azure Opslag ](./images/az106.png){zoomable="yes"}

Als de variabelen correct zijn geconfigureerd, wordt een beeld-URL geretourneerd.

![ Azure Opslag ](./images/az107.png){zoomable="yes"}

Open de URL van de afbeelding om uw afbeelding te controleren.

![ Azure Opslag ](./images/az108.jpg)

## Volgende stappen

Ga naar [ Werkend met Photoshop APIs ](./ex3.md){target="_blank"}

Ga terug naar [ Overzicht van Adobe Firefly Services ](./firefly-services.md){target="_blank"}

Ga terug naar [ Alle Modules ](./../../../overview.md){target="_blank"}