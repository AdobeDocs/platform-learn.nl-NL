---
title: Een gegevenselement met variabele maken
description: Voeg een gegevenselement toe dat omhoog over veelvoudige regels zal worden opgebouwd en dan naar de Edge Network zal worden verzonden en aan Adobe Analytics zal door:sturen
solution: Data Collection, Analytics
feature: Web SDK
jira: KT-16759
source-git-commit: 7ae56d997884cf1558e72c0ad553df1c5d43c081
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---


# Een gegevenselement met variabele maken

Voeg een gegevenselement toe dat over veelvoudige regels zal worden opgebouwd en dan naar de Edge Network wordt verzonden en aan Adobe Analytics door:sturen.

Met dit gegevenselement wordt het object &quot;Data&quot; gemaakt, dat wordt gebruikt om Adobe Analytics-variabelen (props, eVars, gebeurtenissen, enz.) terug door te geven naar Adobe Analytics en Adobe Target. Dus, net als bij het opbouwen van het &#39;s object&#39; in een AppMeasurement-implementatie in Analytics, maken we dit type: Variabel object dat toegankelijk en bijgewerkt moet worden via regels, en het kan worden gebruikt om props en eVars te vullen met Analytics.

1. In de interface van de gegevensinzameling, klik {de Elementen van 0} Gegevens **in de linkernavigatie.**

   U zult aan de gegevenselementen landende pagina worden genomen waar u al uw reeds bestaande gegevenselementen zult zien. We moeten een nieuw gegevenselement maken om de migratie te vergemakkelijken. Klik **toevoegen het Element van Gegevens**.

   ![&#x200B; voeg gegevenselement &#x200B;](assets/add-new-data-alement.jpg) toe

1. Configureer uw gegevenselement.
   1. Geef uw gegevenselement een naam wat u wilt - iets dat u eraan zal helpen herinneren dat dit de gegevens op uw pagina bouwt, en dat dit het type &quot;Variabele&quot;zal zijn. Voor dit leerprogramma, zullen wij het **Variabele van de Gegevens van de Mening van de Pagina** roepen.
   1. Selecteer **SDK van het Web van Adobe Experience Platform** van de drop-down Uitbreiding.
   1. Selecteer **Variabele** van het **Type van Element van Gegevens** drop-down.
   1. In het rechtse paneel, selecteer het **radioknoop van Gegevens**.
   1. Controleer de **oplossing van Adobe Analytics** en één van beide andere oplossingen die u eveneens migreert, b.v. **Adobe Target** die in dit schermafbeelding toont.
1. Klik **sparen**.

   ![&#x200B; vorm veranderlijk gegevenselement &#x200B;](assets/configure-variable-data-element.jpg)
