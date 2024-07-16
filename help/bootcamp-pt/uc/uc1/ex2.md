---
title: Bootkamp - Real-time klantprofiel - Visualiseer uw eigen Real-time klantprofiel - UI - Brazilië
description: Bootkamp - Real-time klantprofiel - Visualiseer uw eigen Real-time klantprofiel - UI - Brazilië
jira: KT-5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
feature: Profiles
exl-id: 4eebb080-77fd-4162-aa64-d599f1274c93
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# 1.2 Visualiseren seu próprio perfil de cliente em tempo real - UI

Neste uitoefício, você irá fazer login na Adobe Experience Platform e visualizar seu próprio Perfil de cliente em tempo real na UI.

## História

No Perfil do cliente em tempo real, todos os dados do perfil são exibidos juntamente com os dados do evento, além das associações de segmentos existentes. Os dados mostrados podem vir de qualquer lugar, de aplicativos da Adobe e solution ções externas. Essa a a exibição mais poderosa da Adobe Experience Platform, o verda deiro local do sistema de experience ência.

## 1.2.1 Gebruik een visualização do perfil do cliente e Adobe Experience Platform

Toegang tot [ Adobe Experience Platform ](https://experience.adobe.com/platform). Depois de fazer login, você irá acessar a página inicial da Adobe Experience Platform.

![ Ingestie van Gegevens ](./images/home.png)

Antes de continuar, você nauwkeurige um **zandbak**. O nome do sandbox a ser selecionado é Bootkamp. É bezível fazer isso clicando no texto **[!UICONTROL Production Prod]** na linha azul na parte superior da tela. Depois de selecionar o sandbox apropriado, você verá a tela mudando e agora você está em seu [!UICONTROL sandbox] oormerk.

![ Ingestie van Gegevens ](./images/sb1.png)

Geen menu à esquerda, toegang **Profielen** e **doorbladeren**.

![ Profiel van de Klant ](./images/homemenu.png)

Geen pijnlijke Visualizador de perfil op seu-locatie, você pode contrasteert een visão geral da identidade. Cada identifier está vinculada a um namespace.

![ Profiel van de Klant ](./images/identities.png)

Geen pijnel Visualizador de perfil, agora você pode ver uma identificeerde semelhante a seguinte:

| Naamruimte | Identiteit |
|:-------------:| :---------------:|
| Experience Cloud-id (ECID) | 19428085896177382402834560825640259081 |

Com a Adobe Experience Platform, todos os IDs são igualmente importantes. Anteriormente, o ECID era o ID mais importante no contexto da Adobe e todos os outros IDs estavam vinculados ao ECID em uma relação hierárquica. Com a Adobe Experience Platform, isso mudou e cada ID pode ser overweging, um identificador primário.

Normalmente, o identificador primário depende do contexto. Se você perguntar ao seu Call Center: **Qual é o ID mais importante?** Eles provavelmente responderão: **o número de telefone!** Mas se você perguntar à sua equipe de CRM, eles responderão: **o endereço de e-mail!** A Adobe Experience Platform entende essa complexidade e gerencia isso para você. Cada aplicativo, seja um aplicativo da Adobe ou não, se comunicará com a Adobe Experience Platform referindo-se ao ID que bezam principal. E simpesmente funciona

Para aan campo **Identiteitsnaamruimte**, verkione **ECID** e para aan campo **de Waarde van de Identiteit** binnen aan ECID que você pode contrar geen schilderij Visualizador de perfil doet plaats Bootkamp. Clique em **Mening**. Você verá seu perfil na lista. Clique geen **identiteitskaart van het Profiel** para abrir seu perfil.

![ Profiel van de Klant ](./images/popupecid.png)

Agora voctem uma visão geral de algun **Atributos de perfil** importantes do seu perfil de cliente.

![ Profiel van de Klant ](./images/profile.png)

Acesse **Gebeurtenissen**, de onde você pode ver als entradas de cada evento de experience ência vinculado ao seu Perfil.

![ Profiel van de Klant ](./images/profileee.png)

Por fim, toegang tot een opção de menu **lidmaatschap van het Segment**. Agora você verá todos os segmentos que se kwalificficam para este perfil.

![ Profiel van de Klant ](./images/profileseg.png)

Agora vamos criar um novo segmento que permitirá que você personalize a experience ência do cliente para um cliente anônimo ou conhecido.

Próxima etapa: [ 1.3 Crie um segmento - UI ](./ex3.md)

[Retornar para Fluxo de Usuário 1](./uc1.md)

[Retornar para Todos os Módulos](../../overview.md)
