---
title: Bootkamp - Customer Journey Analytics - Van inzichten tot actie - Brazilië
description: Bootkamp - Customer Journey Analytics - Van inzichten tot actie - Brazilië
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 28b87e21-3168-447e-9a93-a6ae7e969657
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# 4.6 Dos insights à ação

## Objetivos

- Entenda como criar um público com base em uma visão coletada no Customer Journey Analytics
- Gebruik esse público geen CDP em tempo real op Adobe Journey Optimizer

## 4.6.1 Crie uma audiência e publique-a

Em seu projeto, você criou um filtro chamado **Bellen** e conseguiu visualizar a quantidade de usuários que tiveram suas ligações ao call center classificadas como **positiva**. Agora, você poderá criar um segmento com esses usuários e ativação-los em jornadas ou em canais de comunicação.

O primeiro passo é: Geen pijnlijke criado no último uitoefício, selecione a linha **1. Bellen - Positief**, clique com o botão direito de seu mouse e selecione a opção **publiek maken van selectie**:

![demo](./images/aud1.png)

Em seguida, dê um nome para sua audiência seguindo o modelo **yourLastName - cia publiek belt positief**:

![demo](./images/aud2.png)

Nota que é bezível ter um preview da audiência que está sendo criada:

![demo](./images/aud3.png)

Para finalizar, clique em **Publicar**:

![demo](./images/aud4.png)

## 4.6.2 Gebruik sua audiência como parte de um segmento

Voltando para Adobe Experience Platform, vá em **Segmenten > Bladeren** e você conseguirá visualizar o seu segmento criado no CJA pronto e disponível para ser usado nas suas ativações e jornadas!

![demo](./images/aud5.png)

Vamos agora usar esse segmento em uma ativação no Facebook e em uma jornada do cliente!

## 4.6.3 Gebruik seu segmento na Real-Time CDP em tempo real

Na Adobe Experience Platform, vá em **Segmenten > Bladeren** e encontre a audiência que você criou no CJA:

![demo](./images/aud6.png)

Clique no seu segmento e, em seguida, clique em **Activeren naar doel**:

![demo](./images/aud7.png)

Selecteer een bestemmings chamada bootkamp-facebook e, em seguida, clique em Next:

![demo](./images/aud8.png)

Em seguida, clique em Next novamente:

![demo](./images/aud9.png)

Selecione a opção **Oorsprong van uw publiek** e defina como **Direct van klanten** e clique em Next:

![demo](./images/aud10.png)

Por fim, na página **Controleren** clique em Finish!

![demo](./images/aud11.png)

Pronto! Agora o seu segmento está vinculado aos públicos personalizados do Facebook.
Agora, vamos utilizar esse segmento no AJO!

## 4.6.4 Gebruik volgende segmento&#39;s op Adobe Journey Optimizer

Na interface da Adobe Experience Platform clique em Journey Optimizer e, em seguida, no menu laterale esquerdo, clique em **Reizen** jornada clicando em **Reis maken**:

![demo](./images/aud20.png)

![demo](./images/aud21.png)

![demo](./images/aud22.png)

Em seguida, no menu laterale esquerdo, em Evtos, selecione **Segmentkwalificatie** e arraste-o até a jornada:

![demo](./images/aud23.png)

Em seguida, em **Segment** clique em **Bewerken** para selecionar um segmento:

![demo](./images/aud24.png)

Selecione a audiência que você criou no CJA e clique em **Opslaan**:

![demo](./images/aud25.png)

Pronto! Een partir daí você pode criar uma jornada para clients que se kwalificficam para esse segmento!

[Ga terug naar Gebruikersstroom 4](./uc4.md)

[Voltar para todos os módulos](./../../overview.md)
