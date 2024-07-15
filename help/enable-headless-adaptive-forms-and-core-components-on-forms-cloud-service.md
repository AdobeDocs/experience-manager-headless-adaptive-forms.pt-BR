---
title: Ativar o Forms adaptável headless no AEM Forms as a Cloud Service
seo-title: Step-by-Step Guide for enabling Headless Adaptive Forms on AEM Forms as a Cloud Service
description: Saiba como ativar formulários adaptáveis headless no AEM Forms as a Cloud Service com nosso guia passo a passo. Nosso tutorial o orienta pelo processo, facilitando a ativação desse recurso poderoso para seu ambiente AEM Forms.
seo-description: Learn how to enable headless adaptive forms on AEM Forms as a Cloud Service with our step-by-step guide. Our tutorial walks you through the process, making it easy to enable this powerful feature for your AEM Forms environment.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin
level: Beginner, Intermediate
contentOwner: Khushwant Singh
docset: CloudService
hide: true
hidefromtoc: true
exl-id: 7afff771-1296-4162-84c5-c8266b94af2f
source-git-commit: 999c3d092d03d7a82363bc94ce79ceb33bf0df7e
workflow-type: tm+mt
source-wordcount: '914'
ht-degree: 0%

---

# Ativar o Forms adaptável headless no AEM Forms as a Cloud Service {#enable-headless-adaptive-forms-on-aem-forms-cloud-service}

A habilitação do headless Adaptive Forms no AEM Forms as a Cloud Service permite começar a criar, publicar e fornecer Forms headless usando as instâncias do AEM Forms Cloud Service para vários canais. Você precisa do ambiente habilitado dos Componentes principais adaptáveis do Forms para usar o Forms adaptável headless.

## Considerações

* Ao criar um novo programa AEM Forms as a Cloud Service, o [Headless Adaptive Forms já está habilitado para os seus ambientes](#are-adaptive-forms-core-components-enabled-for-my-environment).

* Se você tiver um programa mais antigo de as a Cloud Service do Forms em que os Componentes principais [não estão habilitados](#enable-components), poderá [adicionar dependências dos Componentes principais do Adaptive Forms](#enable-headless-adaptive-forms-for-an-aem-forms-as-a-cloud-service-environment) ao seu repositório do AEM as a Cloud Service e implantar o repositório nos seus ambientes de Cloud Service para habilitar o Adaptive Forms Headless.

* Se seu ambiente de Cloud Service existente fornecer a opção de [criar Forms adaptável baseado em Componentes principais](create-a-headless-adaptive-form.md), o Forms adaptável headless já estará habilitado para seu ambiente e você poderá fornecer Forms adaptável baseado em Componentes principais como formulários headless para canais como dispositivos móveis, Web, aplicativos nativos e serviços que exigem uma representação headless do Forms adaptável.


>[!NOTE]
>
>
> O Adobe fornece o [kit inicial (Aplicativo React)](create-and-publish-a-headless-form.md) do Adaptive Forms para ajudar os desenvolvedores a iniciar rapidamente o desenvolvimento do Forms Adaptive Headless, sem ativar o ambiente as a Cloud Service do Headless Adaptive Forms no AEM Forms. Você pode habilitar a Forms adaptável headless em um ambiente as a Cloud Service Forms posteriormente após uma [rápida interação com o desenvolvimento de formulários headless](create-and-publish-a-headless-form.md).

## Ativar o Forms adaptável headless para um ambiente as a Cloud Service AEM Forms

Execute as seguintes etapas, na ordem listada, para ativar o Forms adaptável headless para um ambiente as a Cloud Service AEM Forms


![](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service.png)


## 1. Clonar o repositório as a Cloud Service do AEM Forms {#clone-git-repository}

1. Faça logon no [Cloud Manager](https://my.cloudmanager.adobe.com/) e selecione sua organização e programa.

1. Navegue até o cartão **Pipelines** na página **Visão geral do programa**, clique no botão **Acessar informações do repositório** para acessar e gerenciar o Repositório Git. A página inclui as seguintes informações:

   * URL do Repositório Git da Cloud Manager.
   * Credenciais do nome de usuário do Git do Repositório Git (nome de usuário e senha).

   Clique em **Gerar senha** para exibir ou gerar a senha.

1. Abra o terminal ou o prompt de comando no computador local e execute o seguinte comando:

   ```Shell
   git clone [Git Repository URL]
   ```

   Quando solicitado, forneça as credenciais. O repositório é clonado no computador local.


## 2. Adicione as dependências dos Componentes principais do Forms adaptável ao Repositório Git {#add-adaptive-forms-core-components-dependencies}

1. Abra a pasta Repositório Git em um editor de código de texto simples. Por exemplo, Código VS.
1. Abra o arquivo `[AEM Repository Folder]\pom.xml` para edição.
1. Substitua as versões dos componentes `core.forms.components.version`, `core.forms.components.af.version` e `core.wcm.components.version` pelas versões especificadas na [documentação dos componentes principais](https://github.com/adobe/aem-core-forms-components). Se o componente não existir, adicione esses componentes.

   ```XML
   <!-- Replace the version with the latest released version at https://github.com/adobe/aem-core-forms-components/tags -->
   
   <properties>
       <core.forms.components.version>2.0.14</core.formscomponents.version>
       <core.forms.components.af.version>2.0.14</core.forms.components.af.version>  
       <core.wcm.components.version>2.21.2</core.wcmcomponents.version>
   </properties>
   ```

   ![Mencione a versão mais recente dos Componentes principais do Forms](/help/assets/latest-forms-component-version.png)

1. Na seção de dependências do arquivo `[AEM Repository Folder]\pom.xml`, adicione as seguintes dependências e salve o arquivo.

   ```XML
       <!-- WCM Core Component Examples Dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
               <version>${core.wcm.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <version>${core.wcm.components.version}</version>
               <type>zip</type>
           </dependency>    
           <!-- End of WCM Core Component Examples Dependencies -->
           <!-- Forms Core Component Dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-core</artifactId>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <version>${core.forms.components.version}</version>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
               <version>${core.forms.components.version}</version>
           </dependency>
   <!-- End of AEM Forms Core Component Dependencies -->
   ```

1. Abra o arquivo `[AEM Repository Folder]/all/pom.xml` para edição. Adicione as seguintes dependências na seção `<embeddeds>` e salve o arquivo.

   ```XML
   <!-- WCM Core Component Examples Dependencies -->
   
   <!-- inside plugin config of filevault-package-maven-plugin -->  
   <!-- embed wcm core components examples artifacts -->
   
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.cq</groupId>
       <artifactId>core.wcm.components.examples.ui.config</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <!-- embed forms core components artifacts -->
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       <target>/apps/${appId}-vendor-packages/application/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-apps</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   <embedded>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-examples-content</artifactId>
       <type>zip</type>
       <target>/apps/${appId}-vendor-packages/content/install</target>
   </embedded>
   ```

   >[!NOTE]
   >
   >
   >  Substitua `${appId}` com sua appId.
   >
   >  Para encontrar seu `${appId}`, no arquivo `[AEM Repository Folder]/all/pom.xml`, pesquise o termo `-packages/application/install`. O texto antes do termo `-packages/application/install` é o seu `${appId}`. Por exemplo, o código a seguir, `myheadlessform` é `${appId}`.
   >
   >   ```
   >             <embedded>
   >                     <groupId>com.myheadlessform</groupId>
   >                     <artifactId>myheadlessform.ui.apps<artifactId>
   >                     <type>zip</type>
   >                   <target>/apps/myheadlessform-packages/application install</target>
   >             </embedded>
   >   ```

1. Na seção `<dependencies>` do arquivo `[AEM Repository Folder]/all/pom.xml`, adicione as seguintes dependências e salve o arquivo:

   ```XML
           <!-- Other existing dependencies -->
           <!-- wcm core components examples dependencies -->
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.config</artifactId>
               <type>zip</type>
               </dependency>
           <dependency>
               <groupId>com.adobe.cq</groupId>
               <artifactId>core.wcm.components.examples.ui.content</artifactId>
               <type>zip</type>
           </dependency>
               <!-- forms core components dependencies -->
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-af-apps</artifactId>
               <type>zip</type>
           </dependency>
           <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-apps</artifactId>
               <type>zip</type>
           </dependency>
               <dependency>
               <groupId>com.adobe.aem</groupId>
               <artifactId>core-forms-components-examples-content</artifactId>
               <type>zip</type>
           </dependency>
   ```

1. Abra o `[AEM Repository Folder]/ui.apps/pom.xml` para edição. Adicione a dependência `af-core bundle` e salve o arquivo.

   ```XML
       <dependency>
       <groupId>com.adobe.aem</groupId>
       <artifactId>core-forms-components-af-core</artifactId>
       </dependency>
   ```

   >[!NOTE]
   >
   >Verifique se os seguintes artefatos dos Componentes principais adaptáveis do Forms não estão incluídos em seu projeto.
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-apps</artifactId>`
   >
   > `</dependency>`
   >
   > e
   >
   > `<dependency>`
   >
   >   `<groupId>com.adobe.aem</groupId>`
   >   `<artifactId>core-forms-components-core</artifactId>`
   >
   > `</dependency>`


1. Salvar e fechar o arquivo.

## 3. Atualize o projeto para incluir a versão mais recente dos Componentes principais do Forms:

1. Abra a [Pasta do Projeto do Arquétipo AEM]/pom.xml para edição.


1. Salvar e fechar o arquivo.

## 4. Confirme as atualizações no Repositório Git e execute o pipeline para implantar o repositório {#Commit-the-updates-to-your-git-repository}

1. Para confirmar o código no Repositório Git:
   1. Abra o terminal ou o prompt de comando.
   1. Navegue até `[AEM Repository Folder]` e execute os seguintes comandos na ordem listada

      ```Shell
      git add pom.xml
      git add all/pom.xml
      git add ui.apps/pom.xml
      git commit -m "Added dependencies for Adaptive Forms Core Components"
      git push origin
      ```

1. Depois que os arquivos forem confirmados no Repositório Git, [Execute o pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=pt-BR).

   Depois que a execução do pipeline for bem-sucedida, os Componentes principais adaptáveis do Forms serão ativados para o ambiente correspondente. Além disso, um modelo de Forms adaptável (Componentes principais) e o tema do Canvas 3.0 são adicionados ao seu ambiente as a Cloud Service do Forms, fornecendo opções para personalizar e criar Componentes principais com base no Forms adaptável.


## Perguntas frequentes {#faq}

### Quais são os componentes principais? {#core-components}

Os [Componentes principais](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=pt-BR) são um conjunto de componentes padronizados de Gerenciamento de Conteúdo na Web (WCM) para o AEM, a fim de acelerar o tempo de desenvolvimento e reduzir o custo de manutenção de seus sites.

### Quais são todos os recursos adicionados na ativação dos componentes principais? {#core-components-capabilities}

Quando os Componentes principais do Forms adaptável estiverem ativados para seu ambiente, um modelo de Formulário adaptável baseado em Componentes principais em branco e o tema do Canvas 3.0 serão adicionados ao seu ambiente. Depois de ativar os Componentes principais adaptáveis do Forms no seu ambiente, você pode:

* Crie Componentes principais com base no Forms adaptável.
* Crie Componentes principais com base em modelos de formulário adaptável.
* Crie temas personalizados para os Componentes principais com base em modelos de Formulário adaptável.
* Servir representações JSON do Formulário adaptável com base no Componente principal para canais como dispositivos móveis, Web, aplicativos nativos e serviços que exigem a representação headless de um formulário.

### Os Componentes principais adaptáveis do Forms estão habilitados para meu ambiente? {#enable-components}

Para verificar se os Componentes principais do Adaptive Forms estão ativados para o seu ambiente:

1. [Clonar o repositório as a Cloud Service do AEM Forms](#1-clone-your-aem-forms-as-a-cloud-service-git-repository).

1. Abra o arquivo `[AEM Repository Folder]/all/pom.xml` do Repositório Git do AEM Forms Cloud Service.

1. Procure as seguintes dependências:

   * core-forms-components-af-core
   * core-forms-components-core
   * core-forms-components-apps
   * core-forms-components-af-apps
   * core-forms-components-examples-apps
   * core-forms-components-examples-content


   ![localize o artefato core-forms-components-af-core em all/pom.xml](/help/assets/enable-headless-adaptive-forms-on-aem-forms-cloud-service-locate-core-af-artifact.png)

   Se as dependências existirem, os Componentes principais adaptáveis do Forms serão ativados para o seu ambiente.
