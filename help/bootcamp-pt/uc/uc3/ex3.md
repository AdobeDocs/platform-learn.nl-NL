---
title: Bootkamp - Overvloeien fysiek en digitaal - Journey Optimizer Maak een reis en duw - Brazilnotification
description: Bootkamp - Overvloeien fysiek en digitaal - Journey Optimizer Maak een reis en duw - Brazilnotification
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
solution: Journey Optimizer
feature-set: Journey Optimizer
feature: Events
exl-id: a4ef6eaf-6b39-4450-82bf-7db99595a323
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '843'
ht-degree: 0%

---

# 3.3 Crie sua jornada e notificação push

Neste uitoefício, você irá configurar a jornada e a mensagem que precisa ser acionada quando alguém insert ir uma sinalização (baken) usando o aplicativo móvel.

Faça login op Adobe Journey Optimizer toegang tot a [ Adobe Experience Cloud ](https://experience.adobe.com). Clique em **Journey Optimizer**.

![ ACOP ](./images/acophome.png)

Você será redirecionado para a visualização da **Huis** geen Journey Optimizer. Primeiro, verifieque se você está usando sandbox correto. O nome do sandbox que deve ser usado é `Bootcamp` . Para alternar de um sandbox para outro, klique em **Prod** e selecione aan zandbak na lista. Neste voorbeeldig, o nome do zandbak é **Bootkamp**. Você estará na visualização da **Huis** do seu zandbak `Bootcamp`.

![ ACOP ](./images/acoptriglp.png)

## 3.3.1 Crie a sua jornada

Geen menu à esquerda, klikem **Reizen**. Em seguida, kliek em **creeer de 1} parabijis van de Reis { jornada.**

![ ACOP ](./images/createjourney.png)

Você verá uma tela de jornada vazia.

![ ACOP ](./images/journeyempty.png)

Geen uitoefício anterior, você criou um novo **Gebeurtenis**. Você nomeou o evento `yourLastNameBeaconEntryEvent` e substituiu `yourLastName` pelo seu sobrenome. Este foi o resultado da criação do Evento:

![ ACOP ](./images/eventdone.png)

Agora vocdeve aanzienlijke este evento como o início desta Jornada. Você pode fazer isso indo para o lado esquerdo da tela e procurando pelo seu evento na lista de eventos.

![ ACOP ](./images/eventlist.png)

Selecione seu evento, arraste e solte o evento na tela de jornada. Sua jornada agora deve ser semelhante ao seguinte. Clique em **O.K.** para salvar suas alternatieve ações.

![ ACOP ](./images/journeyevent.png)

Como segunda etapa da jornada, você deve adicionar uma ação **Push**. Vá para o lado esquerdo da tela para **Acties**, verkione a ação **Push** e arraste e solte a ação no segundo nó da sua jornada.

![ ACOP ](./images/journeyactions.png)

No lado direito da tela, agora você deve criar sua notificação push.

Definieer a **Categorie** como **marketing** e selecione de oppervlakte van de duw- oppervlakte permite enviar notificações duw. Nesse caso, een superfície duw een ser selecionada é **mmeewis-app-mobile-bootkamp**.

![ ACOP ](./images/journeyactions1.png)

## 3.3.2 Crie a sua mensagem

De klemem **geeft Inhoud** uit.

![ ACOP ](./images/emptymsg.png)

Em seguida, een tela abaixo será exibida:

![ ACOP ](./images/emailmsglist.png)

Vamos definir o conteúdo da notificação push.

De klem op campo de texto **Titel**.

![ Journey Optimizer ](./images/msg5.png)

Na área de texto, comece **Olá**. Clique no ícone de personalização.

![ Journey Optimizer ](./images/msg6.png)

Agora você preca trazer o token de personalização para o campo **Voornaam** que está armazenado em `profile.person.name.firstName`. Geen menu à esquerda, selecione **Attributen van het Profiel**, rolpara baixo/navegue para enconr o elemento **Person** e clique na seta para avançar um nível até chegar ao campo `profile.person.name.firstName`. Clique no ícone **+** para adicionar o campo à tela. Clique em **sparen**.

![ Journey Optimizer ](./images/msg7.png)

Então, você irá retornar para esta tela. Clique no ícone de personalização ao lado do campo **Lichaam**.

![ Journey Optimizer ](./images/msg11.png)

Na área de texto, escreva `Bem-vindo(a)`.

![ Journey Optimizer ](./images/msg12.png)

Em seguida, klique em **Contextuele Attributen** e **Journey Orchestration**.

![ ACOP ](./images/jomsg3.png)

Clique em **Gebeurtenissen**.

![ ACOP ](./images/jomsg4.png)

De klikgenoom doet zeven aan, deve ser semelhante ao seguinte: **yourLastNameBeaconEntryEvent**.

![ ACOP ](./images/jomsg5.png)

Clique em **context van de Plaats**.

![ ACOP ](./images/jomsg6.png)

Clique em **de Interactie van POI**.

![ ACOP ](./images/jomsg7.png)

Het gedetailleerde geheugen van het em van de Clik **POI**.

![ ACOP ](./images/jomsg8.png)

De klem nr **+** pictogram op **Naam van POI**.
Em seguida, o seguinte será exibido. Clique em **sparen**.

![ ACOP ](./images/jomsg9.png)

Sua mensagem agora está pronta Clique na seta no canto superior esquerdo para retornar à sua jornada.

![ ACOP ](./images/jomsg11.png)

Clique em **OK**.

![ ACOP ](./images/jomsg14.png)

## 3.3.2 Envie uma mensagem para uma tela

Como terceira etapa da jornada, você deve adicionar uma ação **sendMessageToScreen**. Vá para o lado esquerdo da tela para **Acties**, verkies a ação **sendMessageToScreen** e arraste e solte a ação no terceiro nó da sua jornada. Em seguida, você verá a tela abaixo.

![ ACOP ](./images/jomsg15.png)

**sendMessageToScreen** é uma ação personalizada que irá publicar uma mensagem no **Eindpunt** usado pela exibição na loja. A ação **sendMessageToScreen** espera que múltiplas variáveis sejam definidas. Você pode visualizar essas variáveis rolando para baixo até ver **Parameters van de Actie**.

![ ACOP ](./images/jomsg16.png)

Agora você preca definir os valores para cada parâmetro de ação. Siga esta tabela para entender quis valores são necessary ários e onde.

| Parameter | value |
|:-------------:| :---------------:|
| LEVERING | `'image'` |
| ECID | `@{yourLastNameBeaconEntryEvent._experienceplatform.identification.core.ecid}` |
| EERSTE NAAM | `#{ExperiencePlatform.ProfileFieldGroup.profile.person.name.firstName}` |
| EVENTSUBJECT | `#{ExperiencePlatform.ProductListItems.experienceevent.first(currentDataPackField.eventType == "commerce.productViews").productListItems.first().name}` |
| EVENTSUBJECTURL | `#{ExperiencePlatform.ProductListItems.experienceevent.first(currentDataPackField.eventType == "commerce.productViews").productListItems.first()._experienceplatform.core.imageURL}` |
| SANDBOX | `'bootcamp'` |
| CONTAINERID | `''` |
| ACTIVITYID | `''` |
| PLACEMENTID | `''` |

{style="table-layout:auto"}

Para definiir verwerkt valores, klikt op ícone **geeft** uit.

![ ACOP ](./images/jomsg17.png)

Em seguida, verkies **Geavanceerde Wijze**.

![ ACOP ](./images/jomsg18.png)

Em seguida, cole o valor com base na tabela acima. Clique em **OK**.

![ ACOP ](./images/jomsg19.png)

Repita esse processo para adicionar valores para cada campo.

>[!IMPORTANT]
>
>Para o campo ECID, há uma referência ao evento `yourLastNameBeaconEntryEvent`. Lembre-se de substituir `yourLastName` pelo seu sobrenome.

O resultado final deve ser semelhante ao seguinte:

![ ACOP ](./images/jomsg20.png)

De para van de rol cicma e clique em **OK**.

![ ACOP ](./images/jomsg21.png)

Je moet je reis nog steeds een naam geven. U kunt dat doen door het **pictogram van Eigenschappen** in de hoogste rechterkant van uw scherm te klikken.

![ ACOP ](./images/journeyname.png)

Você pode insert o nome da jornada aqui. Gebruik `yourLastName - Beacon Entry Journey` . De klikem **O.K.** para salvar suas alternatieve ações.

![ ACOP ](./images/journeyname1.png)

Agora você pode publicar sua jornada clicando em **Publish**.

![ ACOP ](./images/publishjourney.png)

Clique em **Publish** novamente.

![ ACOP ](./images/publish1.png)

Você verá uma barra de confirmação verde informando que sua jornada agora está Publicada.

![ ACOP ](./images/published.png)

Sua jornada agora está ativa e pode ser acionada.

Você terminou este uitoefício.

Próxima etapa: [ 3.4 Teste sua jornada ](./ex4.md)

[Retornar para Fluxo de Usuário 3](./uc3.md)

[Retornar para Todos os Módulos](../../overview.md)
