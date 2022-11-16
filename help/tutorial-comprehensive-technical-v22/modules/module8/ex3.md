---
title: Adobe Journey Optimizer - External Weather API, SMS-actie en meer - Aangepaste acties definiëren
description: Adobe Journey Optimizer - External Weather API, SMS-actie en meer - Aangepaste acties definiëren
kt: 5342
audience: Data Engineer, Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
exl-id: 7ee5aee9-3740-4eee-9f53-a44fdb564a00
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 0%

---

# 8.3 Een aangepaste handeling definiëren

In deze oefening, zult u twee douaneacties creëren door gebruik van Adobe Journey Optimizer in combinatie te maken.

Aanmelden bij Adobe Journey Optimizer door naar [Adobe Experience Cloud](https://experience.adobe.com). Klikken **Journey Optimizer**.

![ACOP](../module7/images/acophome.png)

U wordt omgeleid naar de **Home**  in Journey Optimizer. Eerst, zorg ervoor u de correcte zandbak gebruikt. De sandbox die moet worden gebruikt, wordt `--aepSandboxId--`. Als u van de ene naar de andere sandbox wilt gaan, klikt u op **PRODUCTIEVOORRAAD (VA7)** en selecteert u de sandbox in de lijst. In dit voorbeeld krijgt de sandbox een naam **AEP-activering FY22**. Dan ben je in de **Home** weergave van de sandbox `--aepSandboxId--`.

![ACOP](../module7/images/acoptriglp.png)

Blader in het linkermenu omlaag en klik op **Configuraties**. Klik op de knop **Beheren** knop onder **Handelingen**.

![Demo](./images/menuactions.png)

Dan zie je de **Handelingen** lijst.

![Demo](./images/acthome.png)

U definieert één handeling die een tekst naar een Slack-kanaal verzendt.

## 8.3.1 Actie: Tekst verzenden naar kanaal Slack

U zult nu een bestaand kanaal van Slack gebruiken en berichten verzenden naar dat Kanaal van Slack. Slack heeft een eenvoudig te gebruiken API en wij zullen Adobe Journey Optimizer gebruiken om hun API teweeg te brengen.

![Demo](./images/slack.png)

Klikken **Handeling maken** om een nieuwe handeling toe te voegen.

![Demo](./images/adda.png)

Er verschijnt een leeg actiepopup.

![Demo](./images/emptyact.png)

Als naam voor de handeling gebruikt u `--demoProfileLdap--TextSlack`. In dit voorbeeld is de naam van de handeling `vangeluwTextSlack`.

Beschrijving instellen op: `Send Text to Slack`.

![Demo](./images/slackname.png)

Voor de **URL-configuratie** Gebruik deze optie:

- URL: `https://2mnbfjyrre.execute-api.us-west-2.amazonaws.com/prod`
- Methode: **POST**

>[!NOTE]
>
>De bovenstaande URL verwijst naar een AWS Lambda-functie die uw verzoek doorstuurt naar het Slack-kanaal zoals hierboven vermeld. Dit wordt gedaan om toegang tot een Adobe-Bezit Slack kanaal te beschermen. Als u uw eigen Slack-kanaal hebt, kunt u beter een Slack-app maken via [https://api.slack.com/](https://api.slack.com/), moet u dan een Inkomende Webhaak in die app van Slack tot stand brengen, en dan bovengenoemde URL vervangen door uw Inkomende URL Webhaak.

U hoeft de koptekstvelden niet te wijzigen.

![Demo](./images/slackurl.png)

**Verificatie** moet worden ingesteld op **Geen verificatie**.

![Demo](./images/slackauth.png)

Voor de **Handelingsparameters**, moet u bepalen welke velden naar Slack moeten worden verzonden. Logischerwijze willen we dat Adobe Journey Optimizer en Adobe Experience Platform het brein van personalisatie zijn, dus de tekst die naar Slack moet worden gestuurd, moet door Adobe Journey Optimizer worden gedefinieerd en vervolgens naar Slack worden gestuurd voor executie.

Dus voor de **Handelingsparameters** klikt u op de knop **Payload bewerken** pictogram.

![Demo](./images/slackmsgp.png)

Dan zie je een leeg popup-venster.

![Demo](./images/slackmsgpopup.png)

Kopieer de onderste tekst en plak deze in het lege pop-upvenster.

```json
{
 "text": {
  "toBeMapped": true,
  "dataType": "string",
  "label": "textToSlack"
 }
}
```

FYI: Door de onderstaande velden op te geven, worden deze velden toegankelijk vanaf uw Klantenreis en kunt u ze dynamisch vanuit de Reis vullen:

**&quot;toBeMapping&quot;: true,**

**&quot;dataType&quot;: &quot;string&quot;,**

**&quot;label&quot;: &quot;textToSlack&quot;**

U zult dan dit zien:

![Demo](./images/slackmsgpopup1.png)

Klikken **Opslaan**.

![Demo](./images/twiliomsgpopup2.png)

Omhoog schuiven en klikken **Opslaan** nog een keer om uw aangepaste handeling op te slaan.

![Demo](./images/slackmsgpopup3.png)

Uw aangepaste handeling maakt nu deel uit van de **Handelingen** lijst.

![Demo](./images/slackdone.png)

U hebt gebeurtenissen, externe gegevensbronnen en acties gedefinieerd. Laten we dat allemaal op één reis consolideren.

Volgende stap: [8.4 Maak uw reis en uw berichten](./ex4.md)

[Ga terug naar module 8](journey-orchestration-external-weather-api-sms.md)

[Terug naar alle modules](../../overview.md)
