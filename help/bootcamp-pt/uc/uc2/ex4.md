---
title: Bootkamp - Journey Optimizer Maak je reis - Brazilië
description: Bootkamp - Journey Optimizer Maak je reis - Brazilië
jira: KT-5342
audience: developer
doc-type: tutorial
activity: develop
exl-id: 674a9baa-5900-405e-b744-ea211f60a16d
source-git-commit: 90f7621536573f60ac6585404b1ac0e49cb08496
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# 2.4 Teste sua jornada

## Fluxo da jornada do cliente

Abra uma nova janela e anônima do navegador e vá para [https://bootcamp.aepdemo.net](https://bootcamp.aepdemo.net). Clique em **Alles toestaan**. Com base no seu comportamento de navegação no fluxo de usuário anterior, você verá a personalização acontecer na página inicial do site.

![DSN](./images/web8a.png)

Clique no ícone **Profiel** de superieure direito da tela is niet te vinden .

![Demo](./images/web8b.png)

Clique em **Een account maken**.

![Demo](./images/pv5.png)

Preencha todos os campos do formulário. Gebruik van um valor real para endereço de e-mail e número de telefone, pois será usado em uitoefícios posteriores para envio de e-mail e SMS.

![Demo](./images/pv7a.png)

Rol para baixo. Agora vocdeve insert o eventID do seu evento personalizado que você criou no uitoefício 2.2. Você pode encontrá-lo aqui:

![ACOP](./images/payloadeventID.png)

O eventID é o que precisa ser enviado à Adobe Experience Platform para acionar a jornada que você construiu. Este é o eventID neste voorbeel:
`19cab7852cdef99d25b6d5f1b6503da39d1f486b1d585743f97ed2d1e6b6c74f`

Preencha o eventID no campo **Gebeurtenis-id voor aanmaken van account** e clique em **Registreren**.

![Demo](./images/pv8a.png)

Em seguida, een tela abaixo será exibida:

![Demo](./images/pv9.png)

Você também receberá este e-mail, que é o e-mail que você mesmo criou como parte deste uitoefício.

![Demo](./images/pv10a.png)

Você terminou este uitoefício.

Próxima etapa: [2.5 Installeer het gebruik van aplicativo móvel](./ex5.md)

[Retornar para Fluxo de Usuário 2](./uc2.md)

[Retornar para Todos os Módulos](../../overview.md)
