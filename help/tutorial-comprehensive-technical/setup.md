---
title: Instellen
description: Adobe Experience Platform-instantie instellen
doc-type: multipage-overview
hide: false
exl-id: 1150c5ec-3fba-4506-8f17-c34872f9b3ea
source-git-commit: bbbcb2e60c514aa0785c26f63c2b5b8a7e50a8db
workflow-type: tm+mt
source-wordcount: '1076'
ht-degree: 0%

---

# Adobe Experience Platform-instantie instellen

>[!IMPORTANT]
>
>Deze pagina is alleen bedoeld voor systeembeheerdersrollen. U hebt toegangsrechten voor systeembeheerders nodig om de onderstaande stappen te kunnen volgen. Als u geen systeembeheerder op uw Adobe Experience Cloud-org bent, neemt u contact op met uw systeembeheerder en vraagt u om goedkeuring en hulp voordat u verdergaat met een van de onderstaande stappen.

## Overzicht

Als u al deze zelfstudies in handen wilt hebben, dient u de volgende Adobe Experience Cloud-toepassingen op te nemen in uw IMS-organisatie:

- Adobe in realtime CDP
- Adobe Experience Platform-gegevensverzameling
- Adobe Journey Optimizer
- Customer Journey Analytics
- Data Distiller
- Samenstelling van Federated-doelgroep

Als een specifieke toepassingsservice niet is ingericht voor uw IMS-organisatie, kunt u die specifieke oefening niet in de praktijk uitvoeren.

## Een sandbox maken

Als u de zelfstudie wilt doorlopen in uw eigen Adobe Experience Platform-instantie, is het raadzaam eerst een nieuwe ontwikkelingssandbox in te stellen. Om een nieuwe zandbak tot stand te brengen, ga [&#x200B; https://experience.adobe.com/platform &#x200B;](https://experience.adobe.com/platform), ga naar Sandboxes en ga dan naar **doorbladeren**. Klik **creeer zandbak**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/sandbox1.png)

Maak uw zandbak als volgt:

- Type: **Ontwikkeling**
- Naam: **aep-tutorial**
- Titel: **Zelfstudie van Adobe Experience Platform**

Klik **creëren**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/sandbox2.png)

Uw sandbox wordt nu gemaakt. Na een paar minuten zie je dit.

![&#x200B; creeer zandbak &#x200B;](./assets/images/sandbox3.png)

## Machtigingen instellen

Ga naar **Toestemmingen**, dan gaan **Rollen**.

Klik om de specifieke **Rol** te openen die door de studenten zal worden gebruikt die door dit leerprogramma zullen gaan. Klik **creeer rol**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/perm1.png)

Geef uw rol een naam als **Zelfstudie van Adobe Experience Platform**, klik **bevestigen**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/perm2.png)

In het **zandbakken** dropdown menu, selecteer de zandbak die u enkel creeerde en verzekerde om het even welke andere zandbak (ook verwijder **Prod**) te verwijderen.

![&#x200B; creeer zandbak &#x200B;](./assets/images/perm3.png)

Voeg de verschillende bronnen toe en stel machtigingen in. Gelieve te verzekeren niet om het even welke toestemmingen voor **Beleid Sandbox** toe te voegen.

![&#x200B; creeer zandbak &#x200B;](./assets/images/perm4.png)

Voeg meer bronnen toe zoals aangegeven en stel machtigingen in.

![&#x200B; creeer zandbak &#x200B;](./assets/images/perm5.png)

Voeg meer bronnen toe zoals aangegeven en stel machtigingen in. Klik **sparen**. Dan, klik **dicht**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/perm6.png)

## Adobe I/O instellen

Ga naar
[&#x200B; https://developer.adobe.com/console/integrations &#x200B;](https://developer.adobe.com/console/integrations). Zorg ervoor dat je in de juiste instantie bent. Klik **creëren nieuw project**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/io1.png)

Klik **toevoegen aan Project** en klik dan **API**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/io2.png)

Klik **Adobe Experience Platform** en laat dan **Experience Platform API** toe. Klik **daarna**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/io3.png)

Voor de **Referentienaam**, gebruik **DSN AEP Leerprogramma**. Klik **daarna**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/io4.png)

Selecteer een van de beschikbare productprofielen. Dit productprofiel bepaalt geen toestemmingen voor dit project van Adobe I/O - dit zal in een volgende stap worden gedaan. Klik **sparen gevormde API**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/io5.png)

Klik **toevoegen aan Project** en klik dan **API** opnieuw.

![&#x200B; creeer zandbak &#x200B;](./assets/images/io6.png)

Klik **Adobe Experience Platform** en laat dan **Experience Platform Launch API** toe. Klik **daarna**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/io7.png)

Klik **daarna**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/io8.png)

Selecteer een productprofiel waarmee u eigenschappen voor gegevensverzameling kunt maken en beheren. Klik **sparen gevormde API**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/io9.png)

Dan zie je dit. Klik de huidige **naam van 0&rbrace; Project XXX.**

![&#x200B; creeer zandbak &#x200B;](./assets/images/io10.png)

Klik **uitgeven Project**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/io11.png)

Ga een nieuwe **Titel van het Project** in, zoals **het Leerprogramma van DSN Adobe Experience Platform**. Klik **sparen**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/io12.png)

Uw Adobe I/O-project is nu klaar.

## Adobe I/O-project koppelen aan rol

Ga naar **Toestemmingen**, aan **Rollen** en klik dan de nieuwe rol u vroeger creeerde.

![&#x200B; creeer zandbak &#x200B;](./assets/images/role1.png)

Ga naar **API geloofsbrieven**. Klik op **+ Add API credentials**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/role2.png)

Vervolgens ziet u de Adobe I/O-referentie die u in de vorige stap hebt gemaakt. Selecteer het en klik **sparen**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/role3.png)

Uw Adobe I/O Project is nu ingesteld met de vereiste machtigingen voor toegang tot Adobe Experience Platform API&#39;s.

![&#x200B; creeer zandbak &#x200B;](./assets/images/role4.png)

>[!IMPORTANT]
>
>U moet minimaal 10 minuten wachten voordat u verdergaat met de volgende stappen in Demo System Next.

## Uw omgeving instellen in Demo System Next

Ga naar [&#x200B; https://dsn.adobe.com/tools/org-admin &#x200B;](https://dsn.adobe.com/tools/org-admin). Klik op **+ Org toevoegen** .

![&#x200B; creeer zandbak &#x200B;](./assets/images/dsnorg1.png)

Vul de vereiste velden in:

- IMS Org ID
- Naam
- Identiteitskaart van de huurder (omvat geen **onderstrepingsteken**)
- Regio

Uw systeembeheerder zou u met de waarden voor deze gebieden moeten kunnen helpen.

Klik **sparen**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/dsnorg2.png)

Uw omgeving wordt nu opgenomen in de lijst. Vind het in de lijst en klik het **verbindings** pictogram.

![&#x200B; creeer zandbak &#x200B;](./assets/images/dsnorg3.png)

U moet nu de waarden ingaan die u als deel van de geloofsbrieven van uw Project van Adobe I/O creeerde. U kunt **identiteitskaart van de Cliënt** vinden, **Geheime Cliënt** en **Scopes** hier:

![&#x200B; creeer zandbak &#x200B;](./assets/images/dsnorg4.png)

**identiteitskaart van de Technische Rekening**:

![&#x200B; creeer zandbak &#x200B;](./assets/images/dsnorg5.png)

Kopieer en kleef die hier, klik **sparen**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/dsnorg6.png)

Uw DSN-omgeving is nu op de juiste wijze ingesteld.

## Uw toegang tot de DSN-omgeving instellen

Ga naar [&#x200B; https://dsn.adobe.com/tools/environment-admin &#x200B;](https://dsn.adobe.com/tools/environment-admin). Selecteer IMS Org die u enkel creeerde, uw gebruiker selecteren en dan klikken **+ toewijzen** onder **Sandboxes**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/dsnorg7.png)

Ga de **Naam Sandbox** in die u in de eerste hierboven stap bepaalde. Het moet er als volgt uitzien:

- Naam: **aep-tutorial**

Klik **bevestigen**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/dsnorg8.png)

Uw sandbox is nu beschikbaar voor de gebruiker die u hebt geselecteerd.

![&#x200B; creeer zandbak &#x200B;](./assets/images/dsnorg9.png)

## DSN Quick Setup

Ga naar [&#x200B; https://dsn.adobe.com/quick-setup &#x200B;](https://dsn.adobe.com/quick-setup). Open het **Milieu** dropdown menu en selecteer uw IMS Org/Sandbox.

![&#x200B; creeer zandbak &#x200B;](./assets/images/dsnorg10.png)

Voor **Configuratie**, uitgezochte **Globale v2.0**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/dsnorg11.png)

De rol neer aan **Industrie - Telco** en selecteert **Signaal van Citi - Geavanceerd**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/dsnorg12.png)

De rol omhoog en klikt **Begin**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/dsnorg13.png)

Ga a **Titel** in en klik **Begin**.

![&#x200B; creeer zandbak &#x200B;](./assets/images/dsnorg14.png)

>[!NOTE]
>
>Er kunnen fouten optreden als er geen standaardbeleid voor samenvoegen in de sandbox is gemaakt. Als dat het geval is, of wacht een beetje meer op automatisch tot het fusiebeleid wordt gecreeerd, of ga manueel in Adobe Experience Platform, aan Profielen > het Beleid van de Fusie en creeer een nieuw standaard fusiebeleid.

U zult dan de vooruitgang van de aan de gang zijnde installatie zien, die een paar notulen zal nemen.

![&#x200B; creeer zandbak &#x200B;](./assets/images/dsnorg15.png)

Zodra alles is voltooid, is uw Adobe Experience Platform-exemplaar geconfigureerd en is het klaar voor studenten om de zelfstudie uit te voeren.

>[!NOTE]
>
>De stap van de Invoer van Gegevens wordt niet gebruikt door het leerprogramma, zodat als die stap ontbreekt, maak zich geen zorgen en gelieve verder te gaan.

![&#x200B; creeer zandbak &#x200B;](./assets/images/dsnorg16.png)

Ga naar [&#x200B; https://experience.adobe.com/platform &#x200B;](https://experience.adobe.com/platform), aan **Datasets**. U zou nu een gelijkaardige lijst van datasets moeten zien, die allen door DSN Snelle Opstelling werden gecreeerd.

![&#x200B; creeer zandbak &#x200B;](./assets/images/dsnorg17.png)

>[!NOTE]
>
>Bedankt dat u uw tijd hebt geïnvesteerd in het leren van alles wat er over Adobe Experience Platform en zijn toepassingen te weten komt. Als u vragen hebt, wil algemene terugkoppelen van hebben suggesties over toekomstige inhoud delen, gelieve direct contactTech Insiders, door een e-mail naar **techinsiders@adobe.com** te verzenden.

![&#x200B; Indexen van de Tech &#x200B;](./assets/images/techinsiders.png){width="50px" align="left"}

>[!NOTE]
>
>Als u vragen hebt, wil algemene terugkoppelen van hebben suggesties over toekomstige inhoud delen, gelieve direct contactTech Insiders, door een e-mail naar **techinsiders@adobe.com** te verzenden.

[Terug naar alle modules](./overview.md)
