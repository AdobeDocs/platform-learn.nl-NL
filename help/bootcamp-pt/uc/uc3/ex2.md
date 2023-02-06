---
title: Bootkamp - Overvloeien fysiek en digitaal - Journey Optimizer Maak uw evenement - Brazilië
description: Bootkamp - Overvloeien fysiek en digitaal - Journey Optimizer Maak uw evenement - Brazilië
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
source-git-commit: 9cc01c7d3018319137f915e103bce9dc39b0d472
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# 3.2 Crie seu evento

Faça login no Adobe Journey Optimizer acessando a [Adobe Experience Cloud]. Clique em **Journey Optimizer**.

![ACOP](./images/acophome.png)

Você será redirecionado para **Home** geen Journey Optimizer. Primeiro, verifieque se você está usando sandbox correto. O nome do sandbox que deve ser usado é `Bootcamp`. Para alternar de um sandbox para outro, clique em **Prod** Selecteer een sandbox of lista. Neste voorbeeld, o noome do sandbox é **Bootamp2**. Você estará na visualização da **Home** seu-sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

No menu à esquerda, role para baixo e clique em **Configuraties**. Em seguida, clique no botão **Beheren** em Evtos.

![ACOP](./images/acopmenu.png)

Você verá uma visão geral de todos os eventos disponíveis. Clique em **Gebeurtenis maken** para começar a criar seu próprio evento .

![ACOP](./images/emptyevent.png)

Uma nova janela de evento vazia irá aparecer.

Em primeiro lugar, dê um nome ao seu evento como, por exemplo: `yourLastNameBeaconEntryEvent` e adicione uma describe ção como, por voorbeo: `Beacon Entry Event`.

![ACOP](./images/eventdescription.png)

Em seguida, certifique-se de que **Type** está definido como **Unitair** e, para a seleção de **Type gebeurtenis-id**, selecione **Door systeem gegenereerd**.

![ACOP](./images/eventidtype.png)

A etapa seguinte é a seleção do schema. Het schema foi preparado para este uitoefício. Gebruiken voor schema `Demo System - Event Schema for Mobile App (Global v1.1) v.1`.

![ACOP](./images/eventschema.png)

Depois de selecionar o Schema, você verá vários campos sendo selecionados na seção **Velden**. Agora vocale deve passar o mouse sobre a seção **Velden** e três ícones pop-up serão exibidos. Clique no ícone de **Bewerken**.

![ACOP](./images/eventpayload.png)

Você verá uma janela pop-up de **Velden**, de onde vocdeve selecionar algun dos campos que precisamos para personalizar a jornada. Escolheremos outros atributos de perfil posteriormente, utilizando os dados já existentes e Adobe Experience Platform

![ACOP](./images/eventfields.png)

Rol para baixo até ver o objeto `Place context` e marque a caixa de seleção. Com isso, todo o contexto da localização do cliente será disponibilizado para jornada. Clique em **OK** para salvar suas validações.

![ACOP](./images/eventpayloadbr.png)

Em seguida, você deverá over a tela abaixo. Clique em **Opslaan** mais uma vez para salvar suas validações .

![ACOP](./images/eventsave.png)

Seu evento agora está configurado e salvo.

![ACOP](./images/eventdone.png)

Clique no seu evento novamente para abrir a tela **Gebeurtenis bewerken** mais uma vez. Passe o mouse sobre **Velden** punt ver os 3 ícones. Clique no ícone **Weergave**.

![ACOP](./images/viewevent.png)

Agora você verá um exemplo da carga útil esperada.
Seu evento tem um eventID de orquestração único, que você pode enconr rolando para baixo nessa carga útil até visualiza `_experience.campaign.orchestration.eventID`.

![ACOP](./images/payloadeventID.png)

O eventID é o que deve ser enviado à Adobe Experience Platform para acionar a jornada que você construirá em um dos próximos uitoefícios. Lembre-se deste eventID, você pode precisar dele posteriormente.
`"eventID": "e76c0bf0c77c3517e5b6f4c457a0754ebaf5f1f6b9357d74e0d8e13ae517c3d5"`

Clique em **OK** e, em seguida, clique em **Cancelar**.

Você terminou este uitoefício.

Próxima etapa: [3.3 Crie sua jornada e notificação push](./ex3.md)

[Retornar para Fluxo de Usuário 3](./uc3.md)

[Retornar para Todos os Módulos](../../overview.md)
