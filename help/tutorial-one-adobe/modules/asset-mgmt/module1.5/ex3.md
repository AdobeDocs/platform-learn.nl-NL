---
title: ACCS verbinden met AEM Assets CS
description: ACCS verbinden met AEM Assets CS
kt: 5342
doc-type: tutorial
source-git-commit: 58448049d54ee6124985159577df0e307896a312
workflow-type: tm+mt
source-wordcount: '1651'
ht-degree: 0%

---

# 1.5.3 ACCS verbinden met AEM Assets CS

>[!IMPORTANT]
>
>Om deze oefening te voltooien, moet u toegang tot een werkende AEM Sites en Assets CS met milieu EDS hebben.
>
>Als u zulk een milieu nog niet hebt, ga [ Adobe Experience Manager Cloud Service &amp; Edge Delivery Services ](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"} uitoefenen. Volg de instructies daar, en u zult toegang tot zulk een milieu hebben.

>[!IMPORTANT]
>
>Als u eerder een AEM CS-programma hebt geconfigureerd met een AEM Sites- en Assets CS-omgeving, kan het zijn dat uw AEM CS-sandbox is geminimaliseerd. Gezien het feit dat het vernietigen van zo&#39;n zandbak 10 tot 15 minuten duurt, zou het een goed idee zijn om het ontruimingsproces nu te beginnen zodat u niet op een later tijdstip hoeft te wachten.

Na de vorige oefening kon u een product zien dat door ACCS aan uw website wordt teruggegeven maar het had nog geen beeld. Aan het eind van deze oefening, zou u een beeld moeten zien dat ook wordt teruggegeven.

![ ACCS+AEM Sites ](./images/accsaemsites11.png)

## 1.5.3.1 Configuratie pijplijn bijwerken

Ga naar [ https://my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com){target="_blank"}. De org die u moet selecteren is `--aepImsOrgName--`.

Klik hierop om het Cloud Manager-programma te openen. Dit wordt `--aepUserLdap-- - CitiSignal AEM+ACCS` genoemd.

![ ACCS+AEM Assets ](./images/accsaemassets1.png)

Scoll neer een klein beetje en klik dan **Info van de Reparatie van de Toegang** op de **Pijpleidingen** tabel.

![ ACCS+AEM Assets ](./images/accsaemassets2.png)

Dan moet je dit zien. Klik **produceer Wachtwoord**.

![ ACCS+AEM Assets ](./images/accsaemassets3.png)

Klik **produceer opnieuw Wachtwoord**.

![ ACCS+AEM Assets ](./images/accsaemassets4.png)

U zou dan een wachtwoord beschikbaar moeten hebben. Daarna, klik het **exemplaar** pictogram naast het **bevel van de Git bevel lijn** gebied.

![ ACCS+AEM Assets ](./images/accsaemassets5.png)

Creeer een nieuwe folder in een plaats van keus op uw computer en noem het **AEM Pipeline GitHub**.

![ ACCS+AEM Assets ](./images/accsaemassets6.png)

Klik met de rechtermuisknop op uw map en selecteer vervolgens **Nieuwe terminal bij Map** .

![ ACCS+AEM Assets ](./images/accsaemassets7.png)

Dan moet je dit zien.

![ ACCS+AEM Assets ](./images/accsaemassets8.png)

Plak het **bevel van de het bevellijn van de Git** dat u alvorens in het Eind venster kopieerde.

![ ACCS+AEM Assets ](./images/accsaemassets9.png)

U moet een gebruikersnaam invoeren. Kopieer de gebruikersnaam van de Pijpleiding van het Programma van de Cloud Manager **Reparatie van de Toegang Info** en de slag **gaat** binnen.

![ ACCS+AEM Assets ](./images/accsaemassets10.png)

Vervolgens moet u het wachtwoord invoeren. Kopieer het wachtwoord van de Pijpleiding van het Programma van de Cloud Manager **Reparatie Info van de Toegang** en de slag **gaat** binnen.

![ ACCS+AEM Assets ](./images/accsaemassets11.png)

Dit kan even duren. Zodra voltooid, zult u een lokale kopie van de Repo van het Git hebben die met de Pijpleiding van uw Programma wordt verbonden.

![ ACCS+AEM Assets ](./images/accsaemassets12.png)

U zult een nieuwe folder in de **folder GitHub van de Pijpleiding van AEM** zien. Open die map.

![ ACCS+AEM Assets ](./images/accsaemassets13.png)

Selecteer alle bestanden in die map en verwijder alle bestanden.

![ ACCS+AEM Assets ](./images/accsaemassets14.png)

Zorg ervoor dat de map leeg is.

![ ACCS+AEM Assets ](./images/accsaemassets15.png)

Ga naar [ https://github.com/ankumalh/assets-commerce ](https://github.com/ankumalh/assets-commerce).

Daarna, kopieer het dossier **activa-commerce-main.zip** aan uw Desktop en unzip het. Open de omslag **activa-handel-belangrijkste**.

![ ACCS+AEM Assets ](./images/accsaemassets16.png)

Kopieer alle dossiers van de folder **activa-handel-belangrijkste** aan de lege folder van de folder van de Bewaarplaats van de Pijpleiding van uw Programma.

![ ACCS+AEM Assets ](./images/accsaemassets17.png)

Daarna, open **Code van Microsoft Visual Studio** en open de omslag die de Bewaarplaats van de Pijpleiding van uw Programma in **Code van Microsoft Visual Studio** bevat.

![ ACCS+AEM Assets ](./images/accsaemassets18.png)

Ga naar **Onderzoek** in het linkermenu en onderzoek naar `<my-app>`. U moet alle instanties van `<my-app>` vervangen door `--aepUserLdap--citisignalaemaccs` .

Klik **vervangen allen** pictogram.

![ ACCS+AEM Assets ](./images/accsaemassets19.png)

Klik **vervangen**.

![ ACCS+AEM Assets ](./images/accsaemassets20.png)

De nieuwe bestanden kunnen nu worden geüpload naar de Git Repo die is gekoppeld aan de Pipeline Repository van uw programma. Om dat te doen, open de omslag **AEM Pipeline GitHub** en klik op de omslag met de rechtermuisknop aan die de nieuwe dossiers bevat. Selecteer **Nieuwe Terminal bij Omslag**.

![ ACCS+AEM Assets ](./images/accsaemassets21.png)

Dan moet je dit zien. Plak het bevel `git add .` en de slag **gaat** binnen.

![ ACCS+AEM Assets ](./images/accsaemassets22.png)

Dan moet je dit zien. Plak het bevel `git commit -m "add assets integration"` en de slag **gaat** binnen.

![ ACCS+AEM Assets ](./images/accsaemassets23.png)

Dan moet je dit zien. Plak het bevel `git push origin main` en de slag **gaat** binnen.

![ ACCS+AEM Assets ](./images/accsaemassets24.png)

Dan moet je dit zien. Uw veranderingen zijn nu opgesteld aan de Repo van het Git van uw Programma van de Pijpleiding.

![ ACCS+AEM Assets ](./images/accsaemassets25.png)

Ga terug naar Cloud Manager en klik **dicht**.

![ ACCS+AEM Assets ](./images/accsaemassets26.png)

Na het aanbrengen van veranderingen in de Reparatie van het Git van de Pijpleiding, moet u **opstellen aan Dev** opnieuw pijpleiding. Klik de 3 punten **..** en selecteer **Looppas**.

![ ACCS+AEM Assets ](./images/accsaemassets27.png)

Klik **Looppas**. Het runnen van een pijpleidingsplaatsing kan 10-15 minuten vergen. U moet wachten tot de pijpleidingsplaatsing met succes voltooit alvorens verder te gaan.

![ ACCS+AEM Assets ](./images/accsaemassets28.png)

## 1.5.3.2 AEM Assets-integratie inschakelen in ACCS

Ga terug naar uw ACCS-instantie. In het linkermenu, ga naar **Opslag** en selecteer dan **Configuratie**.

![ ACCS+AEM Assets ](./images/accsaemassets49.png)

De rol neer in het menu aan **DIENSTEN van ADOBE** en opent dan **de Integratie van AEM Assets**. Dan moet je dit zien.

![ ACCS+AEM Assets ](./images/accsaemassets50.png)

Vul de volgende variabelen in:

- **identiteitskaart van het Programma van AEM Assets**: U kunt identiteitskaart van het Programma van de Auteur URL van AEM CS nemen. In dit voorbeeld is de programma-id `166717` .

![ ACCS+AEM Assets ](./images/accsaemassets50a.png)

- **identiteitskaart van het Milieu van AEM Assets**: U kunt milieu identiteitskaart van de Auteur URL van AEM CS nemen. In dit voorbeeld is de milieu-id `1786231` .

![ ACCS+AEM Assets ](./images/accsaemassets50b.png)

- **Identiteitskaart van de Cliënt IMS van de Selecteur van Activa IMS**: reeks aan `1`
- **toegelaten Synchronisatie**: reeks aan `Yes`
- **Eigenaar van de Visualisatie**: reeks aan `AEM Assets`
- **de passende regel van Activa**: `Match by product SKU`
- **Gelijke door productSKU kenmerknaam**: `commerce:skus`

Klik **sparen Config**.

![ ACCS+AEM Assets ](./images/accsaemassets51.png)

Dan moet je dit zien.

![ ACCS+AEM Assets ](./images/accsaemassets52.png)

## 1.5.3.3 Update config.json

Ga naar de gegevensopslagplaats GitHub die werd gecreeerd toen vestiging uw milieu van AEM Sites CS/EDS. Die bewaarplaats werd gecreeerd in de oefening [ 1.1.2 Opstelling uw milieu van AEM CS ](./../../../modules/asset-mgmt/module2.1/ex3.md){target="_blank"} en zou moeten worden genoemd **burgerschap-naam-toegang**.

In de wortelfolder, scrol neer en klik om het dossier **config.json** te openen. Klik **uitgeven** pictogram om veranderingen in het dossier aan te brengen.

![ ACCS+AEM Assets ](./images/accsaemassets101.png)

Voeg het onderstaande codefragment toe onder regel 5 `"commerce-endpoint": "https://na1-sandbox.api.commerce.adobe.com/XXX/graphql",` :

```json
 "commerce-assets-enabled": "true",
```

Klik **Veranderingen vastleggen...**.

![ ACCS+AEM Assets ](./images/accsaemassets102.png)

Klik **Veranderingen** vastleggen.

![ ACCS+AEM Assets ](./images/accsaemassets103.png)

Uw wijziging wordt nu opgeslagen en wordt binnenkort gepubliceerd. Het kan een paar minuten duren voordat de wijziging zichtbaar is op de winkelvoorgrond.

![ ACCS+AEM Assets ](./images/accsaemassets104.png)

## 1.5.3.4 Commerce-velden verifiëren in AEM Assets CS

Login aan uw milieu van de Auteur van AEM CS en ga naar **Assets**.

![ ACCS+AEM Assets ](./images/accsaemassets30.png)

Ga naar **Dossiers**.

![ ACCS+AEM Assets ](./images/accsaemassets31.png)

Open de **CitiSignal** omslag.

![ ACCS+AEM Assets ](./images/accsaemassets32.png)

Beweeg over om het even welk activa en klik het **info** pictogram.

![ ACCS+AEM Assets ](./images/accsaemassets33.png)

U zou a **Commerce** lusje nu moeten zien dat 2 nieuwe meta-gegevensattributen bevat.

![ ACCS+AEM Assets ](./images/accsaemassets34.png)

Uw AEM Assets CS-omgeving biedt nu ondersteuning voor de integratie met Commerce. U kunt nu productafbeeldingen uploaden.

## 1.5.3.4 Product Assets uploaden en koppelen naar producten

[ Download hier de productbeelden ](./images/Product_Images.zip). Exporteer de bestanden na het downloaden naar uw bureaublad.

![ ACCS+AEM Assets ](./images/accsaemassets35.png)

Klik **creëren** en selecteer dan **Omslag**.

![ ACCS+AEM Assets ](./images/accsaemassets36.png)

Ga de waarde **Product_Images** voor de gebieden **Titel** en **Naam** in. Klik **creëren**.

![ ACCS+AEM Assets ](./images/accsaemassets37.png)

Klik om de map te openen die u net hebt gemaakt.

![ ACCS+AEM Assets ](./images/accsaemassets38.png)

Klik **creëren** en selecteer dan **Dossiers**.

![ ACCS+AEM Assets ](./images/accsaemassets39.png)

Navigeer aan de {**omslag 0} Product_Images op uw Desktop, selecteer alle dossiers en klik dan** Open **.**

![ ACCS+AEM Assets ](./images/accsaemassets40.png)

Klik **uploaden**.

![ ACCS+AEM Assets ](./images/accsaemassets41.png)

Uw afbeeldingen zijn dan beschikbaar in uw map. Beweeg over het product **iPhone-AIR-Light-Gold.png** en klik het **3&rbrace; pictogram van Eigenschappen &lbrace;.**

![ ACCS+AEM Assets ](./images/accsaemassets42.png)

De rol neer en plaatst de status van het gebied **Overzicht** aan **Goedgekeurd**. De integratie van AEM Assets CS - ACCS werkt alleen voor goedgekeurde afbeeldingen.

![ ACCS+AEM Assets ](./images/accsaemassets44.png)

De rol omhoog, gaat naar het **Commerce** lusje en klikt dan **&#x200B;**&#x200B;onder **de skus van het Product** toevoegen.

![ ACCS+AEM Assets ](./images/accsaemassets45.png)

Voeg de volgende SKU&#39;s voor dit product toe:

| Sleutel | Waarde | Gebruik |
|:-------------:| :---------------:| :---------------:| 
| `iPhone-Air-Light-Gold` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Light-Gold-256GB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Light-Gold-512GB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Light-Gold-1TB` | `1` | `thumbnail, image, swatch_image, small_image` |

Dan moet je dit hebben. Klik **sparen &amp; Sluiten**.

![ ACCS+AEM Assets ](./images/accsaemassets46.png)

Beweeg over het product **iPhone-Air-Space-Black.png** en klik het **3&rbrace; pictogram van Eigenschappen &lbrace;.**

![ ACCS+AEM Assets ](./images/accsaemassets47.png)

De rol neer en plaatst de status van het gebied **Overzicht** aan **Goedgekeurd**. De integratie van AEM Assets CS - ACCS werkt alleen voor goedgekeurde afbeeldingen.

![ ACCS+AEM Assets ](./images/accsaemassets48.png)

De rol omhoog, gaat naar het **Commerce** lusje en klikt dan **&#x200B;**&#x200B;onder **de skus van het Product** toevoegen.

![ ACCS+AEM Assets ](./images/accsaemassets201.png)

Voeg de volgende SKU&#39;s voor dit product toe:

| Sleutel | Waarde | Gebruik |
|:-------------:| :---------------:| :---------------:| 
| `iPhone-Air-Space-Black` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Space-Black-256GB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Space-Black-512GB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Space-Black-1TB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air` | `1` | `thumbnail, image, swatch_image, small_image` |

Dan moet je dit hebben. Klik **sparen &amp; Sluiten**.

![ ACCS+AEM Assets ](./images/accsaemassets202.png)

Beweeg over het product **iPhone-Air-Sky-Blue.png** en klik het **3&rbrace; pictogram van Eigenschappen &lbrace;.**

![ ACCS+AEM Assets ](./images/accsaemassets203.png)

De rol neer en plaatst de status van het gebied **Overzicht** aan **Goedgekeurd**. De integratie van AEM Assets CS - ACCS werkt alleen voor goedgekeurde afbeeldingen.

![ ACCS+AEM Assets ](./images/accsaemassets204.png)

De rol omhoog, gaat naar het **Commerce** lusje en klikt dan **&#x200B;**&#x200B;onder **de skus van het Product** toevoegen.

![ ACCS+AEM Assets ](./images/accsaemassets205.png)

Voeg de volgende SKU&#39;s voor dit product toe:

| Sleutel | Waarde | Gebruik |
|:-------------:| :---------------:| :---------------:| 
| `iPhone-Air-Sky-Blue` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Sky-Blue-256GB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Sky-Blue-512GB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Sky-Blue-1TB` | `1` | `thumbnail, image, swatch_image, small_image` |

Dan moet je dit hebben. Klik **sparen &amp; Sluiten**.

![ ACCS+AEM Assets ](./images/accsaemassets206.png)

Beweeg over het product **iPhone-Air-Cloud-White.png** en klik het **3&rbrace; pictogram van Eigenschappen &lbrace;.**

![ ACCS+AEM Assets ](./images/accsaemassets207.png)

De rol neer en plaatst de status van het gebied **Overzicht** aan **Goedgekeurd**. De integratie van AEM Assets CS - ACCS werkt alleen voor goedgekeurde afbeeldingen.

![ ACCS+AEM Assets ](./images/accsaemassets208.png)

De rol omhoog, gaat naar het **Commerce** lusje en klikt dan **&#x200B;**&#x200B;onder **de skus van het Product** toevoegen.

![ ACCS+AEM Assets ](./images/accsaemassets209.png)

Voeg de volgende SKU&#39;s voor dit product toe:

| Sleutel | Waarde | Gebruik |
|:-------------:| :---------------:| :---------------:| 
| `iPhone-Air-Cloud-White` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Cloud-White-256GB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Cloud-White-512GB` | `1` | `thumbnail, image, swatch_image, small_image` |
| `iPhone-Air-Cloud-White-1TB` | `1` | `thumbnail, image, swatch_image, small_image` |

Dan moet je dit hebben. Klik **sparen &amp; Sluiten**.

![ ACCS+AEM Assets ](./images/accsaemassets210.png)

Elk **beeld van iPhone AIR** zou a **groene duimen omhoog** nu moeten hebben, erop wijzend dat de activa is goedgekeurd.

![ ACCS+AEM Assets ](./images/accsaemassets250.png)

## 1.5.3.5 Productafbeeldingen verifiëren op AEM Sites CS/EDS Store

>[!NOTE]
>
>Het kan 15 minuten duren voordat de hierboven aangebrachte wijzigingen zijn geïmplementeerd. Als u nog niet ziet dat uw afbeelding wordt weergegeven, wacht u 15 minuten en probeert u het opnieuw.

Als u wilt controleren of de integratie werkt, moet u uw CitiSignal-website openen.

Ga naar `main--citisignal-aem-accs--XXX.aem.page` en/of `main--citisignal-aem-accs--XXX.aem.live` nadat u XXX hebt vervangen door uw GitHub-gebruikersaccount, wat in dit voorbeeld `woutervangeluwe` is.

In dit voorbeeld wordt de volledige URL als volgt:
`https://main--citisignal-aem-accs--woutervangeluwe.aem.page` en/of `https://main--citisignal-aem-accs--woutervangeluwe.aem.live` .

Dan moet je dit zien. Ga naar **Telefoons**.

![ ACCS+AEM Assets ](./images/accsaemassets150.png)

U zou dan een productbeeld moeten zien dat voor **AIR van iPhone** wordt getoond. Klik **AIR van iPhone**.

![ ACCS+AEM Assets ](./images/accsaemassets151.png)

Dan moet je dit zien. Wijzig de kleur- en opslagopties en u ziet de afbeeldingen dynamisch wijzigen op basis van de keuzes die u hebt gemaakt.

![ ACCS+AEM Assets ](./images/accsaemassets152.png)

Hier is een voorbeeld van het veranderen van de kleur in **licht-Goud** en de opslaggrootte aan **256GB**.

![ ACCS+AEM Assets ](./images/accsaemassets153.png)

Volgende Stap: [ Samenvatting &amp; Voordelen ](./summary.md){target="_blank"}

Ga terug naar [ Adobe Commerce as a Cloud Service ](./accs.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}
