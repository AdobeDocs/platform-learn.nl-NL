---
title: Bootkamp - Real-time klantprofiel - Van onbekend naar bekend op de website - Brazilië
description: Bootkamp - Real-time klantprofiel - Van onbekend naar bekend op de website - Brazilië
jira: KT-5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
feature: Profiles
exl-id: 853a69d2-5dac-413d-bb40-ef29604a26ae
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# 1.1. Site van desconhecido ao conhecido em nosso

## Contexto

A Adobe Experience Platform desempenha um papel importante nessa jornada. Een plataforma é o cérebro da comunicação, of **ervaringssysteem van verslag**.

Plataforma é um ambiente em que a palavra cliente engloba mais do que clientes conhecidos. Ubezoekante desconhecido no site também é um cliente do ponto de vista da Plataforma e, como tal, todo o comportamento de um bezoekante desconhecido também é enviado à Plataforma. Graças a essa abordagem, quando esse bezoekante eventualmente se torna um cliente conhecido, uma marca também pode visualizar o que aconteceu antes daquele momento. Isso ajuda a partir de uma perspectiva de otimização de atribuição e experience ência.

## Fluxo da jornada do cliente

Toegang [ https://bootcamp.aepdemo.net ](https://bootcamp.aepdemo.net). De klemem **staat allen** toe.

![ DSN ](./images/web8.png)

Clique no ícone do logotipo da Adobe no canto superior esquerdo da tela para abrir o Visualizador de perfil.

![ Demo ](./images/pv1.png)

Verifique o chilel do Visualizador de perfil e no Perfil do cliente em temtempo real com of **como o identificador primário para este cliente que ainda é desconhecido.**

![ Demo ](./images/pv2.png)

Você também pode ver todos os Eventos de Erência coletados com base no comportamento do cliente. A lista está vazia no momento, mas isso mudará em breve.

![ Demo ](./images/pv3.png)

Heb toegang tot een opção de menu **Diensten van de Toepassing** e klique op product **Real-Time CDP**.

![ Demo ](./images/pv4.png)

Você verá a página de detalhes do produto. Em Evento de experience ncia do tipo **Mening van het Product** agora foi enviado para Adobe Experience Platform usando a implementação do Web SDK que você revisou no Módulo 1. Abra of pijnlijke Visualizador de perfil e verifieque seus **Gebeurtenissen van de Ervaring**.

![ Demo ](./images/pv5.png)

Heb toegang tot een opção de menu **Diensten van de Toepassing** e klique op product **Adobe Journey Optimizer**. Mais um Evento de experience ência foi enviado para a Adobe Experience Platform.

![ Demo ](./images/pv7.png)

Abra o pijnel Visualizador de perfil. Agora você verá 2 Eventos de experience ncia do tipo **Mening van het Product**. Embora o comportamento seja anônimo, cada clique é rastreado e armazenado na Adobe Experience Platform. Depois que o cliente anônimo se tornar conhecido, poderemos mesclar todo o comportamento anônimo automcamente ao perfil conhecido.

![ Demo ](./images/pv8.png)

Agora vamos analisar seu perfil de cliente e usar seu comportamento para personalizar sua experience ência do cliente no site.

Próxima etapa: [ 1.2 visualize seu próprio perfil de cliente em tempo real - UI ](./ex2.md)

[Retornar para Fluxo de Usuário 1](./uc1.md)

[Retornar para Todos os Módulos](../../overview.md)
