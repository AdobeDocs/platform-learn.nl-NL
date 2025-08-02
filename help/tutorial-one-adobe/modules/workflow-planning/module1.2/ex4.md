---
title: Aan de slag met Workfront
description: Aan de slag met Workfront
kt: 5342
doc-type: tutorial
source-git-commit: 34f37a33e874f55eea37290b5626ab613f575764
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# 1.2.4 Workfront + AEM Sites

Login aan Adobe Workfront door naar [ https://experienceplatform.my.workfront.com/ ](https://experienceplatform.my.workfront.com/){target="_blank"} te gaan.

Dan zie je dit.

![ WF ](./images/wfb1.png)

## 1.2.4.1 Uw AEM Sites-integratie configureren

>[!NOTE]
>
>Deze insteekmodule is momenteel op **Vroege wijze van de Toegang** en is over het algemeen nog niet beschikbaar.
>
>Deze insteekmodule is mogelijk al geïnstalleerd in het Workfront-exemplaar dat u gebruikt. Als deze al is geïnstalleerd, kunt u de onderstaande instructies bekijken, maar hoeft u niets te wijzigen in uw configuratie.

Ga naar [ https://experience.adobe.com/#/@experienceplatform/aem/extension-manager/universal-editor ](https://experience.adobe.com/#/@experienceplatform/aem/extension-manager/universal-editor){target="_blank"}.

Zorg ervoor de **knevel** voor deze stop wordt geplaatst aan **Toegelaten**. Dan, klik het **versnelling** pictogram.

![ WF ](./images/wfb8.png)

U zult een **configuratie van de Uitbreiding** popup zien. Configureer de volgende velden om deze insteekmodule te gebruiken.

| Sleutel | Waarde |
| --------------- | ------------------------------ | 
| **`IMS_ENV`** | **PROD** |
| **`WORKFRONT_INSTANCE_URL`** | **https://experienceplatform.my.workfront.com** |
| **`SHOW_CUSTOM_FORMS`** | **&#39;{&quot;previewUrl&quot;: true, &quot;publishUrl&quot;: true}&#39;** |

Klik **sparen**.

![ WF ](./images/wfb8.png)

Ga terug naar uw Workfront UI en klik het 9 punten **hamburger** pictogram. Selecteer **Opstelling**.

![ WF ](./images/wfb9.png)

In het linkermenu, ga naar **Douane Forms** en selecteer **Vorm**. Klik op **+ Nieuw aangepast formulier** .

![ WF ](./images/wfb10.png)

Selecteer **Taak** en klik **verdergaan**.

![ WF ](./images/wfb11.png)

Vervolgens ziet u een leeg aangepast formulier. Voer de formuliernaam in `Content Fragment & Integration ID` .

![ WF ](./images/wfb12.png)

De belemmering en laat vallen een nieuw **Enige lijntekst** gebied op het canvas.

![ WF ](./images/wfb13.png)

Vorm het nieuwe gebied als dit:

- **Etiket**: **het Fragment van de Inhoud**
- **Naam**: **`aem_workfront_integration_content_fragment`**

![ WF ](./images/wfb14.png)

Voeg een nieuw **Enige lijntekst** gebied op het canvas toe en vorm het nieuwe gebied als dit:

- **Etiket**: **identiteitskaart van de Integratie**
- **Naam**: **`aem_workfront_integration_id`**

Klik **toepassen**.

![ WF ](./images/wfb15.png)

U moet nu een tweede aangepast formulier configureren. Klik op **+ Nieuw aangepast formulier** .

![ WF ](./images/wfb10.png)

Selecteer **Taak** en klik **verdergaan**.

![ WF ](./images/wfb11.png)

Vervolgens ziet u een leeg aangepast formulier. Voer de formuliernaam in `Preview & Publish URL` .

![ WF ](./images/wfb16.png)

De belemmering en laat vallen een nieuw **Enige lijntekst** gebied op het canvas.

![ WF ](./images/wfb17.png)

Vorm het nieuwe gebied als dit:

- **Etiket**: **Voorproef URL**
- **Naam**: **`aem_workfront_integration_preview_url`**

![ WF ](./images/wfb18.png)

Voeg een nieuw **Enige lijntekst** gebied op het canvas toe en vorm het nieuwe gebied als dit:

- **Etiket**: **publiceer URL**
- **Naam**: **`aem_workfront_integration_publish_url`**

Klik **toepassen**.

![ WF ](./images/wfb19.png)

U hebt dan twee aangepaste formulieren beschikbaar.

![ WF ](./images/wfb20.png)

Volgende Stap: [ 1.2.2 het Bewijzen met Workfront ](./ex2.md){target="_blank"}

Ga terug naar [ Beheer van het Werkschema met Adobe Workfront ](./workfront.md){target="_blank"}

[ ga terug naar Alle Modules ](./../../../overview.md){target="_blank"}
