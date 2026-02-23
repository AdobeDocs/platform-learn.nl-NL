---
title: Uw eerste formulier maken
description: Uw eerste formulier maken
kt: 5342
doc-type: tutorial
source-git-commit: 8f59b9fdadc9c5aeadb1d4ecccd75090c339b43e
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 9%

---

# 1.3.1 Het eerste formulier maken

>[!IMPORTANT]
>
>U hebt toegang nodig tot een werkende AEM Assets CS Author-omgeving met AEM Assets Dynamic Media ingeschakeld om deze oefening te kunnen voltooien.
>
>Als u zulk een milieu niet hebt, ga naar [&#x200B; Adobe Experience Manager Cloud Service &amp; Edge Delivery Services &#x200B;](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"}. Volg de instructies daar, en u zult toegang tot zulk een milieu hebben.

>[!IMPORTANT]
>
>Als u eerder een AEM CS-programma hebt geconfigureerd met een AEM Assets CS-omgeving, kan het zijn dat de AEM CS-sandbox is geminimaliseerd. Gezien het feit dat het vernietigen van zo&#39;n zandbak 10 tot 15 minuten duurt, zou het een goed idee zijn om het ontruimingsproces nu te beginnen zodat u niet op een later tijdstip hoeft te wachten.

## 1.3.1.1 -

Ga naar [&#x200B; https://my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com){target="_blank"}. De org die u moet selecteren is `--aepImsOrgName--`. Open uw omgeving.

![AEM Forms](./images/aemforms1.png)

Ga naar **Forms**.

![AEM Forms](./images/aemforms2.png)

Ga naar **Forms &amp; Documenten**.

![AEM Forms](./images/aemforms3.png)

Klik **creëren** en selecteer dan **AanpassingsVorm**.

![AEM Forms](./images/aemforms4.png)

Selecteer **Edge Delivery Services** en selecteer dan **Lege Pagina**. Klik **creëren**.

![AEM Forms](./images/aemforms5.png)

Dan moet je dit zien. Vul de volgende velden in:

- **Titel**: `Fiber Max Interest Form`
- **Naam**: zou automatisch moeten worden bevolkt gebaseerd op het gebied **Titel**.
- **Github URL**: verstrek de weg aan de repo van Github die met uw website wordt verbonden

Klik **creëren**.

![AEM Forms](./images/aemforms6.png)

Na het klikken **creeer**, zou de **Universele Redacteur** automatisch moeten openen en u zou iets als dit moeten zien. Klik het pictogram om de **Boom van de Inhoud** te openen.

![AEM Forms](./images/aemforms7.png)

In de **Boom van de Inhoud**, selecteer de objecten **Aangepaste Vorm**.

![AEM Forms](./images/aemforms8.png)

Dan, klik het **+** pictogram om een nieuw element toe te voegen, en **tekstinput** te selecteren.

![AEM Forms](./images/aemforms9.png)

In de **Boom van de Inhoud**, selecteer de input van de gebied **Tekst**.

![AEM Forms](./images/aemforms10.png)

Ga naar de **Basis** mening. Je moet dit zien.

Vul de volgende velden in:

- **Naam**: `first-name`
- **Titel**: `First Name`

Dan, ga naar **Bevestiging**.

![AEM Forms](./images/aemforms11.png)

Draai de schakelaar om van dit een vereist gebied te maken. Vul de volgende velden in:

- **het bericht van de Fout**: `Enter your first name`
- **Patroon**: `[A-Za-z][A-Za-z ]+`
- **de foutenmelding van het Patroon**: `Letters only!`

![AEM Forms](./images/aemforms12.png)

In de **Boom van de Inhoud**, selecteer het gebied **Aangepaste Vorm**. Klik **+** pictogram en selecteer dan **tekstinput**.

![AEM Forms](./images/aemforms13.png)

In de **Boom van de Inhoud**, selecteer de pas gecreëerde gebied **Invoer van de Tekst**. Ga naar **Eigenschappen**.

![AEM Forms](./images/aemforms14.png)

Ga naar de **Basis** mening. Je moet dit zien.

Vul de volgende velden in:

- **Naam**: `last-name`
- **Titel**: `Last Name`

Dan, ga naar **Bevestiging**.

![AEM Forms](./images/aemforms15.png)

Draai de schakelaar om van dit een vereist gebied te maken. Vul de volgende velden in:

- **het bericht van de Fout**: `Enter your last name`
- **Patroon**: `[A-Za-z][A-Za-z ]+`
- **de foutenmelding van het Patroon**: `Letters only!`

![AEM Forms](./images/aemforms16.png)

In de **Boom van de Inhoud**, selecteer het gebied **Aangepaste Vorm**. Klik **+** pictogram en selecteer dan **tekstinput**.

![AEM Forms](./images/aemforms17.png)

In de **Boom van de Inhoud**, selecteer de pas gecreëerde gebied **Invoer van de Tekst**. Ga naar **Eigenschappen**.

![AEM Forms](./images/aemforms18.png)

Ga naar de **Basis** mening. Je moet dit zien.

Vul de volgende velden in:

- **Naam**: `email`
- **Titel**: `Email`

Dan, ga naar **Bevestiging**.

![AEM Forms](./images/aemforms19.png)

Draai de schakelaar om van dit een vereist gebied te maken. Vul de volgende velden in:

- **het bericht van de Fout**: `Enter your email address`
- **Patroon**: `^[^@]+@[^@]+\.[^@]+$`
- **de foutenmelding van het Patroon**: `Please verify your email address!`

![AEM Forms](./images/aemforms20.png)

In de **Boom van de Inhoud**, selecteer het gebied **Aangepaste Vorm**. Klik **+** pictogram en selecteer dan **tekstinput**.

![AEM Forms](./images/aemforms21.png)

In de **Boom van de Inhoud**, selecteer de pas gecreëerde gebied **Invoer van de Tekst**.

![AEM Forms](./images/aemforms22.png)

Ga naar de **Basis** mening. Je moet dit zien.

Vul de volgende velden in:

- **Naam**: `city`
- **Titel**: `city`

Dan, ga naar **Bevestiging**.

![AEM Forms](./images/aemforms23.png)

Draai de schakelaar om van dit een vereist gebied te maken. Vul de volgende velden in:

- **het bericht van de Fout**: `Enter your city`
- **Patroon**: `[A-Za-z][A-Za-z ]+`
- **de foutenmelding van het Patroon**: `Letters only!`

![AEM Forms](./images/aemforms24.png)

Klik **publiceren**.

![AEM Forms](./images/aemforms25.png)

Klik **publiceren** opnieuw.

![AEM Forms](./images/aemforms26.png)

Klik om het formulier te openen.

![AEM Forms](./images/aemforms27.png)

U kunt het formulier vervolgens invullen, maar u kunt het nog niet verzenden.

![AEM Forms](./images/aemforms28.png)

## Volgende stappen

Volgende stap: [&#x200B; -](./ex1.md){target="_blank"}

Ga terug naar [&#x200B; Adobe Experience Manager Forms met Edge Delivery Services &#x200B;](./aemforms.md){target="_blank"}

[&#x200B; ga terug naar Alle Modules &#x200B;](./../../../overview.md){target="_blank"}
