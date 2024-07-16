---
title: Bootkamp - Overvloeien fysiek en digitaal - Journey Optimizer Maak uw evenement - Brazilië
description: Bootkamp - Overvloeien fysiek en digitaal - Journey Optimizer Maak uw evenement - Brazilië
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
solution: Journey Optimizer
feature-set: Journey Optimizer
feature: Events
exl-id: 2133b560-09d8-419d-bb99-05d0f3df52cc
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# 3.2 Crie seu evento

Faça login op Adobe Journey Optimizer toegang tot a [ Adobe Experience Cloud ]. Clique em **Journey Optimizer**.

![ ACOP ](./images/acophome.png)

Você será redirecionado para **Huis** geen Journey Optimizer. Primeiro, verifieque se você está usando sandbox correto. O nome do sandbox que deve ser usado é `Bootcamp` . Para alternar de um sandbox para outro, klique em **Prod** e selecione aan zandbak na lista. Neste voorbeeldig, o nome do zandbak é **Bootkamp**. Você estará na visualização da **Huis** do seu zandbak `Bootcamp`.

![ ACOP ](./images/acoptriglp.png)

Geen menu à esquerda, rolpara baixo e clique em **Configuraties**. Em seguida, kliek op botão **beheert** em Eventos.

![ ACOP ](./images/acopmenu.png)

Você verá uma visão geral de todos os eventos disponíveis. Clique em **creeer Gebeurtenis** para começar een criar seu próprio evento.

![ ACOP ](./images/emptyevent.png)

Uma nova janela de evento vazia irá aparecer.

Em primeiro lugar, dê um nome ao seu evento como, por exemplo: `yourLastNameBeaconEntryEvent` e adicione uma describe ção como, por exemplo: `Beacon Entry Event` .

![ ACOP ](./images/eventdescription.png)

Em seguida, certificaaque-se de que **Type** está definido como **Eenitaire** e, para a seleção de **Identiteitskaart van de Gebeurtenis**, verkiesbaar **Gegenereerd Systeem**.

![ ACOP ](./images/eventidtype.png)

A etapa seguinte é a seleção do schema. Het schema foi preparado para este uitoefício. Gebruiken met schema `Demo System - Event Schema for Mobile App (Global v1.1) v.1` .

![ ACOP ](./images/eventschema.png)

Depois de selecionar o Schema, você verá vários campos sendo selecionados na seção **Gebieden**. Agora vocdeve passar o mouse sobre a seção **Velden** e três ícones pop-up serão exibidos. De klem op ícone geeft **uit**.

![ ACOP ](./images/eventpayload.png)

Você verá uma janela pop-up de **Gebieden**, de onde você deve selecionar algun dos campos que precisamos para personalizar a jornada. Escolheremos outros atributos de perfil posteriormente, utilizando os dados já existentes e Adobe Experience Platform

![ ACOP ](./images/eventfields.png)

Rol para baixo até ver o object `Place context` e marque a caixa de seleção. Com isso, todo o contexto da localização do cliente será disponibilizado para jornada. Clique em **O.K.** para salvar suas alternatieve ações.

![ ACOP ](./images/eventpayloadbr.png)

Em seguida, você deverá over a tela abaixo. De klemem **sparen** mais uma vez para salvar suas validações.

![ ACOP ](./images/eventsave.png)

Seu evento agora está configurado e salvo.

![ ACOP ](./images/eventdone.png)

De klem op seu evento novamente para abrir a tela **geeft Gebeurtenis** mais uma vez uit. Passe aan muis sobre **Gebieden** para over os 3 ícones. De klem op ícone **Mening**.

![ ACOP ](./images/viewevent.png)

Agora você verá um exemplo do payload esperado.
Seu evento tem um eventID de orquestração único, que você pode enconr rolando para baixo nessa carga útil até visualiza `_experience.campaign.orchestration.eventID` .

![ ACOP ](./images/payloadeventID.png)

O eventID é o que deve ser enviado à Adobe Experience Platform para acionar a jornada que você construirá em um dos próximos uitoefícios. Lembre-se deste eventID, você pode precisar dele posteriormente.
`"eventID": "e76c0bf0c77c3517e5b6f4c457a0754ebaf5f1f6b9357d74e0d8e13ae517c3d5"`

Clique em **O.K.** e, em seguida, klikem **annuleert**.

Você terminou este uitoefício.

Próxima etapa: [ 3.3 Crie sua jornada e notificação push ](./ex3.md)

[Retornar para Fluxo de Usuário 3](./uc3.md)

[Retornar para Todos os Módulos](../../overview.md)
