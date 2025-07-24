---
title: Configurar um ambiente de desenvolvimento para uma sandbox do Forms as a Cloud Service
description: Configurar um ambiente de desenvolvimento para uma sandbox Forms as a Cloud Service.
hide: true
exl-id: befac9ad-d2c4-4705-96fc-f0ea0ef823b8
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 1%

---

# Configurar ambiente de desenvolvimento para formulários adaptáveis headless no Cloud Service

<span class="preview"> Este artigo é um **TRABALHO EM ANDAMENTO**.</span>


Pronto para criar e testar formulários adaptáveis headless no Cloud Service? Ative o Forms para seu programa Cloud Service e continue.

## Antes de começar

* Instale a [última versão do Git](https://git-scm.com/downloads) no computador local. Se você é novo no Git, consulte [Instalando o Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git). Você usa o repositório Git para enviar os formulários e o código personalizado desenvolvidos em seu ambiente de desenvolvimento local para seu ambiente de desenvolvimento do Cloud Service.

* Instale o [Node.js 16.13.0 ou posterior](https://nodejs.org/en/download/) no computador local. <!-- URL IS 404! If you are new to Node.js, see [How to install Node.js](https://nodejs.org/en/learn/how-to-install-nodejs). -->


* Crie um programa do AEM as a Cloud Service: Siga as etapas de 1 a 7 do artigo [criar programa](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program) para criar um programa para sua organização.

* Habilite o [Canal de pré-lançamento para seu programa do Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/prerelease#cloud-environments).

## Configurar fluxo de trabalho

Para habilitar formulários adaptáveis headless na sandbox do Forms as a Cloud Service, habilite a solução `Forms - Digital enrolment` para o programa AEM Cloud Service. Em seguida, crie um projeto com base no Archetype 37 ou posterior em sua máquina local e envie-o para o ambiente Forms as a Cloud Service. O processo completo é:

![Fluxo de trabalho para configurar o ambiente de desenvolvimento para uma Sandbox do Forms as a Cloud Service](assets/FORMS-HLAF-SANDBOX-PRODUCTION-ENR.png)

### &#x200B;1. Ativar o Forms para o seu programa

<table style="table-layout:auto">
<tr>
  <td>
  1. Faça logon em <a href="https://experience.adobe.com/" > https://experience.adobe.com/ </a> e selecione a opção <b> Experience Manager </b>.

  </td>
  <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program">
      <img alt="Programas do AEM as a Cloud Service" src="assets/cloud-manager-experience-manager.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  &#x200B;2. Para a opção <b> Cloud Manager </b>, clique em <b> Launch. </b> Uma lista de programas para sua organização é exibida.
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program">
      <img alt="Programas do AEM as a Cloud Service" src="assets/cloud-manager-experience-manager-launch.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    &#x200B;3. Para o seu programa, toque no ... ícone e selecione a opção <b> Editar programa </b>. Uma caixa de diálogo é exibida. 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program">
      <img alt="Programas do AEM as a Cloud Service" src="assets/edit-program.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    &#x200B;4. Na caixa de diálogo Editar programa, vá para a guia <b> Soluções &amp; Complementos </b>, selecione a opção <b> Forms - Inscrição Digital </b> e toque em <b> atualização </b>. 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program">
      <img alt="Programas do AEM as a Cloud Service" src="assets/program-solution-addons.png">
    </a>
    <br>
  </td>
</tr>
</table>

### &#x200B;2. Clonar o repositório Git do programa no computador local

Todos os programas do AEM as a Cloud Service têm um repositório Git. Ele permite fazer upload de código personalizado e ativos de um computador local para o ambiente do Cloud Service. Durante a configuração, o Adobe usa o repositório Git para trazer códigos, modelos e outras informações relacionados aos formulários adaptáveis headless para o programa Cloud Service de seu computador local. A clonagem do repositório Git do Cloud Service em seu computador local é a primeira etapa para trazer o código personalizado e o conteúdo de seu computador local para o Cloud Service.

>[!INFO]
>
> Você sempre pode confirmar em um repositório Git sem cloná-lo. Mas ela tem seus próprios caprichos. Este documento usará a abordagem de clonagem.


Para clonar o repositório:

<table style="table-layout:fixed">
<tr>
  <td>
  1. Na caixa de pipeline do seu programa, toque em <b> Acessar Informações do Repositório. </b> Uma caixa de diálogo com informações do Repositório é exibida 

  </td>
  <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program">
      <img alt="Programas do AEM as a Cloud Service" src="assets/git-repo.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  &#x200B;2. Toque em <b> Gerar senha </b> e copie a URL do Repositório <b>. </b> 
  </td>
  <td>
      <img alt="Programas do AEM as a Cloud Service" src="assets/repository-info.png">
    <br>
  </td>
</tr>
<tr>
  <td>
    &#x200B;3. Na máquina local, abra o prompt de comando, crie uma pasta e execute o seguinte comando e forneça as Credenciais do Repositório, perguntado:
    </br>
    <code> git clone [Repository URL] </code> </br></br>
    Por exemplo, </br> 
    <code> git clone https://git.cloudmanager.adobe.com/stage-aemformsdev/khushwantsingh-p45413-uk89613/ </code>

</br> Quando solicitado, obtenha o <b> Nome de Usuário</b> e a <b>Senha</b> da tela <b>Informações do Repositório</b>.
</td>
  <td>
     <img alt="Programas do AEM as a Cloud Service" src="assets/clone-success.png">
  </td>
</tr>
</table>


### &#x200B;3. Criar um projeto com base no Arquétipo do AEM

O projeto do arquétipo é um modelo baseado no Maven. Ele cria um projeto mínimo com base na prática recomendada para começar a usar formulários adaptáveis headless. Ele também inclui a funcionalidade de formulários adaptáveis principais do Headless para o Forms as a Cloud Service. É obrigatório criar e implantar o projeto baseado no arquétipo 37 ou posterior.
®®
Dependendo do sistema operacional, execute o comando maven para criar um projeto Experience Manager Forms as a Cloud Service. Use a versão 37 ou posterior do arquétipo. Consulte a [Documentação do arquétipo](https://experienceleague.adobe.com/pt-br/docs/experience-manager-core-components/using/developing/archetype/overview) para encontrar a versão mais recente do Arquétipo.

+++ Microsoft® Windows

1. Abra o prompt de comando com privilégios Administrativos (Execute o prompt de comando ou bash shell como administrador).
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

™™™

* Defina `appTitle` para definir o título e os grupos de componentes.
* Defina `appId` para definir o Maven artifactId, os nomes do componente, da configuração e da pasta de conteúdo, e os nomes da biblioteca do cliente.
* Defina `groupId` para definir o Maven groupId e o pacote Java™ Source.
* Use a opção `includeFormsenrollment=y` para incluir configurações específicas do Forms, temas, modelos, Componentes principais e dependências necessárias para criar o Forms adaptável.
* Use a opção `includeFormsheadless=y` para incluir os Componentes principais do Forms e as dependências necessárias para incluir a funcionalidade de formulários adaptáveis headless. Ao ativar essa opção, as seguintes opções são incluídas:
   * O modelo **Em branco com componentes principais** com [componentes principais](https://experienceleague.adobe.com/pt-br/docs/experience-manager-core-components/using/introduction).
   * Um módulo de front-end do React, `ui.frontend.react.forms.af`. Ele ajuda a renderizar o formulário adaptável headless em um aplicativo react.

+++®®


+++ Apple macOS ou Linux®

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

™™™
* Defina `appTitle` para definir o título e os grupos de componentes.
* Defina `appId` para definir o Maven artifactId, o componente, a configuração, os nomes da pasta de conteúdo e os nomes da biblioteca do cliente.
* Defina `groupId` para definir o Maven groupId e o pacote Java™ Source.
* Use a opção `includeFormsenrollment=y` para incluir configurações específicas do Forms, temas, modelos, Componentes principais e dependências necessárias para criar o Forms adaptável.
* Use a opção `includeFormsheadless=y` para incluir os Componentes principais do Forms e as dependências necessárias para incluir a funcionalidade de formulários adaptáveis headless. Ao ativar essa opção, as seguintes opções são incluídas:
   * O modelo **Em branco com componentes principais** com [componentes principais](https://experienceleague.adobe.com/pt-br/docs/experience-manager-core-components/using/introduction).
   * Um front-end reage com o módulo, `ui.frontend.react.forms.af`. Ele ajuda a renderizar o formulário adaptável headless em um aplicativo react.

+++

Após a conclusão bem-sucedida do comando, uma pasta de projeto com o nome especificado em `appID` é criada. Por exemplo, se você usar `appID` com valor `myheadlessform`, uma pasta chamada `myheadlessform` será criada. Ele contém o projeto baseado em Arquétipo.

### &#x200B;4. Enviar o projeto baseado no Arquétipo do AEM para o ambiente do Cloud Service

1. Substitua o conteúdo do repositório Git pelo conteúdo do projeto baseado em Arquétipo.

   >[!VIDEO](https://video.tv.adobe.com/v/3409809/)

1. Abra o prompt de comando, navegue até a pasta do repositório Git e execute os comandos abaixo na ordem listada para fazer upload do conteúdo substituído para o seu ambiente Cloud Service. Você também pode usar um editor visual em vez de usar os comandos abaixo para enviar conteúdo para o repositório do Cloud Service.

   ```
      git add .
      git commit
      git push origin
   ```

### &#x200B;5. Execute um pipeline de build para seu programa



<table style="table-layout:auto">
<tr>
  <td>
  1. Faça logon em <a href="https://experience.adobe.com/" > https://experience.adobe.com/ </a> e selecione a opção <b> Experience Manager </b>.

  </td>
  <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program">
      <img alt="Programas do AEM as a Cloud Service" src="assets/cloud-manager-experience-manager.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
  &#x200B;2. Para a opção <b> Cloud Manager </b>, clique em <b> Launch. </b> Uma lista de programas para sua organização é exibida. Abra o programa. 
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program">
      <img alt="Programas do AEM as a Cloud Service" src="assets/cloud-manager-experience-manager-launch.png">
    </a>
    <br>
  </td>
</tr>
<tr>
  <td>
    &#x200B;3. Para o seu pipeline, toque no ... ícone e selecione a opção <b> Executar </b>. Se solicitado a executar o pipeline, toque em <b> Executar </b> e aguarde o pipeline <b> Status </b> mudar para <b> Concluído </b>.  
  </td>
  <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/demo-add-on/create-program#create-program">
      <img alt="Programas do AEM as a Cloud Service" src="assets/run-build-pipeline.png">
    </a>
    <br>
  </td>
</tr>
</table>

Agora, seu ambiente está pronto para usar formulários adaptáveis headless. Agora é possível carregar uma definição JSON de um formulário no ambiente do Cloud Service. Em seguida, crie um formulário adaptável headless com base nele e use o [getForm](https://opensource.adobe.com/aem-forms-af-runtime/api/#tag/Get-Form-Definition/operation/getForm) e outras APIs rest para usar o formulário adaptável headless em seu aplicativo ou serviço.
