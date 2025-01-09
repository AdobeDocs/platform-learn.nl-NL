---
title: Aan de slag met Firefly Services
description: Aan de slag met Firefly Services
kt: 5342
doc-type: tutorial
exl-id: 5f9803a4-135c-4470-bfbb-a298ab1fee33
source-git-commit: 6c344db00b8296c8ea6d31c83cefd8edcddb51b1
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 0%

---

# 1.1.2 Optimaliseer uw Firefly met Microsoft Azure en vooraf ondertekende URL&#39;s

## 1.1.2.1 Een Azure-abonnement maken

>[!NOTE]
>
>Als u al een bestaand Azure-abonnement hebt, kunt u deze stap overslaan. Ga in dat geval verder met de volgende exercitie.

Ga naar [ https://portal.azure.com ](https://portal.azure.com) en login met uw Azure rekening. Als je er geen hebt, gebruik dan je persoonlijke e-mailadres om je Azure-account te maken.

![ Azure Opslag ](./images/02azureportalemail.png)

Na succesvolle login zult u het volgende scherm zien:

![ Azure Opslag ](./images/03azureloggedin.png)

Klik op het aan linkermenu en selecteer **Alle Middelen**, zal het Azure abonnementsscherm verschijnen als u nog niet wordt ingetekend. In dat geval uitgezocht **Begin met een Azure vrije Proef**.

![ Azure Opslag ](./images/04azurestartsubscribe.png)

Vul het Azure-abonnementsformulier in, geef uw mobiele telefoon en creditcard op voor activering (u hebt 30 dagen een gratis label en u wordt geen kosten in rekening gebracht, tenzij u een upgrade uitvoert).

Als het abonnementsproces is voltooid, kunt u het beste gaan:

![ Azure Opslag ](./images/06azuresubscriptionok.png)

## 1.1.2.2 Azure Storage Account maken

Onderzoek naar `storage account` en klik dan **rekeningen van de Opslag**.

![ Azure Opslag ](./images/azs1.png)

Klik op **+ Maken** .

![ Azure Opslag ](./images/azs2.png)

Vul de volgende gegevens in:

- Selecteer uw **Abonnement**
- Selecteer (of creeer) de groep van het Middel van a ****
- **de rekeningsnaam van de Opslag**: gebruik `--aepUserLdap--`

Klik **Overzicht + creeer**.

![ Azure Opslag ](./images/azs3.png)

Klik **creëren**.

![ Azure Opslag ](./images/azs4.png)

Je krijgt dan een vergelijkbare bevestiging. Klik **gaan naar middel**.

![ Azure Opslag ](./images/azs5.png)

Uw Azure-opslagaccount is nu klaar om te worden gebruikt.

![ Azure Opslag ](./images/azs6.png)

Klik {de Opslag van 0} Gegevens **en ga dan naar** Containers **.** Klik op **+ Container** .

![ Azure Opslag ](./images/azs7.png)

Gebruik `--aepUserLdap--` voor de naam. Klik **creëren**.

![ Azure Opslag ](./images/azs8.png)

Uw container is nu klaar om te worden gebruikt.

![ Azure Opslag ](./images/azs9.png)

## 1.1.2.3 Azure Storage Explorer installeren

U gebruikt Microsoft Azure Storage Explorer om uw bestanden te beheren. U kunt het via [ deze verbinding ](https://azure.microsoft.com/en-us/products/storage/storage-explorer#Download-4) downloaden. Selecteer de juiste versie voor uw specifieke besturingssysteem, download deze en installeer deze.

![ Azure Opslag ](./images/az10.png)

Open de toepassing nadat deze is geïnstalleerd. Je zult iets gelijkaardigs zien. Klik **Teken binnen met Azure**.

![ Azure Opslag ](./images/az11.png)

Klik **Abonnement**.

![ Azure Opslag ](./images/az12.png)

Selecteer **Azure** en klik **daarna**.

![ Azure Opslag ](./images/az13.png)

Selecteer uw Microsoft Azure-account en voltooi het verificatieproces.

![ Azure Opslag ](./images/az14.png)

Zodra voor authentiek verklaard, zult u een bericht als dit zien.

![ Azure Opslag ](./images/az15.png)

Ga terug naar de Microsoft Azure Storage Explorer-app. Selecteer uw abonnement en klik **Open Ontdekkingsreiziger**.

![ Azure Opslag ](./images/az16.png)

U zult dan uw opslagrekening onder **Rekeningen van de Opslag** vinden.

![ Azure Opslag ](./images/az17.png)

Open **Containers van de Klodder** en klik dan de container u in de vorige oefening creeerde.

![ Azure Opslag ](./images/az18.png)

## 1.1.2.4 Handmatig bestanden uploaden en een afbeeldingsbestand gebruiken als stijlreferentie

U moet nu een afbeeldingsbestand naar keuze in uw container uploaden. U kunt om het even welk beelddossier van keus gebruiken, of u kunt [ dit dossier ](./images/gradient.jpg) gebruiken door het uw computer te downloaden.

![ Azure Opslag ](./images/gradient.jpg)

Zet het afbeeldingsbestand neer in uw container in Azure Storage Explorer.

Na het uploaden ziet u het in uw container:

![ Azure Opslag ](./images/az19.png)

Klik uw dossier `gradient.jpg` met de rechtermuisknop aan en klik dan **krijgen de Gedeelde Handtekening van de Toegang**.

![ Azure Opslag ](./images/az20.png)

Onder **Toestemmingen**, slechts **Gelezen** wordt vereist. Klik **creëren**.

![ Azure Opslag ](./images/az21.png)

Vervolgens ziet u de vooraf ondertekende URL voor dit afbeeldingsbestand. Kopieer het naar wens voor de volgende API-aanvraag naar de Firefly.

![ Azure Opslag ](./images/az22.png)

Ga terug naar Postman. Open het verzoek **POST - Firefly - T2I (styleref) V3**. U zult dan dit in **Lichaam** zien.

![ Azure Opslag ](./images/az23.png)

Vervang de tijdelijke aanduiding-URL door de vooraf ondertekende URL voor het afbeeldingsbestand die u hebt gekopieerd vanuit Azure Storage Explorer. Dan heb je dit. Klik **verzenden**.

![ Azure Opslag ](./images/az24.png)

U zult dan een reactie van de Diensten van de Firefly opnieuw, met een nieuw beeld krijgen. Open het afbeeldingsbestand in uw browser.

![ Azure Opslag ](./images/az25.png)

Vervolgens ziet u een andere afbeelding met `horses in a field` , maar deze keer lijkt de stijl op het afbeeldingsbestand dat u als stijlverwijzing hebt opgegeven.

![ Azure Opslag ](./images/az26.png)

## 1.1.2.5 Programmatische bestandsupload

Om programmatic dossier te gebruiken uploadt met de Rekeningen van de Opslag Azure, zult u een nieuw **Gedeelde handtekening van de Toegang (SAS)** token, met toestemmingen moeten tot stand brengen die u toestaan om een dossier te schrijven.

Ga hiervoor terug naar Azure Storage Explorer. Klik uw container met de rechtermuisknop aan, en klik dan **krijgen de Gedeelde Handtekening van de Toegang**.

![ Azure Opslag ](./images/az27.png)

Onder **Toestemmingen**, worden de volgende toestemmingen vereist:

- **Gelezen**
- **voeg toe**
- **creeer**
- **schrijf**
- **Lijst**

Klik **creëren**.

![ Azure Opslag ](./images/az28.png)

U zult dan uw **SAS-teken** krijgen. Klik **Exemplaar**.

![ Azure Opslag ](./images/az29.png)

U kunt dit **SAS-teken** nu gebruiken om een dossier in uw Azure Rekening van de Opslag te uploaden. Ga terug naar Postman om dat te doen.

Klik om de omslag **te selecteren FF - de Technologische Instanties van de Diensten van de Firefly**, dan klik de 3 punten **..** op de omslag **Firefly** en klik dan **verzoek** toevoegen.

![ Azure Opslag ](./images/az30.png)

U hebt dan een leeg verzoek. Verander de naam van het verzoek aan **uploadt dossier aan de Rekening van de opslag Azure**, verander het **Type van Verzoek** in **PUT** en kleef SAS-token URL in de sectie URL.

Dan, klik **Lichaam**.

![ Azure Opslag ](./images/az31.png)

U moet nu een bestand op uw lokale computer selecteren. U kunt een nieuw beelddossier van keus gebruiken, of u kunt een ander beelddossier gebruiken dat u [ hier ](./images/gradient2-p.jpg) kunt vinden.

![ dossier van de Gradiënt ](./images/gradient2-p.jpg)

In **Lichaam**, selecteer **binair** en klik dan **Uitgezochte dossier**, dan klik **+ Nieuw dossier van lokale machine**.

![ Azure Opslag ](./images/az32.png)

Selecteer uw dossier van keus en klik **Open**.

![ Azure Opslag ](./images/az33.png)

Dan zie je dit. Het volgende dat u moet doen, is het opgeven van de bestandsnaam die wordt gebruikt in uw Azure Storage Account. Om dat te doen, moet u uw cursos voor het vraagteken plaatsen **?** in de URL. U kunt dit hier op dit moment zien:

![ Azure Opslag ](./images/az34.png)

De URL ziet er momenteel als volgt uit, maar moet worden gewijzigd.

`https://vangeluw.blob.core.windows.net/vangeluw?sv=2023-01-03...`

De te gebruiken bestandsnaam is `gradient2-p.jpg` . Dat betekent dat de URL moet worden gewijzigd om de bestandsnaam op te nemen, zoals in het volgende voorbeeld:

`https://vangeluw.blob.core.windows.net/vangeluw/gradient2-p.jpg?sv=2023-01-03...`

![ Azure Opslag ](./images/az34a.png)

Daarna, ga naar **Kopballen** waar u een nieuwe kopbal moet manueel toevoegen. Gebruik deze:

| Sleutel | Waarde |
|:-------------:| :---------------:| 
| `x-ms-blob-type` | `BlockBlob` |


![ Azure Opslag ](./images/az35.png)

Ga naar **Vergunning** en plaats het **Type van Auth** aan **Geen Auth**. Klik **verzenden**.

![ Azure Opslag ](./images/az36.png)

Deze lege reactie wordt dan weergegeven in Postman, wat betekent dat het uploaden van het bestand goed is gegaan.

![ Azure Opslag ](./images/az37.png)

Als u vervolgens teruggaat naar Azure Storage Explorer en de inhoud van uw map vernieuwt, vindt u nu het zojuist geüploade bestand.

![ Azure Opslag ](./images/az38.png)

## 1.1.2.5 Programmatisch bestandsgebruik

Om programmatically te gebruiken lees dossiers van de Rekeningen van de Opslag van Azure, zult u een nieuw **Gedeelde handtekening van de Toegang (SAS)**, met toestemmingen moeten tot stand brengen die u toestaan om een dossier te lezen. U kon SAS-teken technisch gebruiken u in de vorige oefening creeerde, maar het is beste praktijken om een afzonderlijk teken met slechts **Gelezen** toestemmingen te hebben.

Ga hiervoor terug naar Azure Storage Explorer. Klik uw container met de rechtermuisknop aan, en klik dan **krijgen de Gedeelde Handtekening van de Toegang**.

![ Azure Opslag ](./images/az27.png)

Onder **Toestemmingen**, worden de volgende toestemmingen vereist:

- **Gelezen**
- **voeg toe**
- **creeer**
- **schrijf**
- **Lijst**

Klik **creëren**.

![ Azure Opslag ](./images/az28.png)


Volgende Stap: [ 1.1.3.. ](./ex3.md)

[Terug naar module 1.1](./firefly-services.md)

[Terug naar alle modules](./../../../overview.md)
