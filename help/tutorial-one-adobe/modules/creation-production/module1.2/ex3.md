---
title: Procesautomatisering met Workfront Fusion
description: Meer informatie over het verwerken van automatisering met Workfront Fusion
role: Developer
level: Beginner
jira: KT-5342
doc-type: Tutorial
exl-id: 1b7b2630-864f-4982-be5d-c46b760739c3
source-git-commit: b083a817700320e8e45645702c2868423c1fae99
workflow-type: tm+mt
source-wordcount: '948'
ht-degree: 0%

---

# 1.2.3 Procesautomatisering met Workfront Fusion

Leer hoe u automatisering kunt verwerken met Workfront Fusion.

## 1.2.3.1 Iteratie over meerdere waarden

Uw scenario zou als dit moeten kijken:

![ WF Fusion ](./images/wffusion200.png)

Tot nu toe hebt u tekst in een Photoshop-bestand gewijzigd met een statische waarde. Als u uw workflows voor het maken van inhoud wilt schalen en automatiseren, moet u de lijst met waarden doorlopen en deze waarden dynamisch invoegen in het Photoshop-bestand. In de volgende stappen voegt u een herhaling toe over waarden in uw bestaande scenario.

1. In tussen de **knoop van de Router** en de **knoop van de Tekst van de Verandering van Photoshop**, selecteer het **moersleutelpictogram** en selecteer **voeg een module** toe.

   ![ WF Fusion ](./images/wffusion201.png)

1. Onderzoek naar `flow` en selecteer **de Controle van de Stroom**.

   ![ WF Fusion ](./images/wffusion202.png)

1. Selecteer **Teller**.

   ![ WF Fusion ](./images/wffusion203.png)

   Uw scherm moet er als volgt uitzien:

   ![ WF Fusion ](./images/wffusion204.png)

   Terwijl het mogelijk is om inputdossiers zoals Csv- dossiers te lezen, moet u momenteel een basisversie van een Csv- dossier gebruiken door een tekstkoord te bepalen en dat tekstdossier te verdelen.

1. U kunt de **gespleten** functie vinden door het **t** pictogram te selecteren, waar u alle beschikbare functies ziet om tekstwaarden te manipuleren. Selecteer de **gespleten** functie, dan zou u dit moeten zien.

   ![ WF Fusion ](./images/wffusion206.png)

1. De splitsfunctie verwacht een array van waarden voor de puntkomma en verwacht dat u het scheidingsteken na de puntkomma opgeeft. Voor deze test, zou u een eenvoudige serie met 2 gebieden moeten gebruiken, **kopen nu** en **klikt hier**, en de separator aan gebruik is **,**.

1. Ga dit op het **gebied van de Serie** door de momenteel lege **gespleten** functie te vervangen: `{{split("Buy now, Click here "; ",")}}`. Selecteer **O.K.**.

   ![ WF Fusion ](./images/wffusion205.png)



1. Selecteer **de Tekst van de Verandering van Photoshop** om in sommige variabelen in plaats van statische waarden voor de input en outputgebieden toe te voegen.

   ![ WF Fusion ](./images/wffusion207.png)

   In **inhoud van het Verzoek**, is de tekst **hier klikt**. Deze tekst moet worden vervangen door de waarden uit uw array.

   ![ WF Fusion ](./images/wffusion208.png)

1. Schrap de tekst **hier** klikt, en vervangt het door de veranderlijke **Waarde** van de **Iterator** knoop te selecteren. Zo weet u zeker dat de tekst op de knop in uw Photoshop-document dynamisch wordt bijgewerkt.

   ![ WF Fusion ](./images/wffusion209.png)

   U moet ook de bestandsnaam bijwerken waarmee het bestand in uw Azure Storage Account wordt geschreven. Als de bestandsnaam statisch is, wordt het vorige bestand door elke nieuwe versie overschreven en gaan de aangepaste bestanden verloren. Huidige statische filename is **burgerschap-vezel-veranderd-text.psd**, en u moet nu dat bijwerken.

1. Plaats de cursor achter het woord `text` .

   ![ WF Fusion ](./images/wffusion210.png)

1. Eerst, voeg een afbreekstreepje `-` toe en selecteer dan de waarde **Positie van de Volgorde van de Bundel**. Dit zorgt ervoor dat Workfront Fusion voor de eerste iteratie `-1` toevoegt aan de bestandsnaam, voor de tweede iteratie `-2` enzovoort. Selecteer **O.K.**.

   ![ WF Fusion ](./images/wffusion211.png)

1. Sparen uw scenario en selecteer dan **Looppas eens**.

   ![ WF Fusion ](./images/wffusion212.png)

   Als het scenario eenmaal is uitgevoerd, gaat u terug naar uw Azure Storage Explorer en vernieuwt u de map. De twee nieuwe bestanden worden dan weergegeven.

   ![ WF Fusion ](./images/wffusion213.png)

1. Download en open elk bestand. U dient verschillende teksten op de knoppen te plaatsen. Dit is bestand `citisignal-fiber-changed-text-1.psd` .

   ![ WF Fusion ](./images/wffusion214.png)

   Dit is bestand `citisignal-fiber-changed-text-2.psd` .

   ![ WF Fusion ](./images/wffusion215.png)

## 1.2.3.2 Activeer uw scenario met een webhaak

Tot dusver, hebt u uw scenario manueel in werking gesteld om te testen. Werk nu uw scenario bij met een webhaak, zodat het vanuit een externe omgeving kan worden geactiveerd.

1. Selecteer **+**, onderzoek naar **webhaak** en selecteer dan **Webhooks**.

   ![ WF Fusion ](./images/wffusion216.png)

1. Selecteer **Webhaak van de Douane**.

1. Sleep en verbind de **knoop van de Douane webhaak** zodat het met de eerste knoop op het canvas verbindt, die **wordt genoemd initialiseert Constanten**.

   ![ WF Fusion ](./images/wffusion217.png)

1. Selecteer de **knoop van de Webhaak van de Douane**. Dan, selecteer **toevoegen**.

   ![ WF Fusion ](./images/wffusion218.png)

1. Plaats **naam Webhaak** aan `--aepUserLdap-- - Tutorial 1.2`.

   ![ WF Fusion ](./images/wffusion219.png)

1. Controle de doos voor **krijgt verzoekkopballen**. Selecteer **sparen**.

   ![ WF Fusion ](./images/wffusion220.png)

1. De URL van uw webhaak is nu beschikbaar. De URL kopiëren.

   ![ WF Fusion ](./images/wffusion221.png)

1. Open Postman, en voeg een nieuwe omslag in de inzameling **toe FF - de Technologie Insiders van de Diensten van Firefly**.

   ![ WF Fusion ](./images/wffusion222.png)

1. Geef de map een naam `--aepUserLdap-- - Workfront Fusion` .

   ![ WF Fusion ](./images/wffusion223.png)

1. In de omslag die u enkel creeerde, selecteer de 3 punten **...** en selecteer **verzoek** toevoegen.

   ![ WF Fusion ](./images/wffusion224.png)

1. Plaats het **type van Methode** aan **POST** en kleef URL van uw webhaak in de adresbar.

   ![ WF Fusion ](./images/wffusion225.png)

   U moet een douanelichaam verzenden, zodat de veranderlijke elementen van een externe bron aan uw scenario van de Fusie van Workfront kunnen worden verstrekt.

1. Ga naar **Lichaam** en selecteer **onbewerkt**.

   ![ WF Fusion ](./images/wffusion226.png)

1. Plak de onderstaande tekst in de hoofdtekst van uw verzoek. Selecteer **verzenden**.

   ```json
   {
       "psdTemplate": "placeholder",
       "xlsFile": "placeholder"
   }
   ```

   ![ WF Fusion ](./images/wffusion229.png)

1. Terug in de Fusie van Workfront, verschijnt een bericht op uw douane webhaak die zegt: **met succes bepaalde**.

   ![ WF Fusion ](./images/wffusion227.png)

1. Selecteer **sparen** en selecteer dan **Looppas eens**. Uw scenario is nu actief maar zal niet lopen tot u **selecteert verzend** opnieuw in Postman.

   ![ WF Fusion ](./images/wffusion230.png)

1. In Postman selecteert **verzend** opnieuw.

   ![ WF Fusion ](./images/wffusion228.png)

   Uw scenario wordt opnieuw uitgevoerd en leidt tot de 2 dossiers enkel als voordien.

   ![ WF Fusion ](./images/wffusion232.png)

1. Wijzig de naam van uw Postman-aanvraag in `POST - Send Request to Workfront Fusion Webhook` .

   ![ WF Fusion ](./images/wffusion233.png)

   Nu moet u beginnen veranderlijk **psdTemplate** te gebruiken. In plaats van hardcoding de plaats van het inputdossier in de **knoop van de Tekst van de Verandering van Photoshop**, zult u de inkomende variabele van het verzoek van Postman gebruiken.

1. Open de **knoop van de Tekst van de Verandering van Photoshop** en ga naar **inhoud van het Verzoek**. Selecteer hardcoded filename **burgerschap-fiber.psd** onder **input** en schrap het.

   ![ WF Fusion ](./images/wffusion234.png)

1. Selecteer veranderlijk **psdTemplate**. Selecteer **O.K.** en bewaar dan uw scenario.

   ![ WF Fusion ](./images/wffusion235.png)

1. Selecteer **AAN** om uw scenario aan te zetten. Uw scenario loopt nu zonder onderbreking.

   ![ WF Fusion ](./images/wffusion236.png)

1. Terug in Postman, ga filename `citisignal-fiber.psd` als waarde voor veranderlijke **psdTemplate** in en selecteer **verzend** opnieuw om uw scenario opnieuw in werking te stellen.

   ![ WF Fusion ](./images/wffusion237.png)

   Door het malplaatje van PSD als variabele te specificeren die door een extern systeem wordt verstrekt, hebt u nu een herbruikbaar scenario gebouwd.

   Nu hebt u deze oefening afgerond.

## Volgende stappen

Ga naar [ Samenvatting en Voordelen van de Automatisering van de Diensten van Firefly ](./summary.md){target="_blank"}

Ga terug naar [ het Automatiseren de Diensten van Adobe Firefly ](./automation.md){target="_blank"}

Ga terug naar [ Alle Modules ](./../../../overview.md){target="_blank"}
