---
title: Bootkamp - Customer Journey Analytics - Een gegevensweergave maken - Brazilië
description: Customer Journey Analytics - Een gegevensweergave maken - Brazilië
jira: KT-5342
audience: Data Engineer, Data Architect, Data Analyst
doc-type: tutorial
activity: develop
solution: Customer Journey Analytics
feature-set: Customer Journey Analytics
feature: Data Views
exl-id: 8cfd4467-167d-4235-a305-4596e3a7d4fb
source-git-commit: 3c86f9b19cecf92c9a324fb6fcfcefaebf82177f
workflow-type: tm+mt
source-wordcount: '1667'
ht-degree: 0%

---

# 4.3 Crie uma Visualização de Dados

## Objetivos

- Entenda a UI de Visualização de Dados
- Compreenda as configurações básicas de definição de visita
- Compreenda a atribuição e a Persistência em uma Visualização de

## 4.3.1 Visualização de Dados

Agora, com sua conexão concluída, é bezível progredir para influenciar a visualização. Uma diferença entre o Adobe Analytics e o CJA é que o CJA precisa de uma visualização de dados para limpar e preparar os dados antes da visualização.

Uma Visualização de Dados é semelhante ao conceito de Virtual Report Suites no Adobe Analytics, onde você estabelece as definições de visita com reconhecimento de contexto, filtragem e também como os componentes são chamados.

Será necessary ário, no mínimo, uma Visualização de Dados por conexão. Geen entanto, para algun casos de uso, é ótimo ter múltiplas Visualizações de Dados para a mesma conexão, com o objetivo de fornecer insights diferentes para equipes distintas. Se você deseja que sua empresa seja orientada por dados, deve adaptar a forma como os dados são vistos em cada equipe. Alweren:

- Métricas de UX apenas para equipe de UX Design
- Gebruik os mesmos nomes para KPIs e métricas para o Googles Analytics e para o Customer Journey Analytics, para que a equipe de análise digital fale apenas 1 idioma.
- Visualização de Dados filtrada para mostrar, por exemplo, dados para apenas um mercado, ou uma marca, ou apenas para Disposivos móveis.

Na tela de **Verbindingen** marque a caixa de seleção da conexão que você acabou de criar. De klikem **leidt de Mening van Gegevens**.

![ demo ](./images/exta.png)

Você será redirecionado para o fluxo de trabalho **creeer het werkschema van de Mening van Gegevens**.

![ demo ](./images/0-v2.png)

## 4.3.2 Definição de Visualização de Dados

Agora você pode configurar as definições básicas para sua Visualização de dados.

![ demo ](./images/0-v2.png)

A **Verbinding** que vocêcriou geen uitoefício anterior já está selecionada. Sua conexão se chama `yourLastName – Omnichannel Data Connection` .

![ demo ](./images/ext5.png)

Em seguida, dê um nome à sua Visualização de Dados seguindo este modelo de nomenclatura: `yourLastName – Omnichannel Data View` .

Insira o mesmo valor para a describe ção: `yourLastName – Omnichannel Data View` .

| Naam | Beschrijving |
| ----------------- |-------------| 
| `yourLastName – Omnichannel Data View` | `yourLastName – Omnichannel Data View` |

![ demo ](./images/1-v2.png)

Para **Tijdzone**, verkiesbaar aan fuso horário **Berlim, Estocolmo, Roma, Berna, Bruxelas, Viena, Amsterdam GMT+01:00**. Este é um cenário realmente interessante, pois algumas empresas operam em diferentes países e geografias. Alocar o fuso horário certo para cada país evitará erros típicos de dados, como, por exemplo, acreditar que a maioria das pessoas compra camisetas às 4h no Peru.

![ demo ](./images/ext7.png)

Você também pode modificar a nomenclatura das métricas princippais (Pessoa, Sessão e Evento). Isso não é obrigatório, mas algun clientes gostam de usar Pessoas, Visitas e Acessos em vez de Pessoa, Sessão e Eventos (convenção de nomenclatura padrão do Customer Journey Analytics).

Agora vocdeve ter as seguintes configurações definidas:

![ demo ](./images/1-v2.png)

De klikem **sparen en gaat** verder.

![ demo ](./images/12-v2.png)

## 4.3.3 Componentes da Visualização de Dados

Neste uitoefício, você irá configurar os componentes necessary ários para analisar os dados e visualizá-los usando Analysis Workspace. Nesta IU, há três áreas princippais:

- Lado esquerdo: Componentes disponíveis dos datasets selecionadobe
- Meio: Component adicionados à Visualização de Dados
- Lado direito: Configurações do componente

![ demo ](./images/2-v2.png)

>[!IMPORTANT]
>
>Se você não encontrar uma métrica ou dimensão específica, verifieque se o campo `Contains data` foi removido de sua visualização de dados. Caso contrário, exclusief esse campo.
>
>![ demo ](./images/2-v2a.png)

Agora você preca arrastar e soltar os componentes necessary ários para a análise nos **Toegevoegde Componenten**. Para is, você deve selecionar os componentes no menu à esquerda e arrastá-los e soltá-los na tela no meio.

Vamos começar com o primeiro componente: **Naam (web.webPageDetails.name)**. Pesquise esse componente e arraste-o e solte-o na tela.

![ demo ](./images/3-v2.png)

Esse componente é o nome da página, como você pode deriar da leitura do campo do schema `(web.webPageDetails.name)` .

Geen entanto, usar **Naam** como nome não é a melhor convção de nomenclatura para um usuário corporativo compender rapidamente essa dimensão.

Vamos mudar om para **Naam van de Pagina** te noemen. De klem geen component om na a área **Montages van de Component** opnieuw te omeren.

![ demo ](./images/3-0-v2.png)

Als Configurações de persistência são **montages van de persistentie**. Os conceitos de Vars e prop não existem no CJA, mas as configurações de Persistência possibilitam um comportamento semelhante.

![ demo ](./images/3-0-v21.png)

Se você não aartessas configurações, o CJA irá interpretar a dimensão como um **Prop** (nível de ocorrência). Além desso, veranderen de podemos een Persistência para tornar a dimensão uma **eVar** (persistir o valor ao longo da jornada).

Se você não estiver familiarizado com Vars e Props, [ leia mais sobre isso na documentação ](https://experienceleague.adobe.com/docs/analytics/landing/an-key-concepts.html).

Vamos deixar o Nome da Página como Prop. Dessa forma, você não precisa alternatieve nenhuma **Persistence Settings**.

| Componentnaam die u wilt zoeken | Nieuwe naam | Persistinstellingen |
| ----------------- |-------------| --------------------| 
| Naam (web.webPageDetails.name) | Paginanaam |          |

Em seguida, escolha a dimensão **phoneNumber** e solte-a na tela. O novo nome deve ser **Aantal van de Telefoon**.

![ demo ](./images/3-1-v2.png)

Por fim, vamos Alternar as Configurações de persistência, pois o Número do Celular deve persistir no nível do usuário.

Para Verandert een Persistência, rolpara baixo op menu à direita e abra a aba **Persistence**:

![ demo ](./images/5-v2.png)

Marque a caixa de seleção para modificar as configurações de persistência. Selecione **Recentste Recentste** e van escopo **Persoon (Meldend venster)**, pis nos preocupamos apenas com o último número de celular da pessoa. Se o cliente não preencher o celular em bezoekas futuras, você ainda verá esse valor preenchido.

![ demo ](./images/6-v2.png)

| Componentnaam die u wilt zoeken | Nieuwe naam | Persistinstellingen |
| ----------------- |-------------| --------------------| 
| phoneNumber | Telefoonnummer | Recentste versie, Persoon (rapportagevenster) |

O próximo componente é `web.webPageDetails.pageViews.value` .

Geen menu à esquerda, pesquise `web.webPageDetails.pageViews.value`. Arraste e solte essa métrica na tela.

Ook noem a para **de Meningen van de Pagina** onder de **montages van de Component**.

| Componentnaam die u wilt zoeken | Nieuwe naam | Attributie-instellingen |
| ----------------- |-------------| --------------------| 
| web.webPageDetails.pageViews.value | Paginaweergaven |         |

![ demo ](./images/7-v2.png)

Para as configurações de atribuição, deixaremos em branco.

Observação: As configurações de persistência nas métricas também podem ser Veranderadas no Analysis Workspace. Em algun casos, você pode optar por configurá-las aqui para evitar que os usuários de negócios tenham que pensar qual é o melhor modelo de persistência.

Em seguida, você terá que configurar várias Dimensões e Métricas, conforme indicado na tabela abaixo.

### AFMETINGEN

| Componentnaam die u wilt zoeken | Nieuwe naam | Persistinstellingen |
| ----------------- |-------------| --------------------| 
| brandName | Merknaam | Recentste versie, sessie |
| beluisteren | Aanroepfunctie |          |
| call-id | Type oproepinteractie |          |
| callTopic | Het Onderwerp van de vraag | Recentste versie, sessie |
| ecid | ECID | Recentste versie, Persoon (rapportagevenster) |
| email | E-mailid | Recentste versie, Persoon (rapportagevenster) |
| Betalingstype | Betalingstype |          |
| Product toevoegen, methode | Product toevoegen, methode | Recentste versie, sessie |
| Type gebeurtenis | Type gebeurtenis |         |
| Naam (productListItems.name) | Productnaam |         |
| SKU | SKU (sessie) | Recentste versie, sessie |
| Transactie-id | Transactie-id |         |
| URL (web.webPageDetails.URL) | URL |         |
| Gebruikersagent | Gebruikersagent | Recentste versie, sessie |

### MÉTRICA

| Componentnaam die u wilt zoeken | Nieuwe naam | Attributie-instellingen |
| ----------------- |-------------| --------------------| 
| Aantal | Aantal |          |
| commerce.order.priceTotal | Ontvangsten |         |

Sua configuração deve ser semelhante ao seguinte:

![ demo ](./images/11-v2.png)

Não se esqueça de Salvar sua Visualização de Dados. Então klique em **sparen**.

![ demo ](./images/12-v2s.png)

## 4.3.4 Berekeningen van Métricas

Embora tenhamos organizado todos os componentes na Visualização de dados, você ainda deve adaptar algun deles para que os usuários de negócios estejam prontos para iniciar suas análises.

Se vocse ê lembra, não trouxemos especificamente Métricas como Adicionar ao Carrinho, Visualização do produto ou Compras para Visualização de dados. Geen entanto, temos uma dimensão chamada: **Type van Gebeurtenis**. Então, vamos deriar esses tipos de interação criando 3 métricas calculadas.

Vamos começar com a primeira Métrica: **de Meningen van het Product**.

Geen lado esquerdo, pesquise **Type van Gebeurtenis** selecteert een afmeting. Em seguida, arraste-o e solte-o na tela **omvatten Componenten**.

![ demo ](./images/calcmetr1.png)

Clique para selecionar a nova métrica **Type van Gebeurtenis**.

![ demo ](./images/calcmetr2.png)

Agora altere o nome e a describe ção do componente para os seguintes valores:

| Componentnaam | Componentbeschrijving |
| ----------------- |-------------| 
| Productweergaven | Productweergaven |

![ demo ](./images/calcmetr3.png)

Agora vamos contar apenas eventos de **Weergaven van het Product**. Para fazer is, rolpara baixo em **de Montages van de Component** até ver Valores de **omvat Exclude Waarden**. Certifique-se de habilitar a opção **Reeks omvat/sluit waarden** uit.

![ demo ](./images/calcmetr4.png)

Como vraagt contar apenas **de Meningen van het Product**, gespecificeerde **commerce.productViews** nos critérios.

![ demo ](./images/calcmetr5.png)

Agora a sua métrica calculada está pronta!

Em seguida, repita of mesmo processo para os eventos **voegt aan Kart** toe e **Schaf**.

### Toevoegen aan winkelwagentje

Primeiro, arraste solte a mesma dimensão **Type van Gebeurtenis**.

![ demo ](./images/calcmetr1.png)

Você verá um alerta pop-up de um Campo Duplicado, pois estamos usando a mesma variável. De klemem **voegt hoe dan ook toe**:

![ demo ](./images/calcmetr6.png)

Agora, siga o mesmo processo que fizemos para a métrica Visualizações de produto:
- Primeiro altere o nome e a description ão.
- Por fim, adicione **commerce.productListAdds** como critério para contar apenas Add aan Kaart

| Naam | Beschrijving | Criteria |
| ----------------- |-------------| -------------|
| Toevoegen aan winkelwagentje | Toevoegen aan winkelwagentje | commerce.productListAdds |

![ demo ](./images/calcmetr6a.png)

### Aankopen

Primeiro, arraste e solte a mesma dimensão **Type van Gebeurtenis** como fizemos para als duas métricas anteriores.

![ demo ](./images/calcmetr1.png)

Você verá um alerta pop-up de um Campo Duplicado, pois estamos usando a mesma variável. De klemem **voegt hoe dan ook toe**:

![ demo ](./images/calcmetr7.png)

Agora, siga o mesmo processo que fizemos para as métricas Product Views e Add to cart:
- Primeiro altere o nome e a description ão.
- Por fim, adicione **commerce.purchase** como critérios para contabilizar apenas als Compras

| Naam | Beschrijving | Criteria |
| ----------------- |-------------| -------------|
| Aankopen | Aankopen | commerce.purchases |

![ demo ](./images/calcmetr7a.png)

Sua configuração final deve ser semelhante ao seguinte. De klikem **sparen en gaat** verder.

![ demo ](./images/calcmetr8.png)

## 4.3.5 Componentes da Configuração de Dados

Você deve ser redirecionado para esta tela:

![ demo ](./images/8-v2.png)

Nesta aba, você pode modificar algumas configurações importantes para alternatieve a forma como os dados são processados. Vamos começar definindo aan **Onderbreking van de Zitting** como 30 min. Graças ao registro de data e hora de cada evento de experience ência, você pode estender o conceito de uma sessão em todos os canais. Por exemplo, o que acontece se um cliente ligar para to call center depois de bezoekar to site? Usando Tempos Limite de Sessão personalizados, você tem muita flexbilidade para decidir o que é uma sessão e como essa sessão irá mesclar os dados.

![ demo ](./images/ext8.png)

Nesta aba você pode modificar outras coisas como filtrar os dados usando um segmento/filtro. Você não precará fazer isso neste uitoefício.

![ demo ](./images/10-v2.png)

Quando eindigt, klikem **sparen en eindigt**.

![ demo ](./images/13-v2.png)

>[!NOTE]
>
>Você pode voltar a esta Visualização de dados posteriormente e corriar as configurações e os componentes a qualquer momento. Als alternações afetarão a forma como os dados históricos são mostrados.

Agora você pode continue ar com a parte de visualização e análise!

Próxima etapa: [ 4.4 Preparação de dados em Customer Journey Analytics ](./ex4.md)

[Retornar para Fluxo de Usuário 4](./uc4.md)

[Retornar para Todos os Módulos](./../../overview.md)
