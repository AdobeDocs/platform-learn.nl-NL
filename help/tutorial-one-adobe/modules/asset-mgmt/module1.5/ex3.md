---
title: ACCS verbinden met AEM Assets CS
description: ACCS verbinden met AEM Assets CS
kt: 5342
doc-type: tutorial
exl-id: 2b944efe-3997-46a0-9eb0-61dfda67f5b9
source-git-commit: 7280f6b7d3579226f2d8c7f94e75ca8d3f2941cc
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 1.5.3 ACCS verbinden met AEM Assets CS

>[!IMPORTANT]
>
>Om deze oefening te voltooien, moet u toegang tot een werkende AEM Sites en Assets CS met milieu EDS hebben.
>
>Als u zulk een milieu nog niet hebt, ga [&#x200B; Adobe Experience Manager Cloud Service &amp; Edge Delivery Services &#x200B;](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"} uitoefenen. Volg de instructies daar, en u zult toegang tot zulk een milieu hebben.

>[!IMPORTANT]
>
>Als u eerder een AEM CS-programma hebt geconfigureerd met een AEM Sites- en Assets CS-omgeving, kan het zijn dat uw AEM CS-sandbox is geminimaliseerd. Gezien het feit dat het vernietigen van zo&#39;n zandbak 10 tot 15 minuten duurt, zou het een goed idee zijn om het ontruimingsproces nu te beginnen zodat u niet op een later tijdstip hoeft te wachten.

Na de vorige oefening kon u een product zien dat door ACCS aan uw website wordt teruggegeven maar het had nog geen beeld. Aan het eind van deze oefening, zou u een beeld moeten zien dat ook wordt teruggegeven.

![&#x200B; ACCS+AEM Sites &#x200B;](./images/accsaemsites11.png)

## 1.5.3.1 Configuratie pijplijn bijwerken

Ga naar [&#x200B; https://my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com){target="_blank"}. De org die u moet selecteren is `--aepImsOrgName--`.

Klik hierop om het Cloud Manager-programma te openen. Dit wordt `--aepUserLdap-- - CitiSignal AEM+ACCS` genoemd.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets1.png)

Scoll neer een klein beetje en klik dan **Info van de Reparatie van de Toegang** op de **Pijpleidingen** tabel.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets2.png)

Dan moet je dit zien. Klik **produceer Wachtwoord**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets3.png)

Klik **produceer opnieuw Wachtwoord**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets4.png)

U zou dan een wachtwoord beschikbaar moeten hebben. Daarna, klik het **exemplaar** pictogram naast het **bevel van de Git bevel lijn** gebied.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets5.png)

Creeer een nieuwe folder in een plaats van keus op uw computer en noem het **AEM Pipeline GitHub**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets6.png)

Klik met de rechtermuisknop op uw map en selecteer vervolgens **Nieuwe terminal bij Map** .

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets7.png)

Dan moet je dit zien.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets8.png)

Plak het **bevel van de het bevellijn van de Git** dat u alvorens in het Eind venster kopieerde.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets9.png)

U moet een gebruikersnaam invoeren. Kopieer de gebruikersnaam van de Pijpleiding van het Programma van de Cloud Manager **Reparatie van de Toegang Info** en de slag **gaat** binnen.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets10.png)

Vervolgens moet u het wachtwoord invoeren. Kopieer het wachtwoord van de Pijpleiding van het Programma van de Cloud Manager **Reparatie Info van de Toegang** en de slag **gaat** binnen.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets11.png)

Dit kan even duren. Zodra voltooid, zult u een lokale kopie van de Repo van het Git hebben die met de Pijpleiding van uw Programma wordt verbonden.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets12.png)

U zult een nieuwe folder in de **folder GitHub van de Pijpleiding van AEM** zien. Open die map.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets13.png)

Selecteer alle bestanden in die map en verwijder alle bestanden.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets14.png)

Zorg ervoor dat de map leeg is.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets15.png)

Ga naar [&#x200B; https://github.com/ankumalh/assets-commerce &#x200B;](https://github.com/ankumalh/assets-commerce). Klik **&lt;> Code** en selecteer dan **ZIP van de Download**. Download het bestand en zet het neer op uw bureaublad.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets15a.png)

Daarna, kopieer het dossier **activa-commerce-main.zip** aan uw Desktop en unzip het. Open de omslag **activa-handel-belangrijkste**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets16.png)

Kopieer alle dossiers van de folder **activa-handel-belangrijkste** aan de lege folder van de folder van de Bewaarplaats van de Pijpleiding van uw Programma.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets17.png)

Daarna, open **Code van Microsoft Visual Studio** en open de omslag die de Bewaarplaats van de Pijpleiding van uw Programma in **Code van Microsoft Visual Studio** bevat.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets18.png)

Ga naar **Onderzoek** in het linkermenu en onderzoek naar `<my-app>`. U moet alle instanties van `<my-app>` vervangen door `--aepUserLdap--citisignalaemaccs` .

Klik **vervangen allen** pictogram.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets19.png)

Klik **vervangen**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets20.png)

De nieuwe bestanden kunnen nu worden geüpload naar de Git Repo die is gekoppeld aan de Pipeline Repository van uw programma. Om dat te doen, open de omslag **AEM Pipeline GitHub** en klik op de omslag met de rechtermuisknop aan die de nieuwe dossiers bevat. Selecteer **Nieuwe Terminal bij Omslag**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets21.png)

Dan moet je dit zien. Plak het bevel `git add .` en de slag **gaat** binnen.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets22.png)

Dan moet je dit zien. Plak het bevel `git commit -m "add assets integration"` en de slag **gaat** binnen.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets23.png)

Dan moet je dit zien. Plak het bevel `git push origin main` en de slag **gaat** binnen.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets24.png)

Dan moet je dit zien. Uw veranderingen zijn nu opgesteld aan de Repo van het Git van uw Programma van de Pijpleiding.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets25.png)

Ga terug naar Cloud Manager en klik **dicht**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets26.png)

Na het aanbrengen van veranderingen in de Reparatie van het Git van de Pijpleiding, moet u **opstellen aan Dev** opnieuw pijpleiding. Klik de 3 punten **..** en selecteer **Looppas**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets27.png)

Klik **Looppas**. Het runnen van een pijpleidingsplaatsing kan 10-15 minuten vergen. U moet wachten tot de pijpleidingsplaatsing met succes voltooit alvorens verder te gaan.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets28.png)

## 1.5.3.2 AEM Assets-integratie inschakelen in ACCS

Ga terug naar uw ACCS-instantie. In het linkermenu, ga naar **Opslag** en selecteer dan **Configuratie**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets49.png)

De rol neer in het menu aan **DIENSTEN van ADOBE** en opent dan **de Integratie van AEM Assets**. Dan moet je dit zien.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets50.png)

Vul de volgende variabelen in:

- **identiteitskaart van het Programma van AEM Assets**: U kunt identiteitskaart van het Programma van de Auteur URL van AEM CS nemen. In dit voorbeeld is de programma-id `166717` .

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets50a.png)

- **identiteitskaart van het Milieu van AEM Assets**: U kunt milieu identiteitskaart van de Auteur URL van AEM CS nemen. In dit voorbeeld is de milieu-id `1786231` .

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets50b.png)

- **Identiteitskaart van de Cliënt IMS van de Selecteur van Activa IMS**: reeks aan `1`
- **toegelaten Synchronisatie**: reeks aan `Yes`
- **Eigenaar van de Visualisatie**: reeks aan `AEM Assets`
- **de passende regel van Activa**: `Match by product SKU`
- **Gelijke door productSKU kenmerknaam**: `commerce:skus`

Klik **sparen Config**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets51.png)

Dan moet je dit zien.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets52.png)

## 1.5.3.3 Update config.json

Ga naar de gegevensopslagplaats GitHub die werd gecreeerd toen vestiging uw milieu van AEM Sites CS/EDS. Die bewaarplaats werd gecreeerd in de oefening [&#x200B; 1.1.2 Opstelling uw milieu van AEM CS &#x200B;](./../../../modules/asset-mgmt/module2.1/ex3.md){target="_blank"} en zou moeten worden genoemd **burgerschap-naam-toegang**.

In de wortelfolder, scrol neer en klik om het dossier **config.json** te openen. Klik **uitgeven** pictogram om veranderingen in het dossier aan te brengen.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets101.png)

Voeg het onderstaande codefragment toe onder regel 5 `"commerce-endpoint": "https://na1-sandbox.api.commerce.adobe.com/XXX/graphql",` :

```json
 "commerce-assets-enabled": "true",
```

Klik **Veranderingen vastleggen...**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets102.png)

Klik **Veranderingen** vastleggen.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets103.png)

Uw wijziging wordt nu opgeslagen en wordt binnenkort gepubliceerd. Het kan een paar minuten duren voordat de wijziging zichtbaar is op de winkelvoorgrond.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets104.png)

## 1.5.3.4 Commerce-velden verifiëren in AEM Assets CS

Login aan uw milieu van de Auteur van AEM CS en ga naar **Assets**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets30.png)

Ga naar **Dossiers**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets31.png)

Open de **CitiSignal** omslag.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets32.png)

Beweeg over om het even welk activa en klik het **info** pictogram.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets33.png)

U zou a **Commerce** lusje nu moeten zien dat 2 nieuwe meta-gegevensattributen bevat.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets34.png)

Uw AEM Assets CS-omgeving biedt nu ondersteuning voor de integratie met Commerce. U kunt nu productafbeeldingen uploaden.

## 1.5.3.4 Product Assets uploaden en koppelen naar producten

[&#x200B; Download hier de productbeelden &#x200B;](./images/Product_Images.zip). Exporteer de bestanden na het downloaden naar uw bureaublad.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets35.png)

Klik **creëren** en selecteer dan **Omslag**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets36.png)

Ga de waarde **Product_Images** voor de gebieden **Titel** en **Naam** in. Klik **creëren**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets37.png)

Klik om de map te openen die u net hebt gemaakt.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets38.png)

Klik **creëren** en selecteer dan **Dossiers**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets39.png)

Navigeer aan de {**omslag 0} Product_Images op uw Desktop, selecteer alle dossiers en klik dan** Open **.**

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets40.png)

Klik **uploaden**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets41.png)

Uw afbeeldingen zijn dan beschikbaar in uw map. Beweeg over het product **iPhone-AIR-Light-Gold.png** en klik het **3&rbrace; pictogram van Eigenschappen &lbrace;.**

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets42.png)

De rol neer en plaatst de status van het gebied **Overzicht** aan **Goedgekeurd**. De integratie van AEM Assets CS - ACCS werkt alleen voor goedgekeurde afbeeldingen.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets44.png)

De rol omhoog, gaat naar het **Commerce** lusje en klikt dan **&#x200B;**&#x200B;onder **de skus van het Product** toevoegen.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets45.png)

Voeg de volgende SKU&#39;s voor dit product toe:

| Sleutel | Waarde | Gebruik |
|:-------------:| :---------------:| :---------------:| 
| `iPhone-Air-Light-Gold` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Light-Gold-256GB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Light-Gold-512GB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Light-Gold-1TB` | `1` | `thumbnail, image, swatch_image, small_image` |

Dan moet je dit hebben. Klik **sparen &amp; Sluiten**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets46.png)

Beweeg over het product **iPhone-Air-Space-Black.png** en klik het **3&rbrace; pictogram van Eigenschappen &lbrace;.**

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets47.png)

De rol neer en plaatst de status van het gebied **Overzicht** aan **Goedgekeurd**. De integratie van AEM Assets CS - ACCS werkt alleen voor goedgekeurde afbeeldingen.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets48.png)

De rol omhoog, gaat naar het **Commerce** lusje en klikt dan **&#x200B;**&#x200B;onder **de skus van het Product** toevoegen.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets201.png)

Voeg de volgende SKU&#39;s voor dit product toe:

| Sleutel | Waarde | Gebruik |
|:-------------:| :---------------:| :---------------:| 
| `iPhone-Air-Space-Black` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Space-Black-256GB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Space-Black-512GB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Space-Black-1TB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air` | `1` | `thumbnail, image, swatch_image, small_image` |

Dan moet je dit hebben. Klik **sparen &amp; Sluiten**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets202.png)

Beweeg over het product **iPhone-Air-Sky-Blue.png** en klik het **3&rbrace; pictogram van Eigenschappen &lbrace;.**

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets203.png)

De rol neer en plaatst de status van het gebied **Overzicht** aan **Goedgekeurd**. De integratie van AEM Assets CS - ACCS werkt alleen voor goedgekeurde afbeeldingen.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets204.png)

De rol omhoog, gaat naar het **Commerce** lusje en klikt dan **&#x200B;**&#x200B;onder **de skus van het Product** toevoegen.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets205.png)

Voeg de volgende SKU&#39;s voor dit product toe:

| Sleutel | Waarde | Gebruik |
|:-------------:| :---------------:| :---------------:| 
| `iPhone-Air-Sky-Blue` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Sky-Blue-256GB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Sky-Blue-512GB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Sky-Blue-1TB` | `1` | `thumbnail, image, swatch_image, small_image` |

Dan moet je dit hebben. Klik **sparen &amp; Sluiten**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets206.png)

Beweeg over het product **iPhone-Air-Cloud-White.png** en klik het **3&rbrace; pictogram van Eigenschappen &lbrace;.**

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets207.png)

De rol neer en plaatst de status van het gebied **Overzicht** aan **Goedgekeurd**. De integratie van AEM Assets CS - ACCS werkt alleen voor goedgekeurde afbeeldingen.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets208.png)

De rol omhoog, gaat naar het **Commerce** lusje en klikt dan **&#x200B;**&#x200B;onder **de skus van het Product** toevoegen.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets209.png)

Voeg de volgende SKU&#39;s voor dit product toe:

| Sleutel | Waarde | Gebruik |
|:-------------:| :---------------:| :---------------:| 
| `iPhone-Air-Cloud-White` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Cloud-White-256GB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Cloud-White-512GB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Cloud-White-1TB` | `1` | `thumbnail, image, swatch_image, small_image` |

Dan moet je dit hebben. Klik **sparen &amp; Sluiten**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets210.png)

Elk **beeld van iPhone AIR** zou a **groene duimen omhoog** nu moeten hebben, erop wijzend dat de activa is goedgekeurd.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets250.png)

## 1.5.3.5 Productafbeeldingen verifiëren op AEM Sites CS/EDS Store

>[!NOTE]
>
>Het kan 15 minuten duren voordat de hierboven aangebrachte wijzigingen zijn geïmplementeerd. Als u nog niet ziet dat uw afbeelding wordt weergegeven, wacht u 15 minuten en probeert u het opnieuw.

Als u wilt controleren of de integratie werkt, moet u uw CitiSignal-website openen.

Ga naar `main--citisignal-aem-accs--XXX.aem.page` en/of `main--citisignal-aem-accs--XXX.aem.live` nadat u XXX hebt vervangen door uw GitHub-gebruikersaccount, wat in dit voorbeeld `woutervangeluwe` is.

In dit voorbeeld wordt de volledige URL als volgt:
`https://main--citisignal-aem-accs--woutervangeluwe.aem.page` en/of `https://main--citisignal-aem-accs--woutervangeluwe.aem.live` .

Dan moet je dit zien. Ga naar **Telefoons**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets150.png)

U zou dan een productbeeld moeten zien dat voor **AIR van iPhone** wordt getoond. Klik **AIR van iPhone**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets151.png)

Dan moet je dit zien. Wijzig de kleur- en opslagopties en u ziet de afbeeldingen dynamisch wijzigen op basis van de keuzes die u hebt gemaakt.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets152.png)

Hier is een voorbeeld van het veranderen van de kleur in **licht-Goud** en de opslaggrootte aan **256GB**.

![&#x200B; ACCS+AEM Assets &#x200B;](./images/accsaemassets153.png)

Volgende Stap: [&#x200B; Samenvatting &amp; Voordelen &#x200B;](./summary.md){target="_blank"}

Ga terug naar [&#x200B; Adobe Commerce as a Cloud Service &#x200B;](./accs.md){target="_blank"}

[&#x200B; ga terug naar Alle Modules &#x200B;](./../../../overview.md){target="_blank"}
