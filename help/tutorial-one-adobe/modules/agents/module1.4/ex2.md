---
title: Brand Concierge op uw website implementeren
description: Brand Concierge op uw website implementeren
kt: 5342
doc-type: tutorial
source-git-commit: fb1fc5c72723cc4e1ede87f90410feb0cc314eea
workflow-type: tm+mt
source-wordcount: '1347'
ht-degree: 0%

---

# 1.4.2 Brand Concierge implementeren op uw website

>[!IMPORTANT]
>
>U hebt toegang nodig tot een werkende AEM Assets CS Author-omgeving en een AEM CS/EDS-website om deze oefening te kunnen voltooien.
>
>Als u zulk een milieu niet hebt, ga naar [&#x200B; Adobe Experience Manager Cloud Service &amp; Edge Delivery Services &#x200B;](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"}. Volg de instructies daar, en u zult toegang tot zulk een milieu hebben.

>[!IMPORTANT]
>
>Als u eerder een AEM CS-programma hebt geconfigureerd met een AEM Assets CS-omgeving, kan het zijn dat de AEM CS-sandbox is geminimaliseerd. Gezien het feit dat het vernietigen van zo&#39;n zandbak 10 tot 15 minuten duurt, zou het een goed idee zijn om het ontruimingsproces nu te beginnen zodat u niet op een later tijdstip hoeft te wachten.

## 1.4.2.1 Uw website configureren om Brand Concierge - AEM Author te tonen

Brand Concierge wordt alleen op uw website weergegeven als u een nieuw aangepast blok maakt dat aan een nieuwe pagina moet worden toegevoegd. U moet ervoor zorgen dat de nieuwe pagina aan de navigatie van uw website wordt toegevoegd.

U moet nu de volgende dingen in deze orde vormen:

- Maak een nieuw aangepast blok dat wordt gebruikt om Brand Concierge op uw website te laden.
- Maak een nieuwe pagina op uw website voor Brand Concierge.
- Koppel het nieuwe aangepaste blok aan de nieuwe Brand Concierge-pagina.
- Voeg een verwijzing toe om naar de nieuwe Brand Concierge-pagina in het navigatiekoptekstbestand van uw website te navigeren.

### Nieuw aangepast blok maken

Als u het nieuwe aangepaste blok wilt maken, navigeert u naar de GitHub-opslagplaats die aan uw website is gekoppeld.

![&#x200B; Blok &#x200B;](./images/block1.png)

#### component-definition.json

De rol neer tot u het dossier **component-definition.json** ziet en het opent

![&#x200B; Blok &#x200B;](./images/block8.png)

Klik het **pictogram 0&rbrace; pencl &lbrace;beginnen het dossier uit te geven.**

![&#x200B; Blok &#x200B;](./images/block8a.png)

De rol neer tot u de **Blokken** ziet. Plaats uw curseur onder de sluitende steun van de component **Kaarten**

![&#x200B; Blok &#x200B;](./images/block9.png)

Plak deze code en voer een komma **&#x200B;**&#x200B;na het codeblok in:

```json
{
  "title": "BrandConcierge",
  "id": "brandconcierge",
  "plugins": {
    "xwalk": {
      "page": {
        "resourceType": "core/franklin/components/block/v1/block",
        "template": {
          "name": "BrandConcierge",
          "model": "brandconcierge"
        }
      }
    }
  }
},
```

Klik **Veranderingen vastleggen...**.

![&#x200B; Blok &#x200B;](./images/block10.png)

Klik **veranderingen** vastleggen.

![&#x200B; Blok &#x200B;](./images/block10a.png)

#### component-models.json

De rol neer tot u het dossier **component-models.json** ziet en klikt het **potlood** pictogram beginnen het dossier uit te geven.

![&#x200B; Blok &#x200B;](./images/block11.png)

Schuif omlaag totdat u het laatste item ziet. Plaats uw curseur naast de sluitende steun van de laatste component.

![&#x200B; Blok &#x200B;](./images/block12.png)

Voer een komma **&#x200B;**&#x200B;in en druk op Enter en op de volgende regel en plak deze code:

```json
{
  "id": "brandconcierge",
  "fields": []
}
```

Klik **Veranderingen vastleggen...**.

![&#x200B; Blok &#x200B;](./images/block13.png)

Klik **veranderingen** vastleggen.

![&#x200B; Blok &#x200B;](./images/block13a.png)

#### component-filters.json

De rol neer tot u het dossier **component-filters.json** ziet en klikt het **potlood** pictogram beginnen het dossier uit te geven.

![&#x200B; Blok &#x200B;](./images/block14.png)

Dan moet je dit zien.

![&#x200B; Blok &#x200B;](./images/block14a.png)

Onder **sectie**, ga een komma `,` in en kleef identiteitskaart van uw component `"brandconcierge"` na de huidige laatste lijn.

Klik **Veranderingen vastleggen...**.

![&#x200B; Blok &#x200B;](./images/block15.png)

Klik **veranderingen** vastleggen.

![&#x200B; Blok &#x200B;](./images/block15a.png)

#### brandconcierge.css

Wanneer u een blok maakt, kunt u het beste een bestand voor de opmaak van het blok maken. Dit bestand moet dezelfde naam hebben als het blok. nu moet u dat bestand maken , dat we voorlopig leeg laten .

Ga naar de **blokken** omslag. Dan, klik **voeg dossier** toe en selecteer **creeer nieuw dossier**.

![&#x200B; Blok &#x200B;](./images/css1.png)

Typ `brandconcierge/brandconcierge.css` in het tekstvak. Het bestand kan voorlopig leeg blijven. Klik **Veranderingen vastleggen...**.

![&#x200B; Blok &#x200B;](./images/css2.png)

Klik **veranderingen** vastleggen.

![&#x200B; Blok &#x200B;](./images/css3.png)

#### brandconcierge.js

Wanneer het creëren van een blok, is het beste praktijken om een dossier voor javascript te creëren met betrekking tot uw blok, en het zou de zelfde naam moeten hebben zoals uw blok.

Klik **toevoegen dossier** en selecteren **nieuw dossier** creëren.

![&#x200B; Blok &#x200B;](./images/js1.png)

Typ `brandconcierge.js` in het tekstvak. Het bestand kan voorlopig leeg blijven. Klik **Veranderingen vastleggen...**.

```javascript
export default function decorate(block) {
  block.setAttribute('id', 'brand-concierge-mount');
}
```

![&#x200B; Blok &#x200B;](./images/js2.png)

Klik **veranderingen** vastleggen.

![&#x200B; Blok &#x200B;](./images/js3.png)

### Nieuwe pagina maken en nieuw aangepast blok koppelen

Ga naar [&#x200B; https://my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com){target="_blank"}. Klik uw **Programma** om het te openen.

![&#x200B; AEMCS &#x200B;](./images/aemcs6.png)

Daarna, klik de 3 punten **..** op het **milieu&#39;s** lusje en klik **Details van de Mening**.

![&#x200B; AEMCS &#x200B;](./images/aemcs9.png)

Dan zie je de omgevingsdetails. Klik URL van uw **milieu van de Auteur**.

>[!NOTE]
>
>Het is mogelijk dat uw omgeving gehiberd is. Als dat het geval is, zult u uw milieu eerst moeten ontberen. In de onderstaande video vindt u instructies over het dehiberneren van de historie.

>[!VIDEO](https://video.tv.adobe.com/v/3478141?quality=12&learn=on)

![&#x200B; AEMCS &#x200B;](./images/aemcs10.png)

Je moet dan de AEM Author-omgeving zien. Ga naar **Plaatsen**.

![&#x200B; AEMCS &#x200B;](./images/block21.png)

Ga naar **CitiSignal**. Klik **creëren** en selecteren **Pagina**.

![&#x200B; AEMCS &#x200B;](./images/block23.png)

Selecteer **Pagina** en klik **daarna**.

![&#x200B; AEMCS &#x200B;](./images/block24.png)

Voer de volgende waarden in:

- Titel: **Brand Concierge**
- Naam: **brandconcierge**
- De Titel van de pagina: **Brand Concierge**

Klik **creëren**.

![&#x200B; AEMCS &#x200B;](./images/block25.png)

Selecteer **Open**.

![&#x200B; AEMCS &#x200B;](./images/block22.png)

Dan moet je dit zien.

![&#x200B; AEMCS &#x200B;](./images/block26.png)

Klik op het lege gebied om de **sectie** component te selecteren. Klik vervolgens op de plusknop **+** in het rechtermenu.

![&#x200B; AEMCS &#x200B;](./images/block27.png)

Vervolgens wordt het aangepaste blok weergegeven in de lijst met beschikbare blokken. Klik om het te selecteren.

![&#x200B; AEMCS &#x200B;](./images/block28.png)

Vervolgens wordt er een leeg blok aan deze pagina toegevoegd. Dit blok wordt dynamisch geladen met de JavaScript-bibliotheken die u in de volgende stap toevoegt.

Klik **publiceren**.

![&#x200B; AEMCS &#x200B;](./images/block29.png)

Klik **publiceren** opnieuw.

![&#x200B; AEMCS &#x200B;](./images/block30.png)

De nieuwe pagina wordt nu gepubliceerd en kan nu in de volgende stap worden toegevoegd aan de navigatiekop.

### Navigatiekopbestand bijwerken

In uw overzicht van AEM Sites, ga **CitiSignal** en controleer checkbox voor het dossier **Kopbal/nav**. Klik **uitgeven**.

![&#x200B; AEMCS &#x200B;](./images/nav0.png)

Selecteer het **gebied van de Tekst** in het voorproefscherm en klik dan het **3&rbrace; gebied van de Tekst &lbrace;op de rechterkant van het scherm om het uit te geven.**

![&#x200B; AEMCS &#x200B;](./images/nav0a.png)

Maak een nieuwe menuoptie in het navigatiemenu met de tekst `Brand Concierge` . Dan, selecteer de tekst **Brand Concierge** en klik het **verbindings** pictogram.

![&#x200B; AEMCS &#x200B;](./images/nav1.png)

Ga dit voor het gebied **Weg of URL** `/content/CitiSignal/brandconcierge.html` in en ga `Brand Concierge` voor het gebied **Titel** in. Klik **sparen**.

![&#x200B; AEMCS &#x200B;](./images/nav3.png)

Dan moet je dit hebben. Klik **Gedaan**.

![&#x200B; AEMCS &#x200B;](./images/nav4.png)

Dan moet je dit hebben. Klik **publiceren**.

![&#x200B; AEMCS &#x200B;](./images/nav4a.png)

Klik **publiceren** opnieuw.

![&#x200B; AEMCS &#x200B;](./images/nav5.png)

De nieuwe pagina wordt nu toegevoegd aan het menu.

## 1.4.2.2 Uw website configureren om Brand Concierge - GitHub weer te geven

Na het bijwerken van de inhoud die uw milieu van de Auteur van AEM gebruikt, moet u nu enkele code in de bewaarplaats bijwerken GitHub die voor uw website wordt gebruikt.

### JavaScript-bibliotheken

U hebt de volgende bibliotheken nodig om Brand Concierge te implementeren op uw website die wordt uitgevoerd op AEM CS/EDS:

- [styleconfigurations.js](./assets/styleconfigurations.js)
- [alloy.js](./assets/alloy.js)
- [brandconciergemain.js](./assets/brandconciergemain.js)

Download alle 3 bestanden naar uw bureaublad.

![&#x200B; Brand Concierge &#x200B;](./images/aem0.png)

Ga naar het GitHub-project van uw AEM CS/EDS-website. Ga naar **manuscripten**.

![&#x200B; Brand Concierge &#x200B;](./images/aem1.png)

Klik **toevoegen dossier** en selecteer dan **dossiers** uploaden.

![&#x200B; Brand Concierge &#x200B;](./images/aem3.png)

Klik **kiezen uw dossiers**.

![&#x200B; Brand Concierge &#x200B;](./images/aem3a.png)

Selecteer alle 3 dossiers **styleConfigurations.js, alloy.js en brandconciergemain.js** van uw Desktop en klik **Open**.

![&#x200B; Brand Concierge &#x200B;](./images/aem4.png)

Klik **veranderingen** vastleggen.

![&#x200B; Brand Concierge &#x200B;](./images/aem5.png)

### head.html bijwerken

In de vorige stap hebt u 3 nieuwe bibliotheken geüpload. Deze bibliotheken moeten nu worden geladen wanneer uw website en de manier wordt geladen om dat te doen verwijzingen naar deze dossiers in het dossier **head.html** toevoegen.

Bovendien, moet u ook instructies in het {**dossier verstrekken 0} head.html om ervoor te zorgen dat de bibliotheken in de juiste orde en op een correcte manier worden geladen.**

Om dat te doen, ga naar het project GitHub van uw website van AEM CS/EDS door **Code** te klikken.

![&#x200B; Brand Concierge &#x200B;](./images/aem6.png)

Schuif een beetje omlaag. Open het dossier **head.html**.

![&#x200B; Brand Concierge &#x200B;](./images/aem7.png)

Klik het **potlood** pictogram om dit dossier uit te geven.

![&#x200B; Brand Concierge &#x200B;](./images/aem8.png)

Dan moet je dit zien.

![&#x200B; Brand Concierge &#x200B;](./images/aem9.png)

Schuif omlaag naar regel 43 en plak de volgende tekst:

De onderstaande code bevat twee velden die u moet bijwerken:

>[!IMPORTANT]
>
>- **datastreamId** is momenteel geplaatst aan &quot;XXXXX&quot;en moet door identiteitskaart van de gegevensstroom worden vervangen die u in de vorige stap creeerde.
>- **orgId** moet door IMS Org identiteitskaart van uw instantie van Adobe Experience Cloud worden vervangen.

```javascript
<script src="/scripts/styleconfigurations.js"></script>

<script>
		!function (n, o) {
      o.forEach(function (o) {
        n[o] || ((n.__alloyNS = n.__alloyNS ||
          []).push(o), n[o] = function () {
            var u = arguments; return new Promise(
              function (i, l) { n[o].q.push([i, l, u]) })
          }, n[o].q = [])
      })
    }
      (window, ["alloy"]);
	</script>


<script src="/scripts/alloy.js"></script>

<script>
	alloy("configure", {
		defaultConsent: "in",
        edgeDomain: "edge.adobedc.net",
        edgeBasePath: "ee",
        datastreamId: "XXXXX", // replace datastreamId
        orgId: "--aepImsOrgId--", // replace ims org Id
        debugEnabled: true,
        idMigrationEnabled: false,
        thirdPartyCookiesEnabled: false,
        prehidingStyle: ".personalization-container { opacity: 0 !important }",
    });

window["alloy"]("sendEvent", {
    conversation: {
        fetchConversationalExperience: true
    }
}).then(result => {
    console.log("Conversation experience fetched", result);
    window["alloy"]("bootstrapConversationalExperience", {
        selector: "#brand-concierge-mount",
        src: "/scripts/brandconciergemain.js",
        stylingConfigurations: window.styleConfiguration,
        stickySession: true // create a sticky session cookie with expiration
    })
});
</script>
```

Klik **Verandering vastleggen...**.

![&#x200B; Brand Concierge &#x200B;](./images/aem10.png)

Klik **Verandering** vastleggen.

![&#x200B; Brand Concierge &#x200B;](./images/aem11.png)

U hebt nu de vereiste code bijgewerkt om de bibliotheken op uw website te laden.

![&#x200B; Brand Concierge &#x200B;](./images/aem12.png)

## 1.4.2.3 De configuratie testen

U kunt nu uw wijzigingen op uw website testen door naar `main--citisignal-aem-accs--XXX.aem.page` of `main--citisignal-aem-accs--XXX.aem.live` te gaan, nadat u XXX hebt vervangen door uw GitHub-gebruikersaccount, die in dit voorbeeld `woutervangeluwe` is.

In dit voorbeeld wordt de volledige URL als volgt:
`https://main--citisignal-aem-accs--woutervangeluwe.aem.page` en/of `https://main--citisignal-aem-accs--woutervangeluwe.aem.live` .

Het kan enige tijd duren voordat alle activa correct zijn weergegeven, aangezien deze eerst moeten worden gepubliceerd.

Dan moet je dit zien. Klik **Brand Concierge**.

![&#x200B; Brand Concierge &#x200B;](./images/aem13.png)

Je moet dan deze Brand Concierge zien waar je je vraag kunt invoeren.

![&#x200B; Brand Concierge &#x200B;](./images/aem14.png)

Ga terug naar [&#x200B; Brand Concierge &#x200B;](./brandconcierge.md){target="_blank"}

[&#x200B; ga terug naar Alle Modules &#x200B;](./../../../overview.md){target="_blank"}