---
title: Bootamp - Journey Optimizer Create your event - Brazilië
description: Bootamp - Journey Optimizer Create your event - Brazilië
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
solution: Journey Optimizer
feature-set: Journey Optimizer
feature: Events
exl-id: 1b9d7a35-cddf-4f4a-ad0a-95723b00c278
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# 2.2 Crie seu evento

Faça login no Adobe Journey Optimizer acessando a [Adobe Experience Cloud](https://experience.adobe.com). Clique em **Journey Optimizer**.

![ACOP](./images/acophome.png)

Você será redirecionado para visualização da **Home** geen Journey Optimizer. Primeiro, verifieque se você está usando sandbox correto. O nome do sandbox que deve ser usado é `Bootcamp`. Para alternar de um sandbox para outro, clique em Prod e selecione o sandbox na lista. Neste voorbeeld, o noome do sandbox é **Bootkamp**. Você estará na visualização da **Home** seu-sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

No menu à esquerda, role para baixo e clique em **Configuraties**. Em seguida, clique no botão **Beheren** abaixo de **Gebeurtenissen**.

![ACOP](./images/acopmenu.png)

Você verá uma visão geral de todos os eventos disponíveis. Clique em **Gebeurtenis maken** para começar a criar seu próprio evento .

![ACOP](./images/emptyevent.png)

Uma nova janela de evento vazia irá aparecer.

![ACOP](./images/emptyevent1.png)

Em primeiro lugar, dê um nome ao seu evento como, por exemplo: `seuSobrenomeAccountCreationEvent` e adicione uma describe ção como, por voorbeo: `Account Creation Event`.

![ACOP](./images/eventdescription.png)

Em seguida, certifique-se de que **Type** está definido como **Unitair** e, para a seleção de **Type gebeurtenis-id**, selecione **Door systeem gegenereerd**.

![ACOP](./images/eventidtype.png)

A etapa seguinte é a seleção do schema. Het schema foi preparado para este uitoefício. Gebruiken voor schema `Demo System - Event Schema for Website (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

Depois de selecionar o Schema, você verá vários campos sendo selecionados na seção **Velden**. Agora vocale deve passar o mouse sobre a seção **Velden** e três ícones pop-up serão exibidos. Clique no ícone **Bewerken**.

![ACOP](./images/eventpayload.png)

Você verá uma janela pop-up de **Velden**, onde vocdeve selecionar algun dos campos que precisamos para personalizar o e-mail. Escolheremos outros atributos de perfil posteriormente, utilizando os dados já existentes na Adobe Experience Platform.

![ACOP](./images/eventfields.png)

Geen object `_experienceplatform.demoEnvironment`, pcertifique-se de selecionar os campos **brandLogo** e **brandName**.

![ACOP](./images/eventpayloadbr.png)

Geen object `_experienceplatform.identification.core`, certifique-se de selecionar o campo **email**.

![ACOP](./images/eventpayloadbrid.png)

Clique em **OK** aan para salvar suas validações.

![ACOP](./images/saveok.png)

Em seguida, een telabaixo deve ser exibida. Clique em **Opslaan**  mais uma vez para salvar suas validações..

![ACOP](./images/eventsave.png)

Seu evento agora está configurado e salvo.

![ACOP](./images/eventdone.png)

Clique no seu evento novamente para abrir mais uma vez a tela **Gebeurtenis bewerken**. Passe o mouse sobre **Velden** para ver os 3 ícones outra vez . Clique no ícone **Payload weergeven**.

![ACOP](./images/viewevent.png)

Agora você verá um exemplo da carga útil esperada.
Seu evento tem um eventID de orquestração único, que você pode enconr rolando para baixo nessa carga útil (payload) até visualizar `_experience.campaign.orchestration.eventID`.

![ACOP](./images/payloadeventID.png)

O eventID é o que deve ser enviado à Adobe Experience Platform para acionar a jornada que você construirá em um dos próximos uitoefícios. Lembre-se deste eventID, você pode precisar dele posteriormente.
`"eventID": "19cab7852cdef99d25b6d5f1b6503da39d1f486b1d585743f97ed2d1e6b6c74f"`

Clique em **OK** e, em seguida, clique em **Annuleren**.

Agora você terminou este uitoefício.

Próxima etapa: [ 2.3 Crie sua mensagem de e-mail](./ex3.md)

[Retornar para Fluxo de Usuário 2](./uc2.md)

[Retornar para Todos os Módulos](../../overview.md)
