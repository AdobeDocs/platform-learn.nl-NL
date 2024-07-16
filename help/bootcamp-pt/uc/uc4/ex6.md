---
title: Bootkamp - Customer Journey Analytics - Van inzichten naar actie - Brazilië
description: Bootkamp - Customer Journey Analytics - Van inzichten naar actie - Brazilië
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
solution: Customer Journey Analytics
feature-set: Customer Journey Analytics
feature: Audiences
exl-id: 28b87e21-3168-447e-9a93-a6ae7e969657
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# 4.6 Dos insights à ação

## Objetivos

- Entenda como criar um público com base em uma visão coletada no Customer Journey Analytics
- Gebruik esse público geen CDP em tempo real op Adobe Journey Optimizer

## 4.6.1 Crie uma audiência e publique-a

Em seu project, você criou um filtro chamado **e conseguiu visualizar a quantidade de usuários que tiveram suas ligações ao call center classificadas como** positivas **.** Agora, você poderá criar um segmento com esses usuários e ativação-los em jornadas ou em canais de comunicação.

O primeiro passo é: Geen pijnlijke criado no último uitoefício, selecione a linha **1. Het Voorkomen van de vraag - Positief**, klique com o botão direito de seu muis e selecione a opção **leidt tot publiek van selectie**:

![ demo ](./images/aud1.png)

Em seguida, dê um nome para sua audiência seguindo o modelo **yourLastName - de publieksvraag van de cia voelt positief**:

![ demo ](./images/aud2.png)

Nota que é bezível ter um preview da audiência que está sendo criada:

![ demo ](./images/aud3.png)

Para finalizar, klique em **Publicar**:

![ demo ](./images/aud4.png)

## 4.6.2 Gebruik sua audiência como parte de um segmento

Voltando para Adobe Experience Platform, vá em **Segments > Browse** e você conseguirá visualizar o seu segmento criado no CJA pronto e disponível para ser usado nas suas ativações e jornadas!

![ demo ](./images/aud5.png)

Vamos agora usar esse segmento em uma ativação no Facebook e em uma jornada do cliente!

## 4.6.3 Gebruik seu segmento na Real-Time CDP em tempo real

Na Adobe Experience Platform, vá em **Segmenten > doorbladert** e neemt een audiência que você criou op CJA op:

![ demo ](./images/aud6.png)

De klem op seu segmento e, em seguida, klikem **activeert aan Bestemming**:

![ demo ](./images/aud7.png)

Selecteer een bestemmings chamada bootkamp-facebook e, em seguida, clique em Next:

![ demo ](./images/aud8.png)

Em seguida, clique em Next novamente:

![ demo ](./images/aud9.png)

Selecione a opção **Oorsprong van uw publiek** e defina como **direct van klanten** e clique em daarna:

![ demo ](./images/aud10.png)

Por fim, na página **het 1} klikem Einde van het Overzicht {!**

![ demo ](./images/aud11.png)

Pronto! Agora o seu segmento está vinculado aos públicos personalizados do Facebook.
Agora, vamos utilizar esse segmento no AJO!

## 4.6.4 Gebruik volgende segmento&#39;s op Adobe Journey Optimizer

Na interface da Adobe Experience Platform klique em Journey Optimizer e, em seguida, geen menu laterale esquerdo, klikem **de Schijven** e komt een kritieke uma jornada kliando em **creëren Weg**:

![ demo ](./images/aud20.png)

![ demo ](./images/aud21.png)

![ demo ](./images/aud22.png)

Em seguida, geen menu laterale esquerdo, em Evtos, selecione **e arraste-o até a jornada de Kwalificatie van het Segment**:

![ demo ](./images/aud23.png)

Em seguida, em **het Clique em van het Segment** **para selecionar um segmento uitgeven:**

![ demo ](./images/aud24.png)

Selecione a audiência que você criou no CJA e clique em **sparen**:

![ demo ](./images/aud25.png)

Pronto! Een partir daí você pode criar uma jornada para clients que se kwalificficam para esse segmento!

[Ga terug naar Gebruikersstroom 4](./uc4.md)

[Voltar para todos os módulos](./../../overview.md)
