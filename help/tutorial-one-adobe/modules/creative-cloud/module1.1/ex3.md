---
title: Werken met Photoshop API's
description: Leer hoe u met de Photoshop API's en Firefly Services kunt werken
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 60eecc24-1713-4fec-9ffa-a3186db1a8ca
source-git-commit: 8e410ad378d61f23d1d880d12e57f9d5e4e523c1
workflow-type: tm+mt
source-wordcount: '935'
ht-degree: 0%

---

# Werken met Photoshop API&#39;s

Leer hoe u met de Photoshop API&#39;s en Firefly Services werkt.

## De Adobe I/O-integratie bijwerken

1. Ga naar [ https://developer.adobe.com/console/home ](https://developer.adobe.com/console/home) {target="_blank"}.

![ Adobe I/O Nieuwe Integratie ](./images/iohome.png)

1. Ga naar **Projecten** en selecteer het project u in de vorige oefening creeerde, die `--aepUserLdap-- Firefly` wordt geroepen.

![ Azure Opslag ](./images/ps1.png)

1. Selecteer **+ toevoegen aan Project** en selecteer dan **API**.

![ Azure Opslag ](./images/ps2.png)

1. Selecteer **Creative Cloud** en kies **Photoshop - de Diensten van de Firefly**. Selecteer **daarna**.

![ Azure Opslag ](./images/ps3.png)

1. Selecteer **daarna**.

![ Azure Opslag ](./images/ps4.png)

Vervolgens moet u een productprofiel selecteren dat definieert welke machtigingen beschikbaar zijn voor deze integratie.

1. Selecteer de Configuratie van de Diensten van de Standaard van de Firefly **en** Configuratie van de Diensten van de Automatisering van het Standaard Creative Cloud **.**

1. Selecteer **sparen gevormde API**.

![ Azure Opslag ](./images/ps5.png)

Uw Adobe I/O-project wordt nu bijgewerkt en werkt nu met de API&#39;s van Photoshop en Firefly Services.

![ Azure Opslag ](./images/ps6.png)

## Programmatische interactie met een PSD-bestand

1. Download [ burgerschap-fiber.psd ](./../../../assets/ff/citisignal-fiber.psd){target="_blank"} aan uw Desktop.

1. Open **burgerschap-fiber.psd** in Photoshop.

![ Azure Opslag ](./images/ps7.png)

In de **ruit van Lagen**, heeft de ontwerper van het dossier een unieke naam aan elke laag gegeven. U kunt de laaginformatie zien door het dossier van de PSD in Photoshop te openen, maar u kunt dit programmatically ook doen.

Stuur uw eerste API-aanvraag naar Photoshop API&#39;s.

1. Voordat u in Postman API-aanvragen naar Photoshop verzendt, moet u zich verifiëren bij Adobe I/O. Open het vorige verzoek met de naam **POST - krijg het Token van de Toegang**.

1. Ga naar **Params** en verifieer dat de parameter **Reikwijdte** behoorlijk wordt geplaatst. De **Waarde** voor **Reikwijdte** zou als dit moeten kijken:

`openid,session,AdobeID,read_organizations,additional_info.projectedProductContext, ff_apis, firefly_api`

1. Selecteer **verzenden**.

![ Azure Opslag ](./images/ps8.png)

Nu hebt u een geldig toegangstoken om met Photoshop APIs in wisselwerking te staan.

![ Azure Opslag ](./images/ps9.png)

### Photoshop API - Hello World

Laten we nu de groeten overbrengen aan Photoshop API&#39;s om te testen of alle machtigingen en toegangsrechten correct zijn ingesteld.

1. In de inzameling **Photoshop**, open verzoek **Photoshop Hello (de Auth van de Test.)**. Selecteer **verzenden**.

![ Azure Opslag ](./images/ps10.png)

U zou het antwoord **Onthaal aan Photoshop API moeten ontvangen!**.

![ Azure Opslag ](./images/ps11.png)

Daarna, om programmatically met het dossier van PSD **te interactie aan te gaan** wordt  gebruikt   , moet u het aan uw opslagrekening uploaden. U kunt dat handmatig doen, door het bestand met Azure Storage Explorer naar uw container te slepen en neer te zetten, maar dit keer moet u het doen via de API.

### PSD uploaden naar Azure

1. In Postman, open het verzoek **uploadt PSD naar de Rekening van de Opslag Azure**. In de vorige oefening, vormde u deze milieuvariabelen in Postman, die u nu zult gebruiken:

- `AZURE_STORAGE_URL`
- `AZURE_STORAGE_CONTAINER`
- `AZURE_STORAGE_SAS_READ`
- `AZURE_STORAGE_SAS_WRITE`

Aangezien u in het verzoek **kunt zien uploadt PSD aan de Rekening van de Opslag Azure**, wordt URL gevormd om deze variabelen te gebruiken.

![ Azure Opslag ](./images/ps12.png)

1. In **Lichaam**, selecteer het dossier **burgerschap-fiber.psd**.

![ Azure Opslag ](./images/ps13.png)

1. Het scherm moet er zo uitzien. Selecteer **verzenden**.

![ Azure Opslag ](./images/ps14.png)

Deze lege reactie moet u terugkrijgen vanuit Azure, wat betekent dat uw bestand in uw container wordt opgeslagen in uw Azure Storage-account.

![ Azure Opslag ](./images/ps15.png)

Als u Azure Storage Explorer gebruikt om uw bestand te bekijken, moet u de map vernieuwen.

![ Azure Opslag ](./images/ps16.png)

### Photoshop API - Get manifest

Vervolgens moet u het manifestbestand van uw PSD-bestand ophalen.

1. In Postman, open het verzoek **Photoshop - krijg PSD Manifest**. Ga naar **Lichaam**.

Het lichaam moet er als volgt uitzien:

```json
{
  "inputs": [
    {
      "storage": "external",
      "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/citisignal-fiber.psd{{AZURE_STORAGE_SAS_READ}}"
    }
  ],
  "options": {
    "thumbnails": {
      "type": "image/jpeg"
    }
  }
}
```

1. Selecteer **verzenden**.

In het antwoord ziet u nu een koppeling. Aangezien het soms enige tijd kan duren om bewerkingen in Photoshop uit te voeren, verschaft Photoshop een statusbestand als antwoord op de meeste binnenkomende aanvragen. Als u wilt weten wat er met uw verzoek gebeurt, moet u het statusbestand lezen.

![ Azure Opslag ](./images/ps17.png)

1. Om het statusdossier te lezen, open het verzoek **Photoshop - krijgt PS Status**. U kunt zien dat dit verzoek een variabele als URL gebruikt, die een variabele is die door het vorige verzoek wordt geplaatst dat u verzendt, **Photoshop - krijgt PSD Manifest**. De variabelen worden geplaatst in **Manuscripten** van elk verzoek. Selecteer **verzenden**.

![ Azure Opslag ](./images/ps18.png)

Het scherm moet er zo uitzien. Momenteel, wordt de status geplaatst aan **hangend**, wat betekent dat het proces nog niet heeft voltooid.

![ Azure Opslag ](./images/ps19.png)

1. Selecteer verzenden een paar meer tijden op **Photoshop - krijgt PS Status**, tot de statusveranderingen in **succesvol**. Dit kan een paar minuten duren.

Wanneer de reactie beschikbaar is, kunt u zien het JSON-bestand informatie bevat over alle lagen van het PSD-bestand. Dit is nuttige informatie, aangezien de dingen zoals de laagnaam of laagidentiteitskaart kunnen worden geïdentificeerd.

![ Azure Opslag ](./images/ps20.png)

Zoek bijvoorbeeld naar de tekst `2048x2048-cta` . Uw scherm moet er als volgt uitzien:

![ Azure Opslag ](./images/ps21.png)

### Photoshop API - Tekst wijzigen

Vervolgens moet u de tekst wijzigen voor de aanroep naar actie met behulp van de API&#39;s.

1. In Postman, open het verzoek **Photoshop - de Tekst van de Verandering** en ga naar **Lichaam**.

Uw scherm moet er als volgt uitzien:

- eerst wordt een invoerbestand opgegeven: `citisignal-fiber.psd`
- vervolgens wordt de te wijzigen laag opgegeven, waarbij de tekst moet worden gewijzigd in
- ten derde wordt een uitvoerbestand opgegeven: `citisignal-fiber-changed-text.psd`

```json
{
  "inputs": [
    {
      "storage": "external",
      "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/citisignal-fiber.psd{{AZURE_STORAGE_SAS_READ}}"
    }
  ],
  "options": {
    "layers": [
      {
        "name": "2048x2048-cta",
        "text": {
          "content": "Get Fiber now!"
        }
      }
    ]
  },
  "outputs": [
    {
      "storage": "azure",
      "href": "{{AZURE_STORAGE_URL}}/{{AZURE_STORAGE_CONTAINER}}/citisignal-fiber-changed-text.psd{{AZURE_STORAGE_SAS_WRITE}}",
      "type": "vnd.adobe.photoshop",
      "overwrite": true
    }
  ]
}
```

Het uitvoerbestand heeft een andere naam, omdat u het oorspronkelijke invoerbestand niet wilt overschrijven.

1. Selecteer **verzenden**.

![ Azure Opslag ](./images/ps23.png)

Net als voorheen bevat het antwoord een koppeling die verwijst naar het statusbestand en de voortgang bijhoudt.

![ Azure Opslag ](./images/ps22.png)

1. Om het statusdossier te lezen, open het verzoek **Photoshop - krijg PS Status** en selecteer **verzend**. Als de status niet aan **wordt geplaatst slaagde** onmiddellijk, wacht een paar seconden en selecteert dan **verzend** opnieuw.

1. Selecteer de URL om het uitvoerbestand te downloaden.

![ Azure Opslag ](./images/ps24.png)

1. Open **burgerschap-vezel-veranderd-text.psd** na het downloaden van het dossier aan uw computer. U zou placeholder voor de vraag aan actie moeten zien is vervangen door de tekst **krijgt nu Vezel!**.

![ Azure Opslag ](./images/ps25.png)

U kunt dit bestand ook in uw container zien met Azure Storage Explorer.

![ Azure Opslag ](./images/ps26.png)

## Volgende stappen

Ga naar [ Modellen API van de Aangepaste Firefly ](./ex4.md){target="_blank"}

Ga terug naar [ Overzicht van de Diensten van de Adobe Firefly ](./firefly-services.md){target="_blank"}

Ga terug naar [ Alle Modules ](./../../../overview.md){target="_blank"}