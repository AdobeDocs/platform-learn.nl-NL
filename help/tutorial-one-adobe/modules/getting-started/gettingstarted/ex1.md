---
title: Aan de slag - Installeer de Chrome-extensie voor de Experience League-documentatie
description: Aan de slag - Installeer de Chrome-extensie voor de Experience League-documentatie
kt: 5342
doc-type: tutorial
exl-id: 3618dacb-2203-4d19-ae51-f78415a693fd
source-git-commit: cc8efbdbcf90607f5a9bc98a2e787b61b4cd66d9
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 0%

---

# De Chrome-extensie installeren voor de Experience League-documentatie

## Over de Chrome-extensie

Deze zelfstudie is algemeen gemaakt, zodat deze eenvoudig door iedereen kan worden hergebruikt, met elke Adobe Experience Cloud-instantie.

Om de documentatie herbruikbaar te maken, **werden de Variabelen van het Milieu** geïntroduceerd in het leerprogramma, zo betekent het dat u hieronder **placeholders** in de documentatie zult vinden. Elke placeholder is een specifieke variabele voor een specifiek milieu, en de uitbreiding van Chrome zal die variabele voor u veranderen om het voor u gemakkelijk te maken om code en tekst van de leerzame pagina&#39;s te kopiëren en het te kleven in de diverse gebruikersinterfaces die u als deel van het leerprogramma zult gebruiken.

Hieronder vindt u een voorbeeld van dergelijke waarden. Deze waarden kunnen momenteel nog niet worden gebruikt, maar zodra u de Chrome-extensie installeert en activeert, worden deze variabelen gewijzigd in normale tekst die u kunt kopiëren en opnieuw kunt gebruiken.

| Naam | Sleutel | Voorbeeld |
|:-------------:| :---------------:| :---------------:|
| IMS Org ID | `--aepImsOrgId--` | `907075E95BF479EC0A495C73@AdobeOrg` |
| IMS-naam | `--aepImsOrgName--` | `Experience Platform International` |
| AEP Tenant ID | `--aepTenantId--` | `_experienceplatform` |
| Naam AEP-sandbox | `--aepSandboxName--` | `one-adobe` |
| Leerlingprofiel LDAP | `--aepUserLdap--` | `vangeluw` |

In de onderstaande schermafbeelding ziet u bijvoorbeeld een verwijzing naar `aepSandboxName` .

![ DSN ](./images/mod7before.png)

Nadat de extensie is geïnstalleerd, wordt dezelfde tekst automatisch gewijzigd om de instantiespecifieke waarden weer te geven.

![ DSN ](./images/mod7.png)

## De Chrome-extensie installeren

Om die uitbreiding van Chrome te installeren, open uw browser van Chrome en ga naar: [ https://chromewebstore.google.com/detail/tech-insiders-learning-fo/hhnbkfgioecmhimdhooigajdajplinfi ](https://chromewebstore.google.com/detail/tech-insiders-learning-fo/hhnbkfgioecmhimdhooigajdajplinfi){target="_blank"}. Dan zie je dit.

Klik **toevoegen aan Chrome**.

![ DSN ](./images/c2.png)

Dan zie je dit. Klik **toevoegen uitbreiding**.

![ DSN ](./images/c3.png)

De extensie wordt dan geïnstalleerd en u ziet een vergelijkbare melding.

![ DSN ](./images/c4.png)

In het **menu van uitbreidingen**, klik het **puzzelstuk** pictogram en speld het **Platform Leren - de uitbreiding van de Configuratie** aan het uitbreidingsmenu.

![ DSN ](./images/c6.png)

## De Chrome-extensie configureren

Ga naar [ https://experienceleague.adobe.com/nl/docs/platform-learn/tutorial-comprehensive-technical/overview ](https://experienceleague.adobe.com/nl/docs/platform-learn/tutorial-comprehensive-technical/overview){target="_blank"} en klik dan het uitbreidingspictogram om het te openen.

![ DSN ](./images/tuthome.png)

Dan zie je deze popup. Klik op het pictogram **+** .

![ DSN ](./images/c7.png)

Voer de waarden in zoals hieronder aangegeven. Deze zijn allemaal gerelateerd aan uw Adobe Experience Platform-exemplaar.

![ DSN ](./images/c8.png)

Als u niet zeker weet welke waarden u voor deze velden moet invoeren, volgt u de onderstaande aanwijzingen.

**AEP IMS Org Name**

Wanneer u login aan uw instantie van Adobe Experience Platform op [ https://platform.adobe.com/ ](https://platform.adobe.com/){target="_blank"}, zult u de naam van uw instantie in de hoogste juiste hoek van uw scherm vinden.

![ DSN ](./images/aepname.png)

**AEP IMS Org ID**

De IMS-organisatie-id is de unieke id voor uw Adobe Experience Cloud-instantie en er wordt in deze zelfstudie naar verwezen op meerdere locaties.

U kunt uw IMS-organisatie-id op meerdere manieren zoeken. Als u niet zeker bent, controleer met één van de systeembeheerders van uw instantie om identiteitskaart te vinden.

U kunt het vinden door [ Admin Console ](https://adminconsole.adobe.com/){target="_blank"} te gaan, waar u het als deel van URL kunt vinden.

![ DSN ](./images/aepid1.png)

U kunt het ook vinden door **het Beheer van Gegevens > Vragen** in uw menu van AEP te gaan, waar u het onder **Gebruikersnaam** kunt vinden.

![ DSN ](./images/aepid2.png)

Kopieer en plak het **@AdobeOrg** -onderdeel samen met de id.

**identiteitskaart van de HTENT van AEP**

Uw Tenant-id is de unieke id voor het AEP-exemplaar van uw organisatie. Wanneer u login aan uw instantie van Adobe Experience Platform op [ https://platform.adobe.com/ ](https://platform.adobe.com/){target="_blank"}, zult u huurder identiteitskaart in URL vinden.

![ DSN ](./images/aeptenantid.png)

Wanneer u het in de uitbreiding van Chrome ingaat, zou u moeten ervoor zorgen dat een onderstrepingsteken als prefix wordt toegevoegd, zodat in dit voorbeeld **ervaringsplatform** **_experiencePlatform** wordt.

**Naam van zandbak van AEP**

De naam van de sandbox is de naam van de omgeving die u in uw AEP-instantie gebruikt. Wanneer u login aan uw instantie van Adobe Experience Platform op [ https://platform.adobe.com/ ](https://platform.adobe.com/){target="_blank"}, zult u huurder identiteitskaart in URL vinden.

Voordat u de naam van de sandbox opgeeft van de URL, moet u ervoor zorgen dat u zich in de sandbox bevindt die u voor deze zelfstudie moet gebruiken. U kunt naar de rechtersandbox schakelen door op het menu met sandboxswitches in de rechterbovenhoek van het scherm te klikken.

![ DSN ](./images/aepsandboxsw.png)

In dit voorbeeld, is de Naam van de zandbak van AEP **one-adobe**.

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

## Inhoud van zelfstudie controleren

Als test, ga [ deze pagina ](https://experienceleague.adobe.com/nl/docs/platform-learn/tutorial-one-adobe/activation/dc/dc13/ex2){target="_blank"}.

U zou nu moeten zien dat alle **Variabelen van het Milieu** op deze pagina door hun ware waarden zijn vervangen, die op het geactiveerde milieu in de chroomuitbreiding worden gebaseerd.

U zou nu een gelijkaardige mening aan hieronder moeten hebben, waar de milieuvariabele `aepSandboxName` door uw echte Naam van de Sandbox van AEP is vervangen, die in dit geval **one-adobe** is.

![ DSN ](./images/mod7.png)

## Volgende stappen

Ga naar [ Systeem van de Demo van het Gebruik naast opstelling uw de cliëntbezit van de Inzameling van Gegevens van Adobe Experience Platform ](./ex2.md){target="_blank"}

Ga terug naar [ Begonnen het worden ](./getting-started.md){target="_blank"}

Ga terug naar [ Alle modules ](./../../../overview.md){target="_blank"}
