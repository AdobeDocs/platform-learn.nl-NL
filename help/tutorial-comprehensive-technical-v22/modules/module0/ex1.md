---
title: Aan de slag - Installeer de Chrome-extensie voor de documentatie van het Experience League
description: Aan de slag - Installeer de Chrome-extensie voor de documentatie van het Experience League
kt: 5342
audience: Data Engineer, Data Architect
doc-type: tutorial
activity: develop
exl-id: 6e0a88e7-65e3-4251-8ab1-e030a397a56b
source-git-commit: cc7a77c4dd380ae1bc23dc75608e8e2224dfe78c
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---

# 0.1 De Chrome-extensie installeren voor de documentatie van het Experience League

## 0.1.1 Waarom hebben we een Chrome-extensie gemaakt?

De documentatie is generiek gemaakt zodat het gemakkelijk door iedereen kan worden hergebruikt, gebruikend om het even welke instantie van Adobe Experience Platform.
Door de documentatie opnieuw bruikbaar te maken, **Omgevingsvariabelen** zijn in de documentatie geïntroduceerd, wat betekent dat u de onderstaande informatie ziet **toetsen** in de documentatie. Elke sleutel is een specifieke variabele voor een specifiek milieu, en de uitbreiding van het Chroom zal die variabele voor u veranderen en als dusdanig zal het voor u gemakkelijk maken om code en tekst van de zelfstudiepagina&#39;s te kopiëren en het te kleven in de diverse Gebruikersinterfaces die u als deel van het leerprogramma zult gebruiken.

Hieronder vindt u een voorbeeld van dergelijke waarden. Deze waarden kunnen momenteel nog niet worden gebruikt, maar zodra u de Chrome-extensie installeert en activeert, worden deze variabelen gewijzigd in &#39;normale&#39; tekst die u kunt kopiëren en opnieuw kunt gebruiken.

| Naam | Sleutel |
|:-------------:| :---------------:|
| AEP IMS Org ID | `--aepImsOrgId--` |
| AEP-huurnummer | `--aepTenantId--` |
| DCS-inlaat-id | `--dcsInletId--` |
| LDAP demoiliteitsprofiel | `--demoProfileLdap--` |

In de onderstaande schermafbeelding ziet u bijvoorbeeld een verwijzing naar `--aepTenantId--`.

![DSN](./images/mod7before.png)

Nadat de extensie is geïnstalleerd, wordt dezelfde tekst automatisch gewijzigd om de instantiespecifieke waarden weer te geven.

![DSN](./images/mod7.png)

Met deze uitbreiding kunt u ook:

- Aanmelden voor zelfstudie
- Volg de voortgang door de voltooiing van elke module voor te leggen, zoals aangegeven in [Hoe wordt Voltooiing gemeten?](../../completion.md)

## 0.1.2 De Chrome-extensie installeren

Als u die Chrome-extensie wilt installeren, opent u de Chrome-browser en gaat u naar: [https://chrome.google.com/webstore/detail/platform-learn-configurat/hhnbkfgioecmhimdhooigajdajplinfi/related?hl=en&amp;authuser=0](https://chrome.google.com/webstore/detail/platform-learn-configurat/hhnbkfgioecmhimdhooigajdajplinfi/related?hl=en&amp;authuser=0). Dan zie je dit.

Klikken **Toevoegen aan chroom**.

![DSN](./images/c2.png)

Dan zie je dit. Klikken **Extensie toevoegen**.

![DSN](./images/c3.png)

De extensie wordt dan geïnstalleerd en u ziet een vergelijkbare melding.

![DSN](./images/c4.png)

In de **extensions** klikt u op de knop **puzzelstuk** pictogram en speld het **Platform leren - Configuratie** aan het extensiemenu.

![DSN](./images/c6.png)

## 0.1.2 De Chrome-extensie configureren

Ga naar [https://experienceleague.adobe.com/docs/platform-learn/comprehensive-technical-tutorial-v22/overview.html?lang=en](https://experienceleague.adobe.com/docs/platform-learn/comprehensive-technical-tutorial-v22/overview.html?lang=en) en klik vervolgens op het extensiepictogram om het te openen.

![DSN](./images/tuthome.png)

Dan zie je deze popup. Klik op de knop **+** pictogram.

![DSN](./images/c7.png)

Voer uw naam en configuratie-id in die voor uw Adobe Experience Platform-omgeving zijn gemaakt. Klikken **Nieuw maken**.

>[!IMPORTANT]
>
>Als je Adobe werknemer bent: u vindt de configuratie-id die u wilt gebruiken in de interne Github-repo (https://git.corp.adobe.com/vangeluw/platformenablement).
>
>Als u een Partner van de Oplossing van Adobe bent, gelieve uw contact van de Partner van de Oplossing of e-mail te contacteren **spphelp@adobe.com**.

![DSN](./images/c8.png)

In het linkermenu van de extensie ziet u nu een pictogram met uw initialen. Klik erop. U zult dan de afbeelding tussen zien **Omgevingsvariabelen** en uw specifieke Adobe Experience Platform-instantiewaarden. Klikken **Configuratie activeren**.

![DSN](./images/c9.png)

Nadat u de configuratie hebt geactiveerd, ziet u een groene stip naast uw initialen. Dit betekent dat uw identiteitskaart van de Configuratie nu actief is. Er wordt ook een aantal aanvullende menuopties weergegeven.

![DSN](./images/c10.png)

U hebt nu twee opties:

- Als u een bestaande gebruiker van enablement met een bestaande opstelling bent, ga naar **0.1.3 Bestaande gebruiker - Aanmelden**
- Als u een volledig nieuwe gebruiker bent die deze zelfstudie voor het eerst start, gaat u naar **0.1.4 Aantekening** en overslaan **0.1.3 Bestaande gebruiker - Aanmelden**

## 0.1.3 Bestaande gebruiker - Aanmelden

>[!IMPORTANT]
>
>Uitoefening **0.1.3 Bestaande gebruiker - Aanmelden** werkt alleen als u een bestaande gebruiker bent die zich eerder heeft aangemeld voor deze zelfstudie.

Als u een bestaande gebruiker bent die deze Chrome-extensie voor het eerst instelt, klikt u op het paarse pictogram in het linkermenu. Dan zie je dit.

![DSN](./images/chromeret1.png)

Vul de waarden naar wens in.

>[!IMPORTANT]
>
>De **LDAP** is het belangrijkste gebied : u moet dezelfde LDAP gebruiken als u hebt gebruikt toen u zich voor het eerst aanmeldt voor de zelfstudie. Zo wordt de voortgang geladen. Kijk naar je e-mailadres als je niet zeker weet wat je LDAP is. Gebruik de tekst vóór het @-symbool in uw e-mailadres als LDAP. Als uw e-mailadres **vangeluw@adobe.com** moet de LDAP die u hier invoert **vangeluw**).

![DSN](./images/chromeret2.png)

Klikken **OK**.

![DSN](./images/chromeret3.png)

Na 30sec-1 minuut, zal uw scherm veranderen en u zult terug naar **Home**, waar je dit ziet:

![DSN](./images/chromeret4.png)

Uw Chrome-extensie is nu geconfigureerd en u kunt nu controleren of alles goed werkt.

## 0.1.4 Nieuwe gebruiker - Aanmelden

>[!IMPORTANT]
>
>Uitoefening **0.1.4 Nieuwe gebruiker - Aanmelden** is bedoeld voor nieuwe gebruikers die deze zelfstudie voor het eerst starten.

Als u een nieuwe gebruiker bent die zich de eerste keer aanmeldt voor deze zelfstudie, klikt u op het gele pictogram in het menu. Dan zie je dit.

![DSN](./images/c11.png)

Vul de velden naar wens in. Klikken **Opslaan**.

>[!IMPORTANT]
>
>De **LDAP** is het belangrijkste terrein. Kijk naar je e-mailadres als je niet zeker weet wat je LDAP is. Gebruik de tekst vóór het @-symbool in uw e-mailadres als LDAP. Als uw e-mailadres **vangeluw@adobe.com** moet de LDAP die u hier invoert **vangeluw**).

![DSN](./images/chrome1.png)

Na 30sec-1 minuut, zal uw scherm veranderen en u zult terug naar **Home**, waar je dit ziet:

![DSN](./images/chrome2.png)

Uw Chrome-extensie is nu geconfigureerd en u kunt nu controleren of alles goed werkt.

## 0.1.5 Lesbestanden controleren

Ga als test naar [deze pagina](https://experienceleague.adobe.com/docs/platform-learn/comprehensive-technical-tutorial-v22/module4/ex3.html?lang=en).

U moet nu zien dat alles **Omgevingsvariabelen** zijn vervangen door hun ware waarden, die op identiteitskaart van de Configuratie in de chroomuitbreiding worden gebaseerd.

U zou nu een gelijkaardige mening moeten hebben zoals hieronder, waar de milieuvariabelen `--aepTenantId--` is vervangen door uw echte huurder-id, die in dit geval **_ervaringsplatform**.

![DSN](./images/c12.png)

Volgende stap: [0.2 Het Systeem van de Demo van het Gebruik naast opstelling uw de cliëntbezit van de Inzameling van Gegevens van Adobe Experience Platform](./ex2.md)

[Ga terug naar module 0](./getting-started.md)

[Terug naar alle modules](./../../overview.md)
