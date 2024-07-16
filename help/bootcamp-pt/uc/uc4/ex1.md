---
title: Bootkamp - Customer Journey Analytics - Customer Journey Analytics 101 - Brazilië
description: Bootkamp - Customer Journey Analytics - Customer Journey Analytics 101 - Brazilië
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
solution: Customer Journey Analytics
exl-id: 63933d9e-b774-483f-b547-188c77440595
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 0%

---

# 4.1 Customer Journey Analytics 101

## Objetivos

- Entenda o que é o CJA
- Entenda qual é of papel do CJA
- Entenda o workflow do CJA: da conexão de dados aos insights

## 4.1.1 O que é o Customer Journey Analytics?

O Customer Journey Analytics (CJA) fornece uma interface em que os times de Analytics, Negócios e Tecnologia conseguem unir todos os dados da Companihia e analisar a jornada cross channel (online e offline) do cliente de ponta a ponta. O CJA é capaz de fornecer contexto e clareza para essa jornada, trazendo uma visão acionável em cima das dificuldades no processo de conversão e possibilitando planejamento de experience ências relevant tes e personalizadas nos pontos marelevantes.

O CJA traz o Analysis Workspace conectado à Adobe Experience Platform. A Adobe Experience Platform é o cérebro da comunicação e da orquestração e, com o CJA, as marcas agora podem contextualizar e visualizar todos esses dados, para que as equipes de negócios e insights possam aprender com eles, analisando toda a jornada on line para off line do ente.

Zoals equipes de negócios e insights podem conversar com o CJA, fazer perguntas e obter respostas em tempo real com a interface do usuário de arrastar e soltar, apontar e clicar e fácil de usar do Analysis Workspace.

![ demo ](./images/cja-adv-analysis1.png)

## 4.1.2 Principesvantaggen

Os três princippais Benefícios para os clientes são:

- A condensidade de disponibilizar insights para todos (ou seja, democratizar o acesso aos dados).
- A condensidade de ver o cliente em uma jornada contextual (ou seja, os dados podem ser visualizados sequencialmente, abrangendo múltiplos canais on-line e off-line).
- A condensidade de aproveitar o poder dos dados sem que haja a necessidade (ou seja, permite que indivíduos usem dados para desbloquear insights e análises profundas para ativação de marketing).

## 4.1.3 # 4.1.3 Kleur of Customer Journey Analytics voor kleurkoppel?

O CJA não se destina a substituir um aplicativo de BI atual, como Power BI, Microstrategy, Locker ou Tableau. O objetivo desses aplicativos de BI é visualizar dados para criar beschéis corporativos para que todos em uma organização possam ver métricas importantes rapidamente. O objetivo do CJA é trazer poder de análise para as equipes de Marketing e Negócios, tornando-o uma ferramenta de análise obrigatória para essas pessoas



Tradicionalmente, os aplicativos de BI têm sido incapazes de permitir a verda deira inteligência do cliente:

- Eles não podem fazer atribuição e não fazem análises de jornada do cliente.
- Os aplicativos de BI precisam saber a pergunta com antecedência
- Als consultas interativas são limitadas pela estrutura do banco de dados
- Habilidades de SQL são necessary árias.
- Os aplicativos de BI não permitem que você pergunte o motivo de um acontecimento.
- Os aplicativos de BI não têm conexão direta com os pontos de contato do cliente.

Portanto, usuários de negócios e analistas chegam a becos sem saída quase imediatamente, tornando a análise cara, lenta, inflexível e desconectada dos sistemas de ação.

Com o CJA você pode ter uma visão completa da jornada do cliente, usando dados offline e online, com as ferramentas certas para reduzir o tempo de insight, tornando os usuários de negócios onafhankentes para entender por que algo aconteceu e como responder a isso.

![ demo ](./images/cja-use-case.png)

## 4.1.4 Compreenda o fluxo de trabalho do Customer Journey Analytics

Antes de iniciar os próximos uitoefícios, é essencial compender quais etapas são necessary árias para trazer dados da Adobe Experience Platform para o CJA para visualizá-los e obter algun inghts profundos. É o que chamamos de fluxo de trabalho do CJA. Vamos verificar:

![ demo ](./images/cja-work-flow.jpg)

Antes de iniciar as etapas acima, não se esqueça da etapa 0, que é compender os dados que estão disponíveis na Adobe Experience Platform.

**huisvuil binnen, huisvuil uit.** Você deve ter uma ideia clara de quais dados estão disponíveis e como os esquemas na Adobe Experience Platform são configurados. Compreender os dados que estão na Adobe Experience Platform facilitará as coisas, não só na parte de conexão de dados, mas também na hora de construir visualizações e fazer análises.

## 4.1.5 Etapa 0: Compreender esquemas e datasets da Adobe Experience Platform

Faça login na Adobe Experience Platform acessando a URL: [ https://experience.adobe.com/platform ](https://experience.adobe.com/platform).

Depois de fazer login, você irá acessar a página inicial da Adobe Experience Platform.

![ Ingestie van Gegevens ](../uc1/images/home.png)

Antes de continuar, você nauwkeurige um **zandbak**. O nome do sandbox a ser selecionado é ``Bootcamp`` . Você pode fazer isso clicando no ícone **[!UICONTROL Prod]** kan geen superieure direito da tela bereiken. Depois de selecionar o sandbox apropriado, você verá a tela mudando e agora você está em seu sandbox toegeado.

![ Ingestie van Gegevens ](../uc1/images/sb1.png)

Verifique esses schema&#39;s e datasets na Adobe Experience Platform.

| Gegevensset | Schema |
| ----------------- |-------------| 
| Demosysteem - Dataset voor gebeurtenissen voor website (Global v1.1) | Demosysteem - Gebeurtenisschema voor website (Global v1.1) |
| Het Systeem van de manifestatie - de Dataset van de Gebeurtenis voor het Centrum van de Vraag (Globale v1.1) | Het Systeem van de demonstratie - het Schema van de Gebeurtenis voor het Centrum van de Vraag (Globale v1.1) |
| Demosysteem - Dataset van de Gebeurtenis voor de Medewerkers van de Stem (Globale v1.1) | Demosysteem - Gebeurtenisschema voor spraakassistenten (Global v1.1) |

Certifique-se de ter verificado ao menos:

- Id&#39;s: CRMID, phoneNumber, ECID, email. Quais identidades são os identificadores primários, aquis são os identificadores secundários?

Você pode contrar os os identificadores abrindo um schema e observando object `_experienceplatform.identification.core` . Verifique aan schema [ demosysteem - het Schema van de Gebeurtenis voor Website (Globale v1.1) ](https://experience.adobe.com/platform/schema).

![ demo ](./images/identity.png)

- Onderzoek aan objeto de comércio dentro doet schema [ het Systeem van de Demo - het Schema van de Gebeurtenis voor Website (Globale v1.1) ](https://experience.adobe.com/platform/schema).

![ demo ](./images/commerce.png)

- Visualiseer todos os [ datasets ](https://experience.adobe.com/platform/dataset/browse?limit=50&amp;page=1&amp;sortDescending=1&amp;sortField=created) e verifieque os dados

Agora você está pronto para começar a usar a interface do usuário do Customer Journey Analytics.

Próxima etapa: [ 4.2 Conecte datasets da Adobe Experience Platform geen Customer Journey Analytics ](./ex2.md)

[Retornar para Fluxo de Usuário 4](./uc4.md)

[Retornar para Todos os Módulos](../../overview.md)
