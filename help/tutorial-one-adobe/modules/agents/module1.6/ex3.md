---
title: Inhoudsfragmenten schalen met ChatGPT en MCP Server
description: Inhoudsfragmenten schalen met ChatGPT en MCP Server
kt: 5342
doc-type: tutorial
exl-id: b7105351-e9de-4b2c-b3d7-2d4c8627f852
source-git-commit: a57050bf40105a0b0c6d4ce615aa640e878ece12
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 0%

---

# 1.6.3 Inhoudsfragmenten schalen met ChatGPT en MCP Server

>[!IMPORTANT]
>
>Om deze oefening te voltooien, moet u toegang tot een werkende AEM Sites en Assets CS met milieu EDS en de diverse agenten van AEM worden toegelaten voor IMS Org u gebruikt.
>
>Als u zulk een milieu nog niet hebt, ga [&#x200B; Adobe Experience Manager Cloud Service &amp; Edge Delivery Services &#x200B;](./../../../modules/asset-mgmt/module2.1/aemcs.md){target="_blank"} uitoefenen. Volg de instructies daar, en u zult toegang tot zulk een milieu hebben.

>[!IMPORTANT]
>
>Als u eerder een AEM CS-programma hebt geconfigureerd met een AEM Sites- en Assets CS-omgeving, kan het zijn dat uw AEM CS-sandbox is geminimaliseerd. Gezien het feit dat het vernietigen van zo&#39;n zandbak 10 tot 15 minuten duurt, zou het een goed idee zijn om het ontruimingsproces nu te beginnen zodat u niet op een later tijdstip hoeft te wachten.

## 1.6.3.1 Inhoudsfragmentmodel maken

Ga terug naar uw milieu van de Auteur van Adobe Experience Manager, aan **Hulpmiddelen** en ga dan naar **Browser van de Configuratie**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm1.png)

Klik **creëren**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm2.png)

Gebruik `Content Fragments` voor de gebieden **Titel** en **Naam**.

Zorg ervoor de opties **Modellen van het Fragment van de Inhoud** en **GraphQL de Verlengde Vragen** allebei worden toegelaten.

Klik **creëren**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm3.png)

Ga terug naar uw milieu van de Auteur van Adobe Experience Manager en ga dan naar **Fragments van de Inhoud**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscf1.png)

Ga naar **Modellen van het Fragment van de Inhoud**, selecteer uw configuratie **Fragmenten van de Inhoud** en klik dan **creeer**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm4.png)

Gebruik de naam `--aepUserLdap-- - CitiSignal CFM` . Klik **creëren en openen**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm5.png)

Dan moet je dit zien. De belemmering en laat vallen a **Enige lijntekst** gebied op het canvas.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm6.png)

Verander het gebied **etiket van het Gebied** in `Header`.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm7.png)

Ga terug naar **Types van Gegevens**. De belemmering en laat vallen a **Enige lijntekst** gebied op het canvas.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm8.png)

Verander het gebied **etiket van het Gebied** in `Subheader`.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm9.png)

Ga terug naar **Types van Gegevens**. De belemmering en laat vallen a **Meerdere lijntekst** gebied op het canvas.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm10.png)

Verander het gebied **etiket van het Gebied** in `Detail Description`.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm11.png)

Ga terug naar **Types van Gegevens**. De belemmering en laat vallen a **Enige lijntekst** gebied op het canvas.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm12.png)

Verander het gebied **etiket van het Gebied** in `CTA Text`.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm13.png)

Ga terug naar **Types van Gegevens**. De belemmering en laat vallen a **Enige lijntekst** gebied op het canvas.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm14.png)

Verander het gebied **etiket van het Gebied** in `CTA Link`. Klik **sparen**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm15.png)

Dan moet je dit zien.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm16.png)

Selecteer uw model van het inhoudsfragment en klik **publiceren**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm17.png)

Klik **publiceren**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfm18.png)

## 1.6.3.2 Inhoudsfragment maken

Ga terug naar uw milieu van de Auteur van Adobe Experience Manager en ga dan naar **Fragments van de Inhoud**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscf1.png)

Dan moet je dit zien. Klik **creëren** en selecteer dan **Omslag**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscf2.png)

Voer de titel in: `--aepUserLdap-- - CF`. Klik **creëren**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscf3.png)

Ga terug naar uw milieu van de Auteur van Adobe Experience Manager en ga dan naar **Assets**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfmm1.png)

Ga naar **Dossiers**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfmm2.png)

Selecteer de omslag u enkel creeerde, die `--aepUserLdap-- - CF` zou moeten worden genoemd en **Eigenschappen** klikken.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfmm3.png)

Ga naar **de Diensten van de Wolk** en klik dan het **omslag** pictogram.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfmm4.png)

Selecteer de wolkenconfiguratie u eerder creeerde, die **de Fragmenten van de Inhoud** zou moeten worden genoemd. Klik **Uitgezocht**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfmm5.png)

Dan moet je dit zien. Klik **sparen &amp; Sluiten**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscfmm6.png)

Ga terug naar uw milieu van de Auteur van Adobe Experience Manager en ga dan naar **Fragments van de Inhoud**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscf1.png)

Dan moet je dit zien. Klik **creëren** en selecteer dan **het Fragment van de Inhoud**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscf4.png)

Selecteer het **Model van het Fragment van de Inhoud** u eerder creeerde, dat zou moeten worden genoemd `--aepUserLdap-- - CitiSignal CFM`. Gebruik de naam `--aepUserLdap-- CitiSignal Fiber Max` .

Klik **creëren en openen**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscf5.png)

Dan moet je dit zien.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscf5a.png)

Vul de velden als volgt in:

- **Kopbal**: `CitiSignal Fiber Max`
- **Subheader**: `Experience high speed internet now`
- **Beschrijving van het Detail**:

```
Experience the future of connectivity with CitiSignal Fiber Max, the ultimate solution for high-speed internet. Designed for homes and businesses that demand performance, Fiber Max delivers blazing-fast fiber speeds, ensuring seamless streaming, ultra-responsive gaming, and crystal-clear video calls.

Key Features:

Unmatched Speed: Enjoy lightning-fast downloads and uploads powered by cutting-edge fiber technology.
Reliable Performance: Consistent connectivity for work, entertainment, and everything in between.
Future-Ready: Built to handle the growing demands of smart homes and digital lifestyles.
Unlimited Potential: No data caps, no throttling—just pure speed.
Why Choose CitiSignal Fiber Max? Stay ahead with internet that works as hard as you do. Whether you’re powering a remote office or streaming in 4K, Fiber Max ensures you never miss a beat.
```

**Tekst van CTA**: `Upgrade now by signing your new contract!`
**Verbinding van CTA**: `https://techinsiders68.adobedemosystem.com/`

Klik **publiceren** en selecteer dan **nu**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscf6.png)

Klik **publiceren**.

![&#x200B; de Agenten van AEM &#x200B;](./images/aemagentscf7.png)

## 1.6.3.3 MCP-server configureren in ChatGPT

>[!NOTE]
>
>Voor het gebruik van Adobe Marketing Agent in ChatGPT is het volgende vereist:
>- Een betaalde versie van ChatGPT Enterprise van OpenAI
>- de ChatGPT Enterprise-webclient gebruiken

Ga naar [&#x200B; https://chatgpt.com/ &#x200B;](https://chatgpt.com/){target="_blank"} en login die uw rekeningsdetails gebruiken. Nadat u zich hebt aangemeld, kunt u dit beter zien. Klik uw gebruikersbenaming en selecteer dan **Montages**.

![&#x200B; ChatGPT &#x200B;](./images/chatgpt2.png)

Ga naar **Apps** en selecteer dan **Geavanceerde montages**.

![&#x200B; ChatGPT &#x200B;](./images/chatgpt3.png)

Zet **wijze van de Ontwikkelaar** aan en klik dan **terug**.

![&#x200B; ChatGPT &#x200B;](./images/chatgpt4.png)

Klik **Create app**.

![&#x200B; ChatGPT &#x200B;](./images/chatgpt5.png)

Vul de velden als volgt in:

- **Naam**: `aem`
- **URL van de Server MCP**: `https://mcp.adobeaemcloud.com/adobe/mcp/content`
- **Authentificatie**: `OAuth`

Controleer checkbox voor **ik begrijp en wil** verdergaan.

Klik **creëren**.

![&#x200B; ChatGPT &#x200B;](./images/chatgpt6.png)

ChatGPT probeert nu verbinding te maken met uw Adobe-account. Selecteer **Toestaan Toegang** en dan zult u login met uw rekening van Adobe moeten.

Zodra u zich met succes hebt aangemeld, zou u moeten zien dat uw Adobe Marketing Agent nu met succes wordt verbonden.

![&#x200B; ChatGPT &#x200B;](./images/chatgpt8.png)

## 1.6.3.4 AEM MCP-server gebruiken in ChatGPT

Sluit dit venster.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt8.png)

Dan moet je dit zien. Klik **+** pictogram, ga **Meer** en selecteer dan **a**.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt10.png)

Ga de volgende herinnering in en klik **verzenden**.

```
I just created a new custom mcp server named 'aem'. what can I do with that?
```

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt11.png)

Dan moet je iets dergelijks zien. Ga de volgende herinnering in en klik **verzenden**.

```
use the author url https://author-pXXXXXX-eXXXXXXX.adobeaemcloud.com/ from now on
```

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt12.png)

Dan moet je iets dergelijks zien. Ga de volgende herinnering in en klik **verzenden**.

```
find the content fragment --aepUserLdap-- - CitiSignal Fiber Max and make a variation called --aepUserLdap-- - CitiSignal Fiber Max (FR), then translate all fields into french
```

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt13.png)

Klik **CreateFragmentVariation**.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt14.png)

Klik **UpdateFragment**.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt15.png)

Dan moet je dit zien. Uw fragmentvariatie is gemaakt.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt16.png)

Je kunt nu ook je nieuwe variatie zien in de gebruikersinterface van AEM.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt17.png)

Gebruik vervolgens ChatGPT om het inhoudsfragment in meer variaties te vertalen. Ga de volgende herinnering in en klik **verzenden**.

```
now do the same thing for the 5 top country's languages that CitiSignal does business with
```

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt18.png)

Bevestig uw taalkeuze.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt23.png)

Klik **CreateFragmentVariation**.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt22.png)

Klik **UpdateFragment**.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt24.png)

Herhaal dit proces voor elk van de talen die u hebt geselecteerd. Als je klaar bent, moet je iets als dit zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt26.png)

Ga terug naar de gebruikersinterface van AEM en vernieuw het scherm. U kunt nu de nieuwe variaties in het inhoudsfragment zien.

![&#x200B; Agent Orchestrator &#x200B;](./images/chatgpt27.png)

## Volgende stappen

Ga terug naar [&#x200B; AEM &amp; Agenten &#x200B;](./aemagents.md){target="_blank"}

[&#x200B; ga terug naar Alle Modules &#x200B;](./../../../overview.md){target="_blank"}
