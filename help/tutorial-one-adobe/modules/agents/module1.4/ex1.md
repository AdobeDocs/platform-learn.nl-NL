---
title: Aan de slag met Brand Concierge
description: Aan de slag met Brand Concierge
kt: 5342
doc-type: tutorial
source-git-commit: 6642acb3fdce2c9d3a9b919d5c9457191e4780a6
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# 1.4.1 Aan de slag met Brand Concierge

## Video

In deze video krijgt u een uitleg en demonstratie van alle stappen die bij deze oefening betrokken zijn.

## 1.4.1.1 Overzicht van Brand Concierge

Tijdens het configureren van Brand Concierge zijn de twee belangrijkste elementen die u gebruikt:

- **Composer van de Agent (de Laag van de Configuratie)**

  Doel: Het primaire UI-platform dat wordt gebruikt om conversationele AI-ervaringen te maken en configureren.

  Belangrijkste verantwoordelijkheden:

   - Gegevensbronnen en kennisbanken definiëren en beheren
   - De uitdrukking van het merk instellen (toon, stijl, instructies)
   - De agent voor het boeken van vergaderingen instellen

- **Agent Orchestrator (de Motor van de Uitvoering)**

  Doel: De redenering- en orkestprogramma die gebruikersverzoeken interpreteert en de juiste handelingen van de agent uitvoert.

  Belangrijkste verantwoordelijkheden:

   - Intenten van gebruikers van natuurlijke talen interpreteren
   - Meerstappenplannen genereren en uitvoeren
   - De juiste operatoren/gereedschappen selecteren en aanroepen
   - De context, de naleving en de begeleiding van merken afdwingen
   - Workflows met meerdere agents coördineren
   - Reacties van meerdere gegevensbronnen samenvoegen en samenstellen

- **Runtime van de Conversie van Brand Concierge (de Laag van de Dienst)**

  Doel: De klantgerichte gespreksservicelaag die chatsessies, context en interactie met de client beheert.

  Belangrijkste componenten:

   - Webagent (client): browserinterface of gebruikersinterface voor mobiel chatten die is geïntegreerd met de Web SDK
   - De Dienst van de dialoog (Achtergrond): Beheert zittingsstaat en doet dienst als gateway van het Orchestration

  Belangrijkste verantwoordelijkheden:

   - Gebruikerssessies en gesprekstranscripties beheren
   - Gebruikersverificatie en -profielen verwerken
   - De berichten van de route tussen de cliënt en Agent Orchestrator
   - De context van het voortdurende gesprek
   - Gedrag- en operationele gebeurtenissen voor AEP vastleggen voor analyse
   - oppervlaktespecifieke configuraties toepassen

## 1.4.1.2 Brand Concierge-instantieconfiguratie

Volg de onderstaande stappen om uw eigen Brand Concierge-exemplaar te maken.

Ga naar [&#x200B; https://experience.adobe.com/ &#x200B;](https://experience.adobe.com/){target="_blank"}. Open **Brand Concierge**.

![&#x200B; Brand Concierge &#x200B;](./images/bc1.png)

Dan moet je dit zien. Klik het **zandbakselectie** menu.

![&#x200B; Brand Concierge &#x200B;](./images/bc2.png)

Kies de sandbox die aan u is toegewezen. Die sandbox moet de naam `--aepUserLdap--` hebben.

![&#x200B; Brand Concierge &#x200B;](./images/bc3.png)

Klik **krijgen Begonnen**.

![&#x200B; Brand Concierge &#x200B;](./images/bc4.png)

Gebruik voor de naam van uw Brand Concierge-instantie: `--aepUserLdap-- - CitiSignal Brand Concierge` .

Ga de volgende tekst onder **in wat u de conciërge zou willen doen?**.

```javascript
Brand Concierge should help customers find their best device, plan or entertainment deal. Brand Concierge should help users discover internet plans, entertainment deals,  and help find the best available packages. Brand Concierge should also answer questions about devices such as phones and watches.
```

Klik **creëren**.

![&#x200B; Brand Concierge &#x200B;](./images/bc5.png)

Dan moet je dit zien. Klik **krijgen Begonnen** om een kennisbron toe te voegen.

![&#x200B; Brand Concierge &#x200B;](./images/bc6.png)

Selecteer **de Verbindingen van de Website** en klik **verdergaan**.

![&#x200B; Brand Concierge &#x200B;](./images/bc7.png)

Dan moet je dit zien. Voer `CitiSignal website` in als naam voor uw kennisbron.

U moet nu een CSV-bestand uploaden dat de koppelingen van uw website bevat. De download [&#x200B; CitiSignal websiteverbindingen CSV- dossier &#x200B;](./assets/citisignal-website-links.csv) aan uw Desktop.

Klik **doorbladeren Dossiers**.

![&#x200B; Brand Concierge &#x200B;](./images/bc8.png)

Open het dossier **burgersignaal-website-links.csv** en werk de verbindingen bij om aan uw eigen website te richten CitiSignal.

![&#x200B; Brand Concierge &#x200B;](./images/bc8a.png)

Selecteer het dossier **burgersignaal-website-links.csv** dat u enkel en alleen downloadde en uitgeeft. Klik **Open**.

![&#x200B; Brand Concierge &#x200B;](./images/bc9.png)

Uw bestand wordt nu toegevoegd aan deze kennisbron. Klik **toevoegen**.

![&#x200B; Brand Concierge &#x200B;](./images/bc10.png)

Dan moet je dit zien. Klik **neem me** mee naar huis.

![&#x200B; Brand Concierge &#x200B;](./images/bc11.png)

Dan moet je dit zien. Klik **krijgen Begonnen** op het **advies van het Product voor consumenten** kaart.

![&#x200B; Brand Concierge &#x200B;](./images/bc12.png)



```
CitiSignal is a telecommunications company that sells devices such as phones and watches and that sells internet services such as their lead product CitiSignal Fiber Max. On top of that, CitiSignal sells entertainment services that offer premium streaming services at a discounted price. CitiSignal is targeting these 3 personas primarily: Smart Home Families, Online Gamers and Remote Professionals.
```

```
Prioritize positioning the CitiSignal Fiber Max offering.
```

```
Competitor pricing, competitor products
```

Uw updates worden automatisch opgeslagen. Klik de **pijl** om terug naar het vorige scherm te gaan.

![&#x200B; Brand Concierge &#x200B;](./images/bc13.png)

Dan moet je dit zien. Klik **krijgen Begonnen** om uw merkuitdrukking aan te passen.

![&#x200B; Brand Concierge &#x200B;](./images/bc14.png)

U kunt uw eigen keuzen op de **Uitdrukking van het Merk** pagina maken.

![&#x200B; Brand Concierge &#x200B;](./images/bc15.png)

De rol neer en selecteert om het even welk plaatsen voor de lengte van de gebied **Reactie**.

Uw updates worden automatisch opgeslagen.

![&#x200B; Brand Concierge &#x200B;](./images/bc16.png)

De rol omhoog en klikt de **pijl** om terug naar het vorige scherm te gaan.

![&#x200B; Brand Concierge &#x200B;](./images/bc17.png)


Ga terug naar [&#x200B; Brand Concierge &#x200B;](./brandconcierge.md){target="_blank"}

[&#x200B; ga terug naar Alle Modules &#x200B;](./../../../overview.md){target="_blank"}