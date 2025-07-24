---
title: Problemas conhecidos do Headless Adaptive Forms
description: Problemas conhecidos de formulários adaptáveis headless.
keywords: headless, formulário adaptável, problemas conhecidos
hide: true
source-git-commit: 28792fe1690e68cd301a0de2ce8bff53fae1605f
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 16%

---


# Problemas conhecidos {#known-issues}

* Não há suporte para padrões de edição, exibição e dados. (CQ-4327047)
* A restrição minItems não pode ser alterada dinamicamente. (CQ-4342499)
* As validações em nível de painel se violadas não geram nenhum erro. (CQ-4342373)
* As validações de arquivo se violadas não geram nenhum erro. (CQ-4342372)
* As propriedades personalizadas não são dinâmicas. (CQ-4342376)
* A alteração dinâmica dos dados de arquivo em um evento de alteração usando expressões leva a um loop infinito. (CQ-4342377)
* O anexo de arquivo não oferece suporte ao texto da Ajuda. (CQ-4342370)
* A caixa de seleção necessária não mostra erros ao enviar, se não estiver selecionada. (CQ-4342371)
* aria-label não é adicionado ao anexo de arquivo. (CQ-4341494)
