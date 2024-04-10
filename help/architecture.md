---
title: Arquitetura headless de formulários adaptáveis
description: Saiba mais sobre a arquitetura do AEM Forms Headless Adaptive Forms e como ele pode ajudar você a criar formulários rapidamente para várias plataformas. Este artigo fornece insights sobre como o Forms adaptável headless funciona e como ele pode ser integrado a diferentes aplicativos para simplificar o processo de criação de formulários.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless, formulário adaptável, arquitetura
hide: false
exl-id: ee7096d8-89e2-41e0-85e7-b26457df96fb
source-git-commit: 56ad9d8fefc4933847061ba6007ad367984bd2e0
workflow-type: tm+mt
source-wordcount: '893'
ht-degree: 0%

---


# Como funciona o formulário adaptável headless?

Um formulário adaptável headless é essencialmente uma estrutura JSON (esquema) que consiste em campos de formulário (caixa de texto, opções e muitos mais campos) e regras correspondentes (lógica condicional) para adicionar comportamento interativo ao formulário. Você pode usar APIs REST no aplicativo ou site para solicitar a estrutura JSON hospedada e renderizar nativamente a estrutura JSON como um formulário no aplicativo ou site. Um único formulário adaptável headless pode atender a várias páginas da Web e aplicativos sem fazer alterações específicas do aplicativo ou do site a ele.

![Como funciona o formulário adaptável headless](/help/assets/how-headless-adaprive-forms-work.png)

## Arquitetura {#architecture}

Uma arquitetura típica de formulários adaptáveis headless constitui um Adobe Experience Manager Forms Server, formulários adaptáveis headless hospedados no Adobe Experience Manager Forms Server e seus aplicativos de front-end (site, aplicativo móvel, aplicativos JavaScript, aplicativos de chat e muito mais) para representações de formulários específicas do canal.

A arquitetura típica de uma implantação de formulários adaptáveis headless é semelhante à seguinte:

![Arquitetura](/help/assets/headless-af-architecture.png)

<!-- 

You can use the React renderer component shipped with Headless adaptive forms to render an Adaptive Form or build your own custom component to natively render a Headless Form in a website or an application or use any UI framework or programming language to build your own components to render your forms.

A typical Headless adaptive forms architecture constitutes an Adobe Experience Manager Server, JSON structure of forms, various frontend apps for channel-specific form renditions.

![Architecture](/help/assets/headless-af-architecture.png) -->

### Componente de uma implementação de formulários adaptáveis headless

**Adobe Experience Manager Server**: além de servir como host para formulários adaptáveis headless, o Adobe Experience Manager fornece os seguintes recursos de back-end:

* APIs RESTful para listar, buscar, preencher previamente, validar, enviar e rastrear o status de envio de formulários headless.
* Editor visual para desenvolver facilmente um formulário adaptável headless.
* Modelo de dados do Forms para receber ou enviar dados para fontes de dados diferentes.
* Mecanismo de workflow para automatizar tarefas complexas.

**Formulários adaptáveis headless**: um formulário adaptável headless é representado como um arquivo .json. A estrutura JSON define componentes, restrições e estrutura de um formulário.

**Aplicativos de front-end**: aplicativos front-end como, SPA (Aplicativos de página única), aplicativos para dispositivos móveis, aplicativos JavaScript, consomem formulários adaptáveis headless (a Representação de formulário JSON) e renderizam o formulário em um cliente. Você pode usar o componente de renderização do React fornecido com formulários adaptáveis headless para renderizar um formulário adaptável ou criar seu próprio componente personalizado para renderizar nativamente formulários adaptáveis headless.

<!-- ### Understanding Headless adaptive forms definition -->



### Ferramentas do desenvolvedor

Em um ciclo de desenvolvimento típico, você começa com a criação e a hospedagem de formulários adaptáveis Headless no Adobe Experience Manager Forms Server. Na segunda etapa, mapeie os componentes da interface ou use uma biblioteca pública de componentes da interface do usuário, como a interface do usuário de materiais do Google ou a interface do usuário Chakra, para estilizar os formulários. Na última etapa, você busca e exibe formulários adaptáveis Headless em seu aplicativo (site, aplicativo móvel, aplicativos JavaScript, aplicativos de chat ou muitas outras superfícies).

As ferramentas a seguir ajudam a criar e integrar formulários adaptáveis Headless aos seus aplicativos:

**Forms Web SDK (tempo de execução do lado do cliente)**: o Forms Web SDK é uma biblioteca JavaScript do lado do cliente. Ele permite aplicar validações do lado do cliente em campos de formulário, manter o estado do formulário e fornecer ganchos para conectar o formulário com a camada da interface do usuário ou o componente renderizado de formulários adaptáveis. Ele permite que os clientes validem as restrições aplicadas a vários campos de um formulário e ganchos para conectar a estrutura JSON do formulário à estrutura da interface do usuário. O Forms Web SDK tem os seguintes componentes:

* **Processador de regra de negócios**: o processador de regras de negócios aceita a estrutura JSON de formulários como entrada, gerencia o estado dos campos de formulário, executa regras e manipuladores de eventos presentes no JSON.
* **Aglutinante de reação**: Fornece ganchos sobre o controlador para adicionar estado aos componentes de formulário. Também é útil no preenchimento prévio de um formulário.
* **Biblioteca de componentes**: fornece Componentes do espectro do React e usa ganchos no módulo React Binder para adicionar estado a esses componentes.

Além de fornecer as APIs para validar as restrições aplicadas a vários campos de um formulário, o Forms Web SDK fornece ganchos para conectar formulários adaptáveis headless à estrutura da interface do usuário. Ele também fornece o Renderizador de reação&#x200B; para formulários adaptáveis headless para ajudar a integrar um formulário adaptável headless ao seu aplicativo. Os seguintes componentes do SDK da Web estão disponíveis:

* **[@aemforms/af-response-components](https://www.npmjs.com/package/@aemforms/af-react-components)**
* **[@aemforms/af-response-renderer](https://www.npmjs.com/package/@aemforms/af-react-renderer)**
* **[@aemforms/af-core](https://www.npmjs.com/package/@aemforms/af-core)**

Todos esses componentes estão incluídos no Arquétipo AEM. Quando você cria um projeto AEM Archetype 37 ou posterior para formulários adaptáveis headless, a versão mais recente das bibliotecas listadas acima é incluída no projeto.

**Aplicativo Iniciado**: o Adobe também lançou um aplicativo iniciado para ajudá-lo a começar rapidamente com formulários adaptáveis headless.

<!-- **View Library (UI Layer)**: A custom form application built in a front-end language. You can use react, Angular, Flutter, NPM, Vue.js, Ionic, BootStrap, or any other language to built front end. You can also use the Headless adaptive forms Super Component, provided out-of-the-box, inside a react application to render a Headless adaptive form. Headless adaptive forms super component makes use of OOTB react spectrum -based form components to render the Headless adaptive form. 

Core-Components: It enables use to render an Adaptive Form using JSON structure. It uses rule grammar to help create dynamic field interactions. The rule grammar is based on [JSON formula](http://github.com/adobe/json-formula/). You can develop your own renderer or embed the React based Adaptive Forms renderer, provided OOTB, in your front-end app to render the form. -->

**Storybook**: [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) fornece uma visão geral de diferentes componentes de formulários adaptáveis headless. Também fornece uma lista de todos os componentes compatíveis, suas propriedades correspondentes e restrições.

**Extensão de Código do Visual Studio**: [Extensão do Visual Studio Code](visual-studio-code-extension-for-headless-adaptive-forms.md) para ajudar a criar uma estrutura JSON válida. Ele fornece suporte e validação do IntelliSense para a estrutura JSON de formulários, juntamente com funções comuns, como adicionar, excluir ou renomear componentes de uma estrutura JSON.

**Especificações da versão 2.0 do Forms adaptável**: a especificação Adaptive Forms versão 2.0 fornece informações detalhadas sobre todos os componentes, restrições e métodos disponíveis para definir formulários adaptáveis headless. A especificação está disponível em [PDF](/help/assets/Headless-Adaptive-Form-Specification.pdf) formato.

**APIs HTTP e JavaScript**: [APIs HTTP](https://opensource.adobe.com/aem-forms-af-runtime/api/) permite listar, buscar, validar, enviar e rastrear o status de envio de formulários headless. [APIs JS](https://opensource.adobe.com/aem-forms-af-runtime/jsdocs/) O ajuda a usar formulários adaptáveis headless com qualquer estrutura de interface do usuário baseada em JavaScript.

**Fórmula JSON**: é uma implementação da gramática de expressão de formulários para ajudar a consultar a estrutura JSON e criar regras para formulários adaptáveis headless. A gramática é um mashup de funções e operadores semelhantes a planilhas e [JMESPath](https://jmespath.org/) uma linguagem de consulta JSON. Você pode usar o [playground](https://opensource.adobe.com/json-formula/dist/index.html) para explorar a sintaxe e os recursos da fórmula JSON.
