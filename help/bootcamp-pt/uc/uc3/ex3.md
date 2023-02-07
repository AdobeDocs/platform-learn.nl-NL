---
title: Bootkamp - Overvloeien fysiek en digitaal - Journey Optimizer Maak een reis en duw - Brazilnotification
description: Bootkamp - Overvloeien fysiek en digitaal - Journey Optimizer Maak een reis en duw - Brazilnotification
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
source-git-commit: 5d824244766135cd4998feab48be7f6a69c42a70
workflow-type: tm+mt
source-wordcount: '838'
ht-degree: 1%

---

# 3.3 Crie sua jornada e notificação push

Neste uitoefício, você irá configurar a jornada e a mensagem que precisa ser acionada quando alguém insert ir uma sinalização (baken) usando o aplicativo móvel.

Faça login no Adobe Journey Optimizer acessando a [Adobe Experience Cloud](https://experience.adobe.com). Clique em **Journey Optimizer**.

![ACOP](./images/acophome.png)

Você será redirecionado para visualização da **Home** geen Journey Optimizer. Primeiro, verifieque se você está usando sandbox correto. O nome do sandbox que deve ser usado é `Bootcamp`. Para alternar de um sandbox para outro, clique em **Prod** Selecteer een sandbox of lista. Neste voorbeeld, o noome do sandbox é **Bootkamp**. Você estará na visualização da **Home**  seu-sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

## 3.3.1 Crie a sua jornada

Geen menu à esquerda, klik op em **Reizen**. Em seguida, clique em **Reis maken** para criar uma nova jornada .

![ACOP](./images/createjourney.png)

Você verá uma tela de jornada vazia.

![ACOP](./images/journeyempty.png)

No uitoefício anterior, você criou um novo **Gebeurtenis**. Você nomeou o evento `yourLastNameBeaconEntryEvent` e substituiu `yourLastName` pelo seu sobrenome . Este foi o resultado da criação do Evento:

![ACOP](./images/eventdone.png)

Agora vocdeve aanzienlijke este evento como o início desta Jornada. Você pode fazer isso indo para o lado esquerdo da tela e procurando pelo seu evento na lista de eventos.

![ACOP](./images/eventlist.png)

Selecione seu evento, arraste e solte o evento na tela de jornada. Sua jornada agora deve ser semelhante ao seguinte. Clique em **OK** para salvar suas validações.

![ACOP](./images/journeyevent.png)

Como segunda etapa da jornada, você deve adicionar uma ação **Push**. Vá para o lado esquerdo da tela para **Handelingen**, selecione a ação **Push** e arraste e solte a ação no segundo nó da sua jornada.

![ACOP](./images/journeyactions.png)

No lado direito da tela, agora você deve criar sua notificação push.

Defina a **Categorie** como **Marketing** e selecione um push surface que permite enviar notificações push. Nesse caso, een superfície duw op een ser selecionada é **mmeewis-app-mobile-bootkamp**.

![ACOP](./images/journeyactions1.png)

## 3.3.2 Crie a sua mensagem

Clique em **Inhoud bewerken**.

![ACOP](./images/emptymsg.png)

Em seguida, een tela abaixo será exibida:

![ACOP](./images/emailmsglist.png)

Vamos definir o conteúdo da notificação push.

Clique no campo de texto **Titel**.

![Journey Optimizer](./images/msg5.png)

Na área de texto, comece **Olá**. Clique no ícone de personalização.

![Journey Optimizer](./images/msg6.png)

Agora você preca trazer o token de personalização para o campo **Voornaam** que está armazenado em `profile.person.name.firstName`. Geen menu à esquerda, selecione **Profielkenmerken**, rol para baixo/navegue para enconr o elemento **Persoon** e clique na seta para avançar um nível até chegar ao campo `profile.person.name.firstName`. Clique no ícone **+** para adicionar o campo à tela. Clique em **Opslaan**.

![Journey Optimizer](./images/msg7.png)

Então, você irá retornar para esta tela. Clique no ícone de personalização ao lado do campo **Lichaam**.

![Journey Optimizer](./images/msg11.png)

Na área de texto, escreva `Bem-vindo(a)`.

![Journey Optimizer](./images/msg12.png)

Em seguida, clique em  **Contextafhankelijke kenmerken** e **Journey Orchestration**.

![ACOP](./images/jomsg3.png)

Clique em **Gebeurtenissen**.

![ACOP](./images/jomsg4.png)

Clique no nome do seu evento, que deve ser semelhante ao seguinte: **yourLastNameBeaconEntryEvent**.

![ACOP](./images/jomsg5.png)

Clique em **Context plaatsen**.

![ACOP](./images/jomsg6.png)

Clique em **Interactie tussen POI**.

![ACOP](./images/jomsg7.png)

Clique em **POI-details**.

![ACOP](./images/jomsg8.png)

Clique no **+** pictogram nr. **POI-naam**.
Em seguida, o seguinte será exibido. Clique em **Opslaan**.

![ACOP](./images/jomsg9.png)

Sua mensagem agora está pronta. Clique na seta no canto superior esquerdo para retornar à sua jornada.

![ACOP](./images/jomsg11.png)

Clique em **OK**.

![ACOP](./images/jomsg14.png)

## 3.3.2 Envie uma mensagem para uma tela

Como terceira etapa da jornada, você deve adicionar uma ação  **sendMessageToScreen**. Vá para o lado esquerdo da tela para **Handelingen**, selecione a ação **sendMessageToScreen** e arraste e solte a ação no terceiro nó da sua jornada. Em seguida, você verá a tela abaixo.

![ACOP](./images/jomsg15.png)

**sendMessageToScreen** é uma ação personalizada que irá publicar uma mensagem no **Endpoint** usado pela exibição na loja. A ação **sendMessageToScreen** espera que múltiplas variáveis sejam definidas. Você pode visualizar essas variáveis rolando para baixo até ver **Handelingsparameters**.

![ACOP](./images/jomsg16.png)

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

{style=&quot;table-layout:auto&quot;}

Para definir esses valores, clique no ícone **Bewerken**.

![ACOP](./images/jomsg17.png)

Em seguida, selecione **Geavanceerde modus**.

![ACOP](./images/jomsg18.png)

Em seguida, cole o valor com base na tabela acima. Clique em **OK**.

![ACOP](./images/jomsg19.png)

Repita esse processo para adicionar valores para cada campo.

>[!IMPORTANT]
>
>Para o campo ECID, há uma referência ao evento`yourLastNameBeaconEntryEvent`. Lembre-se de substituir  `yourLastName` pelo seu sobrenome .

O resultado final deve ser semelhante ao seguinte:

![ACOP](./images/jomsg20.png)

Rol para cima e clique em **OK**.

![ACOP](./images/jomsg21.png)

Je moet je reis nog steeds een naam geven. U kunt dat doen door op de knop **Eigenschappen** in de rechterbovenhoek van het scherm.

![ACOP](./images/journeyname.png)

Você pode insert o nome da jornada aqui. Gebruik `yourLastName - Beacon Entry Journey`. Clique em **OK** para salvar suas validações.

![ACOP](./images/journeyname1.png)

Agora você pode publicar sua jornada clicando **Publiceren**.

![ACOP](./images/publishjourney.png)

Clique em **Publiceren** novamente.

![ACOP](./images/publish1.png)

Você verá uma barra de confirmação verde informando que sua jornada agora está Publicada.

![ACOP](./images/published.png)

Sua jornada agora está ativa e pode ser acionada.

Você terminou este uitoefício.

Próxima etapa: [3.4 Teste sua jornada](./ex4.md)

[Retornar para Fluxo de Usuário 3](./uc3.md)

[Retornar para Todos os Módulos](../../overview.md)
