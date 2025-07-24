---
title: Solução de problemas do Headless Adaptive Forms
description: Solução de problemas do Headless Adaptive Forms
keywords: headless, formulário adaptável, solução de problemas
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
hide: false
exl-id: bfb7e688-d2be-4aaa-ac9b-147cbd74b516
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 6%

---

# Resolução de problemas

## Não é possível implantar o projeto do Arquétipo no ambiente de desenvolvimento local

### Problema

Quando você usa o `mvn -PautoInstallPackage clean install` ou comandos semelhantes para implantar um projeto do Arquétipo do AEM, ocorre uma falha na implantação do projeto.

### Motivo

Isso pode ocorrer devido a uma versão sem suporte ou instalação corrompida de `node.js` ou `NPM`.

### Solução

1. Completamente [remova as instalações atuais do Node.JS](https://khushwantsehgal.wordpress.com/2022/06/28/how-to-remove-node-js-completely-from-windows-10/) de seu ambiente.

1. Instalar `node.JS 16.13.0` ou posterior com `NPM`.

1. Reinicialize o computador.


## Falha ao executar o comando `mvn clean install`

### Problema

Quando você usa o `mvn clean install` ou comandos semelhantes para implantar um projeto do Arquétipo AEM, ocorre falha na execução do comando.

### Motivo

Isso pode acontecer se o Git não estiver instalado.

### Solução

Baixe e instale a [versão mais recente do Git](https://git-scm.com/downloads). Se você é novo no Git, consulte [Instalando o Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
