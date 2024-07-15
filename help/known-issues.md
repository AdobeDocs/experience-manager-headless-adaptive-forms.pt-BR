---
title: Formulários adaptáveis headless problemas conhecidos
description: Formulários adaptáveis headless problemas conhecidos
keywords: headless, formulário adaptável, problemas conhecidos
hide: true
source-git-commit: 0127f8ddede38083f0932b0e8d7efdd0dd77c3a6
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 1%

---


# Problemas conhecidos {#known-issues}

* Não há suporte para padrões de edição, exibição e dados. (CQ-4327047)
* A restrição minItems não pode ser alterada dinamicamente. (CQ-4342499)
* As validações em nível de painel se violadas não geram nenhum erro. (CQ-4342373)
* As validações de arquivo se violadas não geram nenhum erro. (CQ-4342372)
* As propriedades personalizadas não são dinâmicas. (CQ-4342376)
* A alteração dinâmica dos dados de arquivo no evento de alteração usando expressões leva a um loop infinito. (CQ-4342377)
* O anexo de arquivo não oferece suporte ao texto de ajuda. (CQ-4342370)
* A caixa de seleção Obrigatório não mostra erros ao enviar, se não estiver selecionada. (CQ-4342371)
* aria-label não é adicionado ao anexo de arquivo. (CQ-4341494)
