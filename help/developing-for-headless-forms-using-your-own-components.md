---
title: Usar componentes personalizados para renderizar um formulário headless
description: Saiba como criar componentes personalizados e mapeá-los a campos do Forms adaptável headless. Este guia explica como mapear componentes por tipo de campo e tipo de recurso para obter renderização e comportamento personalizados.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
index: true
exl-id: 5aba1821-35dc-4da4-b188-d4853d64d5ee
source-git-commit: 86129488bec7faed87600a237ac034ca1b601187
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# Usar componentes personalizados para renderizar um formulário headless {#developing-for-headless-forms-using-your-own-components}

No Headless Adaptive Forms, você pode criar e implementar componentes personalizados para definir a aparência e a funcionalidade de seus formulários. Embora os componentes padrão forneçam comportamento padrão, você pode precisar de elementos ou interações específicas da interface do usuário, como um componente &quot;Anúncio&quot; personalizado ou um campo &quot;Assinatura Escrita&quot; especializado.

Este artigo orienta você na criação de um componente React personalizado e no mapeamento dele para o formulário adaptável headless.

## &#x200B;1. Criar um componente de reação personalizado

Primeiro, crie o componente React que renderizará seu campo de formulário. Esse componente pode usar qualquer biblioteca do React (como interface de usuário de material, design do Ant ou seus próprios estilos personalizados).

Por exemplo, vamos criar um componente **Anúncio** personalizado que renderiza uma mensagem somente leitura com estilo específico.

1. Navegue até o diretório de componentes do projeto React (por exemplo, `src/components`).
2. Crie uma nova pasta e um novo arquivo para o componente, por exemplo `Announcement/index.tsx`.
3. Implemente o componente. Ele deve aceitar o `props` compatível com o tempo de execução do Forms Headless (normalmente recebendo o estado do campo).

```tsx
import React from 'react';
import { useRuleEngine } from '@aemforms/af-react-renderer';
import { FieldJson, State } from '@aemforms/af-core';

const Announcement = function (props: State<FieldJson>) {
    // The useRuleEngine hook connects the component to the form logic
    const [state, handlers] = useRuleEngine(props);

    if (!state.visible) {
        return null;
    }

    return (
        <div className="custom-announcement" style={{ border: '1px solid #ccc', padding: '10px', backgroundColor: '#f9f9f9' }}>
            <h3>{state?.label?.value}</h3>
            <p>{state?.default}</p>
        </div>
    );
}

export default Announcement;
```

## &#x200B;2. Mapear o componente personalizado

Para usar seu componente personalizado, você deve mapeá-lo no arquivo `mappings.ts`. O tempo de execução do Forms Headless usa esse mapeamento para determinar qual componente do React deve ser renderizado para cada campo no formulário JSON.

Há duas formas principais de mapear componentes: por **Tipo de Campo** ou por **Tipo de Recurso**.

### Mapeamento por tipo de campo

O mapeamento padrão é baseado na propriedade `fieldType` no Formulário JSON (por exemplo, `text-input`, `checkbox`, `button`). Isso é útil quando você deseja substituir *todas* as instâncias de um componente padrão pela sua versão personalizada.

1. Abra `src/utils/mappings.ts` (ou onde seus mapeamentos estiverem definidos).
2. Importe seu componente personalizado.
3. Adicione-o ao objeto de mapeamentos usando a `fieldType` como chave.

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  "text-input": Announcement // This would replace ALL text-input fields (use with caution)
};

export default customMappings;
```

### Mapeamento por tipo de recurso (componentes personalizados)

Se você criou um componente personalizado no AEM (por exemplo, um componente &quot;Anúncio&quot; que estende um componente de Texto padrão) e deseja renderizar *somente* esse componente específico de forma diferente no aplicativo React, mapeie-o pelo **Tipo de recurso** ou por um identificador exclusivo.

Essa abordagem permite que você tenha componentes de Texto padrão renderizados normalmente, enquanto seu componente &quot;Anúncio&quot; personalizado usa sua implementação especializada do React.

1. Identifique o identificador exclusivo do componente. No JSON de Formulário Headless, ele geralmente é encontrado na propriedade `:type` ou em um `fieldType` personalizado, se configurado.
2. Adicione o mapeamento usando esse identificador.

```typescript
import { mappings } from "@aemforms/af-react-components";
import Announcement from "../components/Announcement";

const customMappings: any = {
  ...mappings,
  // Map by resource type or custom identifier
  "my-project/components/announcement": Announcement
};

export default customMappings;
```

> **Observação:** certifique-se de que o modelo de formulário do AEM exporte o `:type` ou identificador correto que corresponda à chave usada em `mappings.ts`.

## &#x200B;3. Aplicar os mapeamentos

Por fim, verifique se a instância de Formulário headless usa esses mapeamentos personalizados.

```tsx
import React from 'react';
import { AdaptiveForm } from '@aemforms/af-react-renderer';
import customMappings from './utils/mappings';
import formJSON from './form-def.json';

function App() {
  return (
    <AdaptiveForm
      formJson={formJSON}
      mappings={customMappings}
    />
  );
}

export default App;
```

Ao seguir essas etapas, você pode estender os recursos do seu Forms adaptável headless com componentes que correspondem a seu design específico e requisitos funcionais.
