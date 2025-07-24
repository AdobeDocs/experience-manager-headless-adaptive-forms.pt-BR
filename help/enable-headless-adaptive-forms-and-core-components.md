---
title: Habilitar o Forms adaptável headless no AEM 6.5 Forms
seo-title: Step-by-Step Guide for enabling Headless Adaptive Forms on AEM 6.5 Forms
description: Saiba como ativar formulários adaptáveis headless no AEM 6.5 Forms com o guia passo a passo da Adobe. Este tutorial o orienta pelo processo, facilitando a integração desse recurso avançado em seu site e melhorando a experiência do usuário.
contentOwner: Khushwant Singh
role: Admin
exl-id: e1a5e7e0-d445-4cca-b8d7-693d9531f075
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# Habilitar o Forms adaptável headless no AEM 6.5 Forms {#enable-headless-adaptive-forms-on-aem-65-forms}

Para ativar o Headless Adaptive Forms no ambiente do AEM 6.5 Forms, configure um projeto com base no AEM Archetype 41 ou posterior e implante-o em todas as instâncias de Autor e Publicação.

Ao implantar o projeto baseado no Arquétipo AEM 41 ou posterior em suas instâncias do Forms do AEM 6.5, você obtém a capacidade de [criar Componentes principais baseados no Forms Adaptável](create-a-headless-adaptive-form.md). Esses formulários são representados no formato JSON e usados como `Headful` e `Headless` Adaptive Forms, permitindo maior flexibilidade e personalização em vários canais, incluindo aplicativos móveis, da Web e nativos.

## Pré-requisitos {#prerequisites}

Antes de ativar o Forms adaptável headless no ambiente Forms do AEM 6.5,

* [Atualize para o AEM 6.5 Forms Service Pack 16 (6.5.16.0) ou posterior](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/release-notes/aem-forms-current-service-pack-installation-instructions).

* Instale a última versão do [Apache Maven](https://maven.apache.org/download.cgi).

* Instale um editor de texto simples. Por exemplo, Microsoft Visual Studio Code.

## Criar e implantar o projeto com base no Arquétipo do AEM mais recente

Para criar um projeto baseado no Arquétipo AEM 41 ou [mais tarde](https://github.com/adobe/aem-project-archetype) e implantá-lo em todas as instâncias de Autor e Publicação:

1. Faça logon no computador, hospedando e executando a instância do Forms do AEM 6.5, como Administrador.
1. Abra o prompt de comando ou o terminal.
1. Execute o seguinte comando para criar um projeto baseado no AEM Archetype 41:

   * Microsoft Windows

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate ^
      -D archetypeGroupId=com.adobe.aem ^
      -D archetypeArtifactId=aem-project-archetype ^
      -D archetypeVersion=41 ^
      -D appTitle="My Form" ^
      -D appId="myform" ^
      -D groupId="com.myform" ^
      -D includeFormsenrollment="y" ^
      -D aemVersion="6.5.23" 
   ```

   * Linux® ou Apple macOS

   ```Shell
      mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
      -D archetypeGroupId=com.adobe.aem \
      -D archetypeArtifactId=aem-project-archetype \
      -D archetypeVersion=41 \
      -D appTitle="My Form" \
      -D appId="myform" \
      -D groupId="com.myform" \
      -D includeFormsenrollment="y" \
      -D aemVersion="6.5.23" 
   ```

   Ao executar o comando acima, considere o seguinte:

   * Atualize o comando para refletir os valores específicos do seu ambiente, incluindo appTitle, appId e groupId. Além disso, defina os valores de includeFormsenrollment para `y`. Se você usa o Forms Portal, defina a opção _includeExamples=y_ para incluir os Componentes principais do Forms Portal no seu projeto.


1. (Somente para projetos baseados no Arquétipo versão 41) Depois que o projeto do Arquétipo do AEM for criado, ative temas para o Adaptive Forms baseado em Componentes principais. Para ativar temas:

   1. Abra a [Pasta de Projeto do Arquétipo do AEM]/ui.apps/src/main/content/jcr_root/apps/__appId__/components/adaptiveForm/page/customheaderlibs.html para edição:

   1. Adicione o seguinte código na linha 21:

      ```XML
      <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
      data-sly-use.formstructparser="com.adobe.cq.forms.core.components.models.form.FormStructureParser"
      data-sly-test.themeClientLibRef="${formstructparser.themeClientLibRefFromFormContainer}">
      <sly data-sly-test="${themeClientLibRef}" data-sly-call="${clientlib.css @ categories=themeClientLibRef}"/>
      </sly>
      ```

      ![Adicionar o código mencionado acima na linha 21](/help/assets/code-to-enable-themes.png)

   1. Salvar e fechar o arquivo.

1. Atualize o projeto para incluir a versão mais recente dos Componentes principais do Forms:

   1. Abra a [Pasta de Projeto do Arquétipo do AEM]/pom.xml para edição.
   1. Defina a versão de `core.forms.components.version` e `core.forms.components.af.version` para a versão [mais recente dos Componentes Principais do Forms](https://github.com/adobe/aem-core-forms-components/tree/release/650).

   1. Salvar e fechar o arquivo.


1. Depois que o projeto do Arquétipo do AEM for criado com sucesso, crie o pacote de implantação para o seu ambiente. Para criar o pacote:

   1. Navegue até o diretório raiz do seu projeto do Arquétipo AEM.


   1. Execute o seguinte comando para criar o projeto do Arquétipo do AEM para o seu ambiente:

      ```Shell
      mvn clean install
      ```

      ![arquétipo-êxito](assets/corecomponent-build-successful.png)


   Depois que o Arquétipo do AEM for criado com êxito, um pacote do AEM será gerado. Você pode encontrar o pacote em [Pasta de Projeto do AEM Archetype]\all\target\[appid].all-[version].zip

1. Use o [Gerenciador de Pacotes](https://experienceleague.adobe.com/pt-br/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager) para implantar o [pacote de Pasta de Projeto do Arquétipo do AEM]\all\target\[appid].all-[version].zip em todas as instâncias de Autor e Publicação.

>[!NOTE]
>
>
>
>Se tiver dificuldade ao acessar a caixa de diálogo de logon em uma instância de publicação para instalar o pacote por meio do Gerenciador de Pacotes, tente fazer logon por meio da seguinte URL: `http://[Publish Server URL]`:[PORT]/system/console. Esse processo dá acesso para fazer logon na instância de publicação e permite prosseguir com o processo de instalação.


Os Componentes principais são ativados para o seu ambiente. Um modelo de Formulário adaptável baseado em Componentes principais em branco e o tema Tela 3.0 são implantados em seu ambiente, permitindo que você [crie Componentes principais baseados no Forms adaptável](create-a-headless-adaptive-form.md).

## Perguntas frequentes

### Quais são os componentes principais?

Os [Componentes principais](https://experienceleague.adobe.com/pt-br/docs/experience-manager-core-components/using/introduction) são um conjunto de componentes padronizados de Gerenciamento de Conteúdo Online (WCM) para que o AEM acelere o tempo de desenvolvimento e reduza o custo de manutenção de seus sites.

### Quais são os recursos adicionados à habilitação dos componentes principais?


Quando os Componentes principais do Forms adaptável estiverem ativados para seu ambiente, um modelo de Formulário adaptável baseado em Componentes principais em branco e o tema do Canvas 3.0 serão adicionados ao seu ambiente. Depois de ativar os Componentes principais adaptáveis do Forms no seu ambiente, você pode:

* Crie Componentes principais com base no Forms adaptável.
* Crie Componentes principais com base em modelos de formulário adaptável.
* Crie temas personalizados para os Componentes principais com base em modelos de Formulário adaptável.
* Servir representações JSON do Formulário adaptável com base no Componente principal para canais como dispositivos móveis, Web, aplicativos nativos e serviços que exigem a representação headless de um formulário.
