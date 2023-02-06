---
title: Bootkamp - Journey Optimizer Je reis en e-mailbericht maken - Brazilië
description: Bootkamp - Journey Optimizer Je reis en e-mailbericht maken - Brazilië
kt: 5342
audience: developer
doc-type: tutorial
activity: develop
source-git-commit: 9cc01c7d3018319137f915e103bce9dc39b0d472
workflow-type: tm+mt
source-wordcount: '984'
ht-degree: 3%

---

# 2.3 Crie sua jornada e mensagem de e-mail

Neste uitoefício, você irá configurar a jornada que precisa ser acionada quando alguém criar uma conta no site de demonstração.

Faça login no Adobe Journey Optimizer acessando a [Adobe Experience Cloud](https://experience.adobe.com). Clique em **Journey Optimizer**.

![ACOP](./images/acophome.png)

Você será redirecionado para visualização da **Home**  geen Journey Optimizer. Primeiro, verifieque se você está usando sandbox correto. O nome do sandbox que deve ser usado é `Bootcamp`. Para alternar de um sandbox para outro, clique em **Prod** Selecteer een sandbox of lista. Neste voorbeeld, o noome do sandbox é **Bootkamp**. Você estará na visualização da **Home** seu-sandbox `Bootcamp`.

![ACOP](./images/acoptriglp.png)

## 2.3.1 Crie a sua jornada

Geen menu à esquerda, klik op em **Reizen**. Em seguida, clique em **Reis maken** para criar uma nova jornada .

![ACOP](./images/createjourney.png)

Você verá uma tela de jornada vazia.

![ACOP](./images/journeyempty.png)

No uitoefício anterior, você criou um novo **Gebeurtenis**. Você nomeou o evento `yourLastNameAccountCreationEvent` e substituiu `yourLastName` pelo seu sobrenome . Este foi o resultado da criação do Evento:

![ACOP](./images/eventdone.png)

Agora vocdeve aanzienlijke este evento como o início desta Jornada. Você pode fazer isso indo para o lado esquerdo da tela e procurando pelo seu evento na lista de eventos.

![ACOP](./images/eventlist.png)

Selecione seu evento, arraste e solte o evento na tela de Jornada. Sua Jornada agora deve ser semelhante ao seguinte:

![ACOP](./images/journeyevent.png)

Como segunda etapa da jornada, você deve adicionar uma etapa curta de **Wachten**. Vá para o lado esquerdo da tela até a seção **Orchestratie** para enconr isso . Você usará atributos de perfil e precisará garantir que eles sejam preenchidos no Perfil do Cliente em tempo real.

![ACOP](./images/journeywait.png)

Sua jornada agora deve ser semelhante ao seguinte. Geen lado direito da tela você preca configurar o tempo de espera. Defina como 1 minuto. Isso dará bastante tempo para que os atributos do perfil estejam disponíveis após o disparo do evento.

![ACOP](./images/journeywait1.png)

Clique em **OK** para salvar suas validações.

Como terceira etapa da jornada, você deve adicionar uma ação **E-mail**. Vá para o lado esquerdo da tela para **Handelingen**, selecione a ação **E-mail** e arraste e solte a ação no segundo nó da sua jornada. Agora o seguinte será exibido.

![ACOP](./images/journeyactions.png)

Stel de **Categorie** tot **Marketing** en selecteer een e-mailoppervlak waarmee u e-mail kunt verzenden. In dit geval is het te selecteren e-mailoppervlak **E-mail**. Zorg ervoor dat de selectievakjes **Klik op e-mail** en **e-mail wordt geopend** zijn beide ingeschakeld.

Defina a **Categorie** como **Marketing** e selecione uma superfície de e-mail que permita o envio de e-mail. Nesse caso, een superfície e-mail een ser selecionada e-mail. Certifique-se de que as caixas de seleção **Klik op e-mail** e **e-mail wordt geopend** estejam marcadas.

![ACOP](./images/journeyactions1.png)

A próximo etapa é criar sua mensagem. Para isso, clique em **Inhoud bewerken**.

![ACOP](./images/journeyactions2.png)

## 2.3.2 Crie a sua mensagem

Para criar sua mensagem, clique em **Inhoud bewerken**.

![ACOP](./images/journeyactions2.png)

O seguinte será exibido.

![ACOP](./images/journeyactions3.png)

Clique no campo de texto **Onderwerpregel**.

![Journey Optimizer](./images/msg5.png)

Na área de texto, comece **Olá**

![Journey Optimizer](./images/msg6.png)

A linha de assunto ainda não está pronta. Em seguida, você preca trazer o token de personalização para o **Voornaam** que está armazenado em `profile.person.name.firstName`. Geen menu à esquerda, rol para baixo para enconr o elemento **Persoon** e clique na seta para ir um nível mais profundo.

![Journey Optimizer](./images/msg7.png)

Agora encontre o elemento **Volledige naam** e clique na seta para ir um nível mais profundo.

![Journey Optimizer](./images/msg8.png)

Por fim, localize to campo **Voornaam** e clique no símbolo **+**  ao lado dele. Você verá o token de personalização aparecer no campo de texto.

![Journey Optimizer](./images/msg9.png)

Em seguida, adicione of texto, **agradecemos a sua inscrição** Clique em Salvar. . Clique em **Opslaan**.

![Journey Optimizer](./images/msg10.png)

Então, você irá retornar para esta tela. Clique em **E-mailontwerper**  para criar o conteúdo do e-mail.

![Journey Optimizer](./images/msg11.png)

Na próxima tela, será solicitado que você forneça o conteúdo e-mail através de 3 métodos diferentes:

- **Ontwerpen vanaf nul**: Comece com uma tela em branco e use o editor WYSIWYG para arrastar e soltar a estrutura e os componentes de conteúdo para criar visualmente o conteúdo e-mail.
- **Uw eigen code schrijven**: Crie seu próprio modelo de e-mail codificando usando HTML
- **HTML importeren**: Importe um modelo HTML existente, que você poderá editar.

Clique em **HTML importeren**.

![Journey Optimizer](./images/msg12.png)

Arraste e solte o arquivo **mailtemplatebootkamp.html**, que você pode baixa [hier](../../assets/html/mailtemplatebootcamp.html.zip). Clique em Importar.

![Journey Optimizer](./images/msg13.png)

Você verá este modelo de e-mail padrão:

![Journey Optimizer](./images/msg14.png)

Vamos personalizar o e-mail. Clique ao lado do texto **Olá** e, em seguida, clique no ícone **Persoonlijkheid toevoegen**.

![Journey Optimizer](./images/msg35.png)

Em seguida, você preca trazer o token de personalização **Voornaam** que está armazenado em `profile.person.name.firstName`. Geen menu, lokaliseren naar element **Persoon**, faça uma busca detalhada no elemento **Volledige naam** e clique no ícone **+** para adicionar o campo **Voornaam** redacteur van de expressão.

Clique em **Opslaan**.

![Journey Optimizer](./images/msg36.png)

Agora você verá como campo de personalização foi adicionado ao seu texto.

![Journey Optimizer](./images/msg37.png)

Clique em **Opslaan** para salvar sua mensagem.

![Journey Optimizer](./images/msg55.png)

Retorne para o pijnel de mensagens clicando na seta ao lado do texto da linha de assunto no canto superior esquerdo.

![Journey Optimizer](./images/msg56.png)

Agora você concluiu a criação do seu e-mail de cadastro. Clique na seta no canto superior esquerdo para retornar à sua jornada.

![Journey Optimizer](./images/msg57.png)

Clique em **OK**.

![Journey Optimizer](./images/msg57a.png)

## 2.3.3 Publique a sua jornada

Você ainda precisa dar um Nome à sua jornada. Você pode fazer isso clicando no ícone **Eigenschappen** de superieure direito da tela is niet te vinden .

![ACOP](./images/journeyname.png)

Você ainda precisa dar um Nome à sua jornada. Você pode fazer isso clicando no ícone `yourLastName - Account Creation Journey`. Clique em **OK** para salvar as mudanças .

![ACOP](./images/journeyname1.png)

Agora você pode publicar sua jornada clicando **Publiceren**.

![ACOP](./images/publishjourney.png)

Clique em **Publiceren**  novamente.

![ACOP](./images/publish1.png)

Você verá uma barra de confirmação verde informando que sua jornada agora está Publicada.

![ACOP](./images/published.png)

Você terminou este uitoefício.

Próxima etapa: [2.4 Teste sua jornada](./ex4.md)

[Retornar para Fluxo de Usuário 2](./uc2.md)

[Retornar para Todos os Módulos](../../overview.md)