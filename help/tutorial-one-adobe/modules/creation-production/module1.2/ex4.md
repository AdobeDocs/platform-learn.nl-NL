---
title: Automatisering met behulp van connectors
description: Automatisering met behulp van connectors
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 0b20ba91-28d4-4f4d-8abe-074f802c389e
source-git-commit: 9ddabdf0b66ea4772352f5aa82c612fa07891db3
workflow-type: tm+mt
source-wordcount: '2058'
ht-degree: 0%

---

# 1.2.4 Automatisering met behulp van connectors

U gaat nu de out-of-the-box connectors gebruiken in Workfront Fusion for Photoshop en u gaat de Firefly Text-2-Image-aanvraag en de Photoshop-aanvragen verbinden met één scenario.

## 1.2.4.1 Uw scenario dupliceren en voorbereiden

In het linkermenu, ga naar **Scenario&#39;s** en selecteer uw omslag `--aepUserLdap--`. Vervolgens ziet u het scenario dat u eerder hebt gemaakt, met de naam `--aepUserLdap-- - Adobe I/O Authentication` .

![&#x200B; WF Fusion &#x200B;](./images/wffc1.png)

Klik de pijl om het dropdown menu te openen en **Kloon** te selecteren.

![&#x200B; WF Fusion &#x200B;](./images/wffc2.png)

Plaats de **Naam** van het gekloonde scenario aan `--aepUserLdap-- - Firefly + Photoshop` en selecteer het aangewezen **team van het Doel**. Klik **toevoegen** om een nieuwe webhaak toe te voegen.

>[!NOTE]
>
>U kunt niet de optie zien om a **Team van het Doel** te selecteren. Deze optie wordt alleen weergegeven als u een gebruiker bent in meer dan 1 Team in Workfront Fusion. Als u deze optie niet ziet, betekent het eenvoudig dat u slechts aan 1 Team bent toegevoegd zodat geen keus wordt vereist.

![&#x200B; WF Fusion &#x200B;](./images/wffc3.png)

Plaats de **naam van Webhaak** aan `--aepUserLdap-- - Firefly + Photoshop Webhook`. Klik **sparen**.

![&#x200B; WF Fusion &#x200B;](./images/wffc4.png)

Dan moet je dit zien. Klik **sparen**.

![&#x200B; WF Fusion &#x200B;](./images/wffc5.png)

Dan moet je dit zien. Klik de **module Webhaak**.

![&#x200B; WF Fusion &#x200B;](./images/wffc6.png)

Klik **adres van het Exemplaar aan klembord** en klik dan **opnieuw bepalen gegevensstructuur**.

![&#x200B; WF Fusion &#x200B;](./images/wffc7.png)

Open Postman. Voeg een nieuw verzoek toe in de map die u eerder gebruikte.

![&#x200B; WF Fusion &#x200B;](./images/wffc9.png)

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

![&#x200B; WF Fusion &#x200B;](./images/wffc10.png)

De Workfront Fusion-webhaak wacht nog steeds op invoer.

![&#x200B; WF Fusion &#x200B;](./images/wffc11.png)

Zodra u **hebt geklikt verzend**, zou het bericht tp **met succes moeten veranderen bepaald**. Klik **OK**.

![&#x200B; WF Fusion &#x200B;](./images/wffc12.png)

## 1.2.4.2 Firefly T2I-module bijwerken

Klik de module **Firefly T2I** met de rechtermuisknop aan en selecteer **module van de Schrapping**.

![&#x200B; WF Fusion &#x200B;](./images/wffcff1.png)

Klik **+** pictogram, ga de onderzoekstermijn `firefly` in en selecteer dan **Adobe Firefly**.

![&#x200B; WF Fusion &#x200B;](./images/wffcff2.png)

Selecteer **produceer een beeld**.

![&#x200B; WF Fusion &#x200B;](./images/wffcff3.png)

Sleep en laat vallen de **Adobe Firefly** module zodat het met de **Router** module verbindt.

![&#x200B; WF Fusion &#x200B;](./images/wffcff4.png)

Klik de **Adobe Firefly** module om het te openen, en dan te klikken **voeg** toe om een nieuwe verbinding tot stand te brengen.

![&#x200B; WF Fusion &#x200B;](./images/wffcff5.png)

Vul de volgende velden in:

- **naam van de Verbinding**: gebruik `--aepUserLdap-- - Firefly connection`.
- **Milieu**: gebruik **Productie**.
- **Type**: gebruik **Persoonlijke rekening**.
- **identiteitskaart van de Cliënt**: kopieer **identiteitskaart van de Cliënt** van uw project van Adobe I/O dat `--aepUserLdap-- - One Adobe tutorial` wordt genoemd.
- **Geheim van de Cliënt**: kopieer het **Geheime Cliënt** van uw project van Adobe I/O dat `--aepUserLdap-- - One Adobe tutorial` wordt genoemd.

U kunt **identiteitskaart van de Cliënt** en **Geheime Cliënt** van uw project van Adobe I/O [&#x200B; hier &#x200B;](https://developer.adobe.com/console/projects.){target="_blank"} vinden.

![&#x200B; WF Fusion &#x200B;](./images/wffc20.png)

Zodra u alle gebieden hebt ingevuld, gaat de klik **&#x200B;**&#x200B;verder. Uw verbinding wordt dan automatisch gevalideerd.

![&#x200B; WF Fusion &#x200B;](./images/wffcff6.png)

Daarna, selecteer de veranderlijke **herinnering** die aan het scenario door de inkomende **Douane webhaak** wordt verstrekt.

![&#x200B; WF Fusion &#x200B;](./images/wffcff7.png)

Daarna, plaats de **Modelversie** **herinnering** aan **image4 norm**. Klik **OK**.

![&#x200B; WF Fusion &#x200B;](./images/wffcff7b.png)

Alvorens u verdergaat, moet u de oude route in het scenario zoals voor deze oefening onbruikbaar maken, zult u slechts de nieuwe route gebruiken die u op het ogenblik vormt. Om dat te doen, klik het **moersleutelpictogram** tussen de **module van de Router** en de **Iterator** module, en selecteer **maak route** onbruikbaar.

![&#x200B; WF Fusion &#x200B;](./images/wffcff7a.png)

Klik **sparen** om uw veranderingen op te slaan en dan **in werking te stellen eens** om uw configuratie te testen.

![&#x200B; WF Fusion &#x200B;](./images/wffcff8.png)

Ga naar Postman, verifieer de herinnering in uw verzoek en klik dan **verzenden**.

![&#x200B; WF Fusion &#x200B;](./images/wffcff8a.png)

Zodra u hebt geklikt verzend, ga terug naar de Fusie van Workfront en klik het borstelpictogram op de **Adobe Firefly** module om de details te verifiëren.

![&#x200B; WF Fusion &#x200B;](./images/wffcff9.png)

Ga in **UITVOER** naar **Details** > **url** om URl van het beeld te vinden dat door **Adobe Firefly** werd geproduceerd.

![&#x200B; WF Fusion &#x200B;](./images/wffcff10.png)

U zou nu een beeld moeten zien dat de herinnering vertegenwoordigt u binnen van het verzoek van Postman, in dit geval **misty graslanden** verzond.

![&#x200B; WF Fusion &#x200B;](./images/wffcff11.png)

## 1.2.4.2 De achtergrond van een PSD-bestand wijzigen

U zult nu uw scenario bijwerken om het slimmer te maken door meer uit-van-de-doos schakelaars te gebruiken. U gaat ook de uitvoer van Firefly naar Photoshop verbinden, zodat de achtergrondafbeelding van het PSD-bestand dynamisch verandert door de uitvoer van de actie Afbeelding genereren door Firefly te gebruiken.

Dan moet je dit zien. Daarna, beweegt over de **Adobe Firefly** module en klikt **+** pictogram.

![&#x200B; WF Fusion &#x200B;](./images/wffc15.png)

In het onderzoeksmenu, ga `Photoshop` in en klik dan de **Adobe Photoshop** actie.

![&#x200B; WF Fusion &#x200B;](./images/wffc16.png)

Selecteer **toepassen PSD geeft uit**.

![&#x200B; WF Fusion &#x200B;](./images/wffc17.png)

Dan moet je dit zien. Klik **toevoegen** om een nieuwe verbinding aan Adobe Photoshop toe te voegen.

![&#x200B; WF Fusion &#x200B;](./images/wffc18.png)

Configureer de verbinding als volgt:

- Het type van verbinding: selecteer **Adobe Photoshop (Server-aan-Server)**
- Naam van verbinding: enter `--aepUserLdap-- - Adobe IO`
- Client-id: uw client-id plakken
- Clientgeheim: plak uw clientgeheim

Klik **verdergaan**.

![&#x200B; WF Fusion &#x200B;](./images/wffc19.png)

Om uw **identiteitskaart van de Cliënt te vinden** en **Geheim van de Cliënt**, ga [&#x200B; https://developer.adobe.com/console/home &#x200B;](https://developer.adobe.com/console/home){target="_blank"} en open uw project van Adobe I/O, dat `--aepUserLdap-- One Adobe tutorial` wordt genoemd. Ga naar **OAuth Server-aan-Server** om uw identiteitskaart van de Cliënt en Geheime cliënt te vinden. Kopieer deze waarden en plak ze in de verbindingsinstelling in Workfront Fusion.

![&#x200B; WF Fusion &#x200B;](./images/wffc20.png)

Na het klikken **ga** verder, zal een popup venster kort worden getoond terwijl uw geloofsbrieven worden geverifieerd. Als je klaar bent, moet je dit zien.

![&#x200B; WF Fusion &#x200B;](./images/wffc21.png)

U moet nu de bestandslocatie invoeren van het PSD-bestand waarmee u Fusion wilt gebruiken. Voor **Opslag**, uitgezochte **Azure** en voor **plaats van het Dossier**, ga `{{1.AZURE_STORAGE_URL}}/{{1.AZURE_STORAGE_CONTAINER}}/{{1.AZURE_STORAGE_SAS_READ}}` in. Plaats de cursor naast de tweede `/` . Dan, heb een blik op de beschikbare variabelen en scrol neer om veranderlijk **psdTemplate** te vinden. Klik veranderlijk **psdTemplate** om het te selecteren.

![&#x200B; WF Fusion &#x200B;](./images/wffc22.png)

Dan moet je dit zien.

![&#x200B; WF Fusion &#x200B;](./images/wffc23.png)

Schuif al manier neer tot u **Lagen** ziet. Klik **toevoegen punt**.

![&#x200B; WF Fusion &#x200B;](./images/wffc24.png)

Dan moet je dit zien. U moet nu de naam invoeren van de laag in de Photoshop PSD-sjabloon die wordt gebruikt voor de achtergrond van het bestand.

![&#x200B; WF Fusion &#x200B;](./images/wffc25.png)

In het dossier **wordt** gebruikt het burgerschap-vezel.psd, zult u de laag vinden die voor de achtergrond gebruikte. In dit voorbeeld, wordt die laag genoemd **2048x2048-background**.

![&#x200B; WF Fusion &#x200B;](./images/wffc26.png)

Plak de naam **2048x2048-achtergrond** in de dialoog van de Fusie van Workfront.

![&#x200B; WF Fusion &#x200B;](./images/wffc27.png)

De rol neer tot u **Input** ziet. U moet nu definiëren wat op de achtergrondlaag moet worden ingevoegd. In dit geval, moet u de output van de **Adobe Firefly** module selecteren, die het dynamisch geproduceerde beeld bevat.

Voor **Opslag**, uitgezochte **Extern**. Voor **plaats van het Dossier**, zult u veranderlijk `{{XX.details[].url}}` van de output van de **Adobe Firefly** module moeten kopiëren en kleven maar u moet **XX** in de variabele door het opeenvolgingsaantal van de **Adobe Firefly** module vervangen, die in dit voorbeeld **22** is.

![&#x200B; WF Fusion &#x200B;](./images/wffc28.png)

Daarna, scrol neer tot u **ziet uitgeven**. De reeks **geeft** **&#x200B;**&#x200B;uit en plaatst **Type** aan **Laag**. Klik **toevoegen**.

![&#x200B; WF Fusion &#x200B;](./images/wffc29.png)

Dan moet je dit zien. Vervolgens moet u de uitvoer van de handeling definiëren. Klik **toevoegen punt** onder **output**.

![&#x200B; WF Fusion &#x200B;](./images/wffc30.png)

Selecteer **Azure** voor **Opslag**, kleef dit `{{1.AZURE_STORAGE_URL}}/{{1.AZURE_STORAGE_CONTAINER}}/citisignal-fiber-replacedbg.psd{{1.AZURE_STORAGE_SAS_WRITE}}` onder **Plaats van het Dossier** en selecteer **vnd.adobe.photoshop** onder **Type**. Klik om **toe te laten tonen geavanceerde montages**.

![&#x200B; WF Fusion &#x200B;](./images/wffc31.png)

Onder **Geavanceerde Montages**, uitgezochte **ja** om dossiers met de zelfde naam te beschrijven.
Klik **toevoegen**.

![&#x200B; WF Fusion &#x200B;](./images/wffc32.png)

Dan moet je dit hebben. Klik **OK**.

![&#x200B; WF Fusion &#x200B;](./images/wffc33.png)

Klik **sparen** om uw veranderingen op te slaan en dan **in werking te stellen eens** om uw configuratie te testen.

![&#x200B; WF Fusion &#x200B;](./images/wffc33a.png)

Ga naar Postman, verifieer de herinnering in uw verzoek en klik dan **verzenden**.

![&#x200B; WF Fusion &#x200B;](./images/wffcff8a.png)

Dan moet je dit zien. Klik de bel op **Adobe Photoshop - pas PSD uit** module uitgeeft.

![&#x200B; WF Fusion &#x200B;](./images/wffc33b.png)

U ziet nu dat er een nieuw PSD-bestand is gegenereerd en opgeslagen in uw Microsoft Azure Storage Account.

![&#x200B; WF Fusion &#x200B;](./images/wffc33c.png)

## 1.2.4.3 Tekstlagen van PSD-bestand wijzigen

Daarna, beweeg over **Adobe Photoshop - pas PSD uit geeft** module uit en klik **+** pictogram.

![&#x200B; WF Fusion &#x200B;](./images/wffc34.png)

Selecteer **Adobe Photoshop**.

![&#x200B; WF Fusion &#x200B;](./images/wffc35.png)

Selecteer **tekstlagen** uitgeven.

![&#x200B; WF Fusion &#x200B;](./images/wffc36.png)

Dan moet je dit zien. Selecteer eerst de eerder geconfigureerde Adobe Photoshop-verbinding met de naam `--aepUserLdap-- Adobe IO` .

U moet nu de plaats van het **dossier van de Input** bepalen, dat de output van de vorige stap en onder **Lagen** is, zult u **+ moeten klikken toevoegt punt** voor elke laag waarvoor de tekst moet veranderen.

![&#x200B; WF Fusion &#x200B;](./images/wffc37.png)

Voor het **dossier van de Input**, uitgezocht **Azure** voor **het dossieropslag van de Input** en zorg ervoor om de output van het vorige verzoek te selecteren, **Adobe Photoshop - pas PSD uit**, die u als dit kunt bepalen: ``{{XX.data[].`_links`.renditions[].href}}`` (vervang XX door het opeenvolgingsaantal van de vorige module Adobe Photoshop - pas PSD uit).

Daarna, klik **+ voeg punt** onder **Lagen** toe beginnen de tekstlagen toe te voegen die moeten worden bijgewerkt.

![&#x200B; WF Fusion &#x200B;](./images/wffc37a.png)

Er zijn 2 te maken veranderingen, de tekst van CTA en de knooptekst in het dossier **wordt aangebracht burgerschap-fiber.psd** moet worden bijgewerkt.

Om de laagnamen te vinden, open het dossier **burgerschap-fiber.psd**. In het dossier, zult u opmerken dat de laag die de vraag aan actie bevat **2048x2048-cta** wordt genoemd.

![&#x200B; WF Fusion &#x200B;](./images/wffc38.png)

In het dossier **wordt** 2048x2048-knoop-tekst **genoemd.**

![&#x200B; WF Fusion &#x200B;](./images/wffc44.png)

U moet eerst de veranderingen vormen die aan de laag **moeten gebeuren 2048x2048-cta**. Ga de naam **2048x2048-cta** onder **Naam** in de dialoog in.

![&#x200B; WF Fusion &#x200B;](./images/wffc39.png)

De rol neer tot u **Tekst** > **Inhoud** ziet. Selecteer veranderlijke **cta** van de lading van de Webhaak. Klik **toevoegen**.

![&#x200B; WF Fusion &#x200B;](./images/wffc40.png)

Dan moet je dit zien. Klik **+ toevoegen punt** onder **Lagen** beginnen de tekstlagen toe te voegen die moeten worden bijgewerkt.

![&#x200B; WF Fusion &#x200B;](./images/wffc40a.png)

Ga de naam **2048x2048-knoop-tekst** onder **Naam** in de dialoog in.

![&#x200B; WF Fusion &#x200B;](./images/wffc40b.png)

De rol neer tot u **Tekst** > **Inhoud** ziet. Selecteer de veranderlijke **knoop** van de payload van de Webhaak. Klik **toevoegen**.

![&#x200B; WF Fusion &#x200B;](./images/wffc40c.png)

Dan moet je dit zien.

![&#x200B; WF Fusion &#x200B;](./images/wffc40d.png)

De rol neer tot u **Output** ziet. Voor **Opslag**, uitgezochte **Azure**. Voor **plaats van het Dossier**, ga de hieronder plaats in. Let op de toevoeging van de variabele `{{timestamp}}` aan de bestandsnaam die wordt gebruikt om ervoor te zorgen dat elk bestand dat wordt gegenereerd een unieke naam heeft. Ook, plaats het **Type** aan **vnd.adobe.photoshop**.

`{{1.AZURE_STORAGE_URL}}/{{1.AZURE_STORAGE_CONTAINER}}/citisignal-fiber-changed-text-{{timestamp}}.psd{{1.AZURE_STORAGE_SAS_WRITE}}`

![&#x200B; WF Fusion &#x200B;](./images/wffc41.png)

Plaats **Type** aan **vnd.adobe.photoshop**. Klik **OK**.

![&#x200B; WF Fusion &#x200B;](./images/wffc41a.png)

Klik **sparen** om uw veranderingen te bewaren.

![&#x200B; WF Fusion &#x200B;](./images/wffc47.png)

## 1.2.4.4 Webhacerespons

Na het toepassen van deze veranderingen in uw dossier van Photoshop, moet u nu de reactie van de a **Webhaak** vormen die zal worden teruggestuurd naar welke toepassing dit scenario heeft geactiveerd.

Beweeg over de module **Adobe Photoshop - geef tekstlagen** uit en klik **+** pictogram.

![&#x200B; WF Fusion &#x200B;](./images/wffc48.png)

Onderzoek naar `webhooks` en selecteer **Webhaak**.

![&#x200B; WF Fusion &#x200B;](./images/wffc49.png)

Selecteer **reactie Webhaak**.

![&#x200B; WF Fusion &#x200B;](./images/wffc50.png)

Dan moet je dit zien. Plak hieronder nuttige lading in **Lichaam**.

```json
{
    "newPsdTemplate": ""
}
```

![&#x200B; WF Fusion &#x200B;](./images/wffc51.png)

Kopieer en kleef veranderlijk `{{XX.data[]._links.renditions[].href}}` en vervang **XX** door het opeenvolgingsaantal van laatste **Adobe Photoshop - geef tekstlagen** module uit, die in dit geval **30** is.

![&#x200B; WF Fusion &#x200B;](./images/wffc52.png)

Laat checkbox voor **toe tonen geavanceerde montages** en klik dan **toevoegen punt**.

![&#x200B; WF Fusion &#x200B;](./images/wffc52b.png)

Op het gebied **Sleutel**, ga `Content-Type` in. Op het gebied **Waarde**, ga `application/json` in. Klik **toevoegen**.

![&#x200B; WF Fusion &#x200B;](./images/wffc52a.png)

Dan moet je dit hebben. Klik **OK**.

![&#x200B; WF Fusion &#x200B;](./images/wffc53.png)

Klik **auto-richt**.

![&#x200B; WF Fusion &#x200B;](./images/wffc54.png)

Dan moet je dit zien. Klik **sparen** om uw veranderingen op te slaan en dan **in werking te stellen eens** om uw scenario te testen.

![&#x200B; WF Fusion &#x200B;](./images/wffc55.png)

Ga terug naar Postman en klik **verzenden**. De herinnering die hier wordt gebruikt is **slechte graslanden**.

![&#x200B; WF Fusion &#x200B;](./images/wffc56.png)

Het scenario wordt vervolgens geactiveerd en na enige tijd wordt een reactie weergegeven in Postman die de URL van het nieuwe PSD-bestand bevat.

![&#x200B; WF Fusion &#x200B;](./images/wffc58.png)

Als herinnering: zodra het scenario in Workfront Fusion in werking is gesteld, zult u informatie over elke module kunnen zien door de bel boven elke module te klikken.

![&#x200B; WF Fusion &#x200B;](./images/wffc59.png)

Met Azure Storage Explorer kunt u het nieuwe PSD-bestand zoeken en openen door erop te dubbelklikken in Azure Storage Explorer.

![&#x200B; WF Fusion &#x200B;](./images/wffc60.png)

Uw dossier zou dan als dit, met de achtergrond moeten kijken die door een achtergrond met **slechte graslanden** wordt vervangen.

![&#x200B; WF Fusion &#x200B;](./images/wffc61.png)

Als u uw scenario opnieuw in werking stelt, en dan een nieuw verzoek van Postman verzendt gebruikend een verschillende herinnering, zult u dan zien hoe gemakkelijk en herbruikbaar uw scenario is geworden. In dit voorbeeld, is de nieuwe herinnering die wordt gebruikt **zonnige woestijn**.

![&#x200B; WF Fusion &#x200B;](./images/wffc62.png)

Een paar minuten later is er een nieuw PSD-bestand met een nieuwe achtergrond gemaakt.

![&#x200B; WF Fusion &#x200B;](./images/wffc63.png)

## Volgende stappen

Ga naar [&#x200B; 1.2.5 Frame.io en Workfront Fusion &#x200B;](./ex5.md){target="_blank"}

Ga terug naar [&#x200B; de Automatisering van het Werkschema van Creative met Workfront Fusion &#x200B;](./automation.md){target="_blank"}

Ga terug naar [&#x200B; Alle Modules &#x200B;](./../../../overview.md){target="_blank"}
