---
title: Noções básicas sobre formulários headless - conceitos e perguntas frequentes
description: Respostas a perguntas comuns sobre o que são formulários headless, como eles diferem das bibliotecas de formulários tradicionais, detalhes de implementação, controle da interface do usuário, desempenho e integração com estruturas e back-end.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: formulários headless, biblioteca de formulários headless, formulários adaptáveis, gerenciamento de estado, validação, sistema de design, SSR, CMS
hide: false
exl-id: a1b2c3d4-e5f6-7890-abcd-ef1234567890
source-git-commit: 780f06a39c75dbf8795ac7a971150410ed7981e9
workflow-type: tm+mt
source-wordcount: '2605'
ht-degree: 0%

---


# Noções básicas sobre formulários headless - conceitos e perguntas frequentes {#understanding-headless-forms}

Este guia responde a perguntas comuns sobre formulários headless em geral e como eles se aplicam ao AEM Headless Adaptive Forms. Use-a para decidir quando usar uma abordagem headless e como implementar, estilizar e integrar formulários em sua pilha.

## Noções básicas e noções básicas {#basics-understanding}

### O que exatamente é uma biblioteca de formulários headless?

Uma **biblioteca de formulários headless** é uma solução de formulário que separa a **lógica de formulário** (estado, validação, regras, envio) da **apresentação** (componentes e estilo da interface do usuário). O &quot;head&quot; é a interface do usuário do formulário visível; &quot;headless&quot; significa que a biblioteca não dita ou envia uma interface do usuário fixa. Em vez disso, ele expõe:

* Um **modelo de formulário** (geralmente JSON): estrutura, campos, restrições e regras.
* **APIs ou ganchos** para ler e atualizar o estado do formulário, executar a validação e manipular o envio.
* **Eventos e ciclo de vida** para que sua interface do usuário possa reagir às alterações.

No AEM Headless Adaptive Forms, o formulário é uma [estrutura JSON](architecture.md) hospedada no Adobe Experience Manager. O [Forms Web SDK](architecture.md#developer-tools) (tempo de execução do lado do cliente) fornece a camada lógica (processador de regras de negócios, gerenciamento de estado, validação), enquanto seu aplicativo fornece a interface do usuário que renderiza essa estrutura.

### Qual é a diferença entre um formulário headless e uma biblioteca de formulários tradicional?

| Aspecto | Biblioteca de formulários tradicional | Biblioteca de formulários headless |
|--------|---------------------------|------------------------|
| **IU** | É fornecido com componentes e estilos integrados | Nenhuma interface prescrita; você traz seus próprios componentes |
| **Estilo** | Theming ou substituições em componentes de biblioteca | Controle total; use seu sistema de design como está |
| **Definição de formulário** | Geralmente, somente código (componentes em JSX/HTML) | Geralmente orientado por dados (JSON/esquema da CMS ou API) |
| **Estado e validação** | Vinculado aos componentes da biblioteca | Exposto por meio de APIs/ganchos; qualquer interface do usuário pode se vincular a eles |
| **Canais** | Normalmente Web (às vezes uma estrutura) | A mesma definição de formulário pode direcionar Web, dispositivos móveis, bate-papo etc. |

Com o AEM Headless Adaptive Forms, você [cria e publica um formulário](create-and-publish-a-headless-form.md) uma vez no AEM; qualquer cliente (React, Angular, nativo móvel, chatbot) pode [buscar o formulário JSON](architecture.md) e renderizá-lo com a interface do usuário apropriada para esse canal.

### Por que devo usar formulários headless em vez de uma solução de formulário baseada em interface do usuário?

Os formulários headless são adequados quando você precisa:

* **Consistência do sistema de design** - Use os componentes e a marca existentes sem combater os padrões da biblioteca.
* **Multicanal** - Uma definição de formulário para Web, dispositivos móveis e outros pontos de contato (consulte [Visão geral](overview.md)).
* **Formulários orientados por CMS ou backend** - Os autores alteram a estrutura do formulário e as regras sem implantações de código; seu aplicativo apenas consome o JSON.
* **Flexibilidade de estrutura** - A biblioteca [AF-core](https://www.npmjs.com/package/@aemforms/af-core) é independente de estrutura; as associações React são fornecidas para conveniência, mas você pode criar associações para outras estruturas.
* **Recursos de back-end** - Aproveite o AEM Forms para preenchimento prévio, validação, envio, fluxos de trabalho e Modelo de Dados do Forms sem travar em uma pilha de interface do usuário específica.

### Quando faz sentido usar uma abordagem headless?

Usar formulários headless quando:

* Você tem ou deseja ter um sistema de design ou uma biblioteca de componentes fortes.
* Os Forms são criados por não desenvolvedores (por exemplo, em uma CMS) e devem funcionar em vários aplicativos ou canais.
* Você precisa da mesma lógica de formulário (validação, regras) entre clientes da Web, móveis ou outros.
* Você deseja minimizar as renderizações e manter a lógica de formulário testável independentemente da interface do usuário.

Considere uma biblioteca de formulários tradicional incluída na interface do usuário quando:

* Você precisa de um formulário de trabalho em um único aplicativo web rapidamente e não se importa com a interface personalizada ou com vários canais.
* Sua equipe prefere definir formulários somente no código em uma estrutura.

### &quot;headless&quot; é apenas um chavão ou resolve problemas reais?

Ele soluciona problemas reais de arquitetura:

* **Separação de interesses** - A estrutura do formulário, as regras e a validação ficam nos dados e em uma camada lógica; a camada da interface do usuário renderiza e envia apenas ações do usuário. Isso melhora a capacidade de teste e a reutilização.
* **Independência de canal** - Uma definição de formulário pode gerar interfaces do usuário diferentes (por exemplo, React, Web, React Native, Angular ou voz). O AEM Headless Adaptive Forms foi criado para isso: [crie uma vez, distribua no React, SPAs, Web, dispositivos móveis e muito mais](overview.md).
* **Criação sem código** - Os usuários empresariais podem alterar campos e regras no [Editor de formulário adaptável](create-a-headless-adaptive-form.md); os desenvolvedores não precisam reimplantar para alterações de conteúdo.
* **Integração com pilhas existentes** - Você mantém o sistema de design, o gerenciamento de estado e o roteamento; a camada headless lida apenas com o estado do formulário, a validação e o envio.

## Implementação e questões técnicas {#implementation-technical}

### Como os formulários headless gerenciam o estado?

No AEM Headless Adaptive Forms, o estado é gerenciado pelo **Forms Web SDK**:

* **Processador de regras de negócios** - Aceita o formulário JSON, gerencia o estado do campo e executa regras e manipuladores de eventos definidos no JSON.
* **Binder de reação** - Fornece ganchos (por exemplo, `useRuleEngine`) sobre o controlador para que os componentes do React recebam o estado atual e manipuladores; o mesmo estado pode ser consumido por interfaces do usuário não-React por meio das APIs principais.
* **State** inclui valores de campo, visibilidade, validade e quaisquer propriedades personalizadas definidas no modelo de formulário.

Seus componentes de interface recebem estado e manipuladores (por exemplo, `[state, handlers] = useRuleEngine(props)`); você renderiza a partir de `state` e chama `handlers` quando o usuário interage. O tempo de execução mantém o estado sincronizado com a definição e as regras do formulário. Consulte [Arquitetura](architecture.md) e [Usar componentes personalizados para renderizar um formulário headless](developing-for-headless-forms-using-your-own-components.md).

### Como a validação funciona em uma configuração de formulário headless?

A validação faz parte da camada lógica do formulário:

* **Restrições** são definidas no formato JSON (por exemplo, obrigatório, mínimo/máximo, padrão). O Forms Web SDK aplica essas restrições e expõe o estado de validação (por exemplo, mensagens de erro válidas/inválidas) aos seus componentes.
* A **validação no lado do cliente** é aplicada pela SDK com base na estrutura do formulário; sua interface do usuário exibe erros desde o estado.
* A **validação no lado do servidor** está disponível por meio das APIs do AEM (por exemplo, validar ponto de extremidade); você pode validar antes ou durante o envio.

Você não implementa a lógica de validação na interface do usuário, apenas exibe o estado de validação e as mensagens fornecidas pelo tempo de execução.

### É possível integrar formulários headless com validação de esquema (Yup, Zod, Joi)?

A validação integrada é orientada pelas restrições do formulário JSON. Para usar Yup, Zod, Joi ou similar:

* Você pode **derivar ou gerar** o JSON do formulário adaptável headless de seu esquema (por exemplo, converter o esquema JSON para formar JSON) para que uma fonte da verdade direcione a validação do esquema e a estrutura do formulário.
* Para **validação personalizada** além do formulário JSON, você pode executar seus próprios validadores (Yup/Zod/Joi) em manipuladores de eventos ou antes de enviar e enviar os resultados para o estado do formulário ou o envio do bloco. Os pontos de integração são os mesmos ganchos/APIs que você usa para o estado e envio.

A [Especificação adaptável do Forms](/help/assets/headless-adaptive-forms-specification.pdf) e a [Fórmula JSON](architecture.md) definem a regra e o modelo de restrição usados pelo tempo de execução.

### Como gerenciar a validação assíncrona (por exemplo, disponibilidade do nome de usuário)?

A validação assíncrona pode ser implementada na camada do aplicativo:

* Use **regras ou manipuladores de eventos** no formulário JSON (onde houver suporte) para acionar a lógica quando um campo for alterado.
* Em seus **componentes personalizados**, use os mesmos ganchos de estado/manipulador para chamar seu back-end (por exemplo, API de disponibilidade de nome de usuário) e, em seguida, atualize a validade do campo ou exiba um erro por meio das APIs de tempo de execução ou do estado local que você exibe na interface.
* Como alternativa, execute a verificação **em desfoque ou antes de enviar** e defina o estado do campo como inválido com uma mensagem personalizada se a verificação assíncrona falhar.

O padrão exato depende de como seu aplicativo se integra ao [processador de regra de negócio](architecture.md) e aos componentes personalizados.

### Como faço para enviar dados para APIs usando formulários headless?

O envio é dissociado da interface do usuário:

* **Ações de envio do AEM** - Você configura o formulário no AEM para enviar para endpoints, emails ou integrações REST (por exemplo, Microsoft Dynamics, Salesforce). O formulário é enviado por meio do AEM, que lida com a chamada HTTP/backend real. Consulte [Usar eventos para manipular e enviar dados de formulário](use-events-to-handle-and-submit-form-data.md).
* **Envio pelo lado do cliente** - Seu aplicativo pode ouvir o envio ou coletar dados de formulário do estado de tempo de execução e enviá-los para suas próprias APIs. As [APIs HTTP](https://opensource.adobe.com/aem-forms-af-runtime/api/) listam, buscam, validam, enviam e rastreiam o status do envio.
* **Preenchimento prévio** - Os dados podem ser preenchidos previamente por meio de pontos de extremidade REST ou do lado do servidor para que, quando o formulário for carregado, o estado já esteja preenchido. Consulte [Storybook - exemplo de preenchimento prévio](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data).

## Interface do usuário e controle de design {#ui-design-control}

### Posso usar meu próprio sistema de design ou biblioteca de componentes com formulários headless?

Sim. Esse é um benefício principal dos formulários headless. Com o AEM Headless Adaptive Forms:

* Você **mapeia** seus próprios componentes para o modelo de formulário (por tipo de campo ou tipo de recurso). Consulte [Usar componentes personalizados para renderizar um formulário headless](developing-for-headless-forms-using-your-own-components.md) e [Usar componentes React da Interface do Usuário de Material do Google para renderizar um formulário headless](use-google-material-ui-react-components-to-render-a-headless-form.md).
* O tempo de execução fornece **estado e manipuladores**; seus componentes são renderizados usando seu sistema de design e chamam os manipuladores para que a lógica do formulário permaneça sincronizada.
* Você pode usar o **Espectro de Reação**, a Interface do Usuário de Material, a Interface do Usuário do Chakra ou qualquer biblioteca de componentes personalizada; a [especificação](/help/assets/headless-adaptive-forms-specification.pdf) pode ser estendida para componentes personalizados (por exemplo, a Interface do Usuário do Chakra, o Vue.js). Consulte [Perguntas frequentes - estruturas personalizadas](faq.md#is-it-possible-to-use-headless-adaptive-forms-with-custom-frameworks).

### Os formulários headless fornecem suporte para acessibilidade (ARIA, manipulação de teclado)?

Acessibilidade implementada na **camada da interface** fornecida. A camada headless não renderiza o DOM, portanto, não adiciona comportamento ARIA ou do teclado por si só. Você obtém acessibilidade ao:

* Usar **componentes acessíveis** do sistema ou biblioteca de design (muitos incluem suporte para ARIA e teclado).
* Seguindo as **práticas recomendadas de acessibilidade** em seus componentes de campo personalizados (rótulos, mensagens de erro, gerenciamento de foco, navegação pelo teclado).
* Garantir que a estrutura do formulário e o estado recebido (por exemplo, obrigatório, inválido, visível) sejam refletidos nos atributos e comportamento ARIA dos componentes.

Se você usar os componentes prontos para uso baseados no Espectro React, você se beneficia da acessibilidade integrada.

### Como lidar com componentes complexos da interface do usuário (seletores de data, menus suspensos personalizados)?

Trate-os como **componentes personalizados** mapeados para os tipos de campo correspondentes ou tipos de recursos personalizados no formulário JSON:

* Implemente seu componente para aceitar o mesmo **props/state/handlers** que outros componentes de campo (por exemplo, via `useRuleEngine`).
* Use **state** para obter valor, visibilidade e validade; use **handlers** para atualizar o valor e acionar a validação.
* Renderize o seletor de datas ou a lista suspensa personalizada com a biblioteca de interface escolhida; ao alterar, chame o manipulador com o novo valor para que o estado do formulário permaneça correto.

Consulte [Usar componentes personalizados para renderizar um formulário headless](developing-for-headless-forms-using-your-own-components.md) para mapear por tipo de campo e tipo de recurso.

### Posso adicionar ou remover campos dinamicamente (formulários dinâmicos)?

A estrutura do formulário é definida pelo **formulário JSON** retornado do servidor. O comportamento dinâmico é alcançado por:

* **Regras no formulário JSON** - Mostrar/ocultar, habilitar/desabilitar ou definir valores com base em expressões. O [processador de regras de negócios](architecture.md) executa essas regras; seus componentes reagem a `state.visible` e semelhante.
* **Estrutura orientada pelo servidor** - Diferentes usuários ou contextos podem receber formulários JSON diferentes (por exemplo, etapas ou seções diferentes), portanto, &quot;dinâmico&quot; pode significar &quot;definição de formulário diferente por solicitação.&quot;
* **Alterações no lado do cliente** - Se o aplicativo puder modificar o modelo de formulário (por exemplo, adicionar/remover itens em uma estrutura repetível), o tempo de execução poderá refletir isso; a capacidade exata depende do esquema de formulário e das APIs de tempo de execução.

O [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) inclui exemplos de comportamento dinâmico.

### Como manipular campos condicionais (mostrar/ocultar com base na entrada)?

A visibilidade condicional é orientada por **regras** no formato JSON, avaliado pelo processador de regras de negócios. Você define condições (por exemplo, &quot;quando o campo A é igual a X, mostrar campo B&quot;); o tempo de execução atualiza o estado (por exemplo, `state.visible`). Seus componentes precisam apenas **respeitar o estado** (por exemplo, `if (!state.visible) return null;`). Nenhuma lógica extra da interface é necessária para mostrar/ocultar além da renderização do estado. O comportamento em cascata e condicional está documentado na [especificação Adaptive Forms](/help/assets/headless-adaptive-forms-specification.pdf) e é demonstrado no [Storybook - campos em cascata](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/adaptive-form-dynamic-behaviour--options&args=formJson.items[0].fieldType:drop-down;formJson.items[0].minimum:!undefined;formJson.items[0].maximum:!undefined;formJson.items[0].label.value:Choose+number+of+options;formJson.items[0].enum[0]:1;formJson.items[0].enum[1]:2;formJson.items[0].enum[2]:3;formJson.items[1].fieldType:drop-down). Consulte também [Perguntas frequentes - campos em cascata](faq.md#do-headless-adaptive-forms-support-cascading-fields).

## Desempenho e escalabilidade {#performance-scalability}

### Os formulários headless têm mais desempenho do que as bibliotecas de formulários tradicionais?

Elas podem ser, mas depende da implementação:

* **Atualizações direcionadas** - Um tempo de execução headless bem projetado atualiza somente o estado que foi alterado e notifica somente os componentes que dependem dele, o que pode reduzir renderizações desnecessárias em comparação a um componente de formulário monolítico.
* **Pacote de interface de usuário menor** - Você envia apenas os componentes de interface de usuário que usa (seu sistema de design), não um conjunto completo de componentes de biblioteca.
* **Carregamento lento** - O formulário JSON pode ser obtido quando necessário; o pacote inicial pode permanecer menor.

O desempenho também depende de como você implementa seus componentes (por exemplo, evitando renderizações desnecessárias, memorização).

### Como eles minimizam as renderizações?

* **Forma de estado** - O tempo de execução mantém o estado de formulário em uma estrutura que permite atualizações refinadas para que somente as partes afetadas da árvore precisem ser renderizadas novamente.
* **Design de ganchos** - Ganchos como `useRuleEngine` podem ser implementados para assinar componentes somente para o estado usado, portanto, as alterações pai ou irmão não forçam cada campo a ser renderizado novamente.
* **Sua responsabilidade** - você pode minimizar ainda mais as renderizações usando as práticas recomendadas do React (por exemplo, `React.memo`, retornos de chamada estáveis) em seus componentes personalizados.

### Os formulários headless são bem dimensionados para formulários grandes de várias etapas?

Sim, quando projetado adequadamente:

* **Definição de formulário** - Formulários grandes podem ser divididos em etapas ou seções no JSON; somente a etapa/seção visível pode precisar estar totalmente ativa na interface do usuário, com avaliação lenta das regras para seções ocultas, se houver suporte.
* **Estado** - O tempo de execução contém um estado de formulário coerente; a navegação de etapa está apenas mostrando/ocultando seções ou atualizando a &quot;etapa atual&quot; sem duplicar dados.
* **Bloqueio e carga lenta** - Você pode buscar o formulário JSON em partes ou carregar seções adicionais com antecedência para manter a carga inicial e o custo de análise baixos.

Para formulários muito grandes, considere a estrutura (por exemplo, etapas do assistente), as variantes de formulário orientadas pelo servidor e a medição da renderização e da execução de regras com cargas reais.

## Integração e ecossistema {#integration-ecosystem}

### Os formulários headless podem funcionar com Next.js / SSR / Ações do servidor?

* **Next.js / React** - Sim. O renderizador e os ganchos do React funcionam em um ambiente React. Usar o Forms Web SDK em componentes do cliente; buscar o formulário JSON no servidor ou cliente, conforme necessário.
* **SSR** - Você pode buscar o formulário JSON no servidor e passá-lo para o cliente para que o formulário se hidrata com os dados. A interatividade de formulários (estado, validação, regras) é executada no cliente onde o SDK é carregado. Evite renderizar campos de formulário que dependem do estado somente do cliente durante o SSR ou use um espaço reservado que se hidrata no cliente.
* **Ações do Servidor (Next.js)** - Você pode chamar Ações do Servidor do seu manipulador de envio: quando o usuário envia, seu código de cliente coleta dados do formulário (do estado headless) e chama uma Ação do Servidor em vez de ou além dos pontos de extremidade de envio do AEM.

### Como os formulários headless se integram ao CMS, ao comércio headless ou aos sistemas de back-end?

* **CMS** - O AEM é o CMS para a definição de formulário: os autores criam e publicam o formulário JSON. Outros CMSs podem fazer referência ou vincular à URL/API do formulário. Seu aplicativo busca o formulário do AEM (ou um CDN) e, opcionalmente, extrai uma cópia ou layout de outra CMS.
* **Preencher e enviar** - [Preencher previamente](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--prefill-form-with-personalised-data) e enviar podem atingir pontos de extremidade REST, para que você possa preencher previamente de um back-end de CRM, DAM ou comércio e enviar para o mesmo sistema ou para sistemas diferentes. A AEM Forms também oferece suporte a [Microsoft Dynamics e Salesforce](faq.md), REST, email e ações de envio personalizadas.
* **Modelo de Dados do Forms** - A AEM Forms fornece um Modelo de Dados do Forms para conectar-se a diferentes fontes de dados; formulários headless podem usar esses recursos para preenchimento prévio, validação e envio sem que você mesmo crie todas as integrações.

Para cenários móveis e offline, a abordagem recomendada é [criar seu próprio aplicativo e buscar definições de formulário por meio da API Headless Adaptive Forms](mobile-forms-best-practices.md).

## Consulte também: {#see-also}

* [Visão geral](overview.md)
* [Arquitetura](architecture.md)
* [Perguntas frequentes](faq.md)
* [Criar e publicar um formulário headless](create-and-publish-a-headless-form.md)
* [APIs de formulários adaptáveis headless](https://opensource.adobe.com/aem-forms-af-runtime/api/)
* [Playground de código](https://experienceleague.adobe.com/landing/aem-headless-forms/developer/code.html?lang=pt-BR)
* [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/)
