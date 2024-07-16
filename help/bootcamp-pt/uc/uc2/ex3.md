---
title: Bootkamp - Journey Optimizer Je reis en e-mailbericht maken - Brazilië
description: Bootkamp - Journey Optimizer Je reis en e-mailbericht maken - Brazilië
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
solution: Journey Optimizer
feature-set: Journey Optimizer
feature: Journeys
exl-id: d486d1aa-7b8e-4301-91e6-4c84fba0c72a
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 0%

---

# 2.3 Crie sua jornada e mensagem de e-mail

Neste uitoefício, você irá configurar a jornada que precisa ser acionada quando alguém criar uma conta no site de demonstração.

Faça login op Adobe Journey Optimizer toegang tot a [ Adobe Experience Cloud ](https://experience.adobe.com). Clique em **Journey Optimizer**.

![ ACOP ](./images/acophome.png)

Você será redirecionado para a visualização da **Huis** geen Journey Optimizer. Primeiro, verifieque se você está usando sandbox correto. O nome do sandbox que deve ser usado é `Bootcamp` . Para alternar de um sandbox para outro, klique em **Prod** e selecione aan zandbak na lista. Neste voorbeeldig, o nome do zandbak é **Bootkamp**. Você estará na visualização da **Huis** do seu zandbak `Bootcamp`.

![ ACOP ](./images/acoptriglp.png)

## 2.3.1 Crie a sua jornada

Geen menu à esquerda, klikem **Reizen**. Em seguida, kliek em **creeer de 1} parabijis van de Reis { jornada.**

![ ACOP ](./images/createjourney.png)

Você verá uma tela de jornada vazia.

![ ACOP ](./images/journeyempty.png)

Geen uitoefício anterior, você criou um novo **Gebeurtenis**. Você nomeou o evento `seuSobrenomeAccountCreationEvent` e substituiu `seuSobrenome` pelo seu sobrenome. Este foi o resultado da criação do Evento:

![ ACOP ](./images/eventdone.png)

Agora vocdeve aanzienlijke este evento como o início desta Jornada. Você pode fazer isso indo para o lado esquerdo da tela e procurando pelo seu evento na lista de eventos.

![ ACOP ](./images/eventlist.png)

Selecione seu evento, arraste e solte o evento na tela de Jornada. Sua Jornada agora deve ser semelhante ao seguinte:

![ ACOP ](./images/journeyevent.png)

Como segunda etapa da jornada, você deve adicionar uma etapa curta de **Wacht**. Vá para o lado esquerdo da tela até a seção **Orchestration** para enconr isso. Você usará atributos de perfil e precisará garantir que eles sejam preenchidos no Perfil do Cliente em tempo real.

![ ACOP ](./images/journeywait.png)

Sua jornada agora deve ser semelhante ao seguinte. Geen lado direito da tela você preca configurar o tempo de espera. Defina como 1 minuto. Isso dará bastante tempo para que os atributos do perfil estejam disponíveis após o disparo do evento.

![ ACOP ](./images/journeywait1.png)

Clique em **O.K.** para salvar suas alternatieve ações.

Como terceira etapa da jornada, você deve adicionar uma ação **E-mail**. Vá para o lado esquerdo da tela para **Acties**, verkione a ação **E-mail** e arraste e solte a ação no segundo nó da sua jornada. Agora o seguinte será exibido.

![ ACOP ](./images/journeyactions.png)

Definieer a **Categorie** como **marketing** e-mailoppervlakte van de gebruikersinterface **e-mail** toestemming om e-mail te envio. Neescaso, a **e-mailoppervlakte** e-mail van de gebruiker selecteionada e-mail. Certifique-se de que als caixas de seleção **klikt op e-mail** e **e-mail opent** estejam marcadas.

![ ACOP ](./images/journeyactions1.png)

A próximo etapa é criar sua mensagem. Para isso, klikem **geeft inhoud** uit.

![ ACOP ](./images/journeyactions2.png)

## 2.3.2 Crie a sua mensagem

Para criar sua mensagem, klikem **geeft inhoud** uit.

![ ACOP ](./images/journeyactions2.png)

O seguinte será exibido.

![ ACOP ](./images/journeyactions3.png)

De klem op campo de texto **Onderwerpregel**.

![ Journey Optimizer ](./images/msg5.png)

Na área de texto, comece **Olá**

![ Journey Optimizer ](./images/msg6.png)

A linha de assunto ainda não está pronta. Em seguida, você preca trazer o token de personalização para o **First name** que está armazenado em `profile.person.name.firstName`. Geen menu à esquerda, rolpara baixo para encontrar o elemento **Peron** e clique na seta para visualizar mais campos

![ Journey Optimizer ](./images/msg7.png)

Agora encontre aan elemento **Volledige naam** e clique na seta para visualizar mais campos.

![ Journey Optimizer ](./images/msg8.png)

Por fim, lokaliseer aan campo **Voornaam** e clique op símbolo **+** ao lado dele. Você verá o token de personalização aparecer no campo de texto.

![ Journey Optimizer ](./images/msg9.png)

Em seguida, adicione o texto, **agradecemos a sua inscrição!**. Clique em **sparen**.

![ Journey Optimizer ](./images/msg10.png)

Então, você irá retornar para esta tela. Clique em **e-mail Designer** para kriar aan conteúdo e-mail.

![ Journey Optimizer ](./images/msg11.png)

Na próxima tela, será solicitado que você forneça o conteúdo e-mail através de 3 métodos diferentes:

- **Ontwerp van kras**: Comece com uma tela em branco e use of redacteur WYSIWYG para arrastar e soltar a estrutura e os componentes de conteúdo para criar visualmente o conteúdo e-mail.
- **Code uw eigen**: Crie seu próprio modelo de e-mail codificando usando HTML
- **de HTML van de Invoer**: Importe um modelo HTML existente, que você poderá editar.

Clique em **de HTML van de Invoer**.

![ Journey Optimizer ](./images/msg12.png)

Arraste e solte aan arquivo **mailtemplatebootkamp.html**, de duidelijke você pode baixa [ aqui ](../../assets/html/mailtemplatebootcamp.html.zip). Clique em Importar

![ Journey Optimizer ](./images/msg13.png)

Você verá este modelo de e-mail padrão:

![ Journey Optimizer ](./images/msg14.png)

Vamos personalizar o e-mail. Clique ao lado doet texto **Olá** e, em seguida, klique no ícone **toevoegen Personalization**.

![ Journey Optimizer ](./images/msg35.png)

Em seguida, você preca trazer of token de personalização **Voornaam** que está armazenado em `profile.person.name.firstName`. Geen menu, lokaliseer aan elemento **Persoon**, faça uma busca detalhada geen element **Volledige naam** e clique no ícone **+** para adicionar aan campo **Voornaam** redacteur.

Clique em **sparen**.

![ Journey Optimizer ](./images/msg36.png)

Agora você verá como campo de personalização foi adicionado ao seu texto.

![ Journey Optimizer ](./images/msg37.png)

Clique em **sparen** para salvar sua mensagem.

![ Journey Optimizer ](./images/msg55.png)

Retorne para o pijnel de mensagens clicando na seta ao lado do texto da linha de assunto no canto superior esquerdo.

![ Journey Optimizer ](./images/msg56.png)

Agora você concluiu a criação do seu e-mail de cadastro. Clique na seta no canto superior esquerdo para retornar à sua jornada.

![ Journey Optimizer ](./images/msg57.png)

Clique em **OK**.

![ Journey Optimizer ](./images/msg57a.png)

## 2.3.3 Publique a sua jornada

Você ainda precisa dar um Nome à sua jornada. Você pode fazer isso clicando no ícone **Eigenschappen** kan geen superieure direito da tela.

![ ACOP ](./images/journeyname.png)

Você pode fazer is dus clicand o no item click no item &quot;Name&quot; e insert to seguinte nome `yourLastName - Account Creation Journey`. De klikem **O.K.** para salvar als mudanças.

![ ACOP ](./images/journeyname1.png)

Agora você pode publicar sua jornada clicando em **Publish**.

![ ACOP ](./images/publishjourney.png)

Clique em **Publish** novamente.

![ ACOP ](./images/publish1.png)

Você verá uma barra de confirmação verde informando que sua jornada agora está Publicada.

![ ACOP ](./images/published.png)

Você terminou este uitoefício.

Próxima etapa: [ 2.4 Teste sua jornada ](./ex4.md)

[Retornar para Fluxo de Usuário 2](./uc2.md)

[Retornar para Todos os Módulos](../../overview.md)
