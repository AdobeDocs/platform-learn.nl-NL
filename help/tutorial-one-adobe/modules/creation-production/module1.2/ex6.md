---
title: Frame I/O en Workfront Fusion
description: Frame I/O en Workfront Fusion
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: f02ecbe4-f1d7-4907-9bbc-04e037546091
source-git-commit: d47b6da364fc6ffdb0c541197edc8a9d2fd34e42
workflow-type: tm+mt
source-wordcount: '1872'
ht-degree: 0%

---

# 1.2.6 Frame I/O naar Workfront Fusion naar AEM Assets

>[!IMPORTANT]
>
>Als u deze bewerking wilt voltooien, hebt u toegang nodig tot een werkende AEM Assets CS Author-omgeving. Als u oefening [ Adobe Experience Manager Cloud Service &amp; Edge Delivery Services ](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"} volgt zult u toegang tot zulk een milieu hebben.

>[!IMPORTANT]
>
>Als u eerder een AEM Assets CS-programma hebt geconfigureerd met een auteursomgeving, kan het zijn dat de AEM CS-sandbox is geminimaliseerd. Gezien het feit dat het vernietigen van zo&#39;n zandbak 10 tot 15 minuten duurt, zou het een goed idee zijn om nu het ontruimingsproces te beginnen zodat u niet op een later tijdstip vastloopt.

In de vorige oefening vormde u een scenario dat automatisch variaties van een dossier van Adobe Photoshop PSD gebruikend Adobe Firefly, Photoshop APIs en Workfront Fusion produceert. De uitvoer van dat scenario was een nieuw Photoshop PSD-bestand.

De zakelijke teams hebben echter geen PSD-bestand nodig, maar een PNG-bestand of een JPG-bestand. In deze oefening, zult u een nieuwe automatisering vormen die in een PNG- dossier zal resulteren dat wordt geproduceerd zodra de activa in Kader I/O wordt goedgekeurd, en dat PNG- dossier zal automatisch in AEM Assets worden opgeslagen.

## 1.2.6.1 Een nieuw scenario maken

Ga naar [ https://experience.adobe.com/ ](https://experience.adobe.com/). Open **de Fusie van Workfront**.

![ WF Fusion ](./images/wffusion1.png)

In het linkermenu, ga naar **Scenario&#39;s** en selecteer uw omslag `--aepUserLdap--`. Klik **creeer een nieuw scenario**.

![ Kader IO ](./images/aemf1.png)

Gebruik de naam `--aepUserLdap-- - Asset Approved PNG AEM Assets` . Klik vervolgens op **?** module, ga de onderzoekstermijn `webhook` in en klik dan **Webhooks**.

![ Kader IO ](./images/aemf2.png)

Klik **WebHaak van de Douane**.

![ Kader IO ](./images/aemf3.png)

Klik **toevoegen** om een nieuwe webhaak tot stand te brengen.

![ Kader IO ](./images/aemf4.png)

Gebruik de naam `--aepUserLdap-- - Frame.io Webhook` . Klik **sparen**.

![ Kader IO ](./images/aemf5.png)

Dan moet je dit zien. Klik **adres van het Exemplaar aan klembord**.

![ Kader IO ](./images/aemf6.png)

## 1.2.6.2 Webhaak configureren in Frame.io

Ga naar [ https://developer.frame.io/ ](https://developer.frame.io/). Klik **TOOLS VAN DE ONTWIKKELAAR** en kies dan **de Acties van de Douane**.

![ Kader IO ](./images/aemf7.png)

Klik **creeer een Webhaak**.

![ Kader IO ](./images/aemf8.png)

Voer de volgende waarden in:

- **NAAM**: gebruik `--aepUserLdap-- - Asset Labels Updated`
- **URL**: ga URL van de webhaak in die u enkel in de Fusie van Workfront creeerde
- **TEAM**: selecteer het aangewezen team Frame.io, in dit geval, **Één Leerprogramma van Adobe**.

![ Kader IO ](./images/aemf9.png)

De rol neer en laat checkbox naast **Etiketten van Activa toe - bijgewerkt**. Klik **voorleggen**.

![ Kader IO ](./images/aemf10.png)

Dan moet je dit zien.

![ Kader IO ](./images/aemf11.png)

Ga naar [ https://app.frame.io/projects ](https://app.frame.io/projects) en ga naar de omslag die u eerder creeerde, die zou moeten worden genoemd `--aepUserLdap--`. Dubbelklik om het element te openen dat tijdens de vorige oefening is gemaakt.

![ Kader IO ](./images/aemf11a.png)

Dan moet je iets dergelijks zien. Klik het gebied **Geen Status** en verander de status in **Bezig**.

![ Kader IO ](./images/aemf12.png)

Ga terug naar Workfront Fusion. U zou nu moeten zien dat de verbinding **met succes werd bepaald**.

![ Kader IO ](./images/aemf13.png)

Klik **sparen** om uw veranderingen te bewaren, en dan **te klikken in werking stellen eens** om een snelle test te doen.

![ Kader IO ](./images/aemf14.png)

De schakelaar terug naar Frame.io en klikt het gebied **Bezig** en verandert de status in **Overzicht van Behoeften**.

![ Kader IO ](./images/aemf15.png)

De schakelaar terug naar de Fusie van Workfront en klikt de bel op de **Webhaak van de Douane** module.

De gedetailleerde mening van de bel toont u de gegevens die van Frame.io werden ontvangen. Je moet verschillende id&#39;s zien. Als voorbeeld, toont het gebied **resource.id** unieke identiteitskaart in Frame.io van de activa **burgerschap-fiber.psd**.

![ Kader IO ](./images/aemf16.png)

## 1.2.6.3 Asset Details ophalen van Frame.io

Nu de communicatie tussen Frame.io en Workfront Fusion via een aangepaste webhaak tot stand is gebracht, dient u meer informatie te krijgen over het element waarvoor het statuslabel is bijgewerkt. Om dit te doen, zult u opnieuw de Schakelaar Frame.io in Workfront Fusion, gelijkend op de vorige oefening gebruiken.

Klik op **?** en voer de zoekterm `frame` in. Klik **Frame.io**.

![ Kader IO ](./images/aemf18.png)

Klik **Frame.io (Verouderd)**.

![ Kader IO ](./images/aemf19.png)

Klik **krijgen activa**.

![ Kader IO ](./images/aemf20.png)

Controleer of de verbinding is ingesteld op dezelfde verbinding als die u in de vorige oefening hebt gemaakt. Deze moet de naam `--aepUserLdap-- - Frame.io Token` hebben.

![ Kader IO ](./images/aemf21.png)

Daarna, moet u **identiteitskaart van Activa verstrekken**. **identiteitskaart van Activa** wordt gedeeld door Frame.io aan de Fusie van Workfront als deel van de aanvankelijke **Webhaak van de Douane** mededeling en kan onder het gebied **resource.id** worden gevonden. Selecteer **resource.id** en klik **O.K.**.

![ Kader IO ](./images/aemf22.png)

Klik **sparen** om uw veranderingen op te slaan en dan **in werking te stellen eens** om uw configuratie te testen.

![ Kader IO ](./images/aemf23.png)

De schakelaar terug naar Frame.io en klikt het gebied **herzien** en verandert de status aan **Bezig**.

![ Kader IO ](./images/aemf24.png)

Ga terug naar de Fusie van Workfront en klik de bel op **Frame.io - krijg een activa** module. Dan zou u een gelijkaardig overzicht moeten zien.

![ Kader IO ](./images/aemf25.png)

In de activa details die door Frame.io werden verstrekt, kunt u een gebied genoemd **Etiket** vinden dat aan **in_progress** wordt geplaatst. U moet dat veld later gebruiken om een filter te configureren.

![ Kader IO ](./images/aemf26.png)

## 1.2.6.4 Omzetten in PNG

Beweeg over de module **Frame.io - krijg activa** en klik **+** pictogram.

![ Kader IO ](./images/aemf27.png)

Ga de onderzoekstermijn `photoshop` in en klik dan **Adobe Photoshop**.

![ Kader IO ](./images/aemf28.png)

Klik **het Formaat van het Beeld van de Bekeerling**.

![ Kader IO ](./images/aemf29.png)

Verifieer dat het gebied **Verbinding** uw eerder gecreeerde verbinding gebruikt, die `--aepUserLdap-- - Adobe IO` wordt genoemd.

Onder **Input**, plaats de gebied **Opslag** aan **Extern** en plaats de **Plaats van het Dossier** om het veranderlijke **Originele** te gebruiken dat door de module **Frame.io is teruggekeerd - krijg een activa**.

Daarna, voegt de klik **punt** onder **Output** toe.

![ Kader IO ](./images/aemf30.png)

Voor de **configuratie van Output**, plaats de gebied **Opslag** aan **interne opslag van de Fusie** en het **Type** aan **beeld/png**. Klik **sparen**.

![ Kader IO ](./images/aemf31.png)

Klik **OK**.

![ Kader IO ](./images/aemf33.png)

Klik **sparen** om uw veranderingen te bewaren.

![ Kader IO ](./images/aemf32.png)

Daarna, zou u opstelling een filter moeten ervoor zorgen dat slechts voor activa die een status hebben die **** wordt goedgekeurd, een PNG- dossier wordt teruggegeven. Om dat te doen, klik het **pictogram van de Sleutel 0} tussen de modules** Frame.io - krijg een activa **en** Adobe Photoshop - zet beeldformaat **om en selecteer dan** Opstelling een filter **.**

![ Kader IO ](./images/aemf34.png)

Configureer de volgende velden:

- **Etiket**: gebruik `Is Asset Approved`.
- **Voorwaarde**: selecteer het gebied **Etiket** van de reactie van **Frame.io - krijg een activa** module.
- **Basisexploitanten**: uitgezochte **Gelijk aan**.
- **Waarde**: `approved`.

Klik **OK**.

![ Kader IO ](./images/aemf35.png)

Klik **sparen** om uw veranderingen op te slaan en dan **in werking te stellen eens** om uw configuratie te testen.

![ Kader IO ](./images/aemf36.png)

De schakelaar terug naar Frame.io en klikt het gebied **Bezig** en verandert de status aan **Goedgekeurd**.

![ Kader IO ](./images/aemf37.png)

Ga terug naar Workfront Fusion. U zou nu moeten zien dat alle modules in uw scenario met succes zijn uitgevoerd. Klik de bel op **Adobe Photoshop - zet beeldformaat** module om.

![ Kader IO ](./images/aemf38.png)

In de details van de uitvoering van **Adobe Photoshop - zet beeldformaat** module om, kunt u zien dat een PNG- dossier nu werd geproduceerd. Vervolgens slaat u dat bestand op in AEM Assets CS.

![ Kader IO ](./images/aemf39.png)

## 1.2.6.5 PNG opslaan in AEM Assets CS

Beweeg over **Adobe Photoshop - zet beeldformaat** module om en klik **+** pictogram.

![ Kader IO ](./images/aemf40.png)

Ga de onderzoekstermijn `aem` in en selecteer **AEM Assets**.

![ Kader IO ](./images/aemf41.png)

Klik **uploaden activa**.

![ Kader IO ](./images/aemf42.png)

U moet nu uw verbinding met AEM Assets CS configureren. Klik **toevoegen**.

![ Kader IO ](./images/aemf43.png)

Gebruik de volgende instellingen:

- **Type van Verbinding**: **AEM Assets as a Cloud Service**.
- **Naam van de Verbinding**: `--aepUserLdap-- AEM Assets CS`.
- **Instantie URL**: kopieer de instantie URL van uw milieu van de Auteur van AEM Assets CS, dat als dit zou moeten kijken: `https://author-pXXXXX-eXXXXXXX.adobeaemcloud.com`.
- **de detailvulopties van de Toegang**: selecteer **verstrekken JSON**.

U moet nu de **Technische rekeningsgeloofsbrieven in formaat verstrekken JSON**. Hiervoor moet u een aantal stappen ondernemen met AEM Cloud Manager. Zorg dat dit scherm open blijft terwijl u dat doet.

![ Kader IO ](./images/aemf44.png)

Ga naar [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com){target="_blank"}. De org die u moet selecteren is `--aepImsOrgName--`. Dan zie je zoiets. Klik om uw programma te openen, dat `--aepUserLdap-- - Citi Signal` zou moeten worden genoemd.

![ Kader IO ](./images/aemf45.png)

Klik de 3 punten **..** en selecteer **Developer Console**.

![ Kader IO ](./images/aemf46.png)

Klik **Teken binnen met Adobe**.

![ Kader IO ](./images/aemf47.png)

U wordt dan genomen aan **Developer Console**. Klik **creëren nieuwe technische rekening**.

![ Kader IO ](./images/aemf48.png)

Dan moet je iets dergelijks zien. Kopieer de volledige JSON-lading naar het klembord.

![ Kader IO ](./images/aemf50.png)

Ga terug naar de Fusie van Workfront en kleef de volledige nuttige lading JSON in de **Technische rekeningsgeloofsbrieven in JSON formaat** gebied. Klik **verdergaan**.

![ Kader IO ](./images/aemf49.png)

Uw verbinding wordt dan gevalideerd en wanneer de verbinding succesvol is, wordt deze automatisch geselecteerd in de AEM Assets-module. Het volgende te doen moet een omslag vormen. Als onderdeel van de oefening, zou u een nieuwe specifieke omslag moeten tot stand brengen.

![ Kader IO ](./images/aemf51.png)

Om een nieuwe specifieke omslag tot stand te brengen, ga [ https://experience.adobe.com ](https://experience.adobe.com/). Zorg ervoor dat de juiste Experience Cloud-instantie is geselecteerd, die moet zijn ingesteld op `--aepImsOrgName--` . Dan, klik **Experience Manager Assets**.

![ Kader IO ](./images/aemf52.png)

Klik **Uitgezocht** op uw milieu van AEM Assets CS, dat zou moeten worden genoemd `--aepUserLdap-- - Citi Signal dev`.

![ Kader IO ](./images/aemf53.png)

Ga naar **Activa** en klik **creeer Omslag**.

![ Kader IO ](./images/aemf54.png)

Ga de naam `--aepUserLdap-- - Frame.io PNG` in en klik **creeer**.

![ Kader IO ](./images/aemf55.png)

Uw map wordt vervolgens gemaakt.

![ Kader IO ](./images/aemf56.png)

Ga terug naar de Fusie van Workfront, klik **hier om omslag** te kiezen en dan de omslag `--aepUserLdap-- - Frame.io PNG` te kiezen.

![ Kader IO ](./images/aemf57.png)

Controleer of het doel is ingesteld op `--aepUserLdap-- - Frame.io PNG` . Dan, onder **het Dossier van Source**, uitgezochte **Kaart**.

Onder **naam van het Dossier**, kies de variabele `{{3.filenames[]}}`.

Onder **Gegevens**, kies de variabele `{{3.files[]}}`.

>[!NOTE]
>
>Variabelen in Workfront Fusion kunnen handmatig worden opgegeven met de volgende syntaxis: `{{3.filenames[]}}` . Het getal in de variabele verwijst naar de module in het scenario. In dit voorbeeld, kunt u zien dat de derde module in het scenario **Adobe Photoshop wordt genoemd - zet beeldformaat** om en heeft een opeenvolgingsaantal van **3**. Dit betekent dat veranderlijk `{{3.filenames[]}}` tot het gebied **filenames[]** van de module met opeenvolgingsaantal 3 zal toegang hebben. De aantallen van de opeenvolging kunnen soms verschillend zijn zodat let op wanneer het kopiëren/het kleven van dergelijke variabelen en verifieer altijd dat het gebruikte opeenvolgingsaantal het correcte is.

Klik **OK**.

![ Kader IO ](./images/aemf58.png)

Klik **sparen** om uw veranderingen te bewaren.

![ Kader IO ](./images/aemf59.png)

Vervolgens moet u specifieke machtigingen instellen voor de technische account die u zojuist hebt gemaakt. Wanneer de rekening in **Developer Console** in **Cloud Manager** werd gecreeerd, werd het **Gelezen** toegangsrechten gegeven maar voor dit gebruiksgeval, **schrijft** toegangsrechten worden vereist. U kunt dat doen door naar de AEM CS Author-omgeving te gaan.

Ga naar [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com){target="_blank"}. De org die u moet selecteren is `--aepImsOrgName--`. Klik om uw programma te openen, dat `--aepUserLdap-- - Citi Signal` zou moeten worden genoemd. Dan zie je zoiets. Klik op de URL van de auteur.

![ Kader IO ](./images/aemf60.png)

Klik **Teken binnen met Adobe**.

![ Kader IO ](./images/aemf61.png)

Ga naar **Montages** > **Veiligheid** > **Gebruikers**.

![ Kader IO ](./images/aemf62.png)

Klik hierop om de gebruikersaccount voor de technische account te openen.

![ Kader IO ](./images/aemf63.png)

Ga naar **Groepen** en voeg deze Technische gebruiker van de Rekening aan de groep **DAM-Gebruikers** toe.

![ Kader IO ](./images/aemf64.png)

Klik **sparen &amp; Sluiten**.

![ Kader IO ](./images/aemf65.png)

Ga terug naar Workfront Fusion. Klik **Looppas eens** om uw scenario te testen.

![ Kader IO ](./images/aemf66.png)

De schakelaar terug naar Frame.io en zorgt ervoor dat het statuut van uw activa wordt veranderd in **goedgekeurd** opnieuw.

>[!NOTE]
>
>U kunt het eerst terug naar **moeten veranderen Bezig** of **het Overzicht van Behoeften**, om het dan terug naar **Goedgekeurd** te veranderen.

![ Kader IO ](./images/aemf15.png)

Uw Workfront Fusion-scenario wordt vervolgens geactiveerd en moet correct worden voltooid. Door de informatie in de bel op de **AEM Assets** module te bekijken, kunt u reeds zien dat het PNG- dossier met succes in AEM Assets CS werd opgeslagen.

![ Kader IO ](./images/aemf67.png)

Ga terug naar AEM Assets CS en open de map `--aepUserLdap-- - Frame.io PNG` . Het PNG-bestand dat is gegenereerd, wordt nu weergegeven in het Workfront Fusion-scenario. Dubbelklik op het bestand om het te openen.

![ Kader IO ](./images/aemf68.png)

U ziet nu meer details over de metagegevens van het gegenereerde PNG-bestand.

![ Kader IO ](./images/aemf69.png)

U hebt deze oefening nu met succes voltooid.

## Volgende stappen

Ga naar [ Samenvatting en Voordelen van de Automatisering van het Werkschema van Creative met Workfront Fusion ](./summary.md){target="_blank"}

Ga terug naar [ de Automatisering van het Werkschema van Creative met Workfront Fusion ](./automation.md){target="_blank"}

Ga terug naar [ Alle Modules ](./../../../overview.md){target="_blank"}
