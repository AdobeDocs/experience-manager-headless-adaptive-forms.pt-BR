---
title: Extensão do Visual Studio Code para formulários adaptáveis Headless
description: Extensão do Visual Studio Code para formulários adaptáveis Headless
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless, formulários adaptáveis, extensão do Visual Studio Code
index: true
exl-id: 11960e91-6c09-48d4-9d57-37537f808cd4
TQID: 'https://experienceleague.adobe.com/sf8qkVgbwMf2CGDsATHRYzq6idFQNFv3Os89oiCoiLU'
product_v2:
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
source-git-commit: b34afbc4f692b81838ad6947895c9b347dff6d62
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%
---
# Extensão do Microsoft Visual Studio Code para formulários adaptáveis Headless

Se você usa o Microsoft® Visual Studio Code como um IDE (Integrated Development Environment), é possível usar a extensão Adaptive Forms para o Microsoft Visual Studio Code. A extensão:

* Adiciona recursos do IntelliSense para o Adaptive Forms ao Visual Studio Code.
* Ajuda a validar e preencher automaticamente a sintaxe JSON para componentes de formulários adaptáveis headless.
* Navega pela estrutura de um formulário adaptável headless facilmente por um painel.
* Ajuda a traduzir um formulário adaptável Headless.

<!-- 

The extension o easily navigate the structure 

Adobe provides an extension for Microsoft&reg; Visual Studio Code to make it easier for you to navigate structure and develop Headless adaptive forms in Visual Studio Code. The extension adds Adaptive Forms related IntelliSense capabilities and helps auto-complete Headless adaptive forms JSON syntax. It also adds a panel, titled Forms Tree, to help navigate structure of Headless adaptive form. 

-->

## Pré-requisitos

* Baixe e instale o [Microsoft Visual Studio Code 1.62.0 ou posterior](https://code.visualstudio.com/docs/supporting/FAQ#_how-do-i-find-the-version). Se você tiver uma versão mais antiga ou nenhuma versão instalada, baixe a versão mais recente do [site da Microsoft](https://code.visualstudio.com/docs/setup/setup-overview). Para usar o Visual Studio a partir da linha de comando no Apple macOS, consulte [Inicialização a partir da linha de comando](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line).
* Baixe a [extensão do construtor de formulários adaptáveis](/help/assets/adaptive-form-builder-0.12.0.vsix).

## Instalar a extensão

1. Abra o prompt de comando e navegue até o diretório que contém o arquivo de extensão baixado, *adaptive-form-builder-[version].vsix*.

1. Execute o seguinte comando para instalar a extensão:

   `code -–install-extension adaptive-form-builder-0.12.0.vsix`

   <br>

   ![Instalando extensão](/help/assets/install-extension.png)


   Para obter informações sobre arquivos .vsix, consulte a [Ajuda do Microsoft Visual Studio Code](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace#_install-from-a-vsix).
