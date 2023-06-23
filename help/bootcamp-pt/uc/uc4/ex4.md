---
title: Bootkamp - Customer Journey Analytics - Gegevensvoorbereiding in Analysis Workspace - Brazilië
description: Bootkamp - Customer Journey Analytics - Gegevensvoorbereiding in Analysis Workspace - Brazilië
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
exl-id: d56128af-dd1e-47ea-922f-85418e9da687
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '793'
ht-degree: 0%

---

# 4.4 Preparação de dados em Customer Journey Analytics

## Objetivos

- Entenda a UO do Analysis Workspace no CJA
- Entenda os conceitos de preparação de dados no Analysis Workspace
- Aprenda a fazer cálculos de dados

## 4.4.1 UI do Analysis Workspace no CJA

O Analysis Workspace remove todas limitações típicas de um único relatório do Analytics. Ele fornece uma tela robusta e flexível para criar projetos de analytics personalizados. Arraste e solte qualquer número de tabelas de dados, visualizações e componentes (dimensões, métricas, segmentos e granularidades de tempo) para um projeto. Criação instantânea de avarias e segmentos, criação de cortes para análise, criação de alertas, comparação de segmentos, análise de fluxo e de falhas e relatórios de curadoria e agendamento para compartilhar com qualquer pessoa em seu negócio.

O Customer Journey Analytics traz essa solution ção além dos dados da plataforma. É altamente recomendável assistir a este vídeo de visão geral de quatro minutos:

>[!VIDEO](https://video.tv.adobe.com/v/35109?quality=12&learn=on)

Se você nunca usou o Analysis Workspace antes, recomendamos este vídeo:

>[!VIDEO](https://video.tv.adobe.com/v/26266?quality=12&learn=on)

### Crie Seu Projeto

Agora é hora de criar seu primeiro project do CJA. Vá para a aba de projetos dentro do CJA. Clique em **Nieuw maken**.

![demo](./images/prmenu.png)

Em seguida, você verá a tela abaixo. Selecion **Leeg project** então clique em **Maken**.

![demo](./images/prmenu1.png)

Você verá um projeto vazio.

![demo](./images/premptyprojects.png)

Primeiro, certifique-se de selecionar a Visualização de dados correta no canto superior direito da tela. Neste voorbeel, een Visualização de dados, een ser selecionada é `vangeluwe - Omnichannel Data View`.

![demo](./images/prdv.png)

Em seguida, você irá salvar seu projeto e dar um nome a ele. Você pode usar o seguinte comando para salvar:

| OS | Korte snede |
| ----------------- |-------------| 
| Windows | Control + S |
| Mac | Command + S |

Pop-up Você verá este:

![demo](./images/prsave.png)

Este modelo de nomenclatura gebruiken:

| Naam | Beschrijving |
| ----------------- |-------------| 
| `yourLastName - Omnichannel Analysis` | `yourLastName - Omnichannel Analysis` |

Em seguida, clique em **Opslaan**.

![demo](./images/prsave2.png)

## 4.4.2 Berekeningen van Métricas

Embora tenhamos organizado todos os componentes na Visualização de dados, você ainda deve adaptar algun deles para que os usuários de negócios estejam prontos para iniciar suas análises. Além disso, durante qualquer processo de analytics, você pode criar métricas calculadas para aprofundar a descoberta de insights.

Como exemplo, criaremos uma Taxa de conversão calculada usando a métrica/evento Compras que definimos na Visualização de dados.

## Taxa de conversão

Vamos começar a abrir o construtor de métricas calculadas. Clique em **+** para criar sua primeira Métrica calculada no Analysis Workspace.

![demo](./images/pradd.png)

O **Berekende metrische bouwer** irá aparecer :

![demo](./images/prbuilder.png)

Encontrol **Aankopen** na lista de métricas no menu do lado esquerdo . Em **Metrisch** clique em **Alles tonen**

![demo](./images/calcbuildercr1.png)

Agora arraste e solte a métrica **Aankopen** na definição da métrica calculada.

![demo](./images/calcbuildercr2.png)

Normalmente, taxa de conversão significant **Conversies/sessies**. Então, vamos fazer o mesmo cálculo na tela de definição de métrica calculada. Encontre a métrica **Sessies** e arraste e solte-a no criador de definição, no evento **Aankopen**.

![demo](./images/calcbuildercr3.png)

Waarnemingspost que o operador de divisão é selecionado automcamente.

![demo](./images/calcbuildercr4.png)

A taxa de conversão é comumente representada em porcentagem. Então, vamos mudar o formato para porcentagem e selecionar 2 casas decimais.

![demo](./images/calcbuildercr5.png)

Ten slotte wijzigt u de naam en beschrijving van de berekende metrische waarde:

| Titel | Beschrijving |
| ----------------- |-------------| 
| Omzetsnelheid | Omzetsnelheid |

Por fim, altere o nome e a describe ção da métrica calculada:

![demo](./images/calcbuildercr6.png)

Não se esqueça de **Salvar** een Métrica calculada.

![demo](./images/pr9.png)

## 4.4.3 Dimensões rekent als volgt: Filtros (segmentação) e intervalos de datas

### Filters: Dimensões calculadas

Os cálculos não devem ser apenas para métricas. Antes de iniciar qualquer análise, também é interessante criar algumas **Berekende Dimension**. Isso significant, essencialmente, **segmenten** geen Adobe Analytics. Geen Customer Journey Analytics, esses segmentos são chamados de **Filters**.

![demo](./images/prfilters.png)

A criação de filtros ajudará os usuários de negócios a iniciar o analytics com algumas dimensões calculadas valiosas. Isso irá automzar algumas tarefas, além de ajudar na parte de adoção. Abaixo estão alweren:

1. Mídia Própria, Mídia Paga,
2. Visitas novas x recorrentes
3. Clientes com carrinho stoponado

Esses filtros podem ser criados antes ou durante a parte de análise (o que você fará no próximo uitoefício).

### Intervalos de data: Dimensões de tempo calculadas

Als dimensões de tempo são outro tipo de dimensões calculadas. Algun já foram criados, mas você também pode criar suas próprias Dimensões de tempo personalizadas na fase de preparação de dados.

Essas Dimensões de tempo calculado ajudarão analistas e usuários de negócios a lembrar datas importantes e usá-las para filtrar e Alternar o tempo de relatório. Perguntas e dúvidas típicas quando fazemos análises:

- Quando foi a Black Vrijdag do ano passado? Wilt u de dias 21 e 29 invoeren?
- Quando veiculamos aquela campanha de TV em dezembro?
- De quando a quando fizemos as vendas de verão de 2018? Quero comparar com 2019. A propósito, você sabe os dias exatos em 2019?

![demo](./images/timedimensions.png)

Agora você concluiu o uitoefício de preparação de dados usando o Analysis Workspace do CJA.

Próxima etapa: [4.5 Visualização usando Customer Journey Analytics](./ex5.md)

[Retornar para Fluxo de Usuário 4](./uc4.md)

[Retornar para Todos os Módulos](./../../overview.md)
