---
title: Zabezpečení textových šablon
description: Seznamte se se zabezpečením a textovými šablonami, včetně témat, jako jsou například libovolný kód a škodlivé procesory direktiv
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d54421ea4df9c54fd4ec8c1804a1a292061996ab
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363793"
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
