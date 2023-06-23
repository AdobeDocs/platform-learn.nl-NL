---
title: Bootkamp - Customer Journey Analytics - Connect Adobe Experience Platform-gegevenssets in Customer Journey Analytics - Brazilië
description: Bootkamp - Customer Journey Analytics - Connect Adobe Experience Platform-gegevenssets in Customer Journey Analytics - Brazilië
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: 51078fca-f234-4e50-96ba-ee7f5e286869
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 0%

---

# 4.2 Conecte datasets da Adobe Experience Platform no Customer Journey Analytics

## Objetivos

- Compreenda a UI da conexão de dados
- Traga os dados da Adobe Experience Platform para o CJA
- Entenda a ID da pessoa e a compilação de dados
- Aprenda o conceito de streaming de dados no Customer Journey

## 4.2.1 Conexão

Acesse [analytics.adobe.com](https://analytics.adobe.com) para acessar o Customer Journey Analytics.

Na página inicial do Customer Journey Analytics, acesse **Verbindingen**.

![demo](./images/cja2.png)

Aqui você pode ver todas as diferentes conexões feitas entre o CJA e a Plataforma. Essas conexões têm o mesmo objetivo dos conjuntos de relatórios no Adobe Analytics. Geen entanto, een coleta dos dados é completamente diferente. Todos os dados vêm de datasets da Adobe Experience Platform.

Vamos criar sua primeira conexão. Clique em **Nieuwe verbinding maken**.

![demo](./images/cja4.png)

Você verá a UI **Verbinding maken** UI.

![demo](./images/cja5.png)

Agora você pode dar um nome à sua conexão.

Este modelo de nomenclatura gebruiken: `yourLastName – Omnichannel Data Connection`.

Voorbeeld: `vangeluw - Omnichannel Data Connection`

Você também deve selecionar o sandbox correto para usar. Geen menusandbox, selectiestandaard tweede sandbox, klokkenluider `Bootcamp`. Neste exemplo, o sandbox a ser usado é o **Bootkamp**. E você também deve definir **Gemiddeld aantal dagelijkse gebeurtenissen** tot **minder dan 1 miljoen**.

![demo](./images/cjasb.png)

Após selecionar seu sandbox, você pode começar a adicionar datasets a esta conexão. Clique em **Gegevenssets toevoegen**.

![demo](./images/cjasb1.png)

## 4.2.2 Selectieve gegevenssets da Adobe Experience Platform

Voorbeeld van gegevensset `Demo System - Event Dataset for Website (Global v1.1)`. Clique em **+** para adicionar o dataset a esta conexão .

![demo](./images/cja7.png)

Agora pesquise e marque as caixas de seleção `Demo System - Event Dataset for Voice Assistants (Global v1.1)` en `Demo System - Event Dataset for Call Center (Global v1.1)`.

Em seguida, você verá a tela abaixo. Clique em **Volgende**.

![demo](./images/cja9.png)

## 4.2.3 ID da pessoa e compilação de dados

### ID da pessoa

O objetivo agora é juntar esses datasets. Para cada dataset selecionado, você verá um campo chamado **Persoon-id**. Cada dataset tem seu próprio campo de ID de pessoa.

![demo](./images/cja11.png)

Como você pode ver, a maioria deles tem o ID da pessoa selecionado automcamente. Isso ocorre porque um identificador principal é selecionado em cada esquema na Adobe Experience Platform. Como exemplo, aqui está o esquema para `Demo System - Event Schema for Call Center (Global v1.1)`, onde você pode ver que o Identificador Primário está definido como `phoneNumber`.

![demo](./images/cja13.png)

Geen entanto, você ainda pode influenciar qual identificador será usado para compar datasets para sua conexão. Você pode usar qualquer identificador configurado no esquema vinculado ao seu dataset. Clique no menu Susenso para explorar os IDs disponíveis em cada dataset.

![demo](./images/cja14.png)

Conforme mencionado, você pode definir diferentes IDs de pessoa para cada dataset. Isso permite reunir diferentes datasets de múltiplas origens no CJA. Stelt u zich eens voor dat trazer NPS ou dados de pesquisa que seriam muito interessantes e úteis para compender o context to e o motivo de um acontecimento.

O nome do campo ID da pessoa não é importante, desde que o valor nos campos ID da pessoa corresponda. Digamos que temos `email` em um dataset e `emailAddress` em outro dataset definido como ID da pessoa. Se `delaigle@adobe.com` tiver o mesmo valor para o campo ID da pessoa em ambos os datasets, o CJA poderá compilar os dados.

Atualmente, existem algumas outras limitações, como compilar o comportamento anônimo para conhecido. Raadpleeg het onderwerp als perguntas frequent aqui: [Veelgestelde vragen](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-faq.html).


### Compilando os dados usando o ID da pessoa

Agora que você uitgebreide o conceito de compilar datasets usando o ID da pessoa, vamos escolher `email` gegevensset van como ID da pessoa para cada.

![demo](./images/cja15.png)

Acesse cada dataset para atualizar o ID da pessoa.

![demo](./images/cja12a.png)

Agora preencha o campo ID da pessoa escolhendo `email` na lista Susensa.

![demo](./images/cja17.png)

Depois de compilar os três datasets, estamos prontos para continuar.

| gegevensset | Persoon-id |
| ----------------- |-------------| 
| Demosysteem - Dataset voor gebeurtenissen voor website (Global v1.1) | email |
| Demosysteem - Dataset van de Gebeurtenis voor de Medewerkers van de Stem (Globale v1.1) | email |
| Het Systeem van de manifestatie - de Dataset van de Gebeurtenis voor het Centrum van de Vraag (Globale v1.1) | email |

Você também precisa garantir que, para cada dataset, essas opções estejam habilitadas:

- Importar todos os novos dados
- Preencher todos os dados existentes
- Preencher tipo de fonte de dados com &quot;Others&quot;
- Preencher a describe ção com o mesmo nome do Dataset

Clique em **Gegevenssets toevoegen**.

![demo](./images/cja16.png)

Clique em **Opslaan** e vá para o próximo uitoefício. Depois de criar sua **Verbinding**, pode levar algumas horas até que seus dados estejam disponíveis no CJA.

![demo](./images/cja20.png)

Próxima etapa: [4.3 Crie uma Visualização de Dados](./ex3.md)

[Retornar para Fluxo de Usuário 4](./uc4.md)

[Retornar para Todos os Módulos](./../../overview.md)
