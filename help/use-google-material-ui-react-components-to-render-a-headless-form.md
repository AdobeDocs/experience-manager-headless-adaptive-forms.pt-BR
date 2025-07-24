---
title: Use os componentes de reação da interface do usuário de material do Google para renderizar um formulário headless
description: Saiba como usar os componentes do Google Material-UI React para renderizar um formulário headless. Este guia abrangente o orienta pelo processo passo a passo para criar componentes personalizados do Headless Adaptive Forms para mapear e usar os componentes do Google Material-UI React para estilizar um formulário adaptável headless.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: 476509d5-f4c1-4d1c-b124-4c278f67b1ef
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '870'
ht-degree: 0%

---


# Usar uma biblioteca de reação personalizada para renderizar um formulário headless

<!-- This article is completely missing the image ALT tags (descriptions) for each added image asset. That is impacting the CQI score for Experience Manager in a negative way. Be sure you add the required missing image ALT tags.  -->

Você pode criar e implementar componentes personalizados para personalizar a aparência e a funcionalidade (Comportamento) de seus formulários adaptáveis headless, de acordo com os requisitos e as diretrizes de sua organização.

Esses componentes atendem a dois objetivos principais: controlar a aparência ou o estilo dos campos de formulário e armazenar os dados coletados por meio desses campos na instância do modelo de formulário. Se isso parecer confuso, não se preocupe - você explorará esses propósitos com mais detalhes em breve. Por enquanto, vamos nos concentrar nas etapas iniciais de criação de componentes personalizados, renderização do formulário usando esses componentes e uso de eventos para salvar e enviar dados para um endpoint REST.

Neste tutorial, os componentes da interface do usuário de materiais do Google são empregados para demonstrar como renderizar um formulário adaptável headless usando componentes personalizados do React. No entanto, você não está limitado a esta biblioteca e pode usar qualquer biblioteca de componentes do React ou desenvolver seus próprios componentes personalizados.

Na conclusão deste artigo, o formulário _Fale Conosco_ criado em [Crie e publique um formulário headless usando o kit inicial](create-and-publish-a-headless-form.md), o artigo se transforma no seguinte:

![](assets/headless-adaptive-form-with-google-material-ui-components.png)


As principais etapas envolvidas no uso dos componentes da interface do usuário de material do Google para renderizar um formulário são:

![](assets/headless-forms-graphics-source-main.svg)

## &#x200B;1. Instalar a interface do usuário de material do Google

Por padrão, o kit inicial usa os componentes [Espectro](https://spectrum.adobe.com/) da Adobe. Vamos configurá-lo para usar a [Interface do usuário de material do Google](https://mui.com/):

1. Verifique se o kit inicial não está em execução. Para interromper o kit inicial, abra o terminal, navegue até o **react-starter-kit-aem-headless-forms** e pressione Ctrl-C (é o mesmo no Windows, Mac e Linux®).

   Não tente fechar o terminal. Fechar o terminal não interrompe o kit inicial.

1. Execute o seguinte comando:

```shell
    
    npm install @mui/material @emotion/react @emotion/styled --force
    
```

Ele instala as bibliotecas npm da interface do usuário do Google Material e adiciona as bibliotecas às dependências dos kits de início. Agora você pode usar os componentes da Interface do usuário do material para renderizar componentes de formulário.


## &#x200B;2. Criar componentes personalizados do React

Vamos criar um componente personalizado que substitua o componente padrão [entrada de texto](https://spectrum.adobe.com/page/text-field/) pelo componente [Campo de texto da interface do usuário de material do Google](https://mui.com/material-ui/react-text-field/).

É necessário um componente separado para cada tipo de componente ([fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-json-properties-fieldtype--text-input) ou `:type`) usado em uma definição de Formulário Headless. Por exemplo, no formulário Fale Conosco criado na seção anterior, os campos Nome, Email e Telefone do tipo `text-input` ([fieldType: &quot;text-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def)) e o campo de mensagem é do tipo `multiline-input` ([&quot;fieldType&quot;: &quot;multiline-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/reference-json-properties-fieldtype--multiline-input)).


Vamos criar um componente personalizado para sobrepor todos os campos de formulário que usam a propriedade [fieldType: &quot;text-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def) com o componente [Campo de texto da interface do usuário do material](https://mui.com/material-ui/react-text-field/).


Para criar o componente personalizado e mapear o componente personalizado com a propriedade [fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def) :

1. Abra o diretório **react-starter-kit-aem-headless-forms** em um editor de código e navegue até `\react-starter-kit-aem-headless-forms\src\components`.


1. Crie uma cópia da pasta **`slider`** ou **`richtext`** e renomeie a pasta copiada como **materialtextfield**. O `slider` e o `richtext` são dois componentes personalizados de amostra disponíveis no aplicativo inicial. Você pode usar esses componentes para criar seus próprios componentes personalizados.

   ![O componente personalizado materialtextfield em VSCode](/help/assets/richtext-custom-component-in-vscode.png)

1. Abra o arquivo `\react-starter-kit-aem-headless-forms\src\components\materialtextfield\index.tsx` e substitua o código existente pelo código abaixo. Este código retorna e renderiza um componente [Campo de texto da interface do usuário do material do Google](https://mui.com/material-ui/react-text-field/).

```JavaScript
 
     import React from 'react';
     import {useRuleEngine} from '@aemforms/af-react-renderer';
     import {FieldJson, State} from '@aemforms/af-core';
     import { TextField } from '@mui/material';
     import Box from '@mui/material/Box';
     import { richTextString } from '@aemforms/af-react-components';
     import Typography from '@mui/material/Typography';


     const MaterialtextField = function (props: State<FieldJson>) {

         const [state, handlers] = useRuleEngine(props);

         return(

         <Box>
             <Typography component="legend">{state.visible ? richTextString(state?.label?.value): ""} </Typography>
             <TextField variant="filled"/>
         </Box>

         )
     }

     export default MaterialtextField;
```


A parte `state.visible` verifica se o componente está definido para ser visível. Se for, o rótulo do campo será recuperado e exibido usando `richTextString(state?.label?.value)`.

![](/help/assets/material-text-field.png)


Seu componente personalizado `materialtextfield` está pronto. Vamos definir este componente personalizado para substituir todas as instâncias de [fieldType: &quot;text-input&quot;](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/docs/adaptive-form-components-text-input-field--def) com o Campo de texto da interface do usuário de material do Google.

## &#x200B;3. Mapear componente personalizado com campos de formulário headless

O processo de usar componentes de biblioteca de terceiros para renderizar campos de formulário é conhecido como mapeamento. Você mapeia cada ([fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-json-properties-fieldtype--text-input)) para um componente correspondente de uma biblioteca de terceiros.

Todas as informações relacionadas ao mapeamento são adicionadas ao arquivo `mappings.ts`. A instrução `...mappings` no arquivo `mappings.ts` se refere aos mapeamentos padrão, que sobrepõem o ([fieldType](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-json-properties-fieldtype--text-input) ou `:type`) com componentes do [Adobe Spectrum](https://spectrum.adobe.com/page/text-field/).

Para adicionar mapeamento para o componente `materialtextfield`, criado na última etapa:

1. Abra o arquivo `mappings.ts`.

1. Adicione a seguinte instrução de importação para incluir o componente `materialtextfield` no arquivo `mappings.ts`:


   ```JavaScript
       import MaterialtextField from "../components/materialtextfield";
   ```

1. Adicione a seguinte instrução para mapear o `text-input` com o componente materialtextfield.


   ```JavaScript
       "text-input": MaterialtextField
   ```

   O código final do arquivo é semelhante ao seguinte:

   ```JavaScript
         import { mappings } from "@aemforms/af-react-components";
         import MaterialtextField from "../components/materialtextfield";
   
   
         const customMappings: any = {
           ...mappings,
           "text-input": MaterialtextField
        };
        export default customMappings;
   ```

1. Salve e execute o aplicativo. Os três primeiros campos do formulário são renderizados usando o [Campo de Texto da Interface do Usuário do Material do Google](https://mui.com/material-ui/react-text-field/):

   ![](assets/material-text-field-form-rendetion.png)


   Da mesma forma, você pode criar componentes personalizados para campos de mensagem (&quot;fieldType&quot;: &quot;multiline-input&quot;) e classificar os campos de serviço (&quot;fieldType&quot;:&quot;number-input&quot;). Você pode clonar o seguinte repositório Git para componentes personalizados da mensagem e classificar os campos de serviço:

   [https://github.com/singhkh/react-starter-kit-aem-headless-forms](https://github.com/singhkh/react-starter-kit-aem-headless-forms)

## Próxima etapa

Você renderizou o formulário com sucesso com componentes personalizados que usam a interface do usuário de materiais do Google. Você tentou enviar o formulário clicando no botão Enviar (mapeado com o componente de interface do usuário do material do Google correspondente)? Caso contrário, vá em frente e experimente.

O formulário está enviando os dados para alguma fonte de dados? Não? Não se preocupe. O motivo é que o formulário não está configurado para se comunicar com a biblioteca de tempo de execução.

Como você pode configurar o formulário para se comunicar com ele? Em breve, virá um artigo explicando tudo em detalhes. Fique atento!
