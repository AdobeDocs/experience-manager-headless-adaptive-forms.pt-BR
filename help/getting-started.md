---
title: Introdução ao Headless Adaptive Forms
description: Introdução ao Headless Adaptive Forms
keywords: headless, formulário adaptável, tutorial
hide: true
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---


# Introdução ao Headless Adaptive Forms

Este tutorial fornece uma estrutura completa para criar um formulário adaptável headless. O tutorial é organizado em um caso de uso e em vários guias. Cada guia ajuda você a aprender e adicionar novos recursos ao formulário adaptável headless criado neste tutorial. Você tem um formulário adaptável headless funcional após cada guia. No final deste tutorial, você poderá fazer o seguinte:

* Criar um formulário adaptável headless
* Adicionar regras de negócios ao formulário
* Usar a interface do usuário de material do Google para criar estilos de formulários
* Preencha o formulário previamente
* Incorporar o formulário a uma página da Web

Você também construirá uma compreensão da arquitetura, dos artefatos disponíveis e da estrutura JSON de formulários adaptáveis headless.

**A jornada começa aprendendo o caso de uso**:

Raya Tan, membro do Departamento de Relações Exteriores de um país conhecido por sua beleza natural e economia do turismo próspera, supervisiona a distribuição de formulários de visto para turistas. Esses formulários estão disponíveis no site do departamento, em aplicativos nativos para dispositivos móveis e no formato PDF, com várias opções de idioma para os turistas escolherem. No entanto, gerenciar e dimensionar esses formulários em diferentes plataformas e tecnologias pode ser desafiador.

Para melhorar a eficiência e a flexibilidade do processo de solicitação de visto, o Departamento de Relações Exteriores decidiu adotar uma abordagem de formulários adaptáveis headless. Essa arquitetura dissociada separa o front-end do back-end, permitindo maior personalização e escalabilidade. O departamento planeja usar os componentes do React da interface do usuário de materiais do Google para aprimorar a experiência do usuário dos formulários. Ele também usará recursos de back-end como os seguintes:

* Assinaturas digitais
* Integração de dados
* Gerenciamento de processos de negócios
* Documento de registro
* Análise de uso

A forma mais popular entre os turistas é o formulário &quot;Contate-nos&quot;, que é usado para fazer várias perguntas e perguntas. Assim, o Departamento de Relações Exteriores optou por começar a implementar a abordagem de formulários adaptáveis Headless com este formulário. Este tutorial o orienta pelo processo de criação do formulário Fale Conosco usando essa nova arquitetura. O resultado final tem esta aparência:

![Contate-nos pelo formulário adaptável headless](assets/contact-us-headless-adaptive-forms.png)