---
title: Bootkamp - Customer Journey Analytics - Visualisatie met Customer Journey Analytics - Brazilië
description: Bootkamp - Customer Journey Analytics - Visualisatie met Customer Journey Analytics - Brazilië
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
solution: Customer Journey Analytics
feature-set: Customer Journey Analytics
feature: Visualizations
exl-id: eb5eac54-22d8-428b-acac-16570f75085e
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '1586'
ht-degree: 0%

---

# 4.5 Visualização usando Customer Journey Analytics

## Objetivos

- Entenda UI do Analysis Workspace
- Conheça algun recursos que tornam o Analysis Workspace tão diferente.
- Aprenda a analisar no CJA usando Analysis Workspace

## Contexto

Neste uitoefício, você usará o Analysis Workspace no CJA para analisar visualizações de produtos, funis de produtos, rotatividade, enz.

Vamos usar o projeto que você criou em  [4.4 Preparação de dados no Analysis Workspace](./ex4.md), então acesse [https://analytics.adobe.com](https://analytics.adobe.com).

![demo](./images/prohome.png)

Abra seu project `yourLastName - Omnichannel Analysis`.

Com seu project aberto e Visualização de dados `yourLastName - Omnichannel Analysis` selecionado, você está pronto para começar a construir suas primeiras visualizações.

![demo](./images/prodataView1.png)

## Quantas visualizações de produtos temos diariamente

Em primeiro lugar, precisamos selecionar as datas certas para analisar os dados. Acesse o menu Susenso do calendário no lado direito da tela. Clique nele e selecione o intervalo de datas aplicável.

>[!IMPORTANT]
>
>Selecione um intervalo de datas como **Deze week** ou **Deze maand**. Os dados disponíveis mais recentes foram absorvidos em 19 de setembro de 2022.

![demo](./images/pro1.png)
No menu do lado esquerdo (área de componentes), encontre as métricas calculadas **Productweergaven**. Selecione-as e arraste e solte na tela, no canto superior direito da tabela de forma livre.

![demo](./images/pro2.png)

Automaticamente a dimensão **Dag** será adicionada para criar sua primeira tabela . Agora você pode ver sua pergunta respondida imediatamente.

![demo](./images/pro3.png)

Em seguida, clique com o botão direito do mouse no resumo da métrica.

![demo](./images/pro4.png)

Clique em **Visualiseren** e selecione **Lijn** como visualização.

![demo](./images/pro5.png)

Você verá as suas visualizações de produto por dia.

![demo](./images/pro6.png)

Você podvarium o escopo de tempo para o dia clicando em **Instellingen** na visualização.

![demo](./images/pro7.png)

Clique no ponto ao lado de **Lijn** e **De gegevensbron beheren**.

![demo](./images/pro7a.png)

Em seguida, clique em **Selectie vergrendelen** e selecione **Geselecteerde items** para bloquear esta visualização para que ela sempre exiba uma linha do tempo de Visualizações de produtos.

![demo](./images/pro7b.png)

## 5 produtos mais vistos

Quais são os 5 produtos mais vistos?

Lembre-se de salvar o projeto de tempos em tempos.

| OS | Korte snede |
| ----------------- |-------------| 
| Windows | Control + S |
| Mac | Command + S |

Vamos começar a enconr os 5 produtos mais vistos. Geen menu do lado esquerdo, encontre o Nome do produto - Dimensão.

![demo](./images/pro8.png)

Agora arraste e solte **Productnaam** para substituir a dimensão **Dag**:

Este será o resultaatado.

![demo](./images/pro10a.png)

Em seguida, tente dividir um dos produtos por Nome da marca. Pesquise **brandName** e arraste para baixo do primeiro nome do produto.

![demo](./images/pro13.png)

Em seguida, faça um detalhamento usando o Agente de usuário. Pesquise **Gebruikersagent** e arraste-o para baixo do nome da marca.

![demo](./images/pro15.png)

Em seguida, será exibida a tela abaixo:

![demo](./images/pro15a.png)

Por fim, você pode adicionar mais visualizações. No lado esquerdo, em visualizações, pesquise `Donut`. Pegue `Donut`, arraste e solte na tela sob a visualização **Lijn** 

![demo](./images/pro18.png)

Selecteer vervolgens in de tabel de eerste 5 **Gebruikersagent**  rijen uit de ineenstorting die we onder **Google Pixel XL 32 GB zwarte smartphone** > **Citi Signal**. Houd tijdens het selecteren van de vijf rijen de knop **CTRL** (in Windows) of de knop **Opdracht** (op Mac).

Em seguida, na Tabela, selecione as primeiras 5 linhas de **Gebruikersagent** do detalhamento que fizemos em **Google Pixel XL 32 GB zwarte smartphone** > **Citi Signal**. Ao selecionar as 5 linhas, segmento botão **CTRL** (geen Windows) u o botão **Opdracht** (geen Mac).

![demo](./images/pro20.png)

Você verá o gráfico de donut aarttaal:

![demo](./images/pro21.png)

Você pode até adaptar o design para ser mais legível, tornando o gráfico de **Lijn** e o gráfico de **Donut** um pouco menor para que sejam exibidos lado a lado:

![demo](./images/pro22.png)

Clique no ponto ao lado de *Donut** para **De gegevensbron beheren**. Em seguida, clique em **Selectie vergrendelen** para bloquear essa visualização para que ela sempre exiba uma linha do tempo de Visualizações de produto.

![demo](./images/pro22b.png)

Saiba mais sobre visualizações usando o Analysis Workspace em:

- [https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/freeform-analysis-visualizations.html](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/freeform-analysis-visualizations.html)
- [https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/t-sync-visualization.html](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/visualizations/t-sync-visualization.html)

## Funil de interação do produto, da visualização à compra

Existem muitas formas de resolver esta questão. Uma delas é usar o Tipo de Interação de Produto e usá-lo em uma tabela de formato livre. Outra forma é usar uma **Vallout Visualisatie**. Vamos usar o último, pois queremos visualizar e analisar ao mesmo tempo.

Feche o pijnel atual clicando aqui:

![demo](./images/pro23.png)

Agora adicione um novo chilel em branco clicando **+ Leeg deelvenster toevoegen**.

![demo](./images/pro24.png)

Clique na visualização de **Fallout**.

![demo](./images/pro25.png)

Selecione o mesmo intervalo de datas do uitoefício anterior.

![demo](./images/prodatef.png)

Em seguida, você verá:

![demo](./images/prodatefa.png)

Omgaan met een dimensie **Type gebeurtenis** nos componentes no lado esquerdo:

![demo](./images/pro26.png)

Clique na seta para abrir a dimensão:

![demo](./images/pro27.png)

Você verá todos os Tipos de eventos disponíveis.

![demo](./images/pro28.png)

Item selecteren **commerce.productViews** e arraste e solte-o no campo **Aanraakpunt toevoegen** dentro da **Vallout Visualisatie**.

![demo](./images/pro29.png)

Faça o mesmo com **commerce.productListAdds** en **commerce.purchase** e solte-os no campo **Aanraakpunt toevoegen** dentro da  **Vallout Visualisatie**. Sua visualização agora deve ser semelhante ao seguinte:

![demo](./images/props1.png)

Você pode fazer muitas coisas aqui. Alweren: vergelijkar ao longo do tempo , vergelijkar cada passo por dispositivo ou comparar por fidelidade . Geen entanto, se quisermos analisar coisas interessantes como porque os clientes não compram depois de adicionar um item ao carrinho, podemos usar a melhor ferramenta do CJA: kliar com o botão direito.

Clique com o botão direito do mouse no touchpoint **commerce.productListAdds**. Em seguida, clique em **Brainstormfallout bij dit aanraakpunt**.

![demo](./images/pro32.png)

Uma nova tabela de formato livre será criada para analisar o que as pessoas fizeram se não compraram.

![demo](./images/pro33.png)

Altere **Type gebeurtenis** door **Paginanaam**, na nova tabela de formato livre, para ver em quais páginas eles estão indo, em vez da Página de confirmação de compra.

![demo](./images/pro34.png)

## O que as pessoas fazem no site antes de acessar a página Cancelar serviço?

Novamente, há muitas formas de realizar essa análise. Vamos usar a análise de fluxo para iniciar parte da descoberta.

Feche o pijnel atual clicando aqui:

![demo](./images/pro0.png)

Agora adicione um novo chilel em branco clicando **+ Leeg deelvenster toevoegen**.

![demo](./images/pro0a.png)

Clique na visualização **Stroom**.

![demo](./images/pro35.png)

Em seguida, será exibido:

![demo](./images/pro351.png)

Selecione o mesmo intervalo de datas do uitoefício anterior.

![demo](./images/pro0b.png)

Omgaan met een dimensie **Paginanaam** nos componentes no lado esquerdo:

![demo](./images/pro36.png)

Clique na seta para abrir a dimensão:

![demo](./images/pro37.png)

Você encontrará todas páginas vistas. Encontre nome da página: **Service annuleren**.
Arraste e solte **Service annuleren** Na Visualização de fluxo no campo do meio:

![demo](./images/pro38.png)

Em seguida, será exibido:

![demo](./images/pro40.png)

Vamos agora analisar se os clientes que bezoekaram a página C **Service annuleren** geen van de locaties também ligaram para om centre e qual foi o resultado te bellen .

Nas dimensões, retorne e encontre Tipo de interação de chamada. Arraste e solte **Type oproepinteractie** para substituir a primeira interação à direita em **Stroomvisualisatie**.

![demo](./images/pro43.png)

Agora você visualiza o ticket de suporte dos clients que ligaram para a central de atendimento depois de bezoekar a página **Service annuleren**.

![demo](./images/pro44.png)

Em seguida, nas dimensões, procureur **Aanroepfunctie**. Arraste e solte para substituir a primeira interação à direita na visualização de fluxo.

![demo](./images/pro46.png)

Em seguida, será exibido:

![demo](./images/flow.png)

Compode ver, executamos uma análise omnichannel usando a visualização de fluxo. Graças a isso, descobrimos que algun clientes que estavam pensando em cancelar o serviço tiveram uma avaliação positiva depois de ligar para o call center. Talvez tenhamos mudado de ideia com uma promoção?

## Qual é o desempenho dos clientes com um contato de Call centre Positivo em relação aos princippais KPIs?

Primeiramente, vamos segmentar os dados para obter apenas usuários com chamadas **positief**. Geen CJA, os Segmentos são chamados de Filtros. Acesse para filtros na área de componentes (no lado esquerdo) e clique em **+**.

![demo](./images/pro58.png)

Dentro do Construtor de filtro, dê um nome ao filtro

| Naam | Beschrijving |
| ----------------- |-------------| 
| Bellen - Positief | Bellen - Positief |

![demo](./images/pro47.png)

nrs-componenten (dentro do Construtor de filtro), encontrol **Aanroepfunctie** e arraste e solte na Definição do constructor de filtro.

![demo](./images/pro48.png)

Agora selecione **positief** comovalor para o filtro.

![demo](./images/pro49.png)

Altere o escopo para o nível **Persoon**.

![demo](./images/pro50.png)

Para finalizar, basta clicar em **Opslaan**.

![demo](./images/pro51.png)

Então, você irá retornar para esta tela. Se ainda não retornou, feche o pijnel anterior.

![demo](./images/pro0c.png)

Agora adicione um novo chilel em branco clicando **+ Leeg deelvenster toevoegen**.

![demo](./images/pro24c.png)

Selecione o mesmo intervalo de datas do uitoefício anterior.

![demo](./images/pro24d.png)

Clique em **Vrije-vormentabel**.

![demo](./images/pro52.png)

Agora arraste e solte o filtro que você acabou de criar.

![demo](./images/pro53.png)

Hora de adicionar algumas métricas. Comece com **Productweergaven**. Arraste e solte na tabela de forma livre. Você também pode excluir a métrica **Gebeurtenissen**.

![demo](./images/pro54.png)

Faça o mesmo com **Mensen**, **Toevoegen aan winkelwagentje** e **Aankopen**. Você vai acabar com uma tabela como a seguinte.

![demo](./images/pro55.png)

Graças à primeira análise de fluxo, uma nova pergunta surgiu. Então decidimos criar esta tabela e verificar algun KPIs em um segmento para responder a essa pergunta. Como você pode ver, o tempo de insight é muito mais rápido do que usar SQL ou usar outras solution ções de BI.

## Recapitulação do Analysis Workspace e do Customer Journey Analytics

O Analysis Workspace verwijdert todas limitações típicas de um relatório do Analytics. Ele fornece uma tela robusta e flexível para criar projetos de analytics personalizados. Arraste e solte qualquer número de tabelas de dados, visualizações e componentes (dimensões, métricas, segmentos e granularidades de tempo) para um projeto. Você pode criar de forma instantânea filtros e analises, gráficos de coorte, alertas, segmentos, análises de fluxo e relatórios de curadoria e agendamento para compartilhar com qualquer pessoa em seu negócio.

Próxima etapa: [4.6 De inzichten a ação](./ex6.md)

[Retornar para Fluxo de Usuário 4](./uc4.md)

[Retornar para Todos os Módulos](./../../overview.md)
