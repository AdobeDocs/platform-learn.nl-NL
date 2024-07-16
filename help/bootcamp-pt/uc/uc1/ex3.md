---
title: Bootkamp - Real-time klantprofiel - Een segment maken - UI - Brazilië
description: Bootkamp - Real-time klantprofiel - Een segment maken - UI - Brazilië
jira: KT-5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
feature: Segments
exl-id: 9b8d93b5-5bed-4600-8602-b438a0893612
source-git-commit: ee5c0af17c12f1d90774a3a4150c9788e2368e39
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 2%

---

# 1.3 Crie um segmento - UI

Neste uitoefício, você irá criar um segmento usando o Construtor de Segmentos da Adobe Experience Platform.

## História

Toegang tot [ Adobe Experience Platform ](https://experience.adobe.com/platform). Depois de fazer login, você irá acessar a página inicial da Adobe Experience Platform.

![ Ingestie van Gegevens ](./images/home.png)

Antes de continuar, você nauwkeurige um **zandbak**. O nome do sandbox a ser selecionado é ``Bootcamp`` . É bezível fazer isso clicando no texto **[!UICONTROL Production Prod]** na linha azul na parte superior da tela. Depois de selecionar o sandbox apropriado, você verá a tela mudando e agora você está em seu [!UICONTROL sandbox] oormerk.

![ Ingestie van Gegevens ](./images/sb1.png)

Geen menu à esquerda, toegang **Segmenten**. Nesta página, você tem uma visão geral de todos os segmentos bestaat. Clique no botão + Criar segmento para começar a criar um novo segmento.

![Segmentatie](./images/menuseg.png)

Quando schatver geen novo construtor de segmentos, você irá perceber imediatamente a opção de menu **Attributes** e a referência do **XDM Individual Profile**.

![Segmentatie](./images/segmentationui.png)

Como XDM é a linguagem que alimenta o setor de experience ência, o XDM também é a base para o construtor de segmentos. Todos os dados ingeridos na plataforma devem ser mapeados em relação ao XDM e, portanto, todos os dados se tornam parte do mesmo modelo de dados, Independent emente da origem desses dados. Isso oferece uma grande vanvoordm ao criar segmentos, pois a partir dessa interface do usuário do construtor de segmento, é bezível combinar dados de qualquer origem no mesmo fluxo de trabalho. Os segmentos criados no Construtor de segmentos podem ser enviados para solções como Adobe Target, Adobe Campaign e Adobe Audience Manager para ativação.

Agora você preca criar um segmento de todos os clients que visualizaram o produto **Real-Time CDP**.

Para construir este segmento, você precisa adicionar um Evento de experience. Você pode contrar todos os Eventos de ervarência clicando no ícone **Gebeurtenissen** na barra de menu **Gebieden**.

![Segmentatie](./images/findee.png)

Em seguida, você verá o nó **XDM ExperienceEvents** do nível superior. Clique em **XDM ExperienceEvent**.

![Segmentatie](./images/see.png)

Heb toegang tot **Punten van de Lijst van het Product**.

![Segmentatie](./images/plitems.png)

Selecione **e arraste e solte of voorwerp** Naam **doet menu à esquerda na tela do construtor de segmentos na seção** Gebeurtenissen **.** Em seguida, o seguinte será exibido:

![Segmentatie](./images/eewebpdtlname.png)

O parâmetro de comparação deve ser **evenaart** e, geen campo de entrada, binnen **in real time CDP**.

![Segmentatie](./images/pv.png)

Sempre que adicionar um elemento ao construtor de segmentos, você pode clicar no botão **Refresh Estimate** para obter uma nova estimativa da população em seu segmento.

![Segmentatie](./images/refreshest.png)

Para **Methode van de Evaluatie**, verkiesbare **Edge**.

![Segmentatie](./images/evedge.png)

Por fim, vamos dar um nome ao seu segmento e salvá-lo.

Como modelo de nomenclatura, gebruik:

- `seuSobrenome - Interest in Real-Time CDP`

Em seguida, kliek op botão **sparen en sluit** para salvar seu segmento.

![Segmentatie](./images/segmentname.png)

Agora vocirá retornar à página de visão geral do segmento, onde verá uma visualização de amostra dos perfis de clientes que se kwalificficam para o seu segmento.

![Segmentatie](./images/savedsegment.png)

Agora você pode continue no próximo uitoefício e usar seu segmento com o Adobe Target.

Próxima etapa: [ 1.4 Ação: envie seu segmento para o Adobe Target ](./ex4.md)

[Retornar para Fluxo de Usuário 1](./uc1.md)

[Retornar para Todos os Módulos](../../overview.md)
