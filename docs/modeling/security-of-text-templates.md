---
title: Zabezpečení textových šablon
description: Seznamte se se zabezpečením a textovými šablonami, včetně témat, jako jsou například libovolný kód a škodlivé procesory direktiv
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a740a6f7a4c532a61a5e412c94fa4321c5da707
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385757"
---
# <a name="security-of-text-templates"></a>Zabezpečení textových šablon
Šablony textu mají následující aspekty zabezpečení:

- Textové šablony jsou zranitelné pro libovolná vložení kódu.

- Pokud mechanismus, který hostitel používá k vyhledání procesoru direktivy, není zabezpečený, může být spuštěný procesor se škodlivými direktivami.

## <a name="arbitrary-code"></a>Libovolný kód
 Při psaní šablony můžete do značek vložit libovolný kód \<# #> . To umožňuje spuštění libovolného kódu z textové šablony.

 Ujistěte se, že jste získali šablony z důvěryhodných zdrojů. Nezapomeňte upozornit koncové uživatele vaší aplikace, aby neprováděly šablony, které nepocházejí z důvěryhodných zdrojů.

## <a name="malicious-directive-processor"></a>Škodlivý procesor direktiv
 Modul textových šablon spolupracuje s hostitelem transformace a jedním nebo více procesory direktiv pro transformaci textu šablony do výstupního souboru. Další informace naleznete v tématu [proces transformace textové šablony](../modeling/the-text-template-transformation-process.md).

 Pokud mechanismus, který hostitel používá k vyhledání procesoru direktivy, není zabezpečený, spustí se riziko spuštění škodlivého procesoru direktiv. Procesor škodlivé direktivy by mohl poskytnout kód, který je spuštěn v `FullTrust` režimu při spuštění šablony. Vytvoříte-li vlastního hostitele transformace textové šablony, je nutné použít zabezpečený mechanismus, jako je například registr, aby modul mohl vyhledat procesory direktiv.
