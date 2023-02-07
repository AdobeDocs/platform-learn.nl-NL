---
title: Bootkamp - Real-time klantprofiel - Een segment maken - UI - Brazilië
description: Bootkamp - Real-time klantprofiel - Een segment maken - UI - Brazilië
kt: 5342
audience: Data Engineer, Data Architect, Marketer
doc-type: tutorial
activity: develop
source-git-commit: 5d824244766135cd4998feab48be7f6a69c42a70
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 2%

---

# 1.3 Crie um segmento - UI

Neste uitoefício, você irá criar um segmento usando o Construtor de Segmentos da Adobe Experience Platform.

## História

Acesse [Adobe Experience Platform](https://experience.adobe.com/platform). Depois de fazer login, você irá acessar a página inicial da Adobe Experience Platform.

![Gegevensopname](./images/home.png)

Antes de continue ar, vocêprecisa selecionar um **sandbox**. O nome do sandbox a ser selecionado é ``Bootcamp``. É bezível fazer isso clicando no texto **[!UICONTROL Productieproduct]** Na linha azul na parte superior da tela. Depois de selecionar o sandbox apropriado, você verá a tela mudando e agora você está em seu [!UICONTROL sandbox] toewijding.

![Gegevensopname](./images/sb1.png)

Geen menu à esquerda, acesse **Segmenten**. Nesta página, você tem uma visão geral de todos os segmentos bestaat. Clique no botão + Criar segmento para começar a criar um novo segmento.

![Segmentering](./images/menuseg.png)

Quando estiver no novo construtor de segmentos, você irá perceber imediatamente a opção de menu **Attributen** e a referência do **Afzonderlijk XDM-profiel**.

![Segmentering](./images/segmentationui.png)

Como XDM é a linguagem que alimenta o setor de experience ência, o XDM também é a base para o construtor de segmentos. Todos os dados ingeridos na plataforma devem ser mapeados em relação ao XDM e, portanto, todos os dados se tornam parte do mesmo modelo de dados, Independent emente da origem desses dados. Isso oferece uma grande vanvoordm ao criar segmentos, pois a partir dessa interface do usuário do construtor de segmento, é bezível combinar dados de qualquer origem no mesmo fluxo de trabalho. Os segmentos criados no Construtor de segmentos podem ser enviados para solções como Adobe Target, Adobe Campaign e Adobe Audience Manager para ativação.

Agora você precar criar um segmento de todos os clientes que visualizaram o produto **Real-Time CDP**.

Para construir este segmento, você precisa adicionar um Evento de experience ência. Você pode enconr todos os Eventos de ervarência clicando no ícone **Gebeurtenissen** na barra de menu **Velden**.

![Segmentering](./images/findee.png)

Em seguida, você verá o nó **XDM ExperienceEvents** nível superior . Clique em **XDM ExperienceEvent**.

![Segmentering](./images/see.png)

Acesse **Objecten in de productlijst**.

![Segmentering](./images/plitems.png)

Selecion **Naam** e arraste e solte o object **Naam** do menu à esquerda na tela do construtor de segmentos na seção **Gebeurtenissen**. Em seguida, o seguinte será exibido:

![Segmentering](./images/eewebpdtlname.png)

O parâmetro de comparação deve ser **equals** e, geen campo de entrada, insira **Real-time CDP**.

![Segmentering](./images/pv.png)

Sempre que adicionar um elemento ao construtor de segmentos, você pode clicar no botão **Offerte vernieuwen** para obter uma nova estimativa da população em seu segmento .

![Segmentering](./images/refreshest.png)

Para **Evaluatiemethode**, selecione **Rand**.

![Segmentering](./images/evedge.png)

Por fim, vamos dar um nome ao seu segmento e salvá-lo.

Como modelo de nomenclatura, gebruik:

- `seuSobrenome - Interest in Real-Time CDP`

Em seguida, clique no botão **Opslaan en sluiten** para salvar seu segmento.

![Segmentering](./images/segmentname.png)

Agora vocirá retornar à página de visão geral do segmento, onde verá uma visualização de amostra dos perfis de clientes que se kwalificficam para o seu segmento.

![Segmentering](./images/savedsegment.png)

Agora você pode continue no próximo uitoefício e usar seu segmento com o Adobe Target.

Próxima etapa: [1.4 Ação: envie seu segmento para o Adobe Target](./ex4.md)

[Retornar para Fluxo de Usuário 1](./uc1.md)

[Retornar para Todos os Módulos](../../overview.md)
