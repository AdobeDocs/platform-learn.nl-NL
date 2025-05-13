---
title: Aan de slag - Adobe I/O
description: Aan de slag - Adobe I/O
kt: 5342
doc-type: tutorial
exl-id: 00f17d4f-a2c8-4e8e-a1ff-556037a60629
source-git-commit: 3b6ae4bb4eb2d9f189438dddc461bb0f2a0a9aac
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Uw Adobe I/O-project configureren

## Adobe I/O-project maken

In deze oefening, wordt Adobe I/O gebruikt om diverse eindpunten van Adobe te vragen. Voer de volgende stappen uit om Adobe I/O in te stellen.

Ga naar [ https://developer.adobe.com/console/home ](https://developer.adobe.com/console/home){target="_blank"}.

![ de Nieuwe Integratie van Adobe I/O ](./images/iohome.png){zoomable="yes"}

Selecteer de juiste instantie in de rechterbovenhoek van het scherm. Uw instantie is `--aepImsOrgName--` .

>[!NOTE]
>
> In de onderstaande schermafbeelding ziet u een specifieke org die wordt geselecteerd. Wanneer u door dit leerprogramma gaat, is het zeer waarschijnlijk dat uw org een verschillende naam heeft. Wanneer u zich hebt aangemeld voor deze zelfstudie, hebt u de te gebruiken omgevingsdetails ontvangen. Volg deze instructies.

Daarna, uitgezochte **creeer nieuw project**.

![ de Nieuwe Integratie van Adobe I/O ](./images/iocomp.png){zoomable="yes"}

### FIREFLY SERVICES API

Dan moet je dit zien. Selecteer **+ toevoegen aan Project** en kies **API**.

![ de Nieuwe Integratie van Adobe I/O ](./images/adobe_io_access_api.png){zoomable="yes"}

Het scherm moet er zo uitzien.

![ de Nieuwe Integratie van Adobe I/O ](./images/api1.png){zoomable="yes"}

Selecteer **Creative Cloud** en kies **Firefly - Firefly Services**, dan selecteer **daarna**.

![ de Nieuwe Integratie van Adobe I/O ](./images/api3.png){zoomable="yes"}

Verstrek een naam voor uw referentie: `--aepUserLdap-- - One Adobe OAuth credential` en selecteer **daarna**.

![ de Nieuwe Integratie van Adobe I/O ](./images/api4.png){zoomable="yes"}

Selecteer de standaardprofiel **StandaardConfiguratie van Firefly Services** en selecteer **sparen Gevormde API**.

![ de Nieuwe Integratie van Adobe I/O ](./images/api9.png){zoomable="yes"}

Dan moet je dit zien.

![ de Nieuwe Integratie van Adobe I/O ](./images/api10.png){zoomable="yes"}

### PHOTOSHOP SERVICES API

Selecteer **+ toevoegen aan Project** en selecteer dan **API**.

![ Azure Opslag ](./images/ps2.png){zoomable="yes"}

Selecteer **Creative Cloud** en kies **Photoshop - Firefly Services**. Selecteer **daarna**.

![ Azure Opslag ](./images/ps3.png){zoomable="yes"}

Selecteer **daarna**.

![ Azure Opslag ](./images/ps4.png){zoomable="yes"}

Vervolgens moet u een productprofiel selecteren dat definieert welke machtigingen beschikbaar zijn voor deze integratie.

Selecteer **de Configuratie van de StandaardFirefly Services** en **configuratie van de Diensten van de Automatisering van Creative Cloud**.

Selecteer **sparen gevormde API**.

![ Azure Opslag ](./images/ps5.png){zoomable="yes"}

Dan moet je dit zien.

![ de Nieuwe Integratie van Adobe I/O ](./images/ps7.png){zoomable="yes"}

### ADOBE EXPERIENCE PLATFORM API

Selecteer **+ toevoegen aan Project** en selecteer dan **API**.

![ Azure Opslag ](./images/aep1.png){zoomable="yes"}

Selecteer **Platform van de Ervaring van Adobe** en kies **Experience Platform API**. Selecteer **daarna**.

![ Azure Opslag ](./images/aep2.png){zoomable="yes"}

Selecteer **daarna**.

![ Azure Opslag ](./images/aep3.png){zoomable="yes"}

Vervolgens moet u een productprofiel selecteren dat definieert welke machtigingen beschikbaar zijn voor deze integratie.

Selecteer **Adobe Experience Platform - Alle Gebruikers - PROD**.

>[!NOTE]
>
>De naam van het productprofiel voor AEP is afhankelijk van de configuratie van de omgeving. Als u het bovengenoemde productprofiel niet ziet, kunt u een productprofiel hebben dat **Standaardproductie Al Toegang** wordt genoemd. Als u niet zeker bent welke u moet kiezen, vraagt u de beheerder van het AEP-systeem.

Selecteer **sparen gevormde API**.

![ Azure Opslag ](./images/aep4.png){zoomable="yes"}

Dan moet je dit zien.

![ de Nieuwe Integratie van Adobe I/O ](./images/aep5.png){zoomable="yes"}

### Projectnaam

Klik op de projectnaam.

![ de Nieuwe Integratie van Adobe I/O ](./images/api13.png){zoomable="yes"}

Selecteer **uitgeven Project**.

![ de Nieuwe Integratie van Adobe I/O ](./images/api14.png){zoomable="yes"}

Ga een vriendschappelijke naam voor uw integratie in: `--aepUserLdap-- One Adobe tutorial` en selecteer **sparen**.

![ de Nieuwe Integratie van Adobe I/O ](./images/api15.png){zoomable="yes"}

De installatie van uw Adobe I/O-project is nu voltooid.

![ de Nieuwe Integratie van Adobe I/O ](./images/api16.png){zoomable="yes"}

## Volgende stappen

Ga naar [ Optie 1: Opstelling van Postman ](./ex7.md){target="_blank"}

Ga naar [ Optie 2: Opstelling PostBuster ](./ex8.md){target="_blank"}

Ga terug naar [ Begonnen het worden ](./getting-started.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../overview.md){target="_blank"}
