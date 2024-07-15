---
title: Crie formulários envolventes usando componentes principais e a tecnologia headless
seo-title: Build Engaging Forms Using Core Components and Headless
description: Crie formulários envolventes usando componentes principais e a tecnologia headless
seo-description: Build Engaging Forms Using Core Components and Headless
topic-tags: develop
exl-id: ef99ffe9-4a37-4f0a-a4d3-78976c92220f
source-git-commit: bcc51bcae3b26cf20e7c0b5b75935bf69a991731
workflow-type: tm+mt
source-wordcount: '2452'
ht-degree: 85%

---

# Crie um Forms envolvente usando os Componentes principais e o Forms adaptável headless no AEM Forms as a Cloud Service {#build-engaging-forms-using-core-components-and-headless}

## Visão geral do laboratório {#lab-overview}

Neste laboratório prático, você aprenderá:

Como usar o AEM Forms para criar adaptive forms de forma fácil, utilizando os componentes principais mais atuais e consistentes com o AEM Sites, e como habilitar experiências de captura de dados omnicanal por meio da entrega de formulários adaptáveis como formulários headless para canais da web, móveis e de bate-papo. Você também aprenderá as práticas recomendadas de estilo, personalização e desenvolvimento do front-end.

## Principais aprendizados {#key-takeaways}

* **Agilidade comercial**: como um usuário empresarial, posso criar uma experiência de formulário para múltiplos canais de forma fácil.

* **Liberdade para o desenvolvedor de front-end**: como um desenvolvedor de front-end, posso controlar a experiência do usuário final utilizando formulários headless.

* **Velocidade do desenvolvedor**: como desenvolvedor, posso personalizar os componentes do Sites e formulários de forma fácil e consistente.

## Pré-requisitos {#prerequisites}

Para usar estas mãos no laboratório:

* Instale a [última versão do Git](https://git-scm.com/downloads). Se você é novo no Git, consulte [Instalando o Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

* Instale o [Node.js 16.13.0 ou posterior](https://nodejs.org/en/download/). Se você é novo no Node.js, consulte [Como instalar o Node.js](https://nodejs.org/en/learn/getting-started/how-to-install-nodejs).

* [Habilite os Componentes principais adaptáveis do Forms](enable-headless-adaptive-forms-and-core-components-on-forms-cloud-service.md) para o seu ambiente as a Cloud Service AEM Forms.

* Instale o [Microsoft Visual Studio Code](https://code.visualstudio.com/download) ou qualquer editor de texto simples. Os exemplos no documento usam o Microsoft Visual Studio Code.



## Lição 1 {#lesson-1}

### Objetivo {#lesson-1-objectives}

Familiarizar-se com o ambiente do AEM Forms as a Cloud Service.

### Contexto da lição {#lesson-1-context}

Nesta lição, você poderá se familiarizar com o AEM Forms as a Cloud Service ao navegar pela interface.

### Exercício {#lesson-1-excercise}

1. Abra o navegador e insira a URL do ambiente de autor do Cloud Service. Por exemplo:
   [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/start.html](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/start.html)

1. Faça logon no ambiente de autor do Cloud Service.
   ![](/help/assets/screenshot2028113829.png){width="50%" align="left"}

1. Para navegar até a interface do usuário do AEM Forms, clique em **Forms > Forms e Documentos**.



   ![](/help/assets/screenshot2028113929.png){width="50%" align="left"}

   Ignore qualquer pop-up relacionado às preferências ou informações. Todos os formulários disponíveis serão exibidos.


## Lição 2

### Objetivo

Criar um formulário adaptável utilizando os componentes principais mais recentes, configurá-lo e enviá-lo.

### Contexto da lição

Nesta lição, você atuará como um usuário empresarial e criará um adaptive form para vários canais, como Web, dispositivos móveis e bate-papo, usando componentes principais padronizados e prontos para uso na captura de dados.

### Exercício

1. Crie um ponto de acesso de envio para o formulário:

   1. Abra <https://requestbin.com/> em uma nova guia do navegador.
   1. Clique em **Criar um compartimento público** e copie a URL do ponto de acesso.
      ![](/help/assets/screenshot2028114329.png){width="50%" align="left"}

      ![](/help/assets/screenshot202023-03-0120at206.10.0020pm.png){width="50%" align="left"}

1. Crie um formulário adaptável usando a interface do assistente:

   1. Na guia do navegador utilizada na lição 1, acesse a interface web do AEM Forms as a Cloud Service e navegue até Formulários e documentos.
      ![](/help/assets/screenshot2028114029.png)

   1. Clique em **Criar** e selecione Formulário adaptável.
      ![](/help/assets/screenshot2028114629.png)

   1. Selecione o modelo **Em branco com componentes principais** na tela de seleção de modelos, conforme mostrado abaixo:
      ![](/help/assets/screenshot202023-03-0120at206.09.1520pm.png)

   1. Clique na guia **Estilo** e selecione o tema **wknd-theme**, conforme mostrado abaixo:
      ![](/help/assets/screenshot202023-03-0120at206.09.2320pm.png)

   1. Clique na guia **Envio**, selecione o cartão **Enviar para o ponto de extremidade REST** e especifique o compartimento público no campo **URL da solicitação POST**, conforme mostrado abaixo:
      ![](/help/assets/screenshot202023-03-0120at206.09.5320pm.png)

   1. Clique em **Criar**. Especifique um nome e um título para o formulário. Por exemplo, **registro**. Clique em **Criar**.

   1. O editor de formulário adaptável é aberto. Ignore quaisquer pop-ups ou caixas de diálogo de preferências ou informações. Clique no navegador de componentes no painel à esquerda e adicione os componentes **Cabeçalho** e **Rodapé** respectivamente à parte superior e inferior do formulário em branco.
      ![](/help/assets/screenshot2028121929.png)

   1. Arraste e solte componentes do navegador Componentes para criar um formulário, semelhante ao seguinte:

      ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}

1. Adicionar validações ao formulário:

   1. Clique no componente **Número de telefone** para que o menu pop-up seja exibido. Clique no **ícone de ferramenta** no menu para configurar o campo.

   1. Abra a **guia de validações**, marque o campo **Obrigatório** e clique em **Concluído**. A mensagem de sucesso é exibida.
      ![](/help/assets/screenshot2028123529.png){width="50%" align="left"}

      ![](/help/assets/screenshot2028123629.png){width="50%" align="left"}

1. Visualize e envie o formulário.

   1. Clique em **Visualizar** para visualizar o formulário pela perspectiva do usuário final.

   1. Preencha o formulário com dados fictícios.

   1. Envie o formulário.
      ![](/help/assets/screenshot2028125729.png)

   1. Na guia Solicitar compartimento, verifique os dados enviados.
      ![](/help/assets/screenshot2028125829.png)

1. Adicionar interatividade ao formulário com regras:

   1. Clique no **Marque a caixa para receber o componente com 5% de desconto**. Na barra de ferramentas de opções, clique no ícone Regras. A opção Editor de regras é aberta.

   1. Criar uma regra, quando a opção **Marcar a caixa para receber 5% de desconto** estiver selecionada, as opções para aplicar cartão de crédito serão desabilitadas.

1. Publish o formulário.

   1. Abra a interface de gerenciamento do AEM Forms, por exemplo, `https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments`, e selecione o formulário.

   1. Clique em **Publicar**.

      ![](/help/assets/screenshot2028115629.png)

      A mensagem de sucesso é exibida.

      ![](/help/assets/screenshot2028115729.png)

      A URL de publicação do formulário seria semelhante a `https://publish-p105303-e986623.adobeaemcloud.com/content/forms/af/registration.html`.

   1. Para exibir o formulário publicado, substitua a ID do programa (pXXXXXX) e a ID do ambiente (eXXXXXX) na URL acima pelas IDs do seu 
ambiente.

## Lição 3

### Objetivo

Atualizar os estilos usando práticas recomendadas de desenvolvimento de front-end.

### Contexto da lição

Nesta lição, como um desenvolvedor de front-end, você aprenderá a atualizar facilmente o estilo do formulário adaptável criado anteriormente.

### Exercício

Configure o repositório local do tema:

1. Abra o prompt de comando ou o shell com direitos de administrador:

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. No prompt de comando, use o seguinte comando para navegar até a pasta **c:\git**

   ```Shell
   cd c:\git
   ```

1. Use o seguinte comando para clonar o código de front-end do tema:

   ```Shell
   git clone -b WKND https://github.com/adobe/aem-forms-theme-canvas
   ```


1. Use o seguinte comando na ordem listada para navegar até o diretório **aem-forms-theme-canvas** e abra o Visual Studio Code.

   ```Shell
   cd aem-forms-theme-canvas
   code .
   ```

   ![](/help/assets/screenshot2028126029.png)

1. Selecione **Confiar nos autores de todos os arquivos da pasta pai** e clique em **Sim, eu confio nos autores**.

   ![](/help/assets/screenshot2028116229.png){width="50%" align="left"}

1. Para renderizar o formulário hospedado no ambiente de publicação do Cloud Service, renomeie o arquivo `env_template`.  Para renomear o arquivo, clique com o botão direito no arquivo **env_template** e selecione a opção **Renomear**.

   ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}

   </br>

   ![](/help/assets/screenshot2028116529.png){width="50%" align="left"}

1. Defina os seguintes valores para as variáveis no arquivo .env e salve o arquivo:

   * **AEM_URL**: especifica o ambiente de publicação do Cloud Service. Por exemplo, `https://publish-p105303-e986623.adobeaemcloud.com/`

   * **AEM_ADAPTIVE_FORM**: especifica o caminho do formulário. Por exemplo, se o caminho do formulário for `/content/forms/af/registration`, o valor dessa variável será `registration`.

     ![](/help/assets/screenshot2028116429.png){width="50%" align="left"}

1. Criar um usuário local no ambiente AEM.

   >[!NOTE]
   > Para criar um usuário local:
   > Ir para `AEM Home` > `Tools` > `Security` > `Users`
   > Certifique-se de que o usuário é membro do grupo de usuários de formulários.


1. Na janela do prompt de comando, execute o seguinte comando:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028117029.png)

   >[!NOTE]
   >
   > * Se você receber uma mensagem solicitando a atualização do npm por meio do comando `npm notice Run npm nstall -g npm@9.6.0`, ignore a mensagem.
   > * Não execute outros comandos de npm, a menos que seja instruído na pasta de trabalho.

1. Em seguida, execute o seguinte comando para visualizar o formulário.

   ```Shell
   npm run live
   ```

   ![](/help/assets/screenshot2028117229.png)

   Depois que o comando acima for executado, aguarde a mensagem `webpack compiled` e você será redirecionado para uma página de logon AEM.

1. Clique em **Fazer logon localmente (somente Tarefas de administrador)** na página de logon do AEM.
1. Insira as credenciais para o usuário local criado e o formulário será exibido em uma guia do navegador.

   >[!NOTE]
   >
   >Se uma tela em branco for exibida no navegador após executar o comando `npm run live` por mais de 3 a 4 minutos, altere o `localhost` na URL do navegador para 127.0.0.1 e pressione **Enter**.


   ![](/help/assets/screenshot2028115129.png){width="50%" align="left"}


1. No Visual Studio Code, abra o arquivo `PROJECT\src\site\_variables.scss`. Observe que a cor do `$error` é um tom de VERMELHO.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. No navegador, envie o formulário para ver a cor vermelha no campo **Nome**.

   ![](/help/assets/screenshot2028120829.png)

1. Defina a cor do **$error** para **#5736eb** e salve o arquivo.

   ![](/help/assets/screenshot2028120729.png){width="50%" align="left"}

1. Atualize o navegador e envie o formulário. Observe que a cor do erro no campo de nome foi alterada de acordo.

   ![](/help/assets/screenshot2028121129.png)

1. No prompt de comando, pressione **CTRL+C**, insira **Y** e pressione **Enter** para encerrar o processo do npm. É importante parar o servidor do npm para evitar conflitos nos próximos exercícios.
1. Feche as janelas do Visual Studio Code e do prompt de comando.

## Lição 4

### Objetivo

Renderizar o formulário para web/dispositivos móveis e outras interfaces como um formulário headless.

### Contexto da lição

Nesta lição, como um desenvolvedor de front-end, você aprenderá a renderizar o formulário adaptável criado anteriormente como um formulário headless usando a estrutura de design do React Spectrum.

### Exercício

Configure o repositório local usando o projeto inicial do React:

1. Abra o prompt de comando usando direitos de administrador.

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}

1. No prompt de comando, use o seguinte comando para navegar até a pasta **c:\git**

   ```Shell
   cd c:\git
   ```

1. Use o seguinte comando para clonar o projeto inicial de formulário adaptável do React:

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

Para renderizar o formulário hospedado no ambiente de publicação do Cloud Service:

1. Renomeie o arquivo env_template para .env. Para renomear, clique com o botão direito no arquivo **env_template** e selecione a opção **Renomear**.

   ![](/help/assets/screenshot2028117629.png){width="50%" align="left"}

   ![](/help/assets/screenshot2028117729.png)

1. Defina os seguintes valores para as variáveis no arquivo .env. Depois de atualizar as variáveis, salve o arquivo.

   * **AEM_URL**: especifica a URL do ambiente de publicação do Cloud Service. Por exemplo, `https://publish-p105303-e986623.adobeaemcloud.com`

   * **AEM_FORM_PATH**: especifica o caminho do formulário adaptável criado na lição anterior. Por exemplo, `/content/forms/af/registration/`

     ![](/help/assets/screenshot202023-03-0820at202.49.1820pm.png)

1. Abra a janela de comando, verifique se você está no diretório react-starter-kit-aem-headless-forms e execute o seguinte comando:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028118029.png)


1. Na janela do prompt de comando, execute o seguinte comando:

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028118129.png)

   O comando acima inicia um servidor de desenvolvimento local que renderiza a definição de formulário obtida do AEM através do método headless usando a biblioteca de front-end do React Spectrum.

   >[!NOTE]
   >
   > 
   > Se uma tela em branco for exibida no navegador após executar o comando `npm start` por mais de 3 a 4 minutos, altere o `localhost` na URL do navegador para 127.0.0.1 e pressione **Enter**.

   ![](/help/assets/screenshot2028118229.png)

Vamos verificar a execução das regras neste formulário headless:

1. Selecione a opção **Marque a caixa para receber 5% de desconto**. A opção subsequente para utilizar o cartão de crédito será desativada.

   ![](/help/assets/screenshot2028126229.png)

1. Desmarque a opção **Marque a caixa para receber 5% de desconto** para ativar a opção do cartão de crédito.

   ![](/help/assets/screenshot2028126329.png)

Vamos fazer alterações no formulário no servidor como um usuário empresarial e vejamos como elas são aplicadas automaticamente no formulário headless.

1. Abra a interface de gerenciamento do AEM Forms no navegador. Por exemplo, [https://author-p105303-e986623.adobeaemcloud.com/ui#/aem/aem/forms.html/content/dam/formsanddocuments](https://author-p105303-e986623.adobeaemcloud.com/ui%23/aem/aem/forms.html/content/dam/formsanddocuments).

1. Selecione o formulário **contatos** e clique em **Editar.** Isso abre o formulário no editor de adaptive forms.


1. Selecione o campo **Número de telefone** e clique no **ícone Editar (ícone de Lápis)** na barra de ferramentas. Se não conseguir visualizar o pop-up da barra de ferramentas, alterne para o modo de edição clicando no botão **Editar** na parte superior direita, à esquerda do botão **Visualizar**.

   ![](/help/assets/screenshot2028119629.png)

1. Altere o rótulo para Número do celular. Clique em qualquer espaço vazio no formulário e as alterações serão salvas.

   ![](/help/assets/screenshot2028119729.png)

Vamos publicar o formulário atualizado para propagar as alterações no ambiente de publicação.

1. Na guia da interface de gerenciamento do AEM Forms, selecione o formulário de registro e clique em **Desfazer a publicação**. Se não estiver vendo o botão **Desfazer a publicação**, pule para a etapa 3 para publicar as alterações diretamente.

1. Clique em **Desfazer a publicação**. Clique em **Fechar** na caixa de diálogo correspondente.

1. Depois que o navegador for atualizado, selecione o formulário de registro e clique em **Publicar**.

1. Clique em **Publicar**. Clique em **Fechar** na caixa de diálogo correspondente.

1. Atualize a guia do navegador que contém o formulário headless exibido. Observe que o rótulo Número de telefone foi alterado para Número de celular.

   ![](/help/assets/screenshot2028120529.png)

1. Abra a janela do prompt de comando usada para iniciar o projeto **response-starter-kit-aem-headless**, pressione **CTRL+C**,
digite **Y** e pressione Enter para encerrar o processo do npm. É importante parar o servidor do npm para evitar conflitos nos próximos exercícios.

1. Feche as janelas do Visual Studio Code e do prompt de comando.


## Lição 5

### Objetivo

Renderizar o formulário como um formulário headless usando a interface do Google Material

### Contexto da lição

Nesta lição, como um desenvolvedor de front-end, você aprenderá a renderizar o formulário adaptável criado anteriormente como um formulário headless usando a interface do Google Material.

### Exercício

Configure o repositório local usando o projeto inicial da interface do Material:

1. Abra o prompt de comando usando direitos de administrador.

   ![](/help/assets/screenshot2028115829.png){width="50%" align="left"}


1. No prompt de comando, use o seguinte comando para navegar até a pasta **c:\git**:

   ```Shell
   cd c:\git
   ```

1. Execute os seguintes comandos na ordem listada para criar uma pasta chamada mui e navegue até ela usando os seguintes comandos:

   ```Shell
   mkdir mui
   
   cd mui
   ```

1. Use o seguinte comando para clonar o projeto inicial de formulário adaptável do React:

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

Para renderizar o formulário hospedado no ambiente de publicação do Cloud Service:

1. Renomeie o arquivo **env_template** para **.env**. Para renomear, clique com o botão direito no arquivo **env_template** e selecione **Renomear**.

   ![](/help/assets/screenshot2028126629.png){width="50%" align="left"}

1. Defina os seguintes valores para as variáveis no arquivo .env. Depois de atualizar as variáveis, salve o arquivo. Use as teclas **CTRL+S** para salvar o arquivo.

   * **AEM_URL**: especifica a URL do ambiente de publicação do Cloud Service. Por exemplo, [https://publish-p105303-e986623.adobeaemcloud.com](https://publish-p105303-e986623.adobeaemcloud.com/)

   * **AEM_FORM_PATH**: especifica o caminho do formulário adaptável criado na lição anterior. Por exemplo, /content/forms/af/registration/

     ![](/help/assets/screenshot2028126929.png)

1. Abra a janela de comando, verifique se você está no diretório **react-starter-kit-aem-headless-forms** e execute o seguinte comando:

   ```Shell
   npm install
   ```

   ![](/help/assets/screenshot2028127029.png)

1. Na janela do prompt de comando, execute o seguinte comando:

   ```Shell
   npm start
   ```

   ![](/help/assets/screenshot2028127129.png)

   O comando inicia um servidor de desenvolvimento local e renderiza a definição de formulário obtida do AEM através do método headless usando a biblioteca 
de front-end da interface do Google Material.

   >[!NOTE]
   >
   >Se uma tela em branco for exibida no navegador após executar o comando `npm start` por mais de 3 a 4 minutos, altere o `localhost` na URL do navegador para 127.0.0.1 e pressione **Enter**.

   ![](/help/assets/screenshot2028127229.png)

1. Para avaliar a execução da mesma lógica de negócios nesta representação de formulário:

   Selecione **Marque a caixa para receber 5% de desconto**. A opção subsequente **Deseja preencher um Formulário de cartão de crédito corporativo da We.Finance?** será desativada.

   ![](/help/assets/screenshot2028127329.png){width="50%" align="left"}

## Lição 6

### Objetivo

Criar uma aparência alternativa para o formulário headless usando variações de componente da interface do Material

### Contexto da lição

Nesta lição, como um desenvolvedor de front-end, você aprenderá a criar uma representação alternativa de diferentes componentes usando a interface do Material para o formulário adaptável criado anteriormente pelo usuário empresarial.

### Exercício

Atualize a variação de componentes no projeto headless. Para alterar a variante do componente de entrada de texto da interface do Material para `OutlinedInput`:

1. No Visual Code, navegue até o componente de entrada de texto abrindo o arquivo `index.tsx` em `src/components/textinput/index.tsx`.

1. Adicione `//` no início da linha de código 103. Isso converte a linha em um comentário.

   ```Shell
   //const Cmp = \'outlined\' === appliedCssClassNames ? OutlinedInput: Input;
   ```

1. Adicione a seguinte informação na linha 104 para usar uma variante diferente do componente e salve o arquivo. Use as teclas **CTRL+S** para salvar o arquivo.

   ```Shell
   const Cmp = OutlinedInput;
   ```

   ![](/help/assets/screenshot2028127629.png)

   É essencial organizar corretamente as letras maiúsculas na variante “OutlinedInput”, caso contrário a compilação falhará. A compilação do ambiente de desenvolvimento local é iniciada automaticamente no prompt de comando. Aguarde até ver a seguinte mensagem

   `webpack 5.75.0 compiled with 3 warnings in 6659 ms`
   `inside proxy req`
   `setting new origin header`

1. Atualize o navegador; se ele não for atualizado automaticamente, utilize uma variante diferente para ver o componente de entrada de texto.

   ![](/help/assets/screenshot2028127729.png)


   Essa alteração ocorre para usuários finais sem qualquer alteração na definição do formulário no servidor do AEM Forms, e é específica para o 
canal headless que está sendo considerado. Por exemplo, o canal da Web neste laboratório.

   ![](/help/assets/screenshot2028127529.png){width="50%" align="left"}


1. Feche as janelas do Visual Studio Code e do prompt de comando.

## Perguntas frequentes

+++ O Assistente de formulário adaptável está disponível publicamente?

Sim, ele está disponível com o AEM Forms as a Cloud Service.

+++


+++ Os componentes principais estão disponíveis publicamente?

Sim, os componentes principais dos formulários adaptáveis estão disponíveis com o AEM Forms as a Cloud Service.

+++

+++ Os formulários headless estão disponíveis publicamente?

Sim, os formulários headless estão disponíveis com o AEM Forms as a Cloud Service.

+++

+++ Os formulários headless exigem uma licença separada?

Não, os formulários headless usam a mesma métrica de valor de licenciamento: o número de envios de formulários.

+++

+++ Os componentes principais e formulários headless estão disponíveis com o AEM Forms 6.5?

Sim, os componentes principais dos adaptive forms e os formulários headless estão disponíveis para o Pacote de serviços 16 do AEM Forms 6.5 e versões posteriores.

+++


## Próximas etapas

Agora que aprendeu a criar adaptive forms e entregá-los a vários canais usando formulários headless, você deve tentar colocar suas novas habilidades em ação. Divirta-se e prossiga com a criação e a entrega de experiências excepcionais de captura de dados em escala para seus usuários finais, onde quer que eles estejam.

## Recursos

* [Introdução aos componentes principais de formulários adaptáveis](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=pt-br)

* [Criar um formulário adaptável usando componentes principais](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html?lang=pt-br)

* [Atualizar estilo do formulário adaptável baseado em componentes principais](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/using-themes-in-core-components.html?lang=pt-br)

* [Headless adaptive forms](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=pt-br)

* [Uso do kit inicial headless do React](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/get-started/create-and-publish-a-headless-form.html?lang=pt-br)
