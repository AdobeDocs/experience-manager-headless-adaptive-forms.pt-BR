---
title: Crie formulários envolventes usando componentes principais e a tecnologia headless
description: Crie um Forms envolvente usando os Componentes principais e o headless.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
topic-tags: develop
hide: true
exl-id: 07a71aac-de38-4839-b8d6-b47c3f575eb3
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '2134'
ht-degree: 40%

---

# Crie Forms envolvente usando componentes principais e Forms adaptável headless no AEM 6.5 Forms {#build-engaging-forms-using-core-components-and-headless}

<!-- This article and many others in this entire repo are completely missing the image ALT tags (descriptions) for each added image asset. That is impacting the CQI score for Experience Manager in a negative way. Be sure you take the time to add the required missing image ALT tags.  -->

## Visão geral do laboratório {#lab-overview}

Neste laboratório prático, você aprenderá a usar o AEM Forms com os Componentes principais mais recentes — alinhados com o AEM Sites — para criar formulários adaptáveis rapidamente. Forneça esses formulários como experiências headless para canais da Web, móveis e de bate-papo, para obter uma captura de dados omnicanal contínua. Você também aprenderá as práticas recomendadas de estilo, personalização e desenvolvimento do front-end.

## Principais aprendizados {#key-takeaways}

* **Agilidade comercial**: como um usuário empresarial, posso criar uma experiência de formulário para múltiplos canais de forma fácil.

* **Liberdade para o desenvolvedor de front-end**: como um desenvolvedor de front-end, posso controlar a experiência do usuário final utilizando formulários headless.

* **Velocidade do desenvolvedor**: como desenvolvedor, posso personalizar os componentes do Sites e formulários de forma fácil e consistente.

## Antes de começar {#pre-requisites}

Para usar este laboratório prático:

* Instale a [última versão do Git](https://git-scm.com/downloads). Se você é novo no Git, consulte [Instalando o Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* Instalar o [Node.js 16.13.0 ou posterior](https://nodejs.org/en/download/). <!-- URL IS 404! If you are new to Node.js, see [How to install Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs).-->

* [Habilite o Forms Adaptável Headless](enable-headless-adaptive-forms-and-core-components.md) no ambiente do AEM 6.5 Forms.

* Instale o [Microsoft Visual Studio Code](https://code.visualstudio.com/download) ou qualquer editor de texto simples. Os exemplos neste documento usam o Microsoft Visual Studio Code.

## Lição 1 {#lesson-1}

### Objetivo {#lesson-1-objectives}

Familiarize-se com o ambiente Forms do AEM 6.5.

### Contexto da lição {#lesson-1-context}

Nesta lição, você se familiariza com o AEM 6.5 Forms navegando na interface do usuário.

### Exercício {#lesson-1-excercise}

1. Abra o navegador e insira o URL do ambiente do autor. Por exemplo:
   [https://localhost:4502](https://localhost:4502).

1. Após fazer o logon, acesse a interface do AEM Forms. Clique em **Formulários**.

   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

1. Clique em **Formulários e documentos**. Ignore quaisquer pop-ups relacionados a preferências ou informações.

   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   Todos os formulários disponíveis serão exibidos.

   ![](/help/assets/screenshot2028114029.png){width="50%" align="left"}

## Lição 2

### Objetivo

Crie um Formulário adaptável usando os Componentes principais mais recentes, configure e envie o formulário.

### Contexto da lição

Como usuário empresarial, você usará o editor Forms adaptável e seus Componentes principais prontos para uso para criar um Formulário adaptável. Em seguida, você pode enviar o formulário para canais da Web, móveis e de chat para capturar dados.

### Exercício

1. Crie um ponto de acesso de envio para o formulário:

   1. Abra <https://pipedream.com/requestbin> em uma nova guia do navegador.
      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

   1. Clique em **Criar um compartimento público** e copie a URL do ponto de acesso.
      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

   Esse endpoint específico serve como exemplo para enviar e exibir dados. Na produção real, você usa seu próprio endpoint ou fontes de dados para armazenar os dados capturados.

1. Criar um formulário adaptável:

   1. Na guia do navegador usada na Lição 1, navegue até a interface da Web do AEM Forms e navegue até **Forms** > **Forms e Documentos**.

   1. Clique em **Criar** e selecione Formulário adaptável.
      ![](/help/assets/creating-adaptive-form-6-5.png){width="50%" align="left"}

   1. Selecione o modelo **Em branco com Componentes Principais** na tela de seleção de modelo como mostrado abaixo e clique em **Avançar**.
      ![](/help/assets/creating-adaptive-form-6-5-select-blank-template.png){width="50%" align="left"}

   1. Especifique `Contact us` como o **Título** do formulário. Verifique se o **Nome** do formulário é `contact-us`.
      ![](/help/assets/creating-adaptive-form-65-specify-title.png){width="50%" align="left"}

   1. Clique em **Criar**. Uma caixa de diálogo é exibida.

   1. Na caixa de diálogo, clique em **Editar**. O formulário é aberto no editor de Formulário adaptável. Ignore pop-ups ou caixas de diálogo para preferências ou informações.

   1. Abra o navegador Componentes e arraste e solte o componente Painel no meio da tela.

      ![](/help/assets/lab65-add-panel.png){width="50%" align="left"}

   1. Arraste e solte componentes do navegador Componentes para criar um formulário, semelhante ao seguinte:

      ![](/help/assets/contact-us-headless-adaptive-form.png){width="50%" align="left"}


   1. Abra o Navegador de Conteúdo, clique no ícone de propriedades do Contêiner do Guia e abra a guia **Envio**.

   1. Selecione a ação enviar **Enviar para o ponto de extremidade REST**

   1. Selecione a opção **Habilitar solicitação POST** e especifique o ponto de extremidade REST criado na lição 2 na caixa de texto **URL para solicitação POST** e clique no ícone **Concluído**.

      ![](/help/assets/configure-submit-action.png){width="50%" align="left"}

1. Publicar um formulário adaptável:

   1. Abra a interface do AEM, navegue até **Forms** > **Forms e Documentos**. Selecione o formulário criado na etapa anterior e clique em **`Publish`**.

   1. Na caixa de diálogo **Publicar Assets**, clique em **Publicar**. A mensagem de sucesso é exibida.

## Lição 3

### Objetivo

Atualizar os estilos usando práticas recomendadas de desenvolvimento de front-end.

### Contexto da lição

Nesta lição, como desenvolvedor front-end, você aprenderá como atualizar facilmente o estilo do Formulário adaptável criado anteriormente.

### Exercício

Configurar um repositório local do tema:

1. Abra o prompt de comando ou o shell com direitos de administrador:

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. No Prompt de Comando, use o seguinte comando para navegar até a pasta `c:\git`.

   ```Shell
   cd git
   ```

   Se a pasta não existir, use o comando `md git` para criá-la.

1. Use o seguinte comando para clonar o código de front-end do tema:

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```

1. Use o seguinte comando na ordem listada para navegar até o diretório **aem-forms-theme-canvas** e abra o Visual Studio Code.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png){width="50%" align="left"}

1. Selecione **Confiar nos autores de todos os arquivos da pasta pai** e clique em **Sim, eu confio nos autores**.

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. Renomeie o arquivo `env_template` como .env.  Para renomear o arquivo, clique com o botão direito no arquivo **env_template** e selecione a opção **Renomear**.

   ![](/help/assets/screenshot2028116429.png){width="30%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. Defina os seguintes valores para as variáveis no arquivo .env e salve o arquivo:

   * **AEM_URL**: especifique a URL de uma instância **publish**. Por exemplo, `https://localhost:4502/`

   * **AEM_ADAPTIVE_FORM**: especifique o nome do formulário. Por exemplo, `contact-us`.

   </br>

   ![](/help/assets/lab65-theme-environment-variable.png)


1. Na janela do prompt de comando, execute o seguinte comando:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * Se você receber uma mensagem solicitando a atualização de `npm` por meio do comando `npm notice Run npm nstall -g npm@9.6.0`, ignore a mensagem.
   > * A menos que você seja instruído na pasta de trabalho, não execute outros comandos `npm`.

1. Agora, execute o seguinte comando para visualizar o formulário.

   ```Shell
   npm run live
   ```

   ![](/help/assets/screenshot2028117229.png)

   Depois que o comando acima for executado, aguarde a mensagem `webpack compiled`. O formulário é exibido em uma guia do navegador.

   >[!NOTE]
   >
   >Se você passar por uma tela em branco no navegador após executar o comando `npm run live` por mais de 3 a 4 minutos, altere `localhost` na URL do navegador para 127.0.0.1 e pressione **Enter**.


   ![](/help/assets/contact-us-headless-adaptive-form-with-canvas-theme.png){width="50%" align="left"}


1. No Visual Studio Code, abra o arquivo `PROJECT\src\site\_variables.scss`. Observe que a cor do `$error` é um tom de VERMELHO.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. No navegador, envie o formulário para ver a cor vermelha no campo **Nome**.

   ![](/help/assets/error-color-before.png)

1. Defina a cor do **$error** para **#5736eb** e salve o arquivo.

1. Atualize o navegador e envie o formulário. Observe que a cor do erro no campo de nome foi alterada de acordo.

   ![](/help/assets/error-color-after.png)

1. No Prompt de Comando, pressione **CTRL+C**, digite **Y** e pressione a tecla **Enter** para encerrar o processo npm. É importante parar o servidor do npm para evitar conflitos nos próximos exercícios.
1. Feche as janelas do Visual Studio Code e do prompt de comando.

## Lição 4

### Objetivo

Renderize o formulário para Web/interfaces móveis e outras interfaces como um formulário headless.

### Contexto da lição

Nesta lição, como desenvolvedor de front-end, você aprenderá a renderizar o Formulário adaptável criado anteriormente como um formulário headless usando uma estrutura de design do espectro React.

### Exercício

Configure um repositório local usando o projeto inicial do React:

1. Abra o prompt de comando usando direitos de administrador.

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. No Prompt de Comando, use o seguinte comando para navegar até a pasta `c:\git`.

   ```Shell
   cd git
   ```

1. Use o seguinte comando para clonar o projeto inicial do Formulário adaptável:

   ```Shell
   git clone https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028117329.png)

1. Use os seguintes comandos na ordem listada para navegar até o diretório **react-starter-kit-aem-headless-forms** e abra o Visual Studio Code.

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028117529.png)


   A janela do Visual Studio Code é aberta.

   ![](/help/assets/screenshot2028117429.png){width="50%" align="left"}

Para renderizar o formulário hospedado em seu ambiente de publicação:

1. Renomeie o arquivo env_template para o arquivo .env. Para renomear, clique com o botão direito no arquivo **env_template** e selecione a opção **Renomear**.

   ![](/help/assets/screenshot2028117629.png){width="30%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. Defina os seguintes valores para as variáveis no arquivo .env. Depois de atualizar as variáveis, salve o arquivo.

   * **AEM_URL**: especifique a URL do ambiente de publicação. Por exemplo, `https://localhost:4503/`

   * **AEM_FORM_PATH**: especifique o caminho do Formulário adaptável criado na lição anterior. Por exemplo, `/content/forms/af/contact-us/`

   </br>

   ![](/help/assets/lab65-starter-kit-environment-variable.png)

1. Abra a janela de comando, verifique se você está no diretório **react-starter-kit-aem-headless-forms** e execute o seguinte comando:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. Na janela do prompt de comando, execute o seguinte comando:

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-starter-kit-start.png)

   O comando acima inicia um servidor de desenvolvimento local que renderiza a definição de formulário obtida do AEM através do método headless usando a biblioteca de front-end do React Spectrum.

   >[!NOTE]
   >
   > 
   > Se você passar por uma tela em branco no navegador após executar o comando `npm start` por mais de 3 a 4 minutos, altere `localhost` na URL do navegador para 127.0.0.1 e pressione **Enter**.

   ![](/help/assets/headless-adaptive-form-lab.png)

Vamos fazer alterações no formulário no servidor como um usuário empresarial e vejamos como elas são aplicadas automaticamente no formulário headless.

1. Abra a interface de gerenciamento do AEM Forms no navegador. Por exemplo, [http://localhost:4502/aem/forms.html/content/dam/formsanddocuments](http://localhost:4502/aem/forms.html/content/dam/formsanddocuments).

1. Selecione o formulário **Fale Conosco** e clique em **Editar.** Ele abre o formulário no editor Adaptive Forms.


1. Selecione o campo **Número do contato** e clique no **ícone Editar (ícone de Lápis)** na barra de ferramentas. Se você não conseguir ver a barra de ferramentas pop-up, alterne para o modo Editar. Clique no botão **Editar** na parte superior direita, à esquerda do botão **Visualizar**.

   ![](/help/assets/change-field-title.png){width="50%" align="left"}

1. Altere o rótulo para **Número de celular**. Clique em qualquer espaço vazio no formulário e as alterações serão salvas.

Vamos publicar o formulário atualizado para propagar as alterações para o ambiente publicado.

1. Na guia da interface de gerenciamento do AEM Forms, selecione o formulário Contate-nos e clique em **Cancelar publicação**. Se não estiver vendo o botão **Desfazer a publicação**, pule para a etapa 3 para publicar as alterações diretamente.


1. Clique em **Desfazer a publicação**. Clique em **Fechar** na caixa de diálogo correspondente.

1. Depois que o navegador for atualizado, selecione o formulário Contate-nos e clique em **Publicar**.


1. Clique em **Publicar**. Clique em **Fechar** na caixa de diálogo correspondente.

1. Atualize a guia do navegador que contém o formulário headless exibido. Aviso: o rótulo Número de contato foi alterado para Número de celular.

   ![](/help/assets/headless-adaptive-form.png)

1. Abra a janela do prompt de comando usada para iniciar o projeto **response-starter-kit-aem-headless**, pressione **CTRL+C**,
digite **Y** e pressione Enter para encerrar o processo do npm. É importante parar o servidor do npm para evitar conflitos nos próximos exercícios.

1. Feche as janelas do Visual Studio Code e do prompt de comando.


## Lição 5

### Objetivo

Renderizar o formulário como um formulário headless usando a interface do Google Material

### Contexto da lição

Nesta lição, como desenvolvedor front-end, você aprenderá a renderizar o formulário adaptável criado anteriormente como um formulário headless usando a interface do usuário do material do Google.

### Exercício

Configure um repositório local usando o projeto inicial da interface do Material:

1. Abra o prompt de comando usando direitos de administrador.

   ![](/help/assets/screenshot2028115829.png){width="30%" align="left"}

1. No Prompt de Comando, use o seguinte comando para navegar até a pasta `c:\git`.

   ```Shell
   cd git
   ```

1. Execute os seguintes comandos na ordem listada para criar uma pasta chamada `mui` e navegar até a pasta `mui` usando os seguintes comandos:

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. Use o seguinte comando para clonar o projeto inicial do Formulário adaptável:

   ```Shell
   git clone -b mui-lab https://github.com/adobe/react-starter-kit-aem-headless-forms
   ```

   ![](/help/assets/screenshot2028126529.png)

1. Use o seguinte comando na ordem listada para navegar até a pasta **react-starter-kit-aem-headless-forms** e abra o código no Visual Studio Code:

   ```Shell
   cd react-starter-kit-aem-headless-forms
   
   code .
   ```

   ![](/help/assets/screenshot2028126829.png)

Para renderizar o formulário hospedado em seu ambiente de publicação:

1. Renomeie o arquivo **env_template** para o arquivo **.env**. Para renomear, clique com o botão direito no arquivo **env_template** e selecione **Renomear**.

   ![](/help/assets/screenshot2028126629.png){width="30%" align="left"}

1. Defina os seguintes valores para as variáveis no arquivo .env. Depois de atualizar as variáveis, salve o arquivo. Use as teclas **CTRL+S** para salvar o arquivo.

   * **AEM_URL**: especifique a URL do ambiente de publicação. Por exemplo, [https://localhost:4503](https://localhost:4503)

   * **AEM_FORM_PATH**: especifique o caminho do Formulário adaptável criado na lição anterior. Por exemplo, /content/forms/af/contact-us/


1. Abra a janela de comando, verifique se você está no diretório **react-starter-kit-aem-headless-forms** e execute o seguinte comando:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. Na janela do prompt de comando, execute o seguinte comando:

   ```Shell
   npm start
   ```

   ![](/help/assets/lab65-mui-starter-kit-start.png)

   O comando inicia um servidor de desenvolvimento local e renderiza a definição do formulário obtido do AEM de forma headless usando a biblioteca de front-end da interface do usuário do material do Google.

   >[!NOTE]
   >
   >Se você passar por uma tela em branco no navegador após executar o comando `npm start` por mais de 3 a 4 minutos, altere `localhost` na URL do navegador para 127.0.0.1 e pressione **Enter**.

   ![](/help/assets/google-mui-form.png)

## Lição 6

### Objetivo

Criar uma aparência alternativa para o formulário headless usando variações de componente da interface do Material

### Contexto da lição

Como desenvolvedor front-end, você aprenderá a criar versões alternativas da interface do usuário do Material para vários componentes nesta lição. Você também as aplicará ao Formulário adaptável que o usuário empresarial criou anteriormente.

### Exercício

Atualize a variação de componentes no projeto headless. Para alterar a variante do componente de entrada de texto da interface do Material para `OutlinedInput`:

1. No Visual Code, navegue até o componente de entrada de texto abrindo o arquivo `index.tsx` em `src/components/textinput/index.tsx`.

1. Adicione `//` no início da linha de código 104. Isso converte a linha em um comentário.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Adicione o seguinte na linha 105 para usar uma variante diferente do componente e salvar o arquivo. Use as teclas **CTRL+S** para salvar o arquivo.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/aem65-lab-code-update.png)

   É essencial usar capitalização correta para a variante &quot;OutlineInput&quot;, caso contrário, a compilação falhará. A compilação do ambiente de desenvolvimento local é iniciada automaticamente no prompt de comando. Aguarde até ver a seguinte mensagem

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. Atualize o navegador, se ele não for atualizado automaticamente, para ver o componente de entrada de texto usar uma variante diferente.

   ![](/help/assets/screenshot2028127729.png){width="50%" align="left"}


   Essa alteração ocorre para usuários finais sem qualquer alteração na definição do formulário no servidor do AEM Forms, e é específica para o 
canal headless que está sendo considerado. Por exemplo, um canal da Web neste laboratório.

   ![](/help/assets/aem65-lab-mui-style-update.png)


1. Feche as janelas do Visual Studio Code e do prompt de comando.

## Perguntas frequentes

+++ Os Componentes principais estão disponíveis publicamente?

Sim, os Componentes principais adaptáveis do Forms estão disponíveis com o AEM 6.5 Forms e o Forms as Cloud Service. Você precisa do AEM Forms 6.5 Service Pack 16 ou posterior para usar os componentes principais adaptáveis do Forms.

+++

+++ Os formulários headless exigem uma licença separada?

Não, os formulários headless usam a mesma métrica de valor de licenciamento: o número de envios de formulários.

+++




## Próximas etapas

Agora você sabe como criar formulários adaptáveis e entregá-los em canais com formulários headless. Use essas habilidades para criar experiências de captura de dados escaláveis e de alta qualidade onde quer que seus usuários estejam.

## Recursos

* [Introdução aos Componentes principais do formulário adaptável](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction)

* [Criar formulário adaptável usando os Componentes principais](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components)

* [Atualizar estilo do formulário adaptável baseado em componentes principais](https://experienceleague.adobe.com/pt-br/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components)

* [Forms Adaptável Headless](https://experienceleague.adobe.com/en/docs/experience-manager-headless-adaptive-forms/using/overview)

* [Usando um kit inicial Headless do React](https://experienceleague.adobe.com/en/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form)
