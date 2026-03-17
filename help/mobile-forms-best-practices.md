---
title: Práticas recomendadas para formulários móveis
description: Para casos de uso de formulários móveis e offline, crie seu próprio aplicativo nativo e busque definições de formulários por meio da API Headless Adaptive Forms. Abordagem recomendada para aplicativos móveis nativos.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: formulários móveis, aplicativo nativo, formulários offline, API headless
index: true
exl-id: 6f25039f-61fc-4366-9e17-6b2809162c58
source-git-commit: 86129488bec7faed87600a237ac034ca1b601187
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# Práticas recomendadas para formulários móveis {#mobile-forms-best-practices}

Para casos de uso de formulários móveis e offline, a abordagem recomendada é criar seu próprio aplicativo nativo e buscar definições de formulários por meio da API Headless Adaptive Forms. Isso proporciona controle total sobre a experiência móvel e garante suporte contínuo à medida que as plataformas móveis evoluem.

## Método recomendado {#recommended-approach}

Crie um aplicativo móvel nativo (iOS ou Android) que:

1. **Busca a definição de formulário headless** - Use as [APIs Adaptive Forms Headless](https://opensource.adobe.com/aem-forms-af-runtime/api/) para recuperar o formulário JSON sob demanda (por exemplo, quando o usuário abre um formulário ou navega até ele no seu aplicativo). Você pode listar os formulários disponíveis e buscar a definição do formulário por ID.

2. **Renderiza o formulário no seu aplicativo** - Use sua estrutura de interface do usuário preferencial (por exemplo, React Native ou exibições nativas) para renderizar o formulário a partir do JSON. Você pode usar o Forms Web SDK e os formulários adaptáveis headless existentes como componentes do React onde eles se encaixam em sua pilha ou criar seu próprio renderizador que consome a mesma estrutura JSON.

3. **Opcionalmente oferece suporte offline** - Implementar o armazenamento local e a sincronização no seu aplicativo. Por exemplo, armazene em cache as definições de formulário quando estiver online, salve os rascunhos localmente e envie ou sincronize os dados quando o dispositivo estiver online novamente.

Essa abordagem mantém o aplicativo acessível para manutenção à medida que o Android e o iOS são alterados e usa a plataforma headless adaptável de Forms compatível para criação, validação e envio de formulários.

## Introdução {#getting-started}

* [Visão geral dos formulários adaptáveis do AEM Headless](overview.md) - Recursos e conceitos.
* [APIs de formulários adaptáveis headless](https://opensource.adobe.com/aem-forms-af-runtime/api/) - lista, busca, valida e envia formulários de forma programática.
* [Arquitetura](architecture.md) - Como os formulários adaptáveis headless funcionam e como os aplicativos front-end os consomem.

Para obter uma integração passo a passo, consulte [Criar e publicar um formulário headless](create-and-publish-a-headless-form.md) e o [Portal do desenvolvedor](https://experienceleague.adobe.com/landing/aem-headless-forms/developer.html?lang=pt-BR).
