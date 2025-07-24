---
title: Extensão do Visual Studio Code para formulários adaptáveis Headless
description: Extensão do Visual Studio Code para formulários adaptáveis Headless
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: headless, formulários adaptáveis, extensão do Visual Studio Code
hide: false
exl-id: 11960e91-6c09-48d4-9d57-37537f808cd4
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '196'
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
