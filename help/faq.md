---
title: Perguntas frequentes sobre o Headless Adaptive Forms
description: Perguntas frequentes
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless, formulário adaptável, Perguntas frequentes
hide: false
exl-id: 5bfc307d-96a3-4007-b65f-32176ecdb710
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# Perguntas frequentes {#headless-adaptive-forms-faq}

## Devo saber o React.js para usar formulários adaptáveis headless?

Você pode usar qualquer estrutura, biblioteca ou idioma para renderizar formulários adaptáveis Headless e usar as APIs REST do Adobe para validar e enviar os formulários. A biblioteca AF-core, fornecida imediatamente, é independente de estrutura. As bibliotecas de componentes React-Render e React-Component, também fornecidas prontas para uso, são para sua conveniência. Você pode criar seus próprios componentes; não se limita aos fornecidos.


<!-- 
## Did Adobe release a new AEM Archetype for Headless adaptive forms?

You can use Archetype 37 with flag `includeFormsheadless` or later flag to create an AEM project with Headless adaptive forms functionality. 

-->

## Preciso da sandbox do Forms as a Cloud Service para usar formulários adaptáveis headless?

Você pode usar o aplicativo inicial para começar a desenvolver e estilizar seus formulários adaptáveis headless. Você precisa do Forms as a Cloud Service para hospedar e fornecer formulários adaptáveis headless junto com recursos de formulários de back-end.

<!-- ## Do I need an archetype project to develop Headless adaptive forms?

You can use the starter app to start developing and styling your Headless adaptive forms. Later on, you can use the 
archetype project to deploy the finished Headless adaptive forms and corresponding custom code, created using starter app, to Forms as a Cloud Service environment. The Forms as a Cloud Service environment helps you test and productionize the forms. -->

## Onde posso obter uma visualização de um formulário adaptável headless? {#storybook-example}

Você pode usar o aplicativo inicial para renderizar e pré-visualizar um formulário adaptável headless personalizado. Você também pode modificar um exemplo de [storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction) para visualizar um formulário adaptável headless.

![](/help/assets/storybook-example.png)

## É possível usar formulários adaptáveis headless com estruturas personalizadas?

Os formulários adaptáveis headless são baseados na [especificação padrão](/help/assets/headless-adaptive-forms-specification.pdf). É possível estender a especificação para usá-la na criação de componentes personalizados. Por exemplo, componentes para a interface do Chakra, Vue.js e muito mais.

## Os formulários adaptáveis headless suportam campos em cascata?

Em campos em cascata, o conteúdo do segundo campo depende do conteúdo escolhido no primeiro campo. O [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&args=formJson.items[0].fieldType:drop-down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down) fornece um exemplo de campos em cascata.

## Os formulários adaptáveis headless permitem preencher formulários com dados personalizados?

Formulários adaptáveis headless permitem preencher formulários com dados personalizados. O [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data) fornece um exemplo de como preencher previamente um formulário adaptável headless.

<!-- >
## Can I use existing Adaptive Forms editor to create a Headless adaptive form?

At this moment, you use the Adaptive Form Editor to specify the JSON structure and set submit action for the forms. Support for drag-and-drop components, applying rules using editor, and more editor-related options would be available later in the beta phase. Keep a watch on release notes.  -->

## Posso usar formulários adaptáveis headless com o Angular SPA?

Você pode usar o Web SDK para integrar formulários adaptáveis headless ao Angular SPA. É independente de qualquer estrutura. Você pode usar o React SDK como referência.

<!-- ## Should the `-r prerelease` switch be used every time to start the AEM SDK instance or only for the first time?

During the limited release program, use the `-r prerelease` switch every time you start the AEM SDK instance. 

## What is AEM Forms add-on (.far file) and how to install it?

Adobe Experience Manager Forms as a Cloud Service feature archive provides tools to create Headless adaptive forms on the local development environment. To install the feature archive, see [Setup development environment](setup-development-environment.md).

<!-- 
## Where do one get the license.properties file from?

You do not require a license.properties file to run AEM Cloud Service SDK. 

-->

## Existe algum plugin para facilitar o desenvolvimento para Headless AF?

Sim — uma extensão do Visual Studio Code permite criar manualmente formulários adaptáveis headless em JSON.

## Um formulário adaptável headless pode se conectar a qualquer CRM para ler ou gravar dados?

Você pode usar o Microsoft Dynamics e o Salesforce para enviar ou preencher previamente um formulário adaptável headless. Além dos CRMs, os formulários adaptáveis headless oferecem suporte ao envio ou preenchimento prévio usando endpoints REST, email e ações de envio personalizadas.
