---
title: Automatisering met behulp van connectors
description: Automatisering met behulp van connectors
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
source-git-commit: 6ef4ce94dbbcd65ab30bcfad24f4ddd746c26b82
workflow-type: tm+mt
source-wordcount: '1721'
ht-degree: 0%

---

# 1.2.4 Automatisering met behulp van connectors

U gaat nu de out-of-the-box connectors gebruiken in Workfront Fusion for Photoshop en u gaat de Firefly Text-2-Image-aanvraag en de Photoshop-aanvragen verbinden met één scenario.

## 1.2.4.1 Uw scenario dupliceren en voorbereiden

In het linkermenu, ga naar **Scenario&#39;s** en selecteer uw omslag `--aepUserLdap--`. Vervolgens ziet u het scenario dat u eerder hebt gemaakt, met de naam `--aepUSerLdap-- - Adobe I/O Authentication` .

![ WF Fusion ](./images/wffc1.png)

Klik de pijl om het dropdown menu te openen en **Kloon** te selecteren.

![ WF Fusion ](./images/wffc2.png)

Plaats de **Naam** van het gekloonde scenario aan `--aepUserLdap-- - Firefly + Photoshop` en selecteer het aangewezen **team van het Doel**. Klik **toevoegen** om een nieuwe webhaak toe te voegen.

![ WF Fusion ](./images/wffc3.png)

Plaats de **naam van Webhaak** aan `--aepUserLdap-- - Firefly + Photoshop Webhook`. Klik **sparen**.

![ WF Fusion ](./images/wffc4.png)

Dan moet je dit zien. Klik **sparen**.

![ WF Fusion ](./images/wffc5.png)

Dan moet je dit zien. Klik de **knoop Webhaak**.

![ WF Fusion ](./images/wffc6.png)

Klik **adres van het Exemplaar aan klembord** en klik dan **opnieuw bepalen gegevensstructuur**.

![ WF Fusion ](./images/wffc7.png)

Open Postman. Voeg een nieuw verzoek toe in de map die u eerder gebruikte.

![ WF Fusion ](./images/wffc9.png)

Controleer of de volgende instellingen zijn toegepast:

- Naam aanvraag: `POST - Send Request to Workfront Fusion Webhook Firefly + Photoshop`
- Type aanvraag: `POST`
- Verzoek-URL: plak de URL die u van de webhaak van het Workfront Fusion-scenario hebt gekopieerd.

Ga naar **Lichaam** en plaats het **Type van Lichaam** aan **onbewerkt** - **JSON**. Plak de volgende nuttige lading in het **Lichaam**.

```json
{
    "psdTemplate": "citisignal-fiber.psd",
    "xlsFile": "placeholder",
    "prompt":"misty meadows",
    "cta": "Buy this now!",
    "button": "Click here to buy!"
}
```

Deze nieuwe lading zal ervoor zorgen dat alle veranderlijke informatie van buiten het scenario wordt verstrekt in plaats van het die in het scenario wordt gecodeerd. In een ondernemingsscenario, moet een organisatie een scenario worden bepaald op een herbruikbare manier, zo betekent het dat een aantal variabelen als inputvariabelen moeten worden verstrekt in plaats van het hebben van hen in het scenario worden verankerd.

Dan moet je dit hebben. Klik **verzenden**.

![ WF Fusion ](./images/wffc10.png)

De Workfront Fusion-webhaak wacht nog steeds op invoer.

![ WF Fusion ](./images/wffc11.png)

Zodra u **hebt geklikt verzend**, zou het bericht tp **met succes moeten veranderen bepaald**. Klik **OK**.

![ WF Fusion ](./images/wffc12.png)

## 1.2.4.2 Firefly T2I-knooppunt bijwerken

Klik de knoop **Firefly T2I**. Dan moet je dit zien. De herinnering in dit verzoek werd eerder hard gecodeerd aan **paarden op een gebied**. U verwijdert nu die geharde tekst en vervangt deze door een veld dat van de webhaak komt.

![ WF Fusion ](./images/wffcfft2i1.png)

Verwijder de tekst **paarden op een gebied** en vervang het door de veranderlijke **herinnering** die onder de **Webhaak** variabelen kan worden gevonden. Klik **O.K.** om uw veranderingen te bewaren.

![ WF Fusion ](./images/wffcfft2i2.png)

## 1.2.4.2 De achtergrond van een PSD-bestand wijzigen

U zult nu uw scenario bijwerken om het slimmer te maken door uit-van-de-doos schakelaars te gebruiken. U gaat ook de uitvoer van Firefly naar Photoshop verbinden, zodat de achtergrondafbeelding van het PSD-bestand dynamisch verandert door de uitvoer van de actie Afbeelding genereren door Firefly te gebruiken.

In de vorige oefening, had u **Firefly T2I** route onbruikbaar gemaakt. Dat moet u nu ongedaan maken. Klik het **eind** - pictogram om de route opnieuw toe te laten.

![ WF Fusion ](./images/wffc13.png)

U zult dan zien dat het **eind** pictogram verdwijnt. Daarna, klik het **moersleutelpictogram** op de andere route naar de configuratie van de vorige oefening en selecteer **route** onbruikbaar maken.

![ WF Fusion ](./images/wffc14.png)

Dan moet je dit zien. Daarna, beweegt over de **Firefly T2I** knoop en klikt **+** pictogram.

![ WF Fusion ](./images/wffc15.png)

In het onderzoeksmenu, ga `Photoshop` in en klik dan de **Adobe Photoshop** actie.

![ WF Fusion ](./images/wffc16.png)

Selecteer **toepassen PSD geeft uit**.

![ WF Fusion ](./images/wffc17.png)

Dan moet je dit zien. Klik **toevoegen** om een nieuwe verbinding aan Adobe Photoshop toe te voegen.

![ WF Fusion ](./images/wffc18.png)

Configureer de verbinding als volgt:

- Het type van verbinding: selecteer **Adobe Photoshop (Server-aan-Server)**
- Naam van verbinding: enter `--aepUserLdap-- - Adobe IO`
- Client-id: uw client-id plakken
- Clientgeheim: plak uw clientgeheim

Klik **verdergaan**.

![ WF Fusion ](./images/wffc19.png)

Om uw **identiteitskaart van de Cliënt** en **Geheime cliënt** te vinden, ga [ https://developer.adobe.com/console/home ](https://developer.adobe.com/console/home) {target="_blank"} en open uw project van Adobe I/O, dat `--aepUserLdap-- One Adobe tutorial` wordt genoemd. Ga naar **OAuth Server-aan-Server** om uw identiteitskaart van de Cliënt en Geheime cliënt te vinden. Kopieer deze waarden en plak ze in de verbindingsinstelling in Workfront Fusion.

![ WF Fusion ](./images/wffc20.png)

Na het klikken **ga** verder, zal een popup venster kort worden getoond terwijl uw geloofsbrieven worden geverifieerd. Als je klaar bent, moet je dit zien.

![ WF Fusion ](./images/wffc21.png)

U moet nu de bestandslocatie invoeren van het PSD-bestand waarmee u Fusion wilt gebruiken. Voor **Opslag**, uitgezochte **Azure** en voor **plaats van het Dossier**, ga `{{1.AZURE_STORAGE_URL}}/{{1.AZURE_STORAGE_CONTAINER}}/{{1.AZURE_STORAGE_SAS_READ}}` in. Plaats de cursor naast de tweede `/` . Dan, heb een blik op de beschikbare variabelen en scrol neer om veranderlijk **psdTemplate** te vinden. Klik veranderlijk **psdTemplate** om het te selecteren.

![ WF Fusion ](./images/wffc22.png)

Dan moet je dit zien.

![ WF Fusion ](./images/wffc23.png)

Schuif al manier neer tot u **Lagen** ziet. Klik **toevoegen punt**.

![ WF Fusion ](./images/wffc24.png)

Dan moet je dit zien. U moet nu de naam invoeren van de laag in de Photoshop PSD-sjabloon die wordt gebruikt voor de achtergrond van het bestand.

![ WF Fusion ](./images/wffc25.png)

In het dossier **wordt** gebruikt het burgerschap-vezel.psd, zult u de laag vinden die voor de achtergrond gebruikte. In dit voorbeeld, wordt die laag genoemd **2048x2048-background**.

![ WF Fusion ](./images/wffc26.png)

Plak de naam **2048x2048-achtergrond** in de dialoog van de Fusie van Workfront.

![ WF Fusion ](./images/wffc27.png)

De rol neer tot u **Input** ziet. U moet nu definiëren wat op de achtergrondlaag moet worden ingevoegd. In dit geval moet u de uitvoer van het Firefly T2I-object selecteren, dat de dynamisch gegenereerde afbeelding bevat.

Voor **Opslag**, uitgezochte **Extern**. Voor **plaats van het Dossier**, onderzoek en vind de variabele `data.outputs[].image.url` van de output van **Firefly T2I** verzoek.

![ WF Fusion ](./images/wffc28.png)

Daarna, scrol neer tot u **ziet uitgeven**. De reeks **geeft** **** uit en plaatst **Type** aan **Laag**. Klik **toevoegen**.

![ WF Fusion ](./images/wffc29.png)

Dan moet je dit zien. Vervolgens moet u de uitvoer van de handeling definiëren. Klik **toevoegen punt** onder **output**.

![ WF Fusion ](./images/wffc30.png)

Selecteer **Azure** voor **Opslag**, kleef dit `{{1.AZURE_STORAGE_URL}}/{{1.AZURE_STORAGE_CONTAINER}}/citisignal-fiber-replacedbg.psd{{1.AZURE_STORAGE_SAS_WRITE}}` onder **Plaats van het Dossier** en selecteer **vnd.adobe.photoshop** onder **Type**. Klik om **toe te laten tonen geavanceerde montages**.

![ WF Fusion ](./images/wffc31.png)

Onder **Geavanceerde Montages**, uitgezochte **ja** om dossiers met de zelfde naam te beschrijven.
Klik **toevoegen**.

![ WF Fusion ](./images/wffc32.png)

Dan moet je dit hebben. Klik **OK**.

![ WF Fusion ](./images/wffc33.png)

## 1.2.4.3 Tekstlagen van PSD-bestand wijzigen

### Aanroep van handelingstekst

Daarna, beweeg over **Adobe Photoshop - pas PSD uit geeft** knoop uit en klik **+** pictogram.

![ WF Fusion ](./images/wffc34.png)

Selecteer **Adobe Photoshop**.

![ WF Fusion ](./images/wffc35.png)

Selecteer **tekstlagen** uitgeven.

![ WF Fusion ](./images/wffc36.png)

Dan moet je dit zien. Selecteer eerst de eerder geconfigureerde Adobe Photoshop-verbinding met de naam `--aepUserLdap-- Adobe IO` .

U moet nu de plaats van het **dossier van de Input** bepalen, dat de output van de vorige stap en onder **Lagen** is, moet u de **Naam** van de tekstlaag ingaan u wilt veranderen.

![ WF Fusion ](./images/wffc37.png)

Voor het **dossier van de Input**, uitgezocht **Azure** voor **de opslag van het het dossierdossier van de Input** en zorg ervoor om de output van het vorige verzoek te selecteren, **Adobe Photoshop - pas PSD uit**, wat u van hier kunt nemen: `data[]._links.renditions[].href`

![ WF Fusion ](./images/wffc37a.png)

Open het dossier **burgerschap-fiber.psd**. In het dossier, zult u opmerken dat de laag die de vraag aan actie bevat **2048x2048-cta** wordt genoemd.

![ WF Fusion ](./images/wffc38.png)

Ga de naam **2048x2048-cta** onder **Naam** in de dialoog in.

![ WF Fusion ](./images/wffc39.png)

De rol neer tot u **Tekst** > **Inhoud** ziet. Selecteer veranderlijke **cta** van de lading van de Webhaak.

![ WF Fusion ](./images/wffc40.png)

De rol neer tot u **Output** ziet. Voor **Opslag**, uitgezochte **Azure**. Voor **plaats van het Dossier**, ga de hieronder plaats in. Let op de toevoeging van de variabele `{{timestamp}}` aan de bestandsnaam die wordt gebruikt om ervoor te zorgen dat elk bestand dat wordt gegenereerd een unieke naam heeft. Ook, plaats het **Type** aan **vnd.adobe.photoshop**. Klik **OK**.

`{{1.AZURE_STORAGE_URL}}/{{1.AZURE_STORAGE_CONTAINER}}/citisignal-fiber-changed-text-{{timestamp}}.psd{{1.AZURE_STORAGE_SAS_WRITE}}`

![ WF Fusion ](./images/wffc41.png)

### Knoptekst

Klik de knoop met de rechtermuisknop aan u enkel creeerde en selecteert **Kloon**. Hiermee wordt een tweede vergelijkbaar object gemaakt.

![ WF Fusion ](./images/wffc42.png)

Dan moet je dit zien. Selecteer eerst de eerder geconfigureerde Adobe Photoshop-verbinding met de naam `--aepUserLdap-- Adobe IO` .

U moet nu de plaats van het **dossier van de Input** bepalen, dat de output van de vorige stap en onder **Lagen** is, moet u de **Naam** van de tekstlaag ingaan u wilt veranderen.

![ WF Fusion ](./images/wffc43.png)

Voor het **dossier van de Input**, uitgezocht **Azure** voor **het dossieropslag van de Input** en zorg ervoor om de output van het vorige verzoek te selecteren, **Adobe Photoshop - geef tekstlagen** uit, die u van hier kunt nemen: `data[]._links.renditions[].href`

Open het dossier **burgerschap-fiber.psd**. In het dossier, zult u opmerken dat de laag die de vraag aan actie bevat wordt genoemd **2048x2048-knoop-tekst**.

![ WF Fusion ](./images/wffc44.png)

Ga de naam **2048x2048-cta** onder **Naam** in de dialoog in.

![ WF Fusion ](./images/wffc43.png)

De rol neer tot u **Tekst** > **Inhoud** ziet. Selecteer veranderlijke **cta** van de lading van de Webhaak.

![ WF Fusion ](./images/wffc45.png)

De rol neer tot u **Output** ziet. Voor **Opslag**, uitgezochte **Azure**. Voor **plaats van het Dossier**, ga de hieronder plaats in. Let op de toevoeging van de variabele `{{timestamp}}` aan de bestandsnaam die wordt gebruikt om ervoor te zorgen dat elk bestand dat wordt gegenereerd een unieke naam heeft. Ook, plaats het **Type** aan **vnd.adobe.photoshop**. Klik **OK**.

`{{1.AZURE_STORAGE_URL}}/{{1.AZURE_STORAGE_CONTAINER}}/citisignal-fiber-changed-text-{{timestamp}}.psd{{1.AZURE_STORAGE_SAS_WRITE}}`

![ WF Fusion ](./images/wffc46.png)

Klik **sparen** om uw veranderingen te bewaren.

![ WF Fusion ](./images/wffc47.png)

## 1.2.4.4 Webhacerespons

Na het toepassen van deze veranderingen in uw dossier van Photoshop, moet u nu de reactie van de a **Webhaak** vormen die zal worden teruggestuurd naar welke toepassing dit scenario heeft geactiveerd.

Beweeg over de knoop **Adobe Photoshop - geef tekstlagen** uit en klik **+** pictogram.

![ WF Fusion ](./images/wffc48.png)

Onderzoek naar **webhaak** en selecteer **Webhaak**.

![ WF Fusion ](./images/wffc49.png)

Selecteer **reactie Webhaak**.

![ WF Fusion ](./images/wffc50.png)

Dan moet je dit zien. Plak hieronder nuttige lading in **Lichaam**.

```json
{
    "newPsdTemplate": ""
}
```

![ WF Fusion ](./images/wffc51.png)

Selecteer het pad `data[]._links.renditions[].href` in de uitvoer van de vorige aanvraag. Laat checkbox voor **toe tonen geavanceerde montages** en klik dan **toevoegen punt**.

![ WF Fusion ](./images/wffc52.png)

Op het gebied **Sleutel**, ga `Content-Type` in. Op het gebied **Waarde**, ga `application/json` in. Klik **sparen**.

![ WF Fusion ](./images/wffc52a.png)

Dan moet je dit hebben. Klik **OK**.

![ WF Fusion ](./images/wffc53.png)

Klik **auto-richt**.

![ WF Fusion ](./images/wffc54.png)

Dan moet je dit zien. Klik **Looppas eens**.

![ WF Fusion ](./images/wffc55.png)

Ga terug naar Postman en klik **verzenden**. De herinnering die hier wordt gebruikt is **slechte graslanden**.

![ WF Fusion ](./images/wffc56.png)

Het scenario wordt vervolgens geactiveerd en na enige tijd wordt een reactie weergegeven in Postman die de URL van het nieuwe PSD-bestand bevat.

![ WF Fusion ](./images/wffc58.png)

Als herinnering: zodra het scenario in Workfront Fusion in werking is gesteld, zult u informatie over elke knoop kunnen zien door de bel boven elke knoop te klikken.

![ WF Fusion ](./images/wffc59.png)

Met Azure Storage Explorer kunt u het nieuwe PSD-bestand zoeken en openen door erop te dubbelklikken in Azure Storage Explorer.

![ WF Fusion ](./images/wffc60.png)

Uw dossier zou dan als dit, met de achtergrond moeten kijken die door een achtergrond met **slechte graslanden** wordt vervangen.

![ WF Fusion ](./images/wffc61.png)

Als u uw scenario opnieuw in werking stelt, en dan een nieuw verzoek van Postman verzendt gebruikend een verschillende herinnering, zult u dan zien hoe gemakkelijk en herbruikbaar uw scenario is geworden. In dit voorbeeld, is de nieuwe herinnering die wordt gebruikt **zonnige woestijn**.

![ WF Fusion ](./images/wffc62.png)

Een paar minuten later is er een nieuw PSD-bestand met een nieuwe achtergrond gemaakt.

![ WF Fusion ](./images/wffc63.png)

## Volgende stappen

Ga naar [ Samenvatting en Voordelen van de Automatisering van de Diensten van Firefly ](./summary.md){target="_blank"}

Ga terug naar [ het Automatiseren de Diensten van Adobe Firefly ](./automation.md){target="_blank"}

Ga terug naar [ Alle Modules ](./../../../overview.md){target="_blank"}
