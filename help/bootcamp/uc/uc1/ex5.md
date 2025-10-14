---
title: Bootkamp - Real-time CDP - Bouw een publiek op en neem actie - verzend uw publiek naar DV360
description: Bootkamp - Real-time CDP - Bouw een publiek en neem actie - verzend uw publiek naar DV360
jira: KT-5342
audience: Data Architect, Orchestration Engineer, Marketer
doc-type: tutorial
activity: develop
feature: Destinations
exl-id: 31f46e37-f1c0-4730-8520-1ccd98df6501
source-git-commit: 5876de5015e4c8c337c235c24cc28b0a32e274dd
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 0%

---

# 1.5 Actie nemen: stuur je publiek naar Facebook

Ga naar [&#x200B; Adobe Experience Platform &#x200B;](https://experience.adobe.com/platform). Na het aanmelden landt je op de homepage van Adobe Experience Platform.

![&#x200B; Ingestie van Gegevens &#x200B;](./images/home.png)

Alvorens u verdergaat, moet u a **zandbak** selecteren. De te selecteren sandbox krijgt de naam ``Bootcamp`` . U kunt dit doen door op de tekst **[!UICONTROL Production Prod]** in de blauwe lijn boven op het scherm te klikken. Nadat u de juiste [!UICONTROL sandbox] hebt geselecteerd, ziet u de schermwijziging en nu bevindt u zich in uw toegewezen [!UICONTROL sandbox] .

![&#x200B; Ingestie van Gegevens &#x200B;](./images/sb1.png)

In het linkermenu, ga naar **Doelen**, dan gaan naar **Catalogus**. U zult dan de **Catalogus van Doelen** zien. In **Doelen**, klik **activeren publiek** op de **kaart van het publiek van de Douane van Facebook**.

![&#x200B; RTCDP &#x200B;](./images/rtcdpgoogleseg.png)

Selecteer de bestemming **bootkamp-facebook** en klik **daarna**.

![&#x200B; RTCDP &#x200B;](./images/rtcdpcreatedest2.png)

Selecteer in de lijst met beschikbare doelgroepen het publiek dat u in de vorige oefening hebt gemaakt. Klik **daarna**.

![&#x200B; RTCDP &#x200B;](./images/rtcdpcreatedest3.png)

Op de **Afbeelding** pagina, zorg ervoor dat **checkbox van de Transformatie** toepast wordt toegelaten. Klik **daarna**.

![&#x200B; RTCDP &#x200B;](./images/rtcdpcreatedest4a.png)

Op de **pagina van het Programma van de Auditie**, selecteer de **Oorsprong van uw publiek** en plaats het aan **direct van klanten**. Klik **daarna**.

![&#x200B; RTCDP &#x200B;](./images/rtcdpcreatedest4.png)

Tot slot op de **pagina van het Overzicht**, klik **Afwerking**.

![&#x200B; RTCDP &#x200B;](./images/rtcdpcreatedest5.png)

Uw publiek is nu gekoppeld aan het aangepaste publiek van Facebook. Telkens wanneer een klant voor dit publiek in aanmerking komt, wordt een signaal verzonden naar de Facebook-server om die klant op te nemen in het aangepaste publiek aan Facebook-zijde.

In Facebook vindt u uw publiek in Adobe Experience Platform onder Aangepast publiek:

![&#x200B; RTCDP &#x200B;](./images/rtcdpcreatedest5b.png)

Je kunt nu een aangepast publiek weergeven in Facebook:

![&#x200B; RTCDP &#x200B;](./images/rtcdpcreatedest5a.png)

[Ga terug naar gebruikersstroom 1](./uc1.md)

[Terug naar alle modules](../../overview.md)
