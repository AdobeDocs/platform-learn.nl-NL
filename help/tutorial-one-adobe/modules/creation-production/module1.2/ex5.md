---
title: Frame.io en Workfront Fusion
description: Frame.io en Workfront Fusion
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 37de6ceb-833e-4e75-9201-88bddd38a817
source-git-commit: 7df1daa33a67f177ba07f3ca4add08ebc317973c
workflow-type: tm+mt
source-wordcount: '2674'
ht-degree: 0%

---

# 1.2.5 Frame.io en Workfront Fusion

In de vorige oefening vormde u het scenario `--aepUserLdap-- - Firefly + Photoshop` en vormde een inkomende webhaak om het scenario, en een webhaakreactie teweeg te brengen wanneer het scenario met succes voltooide. Vervolgens hebt u Postman gebruikt om dat scenario te activeren. Postman is een groot hulpmiddel voor het testen, maar in een echt bedrijfsscenario, zouden de bedrijfsgebruikers Postman niet gebruiken om een scenario teweeg te brengen. In plaats daarvan zouden ze een andere toepassing gebruiken en verwachten ze dat andere toepassing een scenario in Workfront Fusion activeert. In deze oefening, is dat precies wat u met Frame.io zult doen.

>[!NOTE]
>
>Om deze oefening met succes te voltooien, moet u een gebruiker Admin in uw Frame.io- rekening zijn. De onderstaande exercitie is gemaakt voor Frame.io V3 en wordt later bijgewerkt voor Frame.io V4.

## 1.2.5.1 Toegang tot Frame.io

Ga naar [ https://app.frame.io/projects ](https://app.frame.io/projects){target="_blank"}.

Klik het **+ pictogram** om uw eigen project in Frame.io tot stand te brengen.

![ Kader IO ](./images/frame1.png)

Ga de naam `--aepUserLdap--` in en klik **creeer Project**.

![ Kader IO ](./images/frame2.png)

U zult dan uw project in het linkermenu zien.
In één van de vorige oefeningen, downloadde u [ burgersignaal-fiber.psd ](./../../../assets/ff/citisignal-fiber.psd){target="_blank"} aan uw Desktop. Selecteer dat bestand en sleep het naar de net gemaakte projectmap.

![ Kader IO ](./images/frame3.png)

## 1.2.5.2 Workfront Fusion en Frame.io

In de vorige oefening, creeerde u het scenario `--aepUserLdap-- - Firefly + Photoshop`, dat met een douane webhaak begon en dat met een webshreactie beëindigde. Het gebruik van de webhaken werd vervolgens getest met Postman, maar het is duidelijk dat het punt van een dergelijk scenario moet worden genoemd door een externe toepassing. Zoals eerder vermeld, is Frame.io die oefening, maar tussen Frame.io en `--aepUserLdap-- - Firefly + Photoshop` is een ander Workfront Fusion-scenario nodig. u zult nu dat scenario vormen.

Ga naar [ https://experience.adobe.com/ ](https://experience.adobe.com/){target="_blank"}. Open **de Fusie van Workfront**.

![ WF Fusion ](./images/wffusion1.png)

In het linkermenu, ga naar **Scenario&#39;s** en selecteer uw omslag `--aepUserLdap--`. Klik **creeer een nieuw scenario**.

![ Kader IO ](./images/frame4.png)

Gebruik de naam `--aepUserLdap-- - Frame IO Custom Action` .

![ Kader IO ](./images/frame5.png)

Klik het **voorwerp van het vraagteken** op het canvas. Ga de tekst `webhook` in het onderzoeksvakje in en klik **Webhooks**.

![ Kader IO ](./images/frame6.png)

Klik **WebHaak van de Douane**.

![ Kader IO ](./images/frame7.png)

Klik **toevoegen** om een nieuwe webhaakURL tot stand te brengen.

![ Kader IO ](./images/frame8.png)

Voor de **naam van Webhaak**, gebruik `--aepUserLdap-- - Frame IO Custom Action Webhook`. Klik **sparen**.

![ Kader IO ](./images/frame9.png)

Dan moet je dit zien. Laat dit scherm open en onaangeroerd zoals u het in een volgende stap nodig hebt. U zult WebHaak URL in een volgende stap moeten kopiëren, door **adres van het Exemplaar aan klembord** te klikken.

![ Kader IO ](./images/frame10.png)

Ga naar [ https://developer.frame.io/ ](https://developer.frame.io/){target="_blank"}. Klik **TOOLS VAN DE ONTWIKKELAAR** en kies dan **de Acties van de Douane**.

![ Kader IO ](./images/frame11.png)

Klik **creeer een Actie van de Douane**.

![ Kader IO ](./images/frame12.png)

Voer de volgende waarden in:

- **NAAM**: gebruik `--aepUserLdap-- - Frame IO Custom Action Fusion`
- **BESCHRIJVING**: gebruik `--aepUserLdap-- - Frame IO Custom Action Fusion`
- **GEBEURTENIS**: gebruik `fusion.tutorial`.
- **URL**: ga URL van de webhaak in die u enkel in de Fusie van Workfront creeerde
- **TEAM**: selecteer het aangewezen team Frame.io, in dit geval, **Één Leerprogramma van Adobe**.

Klik **voorleggen**.

![ Kader IO ](./images/frame15.png)

Dan moet je dit zien.

![ Kader IO ](./images/frame14.png)

Ga terug naar [ https://app.frame.io/projects ](https://app.frame.io/projects){target="_blank"}. Vernieuw de pagina.

![ Kader IO ](./images/frame16.png)

Na het hebben van de pagina verfrist, klik de 3 punten **...** op de activa **burgersignaal-fiber.psd**. De aangepaste handeling die u eerder hebt gemaakt, wordt dan weergegeven in het menu dat wordt weergegeven. Klik op de aangepaste handeling `--aepUserLdap-- - Frame IO Custom Action Fusion` .

![ Kader IO ](./images/frame17.png)

U zou dan een gelijkaardig **Succes moeten zien!** popup. Deze pop-up is het resultaat van de communicatie tussen Frame.io en Workfront Fusion.

![ Kader IO ](./images/frame18.png)

Zet het scherm terug op Workfront Fusion. U zou nu **met succes moeten zien bepaalde** verschijnen op het voorwerp van de Verbinding van de Douane WebHaak. Klik **OK**.

![ Kader IO ](./images/frame19.png)

Klik **Looppas Eenmaal** om testwijze toe te laten, en de mededeling met Frame.io opnieuw te testen.

![ Kader IO ](./images/frame20.png)

Ga terug naar Frame.io en klik nogmaals op de aangepaste handeling `--aepUserLdap-- - Frame IO Custom Action Fusion` .

![ Kader IO ](./images/frame21.png)

Schakel het scherm weer in op Workfront Fusion. U zou nu een groen controleteken, en een bel moeten zien die **1** tonen. Klik op de ballon om de details weer te geven.

![ Kader IO ](./images/frame22.png)

De gedetailleerde mening van de bel toont u de gegevens die van Frame.io werden ontvangen. Je moet verschillende id&#39;s zien. Als voorbeeld, toont het gebied **resource.id** unieke identiteitskaart in Frame.io van de activa **burgerschap-fiber.psd**.

![ Kader IO ](./images/frame23.png)

Nu communicatie tot stand is gebracht tussen Frame.io en Workfront Fusion, kunt u uw configuratie voortzetten.

## 1.2.5.3 Een aangepaste formulierreactie bieden op Frame.io

Wanneer de aangepaste handeling wordt aangeroepen in Frame.io, verwacht Frame.io een reactie van Workfront Fusion te ontvangen. Als u terugdenkt aan het scenario u in de vorige oefening bouwde, wordt een aantal variabelen vereist om het standaardPhotoshop PSD dossier bij te werken. Deze variabelen worden gedefinieerd in de payload die u hebt gebruikt:

```json
{
    "psdTemplate": "citisignal-fiber.psd",
    "xlsFile": "placeholder",
    "prompt":"misty meadows",
    "cta": "Buy this now!",
    "button": "Click here to buy!"
}
```

Zo in orde voor het scenario `--aepUserLdap-- - Firefly + Photoshop` om met succes in werking te stellen, zijn de gebieden zoals **herinnering**, **cta**, **knoop** en **psdTemplate** nodig.

De eerste 3 gebieden, **herinnering**, **cta**, **knoop**, vereisen gebruikersinput die in Frame.io moet worden verzameld wanneer de gebruiker de douaneactie aanhaalt. Dus het eerste wat we moeten doen binnen Workfront Fusion is controleren of deze variabelen al dan niet beschikbaar zijn en als dat niet het geval is, moet Workfront Fusion reageren op Frame.io met het verzoek om deze variabelen in te voeren. De manier om dat te bereiken is door een formulier in Frame.io te gebruiken.

Ga terug naar Workfront Fusion en open uw scenario `--aepUserLdap-- - Frame IO Custom Action` . Beweeg over het **Webhaak van de Douane** voorwerp en klik **+** pictogram om een andere module toe te voegen.

![ Kader IO ](./images/frame24.png)

Onderzoek naar `Flow Control` en klik **de Controle van de Stroom**.

![ Kader IO ](./images/frame25.png)

Klik om **Router** te selecteren.

![ Kader IO ](./images/frame26.png)

Dan moet je dit zien.

![ Kader IO ](./images/frame27.png)

Klik op **?** voorwerp en klik dan om **Webhooks** te selecteren.

![ Kader IO ](./images/frame28.png)

Selecteer **reactie Webhaak**.

![ Kader IO ](./images/frame29.png)

Dan moet je dit zien.

![ Kader IO ](./images/frame30.png)

Kopieer de hieronder code JSON en kleef het op het gebied **Lichaam**.


```json
{
  "title": "What do you want Firefly to generate?",
  "description": "Enter your Firefly prompt.",
  "fields": [
    {
      "type": "text",
      "label": "Prompt",
      "name": "Prompt",
      "value": ""
    },
    {
      "type": "text",
      "label": "CTA Text",
      "name": "CTA Text",
      "value": ""
    },
    {
      "type": "text",
      "label": "Button Text",
      "name": "Button Text",
      "value": ""
    }
  ]
}
```

Klik op het pictogram om de JSON-code op te schonen en te verfraaien. Dan, klik O.K. ****.

![ Kader IO ](./images/frame31.png)

Klik **sparen** om uw veranderingen te bewaren.

![ Kader IO ](./images/frame32.png)

Daarna, moet u opstelling een filter ervoor zorgen dat dit weg van het scenario slechts loopt wanneer geen herinnering beschikbaar is. Klik het **moersleutelpictogram** en selecteer dan **Opstelling een filter**.

![ Kader IO ](./images/frame33.png)

Configureer de volgende velden:

- **Etiket**: gebruik `Prompt isn't available`.
- **Voorwaarde**: gebruik `{{1.data.Prompt}}`.
- **Basisexploitanten**: uitgezochte **bestaat niet**.

>[!NOTE]
>
>Variabelen in Workfront Fusion kunnen handmatig worden opgegeven met de volgende syntaxis: `{{1.data.Prompt}}` . Het getal in de variabele verwijst naar de module in het scenario. In dit voorbeeld, kunt u zien dat de eerste module in het scenario **Webhooks** wordt genoemd en een opeenvolgingsaantal van **1** heeft. Dit betekent dat veranderlijk `{{1.data.Prompt}}` tot het gebied **data.Prompt** van de module met opeenvolgingsaantal 1 zal toegang hebben. De aantallen van de opeenvolging kunnen soms verschillend zijn zodat let op wanneer het kopiëren/het kleven van dergelijke variabelen en verifieer altijd dat het gebruikte opeenvolgingsaantal het correcte is.

Klik **OK**.

![ Kader IO ](./images/frame34.png)

Dan moet je dit zien. Klik **sparen** pictogram eerst, en klik dan **in werking stellen eens** om uw scenario te testen.

![ Kader IO ](./images/frame35.png)

Dan moet je dit zien.

![ Kader IO ](./images/frame36.png)

Ga terug naar Frame.io en klik de douaneactie `--aepUserLdap-- - Frame IO Custom Action Fusion` op de activa **burgerschap-fiber.psd** opnieuw.

![ Kader IO ](./images/frame37.png)

U zou nu een herinnering binnen Frame.io moeten zien. Vul de velden nog niet in en verzend het formulier nog niet. Deze herinnering wordt getoond gebaseerd van de reactie van de Fusie van Workfront die u enkel vormde.

![ Kader IO ](./images/frame38.png)

De schakelaar terug naar de Fusie van Workfront en klikt de bel op de **module van de Reactie van Webhaak**. U zult zien dat onder **UITVOER**, u het lichaam ziet dat de nuttige lading JSON voor de vorm bevat. Klik **Looppas eens** opnieuw.

![ Kader IO ](./images/frame40.png)

Dan moet u dit nog eens zien.

![ Kader IO ](./images/frame41.png)

Ga terug naar Frame.io en vul de velden in zoals aangegeven. Klik **voorleggen**.

![ Kader IO ](./images/frame39.png)

U zou a **Succes dan moeten zien!** popup.

![ Kader IO ](./images/frame42.png)

De schakelaar terug naar de Fusie van Workfront en klikt de bel op de **Webhaak van de Douane** module. In Verrichting 1, onder **UITVOER**, kunt u een nieuw **gegevens** voorwerp nu zien dat gebieden als **Tekst van de Knoop** bevat, **Tekst van CTA** en **Vragen**. Met deze variabelen van de gebruikersinvoer beschikbaar in uw scenario, hebt u genoeg om uw configuratie voort te zetten.

![ Kader IO ](./images/frame43.png)

## 1.2.5.4 Bestandslocatie ophalen van Frame.io

Zoals eerder besproken, zijn de gebieden zoals **herinnering**, **cta**, **knoop** en **psdTemplate** nodig voor dit scenario aan functie. De eerste 3 gebieden zijn nu reeds beschikbaar maar **psdTemplate** aan gebruik nog mist. **psdTemplate** zal nu een plaats Frame.io van verwijzingen voorzien aangezien het dossier **wordt** ontvangen {in Frame.io. Om de locatie van dat bestand op te halen, moet u de verbinding Frame.io configureren en gebruiken in Workfront Fusion.

Ga terug naar Workfront Fusion en open uw scenario `--aepUserLdap-- - Frame IO Custom Action` . Over de **heen?** klikt u op het pictogram **+** om een andere module toe te voegen en te zoeken naar `frame` . Klik **Frame.io**.

![ Kader IO ](./images/frame44.png)

Klik **Frame.io (erfenis)**.

![ Kader IO ](./images/frame45.png)

Klik **krijgen activa**.

![ Kader IO ](./images/frame46.png)

Om de verbinding te gebruiken Frame.io, moet u het eerst vormen. Klik **toevoegen** om dat te doen.

![ Kader IO ](./images/frame47.png)

Open het **type van Verbinding** dropdown.

![ Kader IO ](./images/frame48.png)

Selecteer **Frame.io API Sleutel** en ga de naam `--aepUserLdap-- - Frame.io Token` in.

![ Kader IO ](./images/frame49.png)

Ga naar [ https://developer.frame.io/ ](https://developer.frame.io/){target="_blank"} om een API-token te krijgen. Klik **TOOLS VAN DE ONTWIKKELAAR** en kies dan **Tokens**.

![ Kader IO ](./images/frame50.png)

Klik **creëren een Symbolisch**.

![ Kader IO ](./images/frame51.png)

Gebruik de **Beschrijving** `--aepUserLdap-- - Frame.io Token` en klik **Uitgezocht alle werkingsgebied**.

![ Kader IO ](./images/frame52.png)

De rol neer en klikt **legt** voor.

![ Kader IO ](./images/frame53.png)

Uw token is nu gemaakt. Klik **Exemplaar** om het aan uw klembord te kopiëren.

![ Kader IO ](./images/frame54.png)

Ga terug naar je scenario in Workfront Fusion. Plak het teken op het gebied **Uw Sleutel Frame.io API**. Klik **OK**. De verbinding wordt nu getest door Workfront Fusion.

![ Kader IO ](./images/frame55.png)

Als de verbinding met succes werd getest, zal het automatisch onder **Verbinding** verschijnen. U hebt nu een succesvolle verbinding, en u moet de configuratie voltooien om alle elementdetails van Frame.io, met inbegrip van de dossierplaats te krijgen. Om dit te doen, moet u **identiteitskaart van Activa** verstrekken.

![ Kader IO ](./images/frame56.png)

**identiteitskaart van Activa** wordt gedeeld door Frame.io aan de Fusie van Workfront als deel van de aanvankelijke **Webhaak van de Douane** mededeling en kan onder het gebied **resource.id** worden gevonden. Selecteer **resource.id** en klik **O.K.**.

![ Kader IO ](./images/frame57.png)

U moet dit nu zien. Sparen uw veranderingen en klik dan **Looppas eens** om uw scenario te testen.

![ Kader IO ](./images/frame58.png)

Ga terug naar Frame.io en klik de douaneactie `--aepUserLdap-- - Frame IO Custom Action Fusion` op de activa **burgerschap-fiber.psd** opnieuw.

![ Kader IO ](./images/frame37.png)

U zou nu een herinnering binnen Frame.io moeten zien. Vul de velden nog niet in en verzend het formulier nog niet. Deze herinnering wordt getoond gebaseerd van de reactie van de Fusie van Workfront die u enkel vormde.

![ Kader IO ](./images/frame38.png)

Ga terug naar Workfront Fusion. Klik **Looppas eens** opnieuw.

![ Kader IO ](./images/frame59.png)

Ga terug naar Frame.io en vul de velden in zoals aangegeven. Klik **voorleggen**.

![ Kader IO ](./images/frame39.png)

De schakelaar terug naar de Fusie van Workfront en klikt de bel op **Frame.io - krijgt een activa** module.

![ Kader IO ](./images/frame60.png)

U kunt nu veel meta-gegevens over de specifieke activa **** zien burgerschap-vezel.psd.

![ Kader IO ](./images/frame61.png)

Het specifieke stuk van informatie dat voor dit gebruiksgeval nodig is, is de plaatsURL van het dossier **burgerschap-fiber.psd**, die u kunt vinden door neer aan het gebied **Origineel** te scrollen.

![ Kader IO ](./images/frame62.png)

U hebt nu alle gebieden (**herinnering**, **cta**, **knoop** en **psdTemplate**) beschikbaar die voor dit scenario aan functie nodig zijn.

## 1.2.5.5 Workfront-scenario aanroepen

In de vorige oefening vormde u het scenario `--aepUserLdap-- - Firefly + Photoshop`. Nu moet u een kleine wijziging aanbrengen in dat scenario.

Open het scenario `--aepUserLdap-- - Firefly + Photoshop` in een ander lusje en klik eerste **Adobe Photoshop - pas PSD uit** module. U moet nu zien dat het invoerbestand is geconfigureerd voor het gebruik van een dynamische locatie in Microsoft Azure. Aangezien voor dit gebruik het invoerbestand niet meer in Microsoft Azure wordt opgeslagen, maar in plaats daarvan met Frame.io-opslag, moet u deze instellingen wijzigen.

![ Kader IO ](./images/frame63.png)

De opslag van de verandering **aan** Externe **en verandert** plaats van het Dossier **om slechts de** psdTemplate **variabele te gebruiken die van de inkomende** WebHaak van de Douane **module wordt genomen.** Klik **O.K.** en klik dan **sparen** om uw veranderingen te bewaren.

![ Kader IO ](./images/frame64.png)

Klik de **Webhaak van de Douane** module en klik dan **adres van het Exemplaar aan klembord**. U moet URL kopiëren aangezien u het in het andere scenario zult moeten gebruiken.

![ Kader IO ](./images/frame65.png)

Ga terug naar uw scenario `--aepUserLdap-- - Frame IO Custom Action`. Beweeg over **Frame.io - krijg een activa** module en klik **+** pictogram.

![ Kader IO ](./images/frame66.png)

Ga `http` in en klik dan **HTTP**.

![ Kader IO ](./images/frame67.png)

Selecteer **maak een verzoek**.

![ Kader IO ](./images/frame68.png)

Plak URL van de douane webhaak op het gebied **URL**. Plaats de **Methode** aan POST**.

![ Kader IO ](./images/frame69.png)

Plaats **type van Lichaam** aan **Onbewerkte** en **inhoudstype** aan **JSON (toepassing/json)**.
Plak hieronder JSON nuttige lading op het gebied **inhoud van het Verzoek** en laat checkbox voor **toe ontleed reactie**.

```json
{
    "psdTemplate": "citisignal-fiber.psd",
    "xlsFile": "placeholder",
    "prompt":"misty meadows",
    "cta": "Buy this now!",
    "button": "Click here to buy!"
}
```

U hebt nu een statische gevormde lading, maar het moet dynamisch worden gebruikend de eerder verzamelde variabelen.

![ Kader IO ](./images/frame70.png)

Voor het gebied **psdTemplate**, vervang de statische veranderlijke **burgerschap-fiber.psd** door veranderlijk **Origineel**.

![ Kader IO ](./images/frame71.png)

Voor de gebieden **herinnering**, **cta** en **knoop**, vervang de statische variabelen door de dynamische variabelen die in het scenario door het inkomende webhaakverzoek van Frame.io werden opgenomen, die de velden **data.Prompt**, **data.CTA Tekst** en **data.Button Tekst** zijn.

Klik **OK**.

![ Kader IO ](./images/frame72.png)

Klik **sparen** om uw veranderingen te bewaren.

![ Kader IO ](./images/frame73.png)

## 1.2.5.6 Nieuw element opslaan in Frame.io

Nadat het andere Workfront Fusion-scenario is aangeroepen, wordt het resultaat een nieuwe Photoshop PSD-sjabloon die beschikbaar is. Dat PSD-bestand moet weer worden opgeslagen in Frame.io. Dit is de laatste stap in dit scenario.

Beweeg over **HTTP - doe een verzoek** module en klik **+** pictogram.

![ Kader IO ](./images/frame74.png)

Selecteer **Frame.io (Verouderd)**.

![ Kader IO ](./images/frame75.png)

Selecteer **creeer een activa**.

![ Kader IO ](./images/frame76.png)

De verbinding Frame.io wordt automatisch geselecteerd.

![ Kader IO ](./images/frame77.png)

Selecteer de volgende opties:

- **identiteitskaart van het Team**: selecteer juiste identiteitskaart van het Team, in dit geval `One Adobe Tutorial`.
- **identiteitskaart van het Project**: gebruik `--aepUserLdap--`.
- **identiteitskaart van de Omslag**: gebruik `root`.
- **Type**: gebruik `File`.

![ Kader IO ](./images/frame78.png)

Voor het gebied **Naam**, kunt u een variabele zoals **gebruiken timestamp** (of dit veranderen in iets dat redelijker aan u) maakt. U kunt de vooraf bepaalde veranderlijke **timestamp** onder de **Datum en tijd** tabel vinden.

![ Kader IO ](./images/frame79.png)

Voor het gebied **Source URL**, gebruik de hieronder code JSON.

```json
{{6.data.newPsdTemplate}}
```

>[!NOTE]
>
>Variabelen in Workfront Fusion kunnen handmatig worden opgegeven met de volgende syntaxis: `{{6.data.newPsdTemplate}}` . Het getal in de variabele verwijst naar de module in het scenario. In dit voorbeeld, kunt u zien dat de zesde module in het scenario **HTTP wordt genoemd - doe een verzoek** en heeft een opeenvolgingsaantal van **6**. Dit betekent dat veranderlijk `{{6.data.newPsdTemplate}}` tot het gebied **data.newPsdTemplate** van de module met opeenvolgingsaantal 6 zal toegang hebben. De aantallen van de opeenvolging kunnen soms verschillend zijn zodat let op wanneer het kopiëren/het kleven van dergelijke variabelen en verifieer altijd dat het gebruikte opeenvolgingsaantal het correcte is.

Klik **OK**.

![ Kader IO ](./images/frame80.png)

Klik **sparen** om uw veranderingen te bewaren.

![ Kader IO ](./images/frame81.png)

Tot slot moet u opstelling een filter ervoor zorgen dat dit weg van het scenario slechts loopt wanneer een herinnering beschikbaar is. Klik het **moersleutelpictogram** en selecteer dan **Opstelling een filter**.

![ Kader IO ](./images/frame82.png)

Configureer de volgende velden:

- **Etiket**: gebruik `Prompt is available`.
- **Voorwaarde**: gebruik `{{1.data.Prompt}}`.
- **Basisexploitanten**: uitgezochte **bestaat**.

>[!NOTE]
>
>Variabelen in Workfront Fusion kunnen handmatig worden opgegeven met de volgende syntaxis: `{{1.data.Prompt}}` . Het getal in de variabele verwijst naar de module in het scenario. In dit voorbeeld, kunt u zien dat de eerste module in het scenario **Webhooks** wordt genoemd en een opeenvolgingsaantal van **1** heeft. Dit betekent dat veranderlijk `{{1.data.Prompt}}` tot het gebied **data.Prompt** van de module met opeenvolgingsaantal 1 zal toegang hebben. De aantallen van de opeenvolging kunnen soms verschillend zijn zodat let op wanneer het kopiëren/het kleven van dergelijke variabelen en verifieer altijd dat het gebruikte opeenvolgingsaantal het correcte is.

Klik **OK**.

![ Kader IO ](./images/frame83.png)

Klik **sparen** om uw veranderingen te bewaren.

![ Kader IO ](./images/frame84.png)

## 1.2.5.7 Test uw gebruiksscenario van begin tot eind

Klik **Looppas eens** in uw scenario `--aepUserLdap-- - Frame IO Custom Action`.

![ Kader IO ](./images/frame85.png)

Ga terug naar Frame.io en klik de douaneactie `--aepUserLdap-- - Frame IO Custom Action Fusion` op de activa **burgerschap-fiber.psd** opnieuw.

![ Kader IO ](./images/frame37.png)

U zou nu een herinnering binnen Frame.io moeten zien. Vul de velden nog niet in en verzend het formulier nog niet. Deze herinnering wordt getoond gebaseerd van de reactie van de Fusie van Workfront die u enkel vormde.

![ Kader IO ](./images/frame38.png)

Ga terug naar Workfront Fusion. Klik **Looppas eens** in uw scenario `--aepUserLdap-- - Frame IO Custom Action`.

![ Kader IO ](./images/frame86.png)

In de Fusie van Workfront, open het scenario `--aepUserLdap-- - Firefly + Photoshop` en klik ook **in werking stellen eens** in dat scenario.

![ Kader IO ](./images/frame87.png)

Ga terug naar Frame.io en vul de velden in zoals aangegeven. Klik **voorleggen**.

![ Kader IO ](./images/frame39.png)

Na 1-2 minuten, zou u een nieuw middel moeten zien automatisch verschijnen in Frame.io. Dubbelklik op het nieuwe element om het te openen.

![ Kader IO ](./images/frame88.png)

U ziet nu duidelijk dat alle variabelen voor gebruikersinvoer automatisch zijn toegepast.

![ Kader IO ](./images/frame89.png)

U hebt deze oefening nu met succes voltooid.

## Volgende stappen

Ga naar [ 1.2.6 Frame.io aan Fusie aan AEM Assets ](./ex6.md){target="_blank"}

Ga terug naar [ de Automatisering van het Werkschema van Creative met Workfront Fusion ](./automation.md){target="_blank"}

Ga terug naar [ Alle Modules ](./../../../overview.md){target="_blank"}

