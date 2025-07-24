---
title: Crie seu primeiro formulário adaptável headless
description: Crie seu primeiro formulário adaptável headless.
keywords: headless, formulário adaptável
hide: true
exl-id: 99985fed-4a34-47d6-bb6f-79f81e1cd71b
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '1492'
ht-degree: 3%

---

# Crie seu primeiro formulário adaptável headless

Use os formulários adaptáveis sem periféricos do Adobe Experience Manager para criar aplicativos de formulários usando a interface do usuário front-end, como o React, e use o Forms Web SDK para recursos como gerenciamento de estado, validação e integrações com vários outros pontos de contato.

Por exemplo, uma organização da We.Org está procurando digitalizar sua jornada de inscrição de clientes. Seus desenvolvedores são versados em usar o Angular para criar soluções de front-end. Eles buscam criar um front-end personalizado e, ao mesmo tempo, transferir a validação de formulários e assinaturas eletrônicas para soluções especializadas.

Os formulários adaptáveis headless do Adobe Experience Manager oferecem a essas organizações a liberdade de criar formulários usando sua experiência existente em idiomas de front-end, além de fornecer suporte para usar recursos de back-end para criar uma experiência de formulários de nível empresarial.

<!-- >>[!VIDEO](https://video.tv.adobe.com/v/341011/) -->

<!--  ![Create a Headless adaptive form](/help/assets/headless-forms.png) -->

## Antes de começar

* Configure o [ambiente de desenvolvimento](setup-development-environment.md) para permitir que você crie e teste um Formulário adaptável headless em seu computador local.
* Os softwares a seguir devem ser instalados em sua máquina de desenvolvimento local:
   * [Java Development Kit 11](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html?1_group.propertyvalues.property=.%2Fjcr%3Acontent%2Fmetadata%2Fdc%3AsoftwareType&1_group.propertyvalues.operation=equals&1_group.propertyvalues.0_values=software-type%3Atooling&fulltext=Oracle%7E+JDK%7E+11%7E&orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&orderby.sort=desc&layout=list&p.offset=0&p.limit=14)
   * [Versão mais recente do Git](https://git-scm.com/downloads). Se você é novo no Git, consulte [Instalando o Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
   * [Node.js 16.13.0 ou posterior](https://nodejs.org/en/download/). <!-- URL is 404! If you are new to Node.js, see [How to install Node.js](https://nodejs.dev/en/learn/how-to-install-nodejs). -->
   * [Maven 3.6 ou posterior](https://maven.apache.org/download.cgi). Se você é novo no Maven, consulte [Instalando o Apache Maven](https://maven.apache.org/install.html).


## Usar o projeto de arquétipo para criar um formulário adaptável headless

O projeto do arquétipo é um modelo baseado no Maven. Ele cria um projeto mínimo com base na prática recomendada para começar a usar formulários adaptáveis headless. Ele também inclui a funcionalidade de formulários adaptáveis headless para Forms as a Cloud Service e ambientes de desenvolvimento local. É obrigatório criar e implantar o projeto baseado no arquétipo 37 ou posterior durante a fase beta. Após a versão beta, o projeto seria necessário somente para personalizações.

Execute as seguintes etapas para criar e renderizar seu primeiro formulário adaptável headless:

1. [Criar e implantar um projeto baseado no Arquétipo do AEM](#create-an-archetype-based-project)
1. [Implantar o projeto no AEM SDK](#deploy-the-project-to-a-local-development-environment)
1. [Crie um esquema JSON do formulário adaptável headless e carregue-o para sua instância do AEM SDK](#create-add-json-representation-of-headless-adaptive-forms)
1. [Criar um formulário adaptável com base no modelo em branco com componentes principais](#create-adaptive-form-with-blank-with-core-components-template)


### &#x200B;1. Criar e implantar um projeto baseado no Arquétipo do AEM {#create-an-archetype-based-project}

Dependendo do sistema operacional, execute o comando abaixo para criar um projeto do Experience Manager Forms as a Cloud Service. Use a versão 37 ou posterior do arquétipo. Consulte a [Documentação do arquétipo](https://experienceleague.adobe.com/pt-br/docs/experience-manager-core-components/using/developing/archetype/overview) para encontrar a versão mais recente do Arquétipo.

**Microsoft Windows**

1. Abra o prompt de comando com privilégios Administrativos (Execute o prompt de comando ou bash shell como administrador)
1. Execute o comando abaixo:

   ```shell
     mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate ^
     -D archetypeGroupId=com.adobe.aem ^
     -D archetypeArtifactId=aem-project-archetype ^
     -D archetypeVersion=37 ^
     -D appTitle=myheadlessform ^
     -D appId=myheadlessform ^
     -D groupId=com.myheadlessform ^
     -D includeFormsenrollment="y" ^
     -D includeFormsheadless="y" 
   ```

   * Defina `appTitle` para definir o título e os grupos de componentes.
   * Defina `appId` para definir o Maven artifactId, os nomes do componente, da configuração e da pasta de conteúdo, e os nomes da biblioteca do cliente.
   * Defina `groupId` para definir o Maven groupId e o Pacote Java Source.
   * Use a opção `includeFormsenrollment=y` para incluir configurações específicas do Forms, temas, modelos, Componentes principais e dependências necessárias para criar o Forms adaptável.
   * Use a opção `includeFormsheadless=y` para incluir os Componentes principais do Forms e as dependências necessárias para incluir a funcionalidade Forms adaptável headless. Ao ativar essa opção, as seguintes opções são incluídas:
      * O modelo **Em branco com componentes principais** com [componentes principais](https://experienceleague.adobe.com/pt-br/docs/experience-manager-core-components/using/introduction).
      * Um módulo de front-end do React, `ui.frontend.react.forms.af`. Ele ajuda a renderizar um Formulário adaptável headless em um aplicativo do react.


**Apple macOS ou Linux®**:

1. Abra o terminal como um usuário raiz. Permite executar comandos com privilégios administrativos. Você também pode usar o comando `sudo root` depois de abrir a janela do terminal para executar comandos com privilégios administrativos.
1. Execute o comando abaixo:

   ```shell
     mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
     -D archetypeGroupId=com.adobe.aem \
     -D archetypeArtifactId=aem-project-archetype \
     -D archetypeVersion=37 \
     -D appTitle=myheadlessform \
     -D appId=myheadlessform \
     -D groupId=com.myheadlessform \
     -D includeFormsenrollment="y" \
     -D includeFormsheadless="y"  
   ```

   * Defina `appTitle` para definir o título e os grupos de componentes.
   * Defina `appId` para definir o Maven artifactId, o componente, a configuração, os nomes da pasta de conteúdo e os nomes da biblioteca do cliente.
   * Defina `groupId` para definir o Maven groupId e o Pacote Java Source.
   * Use a opção `includeFormsenrollment=y` para incluir configurações específicas do Forms, temas, modelos, Componentes principais e dependências necessárias para criar o Forms adaptável.
   * Use a opção `includeFormsheadless=y` para incluir os Componentes principais do Forms e as dependências necessárias para incluir a funcionalidade Forms adaptável headless. Ao ativar essa opção, as seguintes opções são incluídas:
      * O modelo **Em branco com componentes principais** com [componentes principais](https://experienceleague.adobe.com/pt-br/docs/experience-manager-core-components/using/introduction).
      * Um front-end reage com o módulo, `ui.frontend.react.forms.af`. Ele ajuda a renderizar um Formulário adaptável headless em um aplicativo do react.

Após a conclusão bem-sucedida do comando, uma pasta de projeto com o nome especificado em `appID` é criada. Por exemplo, se você usar `appID` com valor `myheadlessform`, uma pasta chamada `myheadlessform` será criada. Ele contém o projeto baseado em Arquétipo.


### &#x200B;2. Implantar o projeto no AEM SDK {#deploy-the-project-to-a-local-development-environment}

Quando você implanta o projeto na sua instância do AEM SDK, ele adiciona a funcionalidade Headless Adaptive do Forms, o modelo **Em branco com componentes principais** e outros recursos incluídos no projeto para o seu ambiente de desenvolvimento. <!-- Deploy the project to your local development environment to locally create Headless Adaptive Forms. or deploy directly to your Forms as a Cloud Service environment. !--> Para implantar em sua instância do AEM SDK:

1. Abra o prompt de comando. Se você estiver no Windows, abra o prompt de comando com privilégios Administrativos (Execute o prompt de comando ou o [Git bash shell](https://khushwantsehgal.wordpress.com/2022/06/29/check-if-git-bash-is-running-in-administrator-mode/) como administrador).

1. Navegue até o diretório do projeto criado na etapa anterior. Por exemplo, `/myheadlessform`

   ![diretório-projeto](assets/project-directory.png)

1. Execute o seguinte comando:

   ```shell
   mvn -PautoInstallPackage clean install
   ```

   Aguarde a mensagem &quot;BUILD SUCCESS&quot;.
   ![Projeto implantado com êxito](assets/project-deployed-successfully.png)

   Pode levar muito tempo para resolver as dependências e implantar o projeto. Se houver uma falha na implantação do projeto, consulte o artigo [solução de problemas](troubleshooting.md) para obter os problemas comuns e sua resolução.


<!-- *  To learn how to deploy code to AEM as a Cloud Service, see the video in [Deploying to AEM as a Cloud Service]https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=pt-BR#coding-against-the-right-aem-version) article : -->


### &#x200B;3. Crie um esquema JSON de formulário adaptável headless e carregue-o para sua instância do AEM SDK {#create-add-json-representation-of-headless-adaptive-forms}

Um Forms adaptável headless é representado como um arquivo JSON. Você pode obter um formulário de exemplo do [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--contact) ou usar as inclusões de formulário de exemplo no projeto de arquétipo em `[Archetype Project]\ui.content\src\main\content\jcr_root\content\dam\myheadlessform\af_model_sample.json`. Este documento usa o formulário [introdução](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction) do Storybook. É um formulário de campo único para ajudar você a começar rapidamente a usar o Headless Adaptive Forms. <!-- The [specifications](/help/assets/Headless-Adaptive-Form-Specification.pdf) document provides detailed information about various components, rules, and constraints for Headless Adaptive Forms -->

Para criar e fazer upload do esquema:

1. Crie um arquivo de texto sem formatação com a extensão `.json`. Por exemplo, `myfirstform.json`. Você pode criar o arquivo em qualquer lugar no seu sistema de arquivos ou no projeto baseado no Arquétipo do AEM em `\<project-name>\ui.content\src\main\content\jcr_root\content\dam\myheadlessform\<formname>.json`
1. Adicione o seguinte conteúdo JSON ao arquivo `.json` e salve-o:

   ```JSON
   {
     "adaptiveform": "0.10.0",
     "items": [
       {
         "fieldType": "text-input",
         "label": {
           "value": "Enter your Name"
         },
         "name": "textInput"
       }
     ],
     "metadata": {
       "grammar": "json-formula-1.0.0",
       "version": "1.0.0"
     }
   }
   ```

   Ele adiciona um único campo ao formulário:

   ![Olá, Mundo](assets/introduction.png)

1. Faça logon em sua [instância local do AEM SDK](setup-development-environment.md#setup-author-instance)
1. Navegue até Adobe Experience Manager > Forms > Forms e Documentos. Toque em Criar > Upload de arquivo.
1. Selecione o `.json` criado na etapa 2 e carregue-o. Você está pronto para criar o Formulário adaptável headless. Se você salvar o arquivo .json no seu projeto baseado no Arquétipo AEM em `\<project-name>\ui.content\src\main\content\jcr_root\content\dam\myheadlessform\<formname>.json`. Você pode usar o `mvn -PautoInstallPackage clean install` para implantar o projeto no seu SDK AEM e o `<formname>.json` junto com ele.

Se houver uma falha no carregamento do `.json`, verifique se o [projeto do Arquétipo do AEM foi implantado com êxito](#deploy-the-project-to-a-local-development-environment).

<!-- 1. Open the [contact form](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--contact) and tap the [![Raw](assets/raw.png)](faq.md#storybook-example) icon on bottom-right side of the Storybook page to view the source code of the headless . 

You can use [Adaptive Forms builder extension for Visual Studio Code](/help/setup-development-environment.md#microsot-visual-studio-code-extension-for-headless-adaptive-forms) to build a JSON schema of your Headless Adaptive Forms. 

You can see [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/?path=/story/reference-examples--introduction) for sample JSON schemas and list of components, attributes, and properties. You can also see the [specifications document](/help/assets/Headless-Adaptive-Form-Specification.pdf) for detailed information on all the components, constraints, and methods available to define Headless Adaptive Forms.

File extension of a JSON schema of Headless Adaptive Forms is .json. For example, formname.json. Create or add the file to your AEM Archetype based project. For example, `\myheadlessform\ui.content\src\main\content\jcr_root\content\dam\myheadlessform\home-loan.json` -> 

### 3. Deploy the project to a local development environment {#deploy-the-project-to-a-local-development-environment}

You can deploy the project to local development environment. It adds Headless Adaptive Forms functionality, the **Blank with core components** template, JSON schema of form, and other resources included in the project to your development environment. <!-- Deploy the project to your local development environment to locally create Headless Adaptive Forms. or deploy directly to your Forms as a Cloud Service environment. To deploy to your local development environment, use the following command: 

    `mvn -PautoInstallPackage clean install`

If you are on Windows, run the above with Administrative privileges (Run command prompt or [bash shell as an administrator](https://khushwantsehgal.wordpress.com/2022/06/29/check-if-git-bash-is-running-in-administrator-mode/)). For the complete list of commands, see [Building and Installing](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/using.html?lang=pt-BR#building-and-installing).
    
<!-- *  To learn how to deploy code to AEM as a Cloud Service, see the video in [Deploying to AEM as a Cloud Service]https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=pt-BR#coding-against-the-right-aem-version) article : -->

### &#x200B;4. Crie um formulário adaptável com base no modelo em branco com componentes principais {#create-adaptive-form-with-blank-with-core-components-template}

1. Faça logon em sua [instância do AEM SDK](http://localhost:4502/).

1. Navegue até Adobe Experience Manager > Forms > Forms e Documentos.

1. Toque em Criar e selecione Formulário adaptável. Selecione o modelo **Em branco com componentes principais** e toque em Criar.

   ![Modelo](assets/template.png)

1. Especifique os valores dos campos de propriedade a seguir. Os campos Título e Nome são obrigatórios:

   * **Título**: especifica o nome para exibição do formulário. O título ajuda a identificar o formulário na interface do usuário do Experience Manager Forms.
   * **Nome**: especifica o nome do formulário. Um nó com o nome especificado será criado no repositório. Quando você começa a digitar um título, o valor do campo de nome é gerado automaticamente. É possível alterar o valor sugerido. O campo de nome pode incluir apenas caracteres alfanuméricos, hifens e sublinhados. Todas as entradas inválidas são substituídas por um hífen.

1. Toque em Criar. Um Formulário adaptável é criado.

Se você não vir o modelo **Em branco com componentes principais**, verifique se o [Projeto do Arquétipo do AEM foi implantado com êxito](#deploy-the-project-to-a-local-development-environment).

### &#x200B;5. Configurar o formulário adaptável para usar o esquema JSON {#configure-adaptive-form-to-use-the-JSON-representation}

O formulário adaptável criado na etapa anterior está em branco. Configure o Formulário adaptável para usar o esquema JSON:

1. Faça logon em sua [instância do AEM SDK](http://localhost:4502/).

1. Navegue até Adobe Experience Manager > Forms > Forms e Documentos. Selecione o Formulário adaptável criado na etapa anterior e toque em Editar. O Formulário adaptável é aberto no editor.

1. Toque no componente de Contêiner do Forms adaptável e em Propriedades. Ele exibe as propriedades do explorador na barra lateral.

1. No explorador de propriedades, expanda a opção BÁSICO e especifique o caminho do esquema JSON carregado em uma etapa anterior para a opção Caminho do documento do Forms Runtime. O componente de container exibe uma representação do formulário.

1. No explorador de propriedades, expanda a opção ENVIO e defina uma Ação enviar para o Formulário adaptável. Seu formulário está pronto para ser usado em um aplicativo react.

1. Para renderizar o formulário, hospedado em seu computador de desenvolvimento local:

   1. Abra o arquivo `[Archetype project]\ui.frontend.react.forms.af\.env` e defina o caminho do formulário. Por exemplo, /content/forms/af/contact

   1. Abra o prompt de comando e navegue até o projeto ui.frontend.react.forms.af e execute o seguinte comando:

      `npm run start`

   1. Após a conclusão, abra localhost:3000 na janela do navegador para exibir um Formulário adaptável headless renderizado.
   1. Para testar a funcionalidade de envio, faça logon no AEM Forms Server e use a opção **Visualizar o formulário no HTML** para abrir o formulário no modo de visualização.

O [Storybook](https://opensource.adobe.com/aem-forms-af-runtime/storybook/) fornece uma lista de componentes e regras que podem ser definidos em vários Forms adaptáveis headless, juntamente com alguns exemplos do esquema JSON do Forms adaptável headless. Você também pode consultar o documento [especificações](/help/assets/Headless-Adaptive-Form-Specification.pdf) para saber mais sobre várias regras e propriedades relacionadas ao Headless Adaptive Forms.
