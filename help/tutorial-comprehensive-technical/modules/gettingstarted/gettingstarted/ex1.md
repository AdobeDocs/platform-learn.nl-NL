---
title: Aan de slag - Installeer de Chrome-extensie voor de documentatie van het Experience League
description: Aan de slag - Installeer de Chrome-extensie voor de documentatie van het Experience League
kt: 5342
doc-type: tutorial
exl-id: da7aa686-7f25-49fd-af3e-d243ffda025f
source-git-commit: 1526661a80b4d551627dfca42a7e97c9498dd1f2
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 0%

---

# De Chrome-extensie installeren voor de documentatie van het Experience League

## Over de Chrome-extensie

De documentatie is generiek gemaakt zodat het gemakkelijk door iedereen kan worden hergebruikt, gebruikend om het even welke instantie van Adobe Experience Platform.
Om de documentatie herbruikbaar te maken, **Variabelen van het Milieu** werden geïntroduceerd in de documentatie, zo betekent het dat u hieronder **placeholders** in de documentatie zult vinden. Elke placeholder is een specifieke variabele voor een specifiek milieu, en de uitbreiding van Chrome zal die variabele voor u veranderen om het voor u gemakkelijk te maken om code en tekst van de leerzame pagina&#39;s te kopiëren en het te kleven in de diverse gebruikersinterfaces die u als deel van het leerprogramma zult gebruiken.

Hieronder vindt u een voorbeeld van dergelijke waarden. Deze waarden kunnen momenteel nog niet worden gebruikt, maar zodra u de Chrome-extensie installeert en activeert, worden deze variabelen gewijzigd in normale tekst die u kunt kopiëren en opnieuw kunt gebruiken.

| Naam | Sleutel | Voorbeeld |
|:-------------:| :---------------:| :---------------:|
| AEP IMS Org ID | `--aepImsOrgId--` | `907075E95BF479EC0A495C73@AdobeOrg` |
| AEP IMS Org Name | `--aepImsOrgName--` | `Experience Platform International` |
| AEP-huurnummer | `--aepTenantId--` | `_experienceplatform` |
| Naam AEP-sandbox | `--aepSandboxName--` | `tech-insiders` |
| Leerlingprofiel LDAP | `--aepUserLdap--` | `vangeluw` |

In de onderstaande schermafbeelding ziet u bijvoorbeeld een verwijzing naar `aepTenantId` .

![&#x200B; DSN &#x200B;](./images/mod7before.png)

Nadat de extensie is geïnstalleerd, wordt dezelfde tekst automatisch gewijzigd om de instantiespecifieke waarden weer te geven.

![&#x200B; DSN &#x200B;](./images/mod7.png)

## De Chrome-extensie installeren

Om die uitbreiding van Chrome te installeren, open uw browser van Chrome en ga naar: [&#x200B; https://chromewebstore.google.com/detail/tech-insiders-learning-fo/hhnbkfgioecmhimdhooigajdajplinfi &#x200B;](https://chromewebstore.google.com/detail/tech-insiders-learning-fo/hhnbkfgioecmhimdhooigajdajplinfi). Dan zie je dit.

Klik **toevoegen aan Chrome**.

![&#x200B; DSN &#x200B;](./images/c2.png)

Dan zie je dit. Klik **toevoegen uitbreiding**.

![&#x200B; DSN &#x200B;](./images/c3.png)

De extensie wordt dan geïnstalleerd en u ziet een vergelijkbare melding.

![&#x200B; DSN &#x200B;](./images/c4.png)

In het **menu van uitbreidingen**, klik het **puzzelstuk** pictogram en speld het **Platform Leren - de uitbreiding van de Configuratie** aan het uitbreidingsmenu.

![&#x200B; DSN &#x200B;](./images/c6.png)

## De Chrome-extensie configureren

Ga naar [&#x200B; https://experienceleague.adobe.com/nl/docs/platform-learn/tutorial-comprehensive-technical/overview &#x200B;](https://experienceleague.adobe.com/nl/docs/platform-learn/tutorial-comprehensive-technical/overview) en klik dan het uitbreidingspictogram om het te openen.

![&#x200B; DSN &#x200B;](./images/tuthome.png)

Dan zie je deze popup. Klik op het pictogram **+** .

![&#x200B; DSN &#x200B;](./images/c7.png)

Voer de waarden in zoals hieronder aangegeven. Deze zijn allemaal gerelateerd aan uw Adobe Experience Platform-exemplaar.

![&#x200B; DSN &#x200B;](./images/c8.png)

Als u niet zeker weet welke waarden u voor deze velden moet invoeren, volgt u de onderstaande aanwijzingen.

**Adobe Experience Platform IMS Org Name**

Wanneer u login aan uw instantie van Adobe Experience Platform op [&#x200B; https://platform.adobe.com/ &#x200B;](https://platform.adobe.com/), zult u de naam van uw instantie in de hoogste juiste hoek van uw scherm vinden.

![&#x200B; DSN &#x200B;](./images/aepname.png)

**Adobe Experience Platform IMS Org ID**

De IMS-organisatie-id is de unieke id voor uw Adobe Experience Cloud-instantie en er wordt in deze zelfstudie naar verwezen op meerdere locaties.

U kunt uw IMS-organisatie-id op meerdere manieren zoeken. Als u niet zeker bent, controleer met één van de systeembeheerders van uw instantie om identiteitskaart te vinden.

U kunt het vinden door naar [&#x200B; Admin Console &#x200B;](https://adminconsole.adobe.com/) te gaan, waar u het als deel van URL kunt vinden.

![&#x200B; DSN &#x200B;](./images/aepid1.png)

U kunt het ook vinden door **het Beheer van Gegevens > Vragen** in uw menu van Adobe Experience Platform te gaan, waar u het onder **Gebruikersnaam** kunt vinden.

![&#x200B; DSN &#x200B;](./images/aepid2.png)

Kopieer en plak het **@AdobeOrg** -onderdeel samen met de id.

**identiteitskaart van de HTENT van Adobe Experience Platform**

Uw Tenant-id is de unieke id voor het Adobe Experience Platform-exemplaar van uw organisatie. Wanneer u login aan uw instantie van Adobe Experience Platform op [&#x200B; https://platform.adobe.com/ &#x200B;](https://platform.adobe.com/), zult u huurder identiteitskaart in URL vinden.

![&#x200B; DSN &#x200B;](./images/aeptenantid.png)

Wanneer u het in de uitbreiding van Chrome ingaat, zou u moeten ervoor zorgen dat een onderstrepingsteken als prefix wordt toegevoegd, zodat in dit voorbeeld **ervaringsplatform** **_experiencePlatform** wordt. Ook, zorg ervoor om het **@** symbool te verwijderen wanneer het kopiëren van URL.

**Naam van zandbak van Adobe Experience Platform**

De naam van de sandbox is de naam van de omgeving die u in uw Adobe Experience Platform-instantie gebruikt. Wanneer u login aan uw instantie van Adobe Experience Platform op [&#x200B; https://platform.adobe.com/ &#x200B;](https://platform.adobe.com/), zult u huurder identiteitskaart in URL vinden.

Voordat u de naam van de sandbox opgeeft van de URL, moet u ervoor zorgen dat u zich in de sandbox bevindt die u voor deze zelfstudie moet gebruiken. U kunt naar de rechtersandbox schakelen door op het menu met sandboxswitches in de rechterbovenhoek van het scherm te klikken.

![&#x200B; DSN &#x200B;](./images/aepsandboxsw.png)

In dit voorbeeld, is de Naam van de zandbak van Adobe Experience Platform **technologie-insiders**.

![&#x200B; DSN &#x200B;](./images/aepsname.png)

**Uw LDAP**

Dit is de gebruikersnaam die wordt gebruikt als onderdeel van de zelfstudie. In dit voorbeeld is de LDAP gebaseerd op het e-mailadres van deze gebruiker. Het e-mailadres is **vangeluw@adobe.com** zodat wordt LDAP **vangeluw**.

LDAP wordt gebruikt om ervoor te zorgen dat de configuratie u zult doen met u verbonden zijn, en niet met andere gebruikers die de zelfde instantie en zandbak kunnen gebruiken die u gebruikt.

Uw waarden moeten er ongeveer zo uitzien.
Tot slot klik **creeer Nieuw**.

![&#x200B; DSN &#x200B;](./images/c8a.png)


In het linkermenu van de extensie ziet u nu een nieuw pictogram met de initialen van uw omgeving. Klik erop. U zult dan de afbeelding tussen de **Variabelen van het Milieu** en uw specifieke de instantieswaarden van Adobe Experience Platform zien. Klik **activeren Configuratie**.

![&#x200B; DSN &#x200B;](./images/c9.png)

Nadat u de configuratie hebt geactiveerd, ziet u een groene stip naast de initialen van uw omgeving. Dit betekent dat uw omgeving nu actief is.

![&#x200B; DSN &#x200B;](./images/c10.png)

## Inhoud van zelfstudie controleren

Als test, ga [&#x200B; deze pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/platform-learn/tutorial-comprehensive-technical/datadistiller/module51/ex4).

U zou nu moeten zien dat alle **Variabelen van het Milieu** door hun ware waarden zijn vervangen, die op het geactiveerde milieu in de chroomuitbreiding worden gebaseerd.

U zou nu een gelijkaardige mening aan hieronder moeten hebben, waar de omgevingsvariabele `aepTenantId` door uw echte identiteitskaart van de Huurder van Adobe Experience Platform is vervangen, die in dit geval **_experiencePlatform** is.

![&#x200B; DSN &#x200B;](./images/mod7.png)

Volgende Stap: [&#x200B; Systeem van de Demo van het Gebruik naast opstelling uw de cliëntbezit van de Inzameling van Gegevens van Adobe Experience Platform &#x200B;](./ex2.md)

[Terug naar Aan de slag](./getting-started.md)

[Terug naar alle modules](./../../../overview.md)
