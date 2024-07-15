---
title: Visão geral dos formulários adaptáveis AEM Headless
description: O AEM Forms Headless Adaptive Forms fornece uma maneira rápida e eficiente de criar formulários para várias plataformas, incluindo Headless ou Headful CMS, aplicativos React, aplicativos de página única (SPA), aplicativos Web, aplicativos móveis, Amazon Alexa, Google Assistant, WhatsApp e muito mais. Com o headless Adaptive Forms, é possível simplificar o processo de criação de formulários, facilitando a coleta de dados dos usuários em diferentes dispositivos e plataformas.
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Headless
role: Admin, Developer
level: Beginner, Intermediate
keywords: CMS headless, formulários adaptáveis, interface do usuário headless, CMS headful, assistentes de voz, alexa, chatbots, arquitetura WhatsApp
hide: true
hidefromtoc: true
exl-id: f6a383ea-684b-479d-a15f-8ebced75635e
source-git-commit: 1f70e2bb0e5f12e8ee5d948ef1d3cd2935f2274f
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 13%

---

# Introdução

O Adobe Experience Manager (AEM) Headless Adaptive Forms é uma solução para criar e gerenciar formulários web headless na plataforma do Adobe Experience Manager. Esse recurso permite que as organizações criem, publiquem e gerenciem formulários interativos que podem ser acessados e interagidos por meio de APIs, em vez de uma interface gráfica tradicional. O AEM Headless Adaptive Forms permite maior flexibilidade e escalabilidade no desenvolvimento e implantação de formulários, bem como melhor experiência do usuário através da capacidade de adaptar o design e a funcionalidade de formulários às necessidades específicas. Utilizando os recursos do AEM e a tecnologia headless, esta solução oferece uma plataforma robusta para criar, gerenciar e implantar formulários web para vários casos de uso e aplicativos.

![Crie e renderize nativamente um formulário em qualquer site, aplicativo ou interação não visual](/help/assets/headless-forms-for-any-device.jpeg)

Os formulários adaptáveis headless ajudam a:

* criar formulários multicanal de alta qualidade na linguagem de programação de sua escolha
* integrar formulários nativamente a seus aplicativos móveis e de desktop, sites e aplicativos de bate-papo
* reutilizar os componentes de interface de sua propriedade com aplicativos de formulários
* aproveitar a [potência do Adobe Experience Manager Forms](https://experienceleague.adobe.com/docs/experience-manager-65/forms/getting-started/introduction-aem-forms.html)

Além disso, você tem a liberdade de desenvolver seus próprios componentes para renderizar um formulário usando qualquer estrutura de interface do usuário e linguagem de programação de sua escolha. Você também pode usar os componentes do React disponíveis prontos para uso para renderizar um formulário adaptável headless.

<!-- 

## Key Features

<table style="width:100%;">
  <tr>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px;">
        <img src="/help/assets/01-overview-responsive-forms.jpeg" alt="Card Image 1" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Responsive Forms</h2>
          <p>The adaptive form feature enables you to create a single source for a form that automatically sizes and re-flows on mobile devices.</p>
        </div>
      </div>
    </td>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/01-overview-responsive-forms.jpeg" alt="Card Image 1" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Communication API</h2>
          <p>The adaptive form feature enables you to create a single source for a form that automatically sizes and re-flows on mobile devices.</p>
        </div>
      </div>
    </td>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/02-overview-backend-systems.jpeg" alt="Card Image 2" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Business Process Management</h2>
          <p>Integrate RDBMS, OData, Or Microsoft SOAP services, as well as protocols like Swagger 2.0 to connect to just about anything.</p>
        </div>
      </div>
    </td>
  </tr>
  <tr>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/03-overview-save-and-resume.jpeg" alt="Card Image 3" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Save and resume forms</h2>
          <p>Allow clients to save in-progress forms and return later to complete them, even on another device.</p>
        </div>
      </div>
    </td>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/04-overview-search.jpeg" alt="Card Image 1" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Forms Search and Discovery</h2>
          <p>Let customers easily find relevant forms based on a simple search query, tags, filters, and even geolocation — on any device through a personalized portal, with or without authentication.
          </p>
        </div>
      </div>
    </td>
      <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/04-overview-search.jpeg" alt="Card Image 1" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Forms Search and Discovery</h2>
          <p>Let customers easily find relevant forms based on a simple search query, tags, filters, and even geolocation — on any device through a personalized portal, with or without authentication.
          </p>
        </div>
      </div>
    </td>
  </tr>
  <tr>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/05-overview-analytics.jpeg" alt="Card Image 2" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Form analytics and reporting</h2>
          <p>Out-of-the-box, customizable dashboards make it easy to apply analytics to forms to gain insight for actionable areas of improvement.</p>
        </div>
      </div>
    </td>
    <td style="width:33.33%;">
      <div style="width: 250px; border: 1px solid #ccc; border-radius: 8px; ">
        <img src="/help/assets/06-overview-business-process.jpeg" alt="Card Image 3" style="width:33.33; height: auto;">
        <div style="padding: 20px;">
          <h2 style="margin-top: 0;">Business Process Management</h2>
          <p>Route application submissions through customized workflows and a centralized dashboard for review, approval, and digital signatures by back-office employees — even when employees are on the go on a mobile device.
          </p>
        </div>
      </div>
    </td>
  </tr>
</table>




<div style="display: flex; flex-wrap: wrap; justify-content: space-between; margin: 20px;">
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/01-overview-responsive-forms.jpeg" alt="Icon 1" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 1</h2>
        <p>Description 1</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/02-overview-backend-systems.jpeg" alt="Icon 2" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 2</h2>
        <p>Description 2</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/03-overview-save-and-resume.jpeg" alt="Icon 3" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 3</h2>
        <p>Description 3</p>
    </div>
        <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/04-overview-search.jpeg" alt="Icon 1" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 1</h2>
        <p>Description 1</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/05-overview-analytics.jpeg" alt="Icon 2" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 2</h2>
        <p>Description 2</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/06-overview-business-process.jpeg" alt="Icon 3" style="width: 50px; height: 50px;">
        <h2 style="margin-top: 10px;">Heading 3</h2>
        <p>Description 3</p>
    </div>
    <!-- Add more cards as needed -->
</div>




<div style="display: flex; flex-wrap: wrap; justify-content: space-between; margin: 20px;">
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/01-overview-responsive-forms.jpeg" alt="Imagem 1" style="width: 100%; border-radius: 5px;">
        <h2 style="margin-top: 10px;">Cabeçalho 1</h2>
        <p>Descrição 1</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/02-overview-backend-systems.jpeg" alt="Imagem 2" style="width: 100%; border-radius: 5px;">
        <h2 style="margin-top: 10px;">Cabeçalho 2</h2>
        <p>Descrição 2</p>
    </div>
    <div style="width: 30%; margin-bottom: 20px; border: 1px solid #ccc; border-radius: 5px; padding: 20px; box-sizing: border-box;">
        <img src="/help/assets/03-overview-save-and-resume.jpeg" alt="Imagem 3" style="width: 100%; border-radius: 5px;">
        <h2 style="margin-top: 10px;">Cabeçalho 3</h2>
        <p>Descrição 3</p>
    </div>
    <!-- Add more cards as needed -->
</div>

—>

## Quem pode usar formulários adaptáveis headless? {#who-can-use-headless-adaptive-forms}

Qualquer desenvolvedor front-end familiarizado com as estruturas modernas do JavaScript pode usar formulários adaptáveis headless. Os desenvolvedores podem aproveitar sua experiência existente em idiomas de front-end, como o React, para criar belas experiências de captura de dados de nível empresarial.

Você não precisa de conhecimento prévio do Adobe Experience Manager para desenvolver formulários adaptáveis headless.

<!-- 
## How to join the early adopter program? {#how-to-join-early-adopter-forms}

The service is available for AEM Forms as a Cloud Service and AEM 6.5.16.0 Forms or later On-Premise term customers and Adobe-Managed Service enterprise customers. Send an email to [headlessadaptiveforms@adobe.com](mailto:headlessadaptiveforms@adobe.com) from your official email ID to join the early adopter program. 

-->
