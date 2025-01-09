---
title: 1.1 Adobe Firefly
description: Adobe Firefly
kt: 5342
doc-type: tutorial
source-git-commit: d658ebcecea1cb98f6c7176a9238fcb740fb03e3
workflow-type: tm+mt
source-wordcount: '935'
ht-degree: 0%

---

# Aan de slag

De volgende toepassingen moeten op uw computer zijn geïnstalleerd voordat u deze zelfstudie kunt uitvoeren:

- Adobe Creative Cloud
- Photoshop 2025
- Postman

## 1. Installeer de Chrome-extensie voor de documentatie van het Experience League

### Over de Chrome-extensie

De documentatie is algemeen gemaakt zodat het gemakkelijk door iedereen kan worden hergebruikt, gebruikend om het even welke instantie van de Adobe.
Om de documentatie herbruikbaar te maken, **Variabelen van het Milieu** werden geïntroduceerd in de documentatie, zo betekent het dat u hieronder **placeholders** in de documentatie zult vinden. Elke placeholder is een specifieke variabele voor een specifiek milieu, en de uitbreiding van Chrome zal die variabele voor u veranderen om het voor u gemakkelijk te maken om code en tekst van de leerzame pagina&#39;s te kopiëren en het te kleven in de diverse gebruikersinterfaces die u als deel van het leerprogramma zult gebruiken.

Hieronder vindt u een voorbeeld van dergelijke waarden. Deze waarden kunnen momenteel nog niet worden gebruikt, maar zodra u de Chrome-extensie installeert en activeert, worden deze variabelen gewijzigd in normale tekst die u kunt kopiëren en opnieuw kunt gebruiken.

| Naam | Sleutel |
|:-------------:| :---------------:|
| IMS Org ID | `--aepImsOrgId--` |
| AEP-huurnummer | `--aepTenantId--` |
| Naam AEP-sandbox | `--aepSandboxName--` |
| Leerlingprofiel LDAP | `--aepUserLdap--` |

In de onderstaande schermafbeelding ziet u bijvoorbeeld een verwijzing naar `aepTenantId` .

![ DSN ](./images/mod7before.png)

Nadat de extensie is geïnstalleerd, wordt dezelfde tekst automatisch gewijzigd om de instantiespecifieke waarden weer te geven.

![ DSN ](./images/mod7.png)

### De Chrome-extensie installeren

Om die uitbreiding van Chrome te installeren, open uw browser van Chrome en ga naar: [ https://chromewebstore.google.com/detail/tech-insiders-learning-fo/hhnbkfgioecmhimdhooigajdajplinfi ](https://chromewebstore.google.com/detail/tech-insiders-learning-fo/hhnbkfgioecmhimdhooigajdajplinfi). Dan zie je dit.

Klik **toevoegen aan Chrome**.

![ DSN ](./images/c2.png)

Dan zie je dit. Klik **toevoegen uitbreiding**.

![ DSN ](./images/c3.png)

De extensie wordt dan geïnstalleerd en u ziet een vergelijkbare melding.

![ DSN ](./images/c4.png)

In het **menu van uitbreidingen**, klik het **puzzelstuk** pictogram en speld het **Platform Leren - de uitbreiding van de Configuratie** aan het uitbreidingsmenu.

![ DSN ](./images/c6.png)

### De Chrome-extensie configureren

Ga naar [ https://experienceleague.adobe.com/en/docs/platform-learn/tutorial-comprehensive-technical/overview ](https://experienceleague.adobe.com/en/docs/platform-learn/tutorial-comprehensive-technical/overview) en klik dan het uitbreidingspictogram om het te openen.

![ DSN ](./images/tuthome.png)

Dan zie je deze popup. Klik op het pictogram **+** .

![ DSN ](./images/c7.png)

Voer de waarden in zoals hieronder aangegeven. Deze zijn allemaal gerelateerd aan uw Adobe Experience Platform-exemplaar.

![ DSN ](./images/c8.png)

Als u niet zeker weet welke waarden u voor deze velden moet invoeren, volgt u de onderstaande aanwijzingen.

**AEP IMS Org Name**

Wanneer u login aan uw instantie van Adobe Experience Platform op [ https://platform.adobe.com/ ](https://platform.adobe.com/), zult u de naam van uw instantie in de hoogste juiste hoek van uw scherm vinden.

![ DSN ](./images/aepname.png)

**AEP IMS Org ID**

De IMS-organisatie-id is de unieke id voor uw Adobe Experience Cloud-instantie en er wordt in deze zelfstudie naar verwezen op meerdere locaties.

U kunt uw IMS-organisatie-id op meerdere manieren zoeken. Als u niet zeker bent, controleer met één van de systeembeheerders van uw instantie om identiteitskaart te vinden.

U kunt het vinden door naar [ Admin Console ](https://https://adminconsole.adobe.com/) te gaan, waar u het als deel van URL kunt vinden.

![ DSN ](./images/aepid1.png)

U kunt het ook vinden door naar **het Beheer van Gegevens > Vragen** in uw menu van AEP te gaan, waar u het onder **Gebruikersnaam** kunt vinden.

![ DSN ](./images/aepid2.png)

Kopieer en plak het **@AdobeOrg** -onderdeel samen met de id.

**identiteitskaart van de HUIDIGE VAN AEP**

Uw huurnummer is de unieke id voor de AEP-instantie van uw organisatie. Wanneer u login aan uw instantie van Adobe Experience Platform op [ https://platform.adobe.com/ ](https://platform.adobe.com/), zult u huurder identiteitskaart in URL vinden.

![ DSN ](./images/aeptenantid.png)

Wanneer u het in de uitbreiding van Chrome ingaat, zou u moeten ervoor zorgen dat een onderstrepingsteken als prefix wordt toegevoegd, zodat in dit voorbeeld **ervaringsplatform** **_experiencePlatform** wordt.

**AEP Sandbox Naam**

De naam van de sandbox is de naam van de omgeving die u in uw AEP-instantie gebruikt. Wanneer u login aan uw instantie van Adobe Experience Platform op [ https://platform.adobe.com/ ](https://platform.adobe.com/), zult u huurder identiteitskaart in URL vinden.

Voordat u de naam van de sandbox opgeeft van de URL, moet u ervoor zorgen dat u zich in de sandbox bevindt die u voor deze zelfstudie moet gebruiken. U kunt naar de rechtersandbox schakelen door op het menu met sandboxswitches in de rechterbovenhoek van het scherm te klikken.

![ DSN ](./images/aepsandboxsw.png)

In dit voorbeeld, is de Naam van de zandbak AEP **technologie-insiders**.

![ DSN ](./images/aepsname.png)

**Uw LDAP**

Dit is de gebruikersnaam die wordt gebruikt als onderdeel van de zelfstudie. In dit voorbeeld is de LDAP gebaseerd op het e-mailadres van deze gebruiker. Het e-mailadres is **vangeluw@adobe.com** zodat wordt LDAP **vangeluw**.

LDAP wordt gebruikt om ervoor te zorgen dat de configuratie u zult doen met u verbonden zijn, en niet met andere gebruikers die de zelfde instantie en zandbak kunnen gebruiken die u gebruikt.

Uw waarden moeten er ongeveer zo uitzien.
Tot slot klik **creeer Nieuw**.

![ DSN ](./images/c8a.png)


In het linkermenu van de extensie ziet u nu een nieuw pictogram met de initialen van uw omgeving. Klik erop. U zult dan de afbeelding tussen de **Variabelen van het Milieu** en uw specifieke de instantieswaarden van Adobe Experience Platform zien. Klik **activeren Configuratie**.

![ DSN ](./images/c9.png)

Nadat u de configuratie hebt geactiveerd, ziet u een groene stip naast de initialen van uw omgeving. Dit betekent dat uw omgeving nu actief is.

![ DSN ](./images/c10.png)

### Inhoud van zelfstudie controleren

Als test, ga [ deze pagina ](https://experienceleague.adobe.com/en/docs/platform-learn/tutorial-comprehensive-technical/datadistiller/module51/ex3).

U zou nu moeten zien dat alle **Variabelen van het Milieu** door hun ware waarden zijn vervangen, die op het geactiveerde milieu in de chroomuitbreiding worden gebaseerd.

U zou nu een gelijkaardige mening aan hieronder moeten hebben, waar de omgevingsvariabele `aepTenantId` door uw echte identiteitskaart van de Huurder van AEP is vervangen, die in dit geval **_experiencePlatform** is.

![ DSN ](./images/mod7.png)


>[!NOTE]
>
>Bedankt dat u uw tijd hebt geïnvesteerd in het leren van alles wat er over Adobe Experience Platform en zijn toepassingen te weten komt. Als u vragen hebt, wil algemene terugkoppelen van hebben suggesties over toekomstige inhoud delen, gelieve direct contactTech Insiders, door een e-mail naar **techinsiders@adobe.com** te verzenden.

[Terug naar alle modules](../../overview.md)
