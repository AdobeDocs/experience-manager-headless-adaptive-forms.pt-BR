---
title: Visão geral dos formulários adaptáveis AEM Headless
description: Visão geral para formulários adaptáveis AEM Headless.
hide: true
exl-id: cd7c7972-376c-489f-a684-f479d92c37e7
source-git-commit: 0127f8ddede38083f0932b0e8d7efdd0dd77c3a6
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 3%

---


# Notas de versão

Bem-vindo ao lançamento antecipado do Experience Manager Headless Adaptive Forms. Leia a seguir os recursos e as instruções para começar e aproveitar ao máximo a versão.

Você pode usar os formulários adaptáveis do Adobe Experience Manager Headless para criar aplicativos de formulários usando estruturas de interface do usuário de front-end, como o React, o Angular e muito mais, e usar o SDK da Web do Adaptive Forms para recursos como gerenciamento de estado, validação e integrações com vários outros pontos de contato.

A versão inicial do adotor fornece acesso para usar formulários adaptáveis Headless em um [ambiente de desenvolvimento local](setup-development-environment.md). Você pode usar o ambiente de desenvolvimento local para criar e testar formulários adaptáveis Headless.

Os formulários adaptáveis headless recebem melhorias contínuas. Para se manter atualizado com os desenvolvimentos mais recentes, visite esta página regularmente. Esta página fornece informações sobre acesso antecipado, versões mais recentes, novos recursos, melhorias, correções de erros, funcionalidades obsoletas, instruções especiais e planos futuros para alterações.

<!-- 

## July 2022 (v0.22.1)

### New features

* Introduced the `validateFormData` API. It validates all the components against the rules and constraints an returns the list of errors. The validation takes place on the server.
* Introduced the `FormLoad` event.
* Introduced the `importData` and `exportData`.
* You can now dynamically add or remove items, that expect unqiue values, from a repeatable panel. You can use the `minItems` and `maxitems` constraint to set limit of item.
* You can now use constraint to set maximum file upload size, accepted file types, minimum files, and maximum files to upload.

### Improvements and bug fixes

* The service was executing some event handlers twice. The issue is fixed.
* Fixing Data Generation with different values of dataRef, name and type.

<!-- ### React Renderer component -->

## Artefatos disponíveis na versão inicial do adotante

Na jornada para trazer os formulários adaptáveis do Adobe Experience Manager Headless para você, os seguintes artefatos estão disponíveis na versão mais recente do Adoter:

### AEM FORMS AS A CLOUD SERVICE SDK

AEM Forms as a Cloud Service SDK para ajudá-lo a criar, armazenar e buscar formulários adaptáveis Headless. Também ajuda a fornecer preenchimento, validação de regras do lado do servidor e serviços de envio para formulários adaptáveis headless.

### Forms Web SDK

O Forms Web SDK fornece as APIs para validar restrições aplicadas a vários campos de um formulário e ganchos para conectar a estrutura JSON do formulário à estrutura da interface do usuário. Ele também fornece o Renderizador de reação&#x200B; para formulários adaptáveis headless para ajudar a integrar um formulário adaptável headless ao seu aplicativo. Os seguintes componentes do SDK da Web estão disponíveis:

* **[@aemforms/af-response-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-response-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

<!-- npm i --save @aemforms/af-react-components @aemforms/af-react-renderer @aemforms/af-core -->

#### Storybook

O [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) fornece uma visão geral de diferentes componentes de formulários adaptáveis headless. Também fornece uma lista de todos os componentes compatíveis, suas propriedades correspondentes e restrições.

### Componente principal do Forms

<!-- Forms components are the structural elements that constitute the content of the form being authored. These components provide various form fields and ability to customize those fields. -->

Os Componentes principais são um conjunto de componentes padronizados de Gerenciamento de Conteúdo Online (WCM, na sigla em inglês) para ajudar você a acelerar o tempo de desenvolvimento e reduzir o custo de manutenção de seus formulários. O componente de Contêiner do Forms é um componente principal. Ele ajuda a incorporar e renderizar uma estrutura JSON de formulário adaptável headless no editor Forms adaptável do SDK as a Cloud Service do Forms.

### Especificações adaptáveis do Forms V2

A especificação de formulários adaptáveis headless fornece informações detalhadas sobre todos os componentes, restrições e métodos disponíveis para definir formulários adaptáveis headless. A especificação está disponível no formato [PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf).

### API HTTP e JS

As [APIs HTTP](https://opensource.adobe.com/aem-forms-af-runtime/api/) permitem listar, buscar, validar, enviar e rastrear o status de envio de formulários headless. As [APIs JS](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) ajudam você a usar formulários adaptáveis headless com qualquer estrutura de interface do usuário baseada no JavaScript.

### Extensão de Código do Visual Studio

[Extensão do Visual Studio Code](visual-studio-code-extension-for-headless-adaptive-forms.md) para ajudar a criar uma estrutura JSON válida. Ele fornece suporte e validação do IntelliSense para a estrutura JSON de formulários, juntamente com funções comuns, como adicionar, excluir ou renomear componentes de uma estrutura JSON.

<!-- ## What's next

The following features would be available in upcoming releases:

* HTTP APIs to invoke a business logic.
* Server-side capabilities (Prefill, server-side validation, generating Document of Record (DoR), Submitting to a Form Data Model or using Form Data Models for creating rules, and more).
* Continuous improvements to specifications and Headless adaptive form runtime.
* Use  Adaptive Forms editor for easier management and authoring Headless adaptive forms.
-->