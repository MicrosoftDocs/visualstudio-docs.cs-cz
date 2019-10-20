---
title: Zabezpečení textových šablon
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eab987d406d6a2c05c8350aaac9dd1ecfc13e4a8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660093"
---
# <a name="security-of-text-templates"></a>Zabezpečení textových šablon
Šablony textu mají následující aspekty zabezpečení:

- Textové šablony jsou zranitelné pro libovolná vložení kódu.

- Pokud mechanismus, který hostitel používá k vyhledání procesoru direktivy, není zabezpečený, může být spuštěný procesor se škodlivými direktivami.

## <a name="arbitrary-code"></a>Libovolný kód
 Když napíšete šablonu, můžete do značek \< # # > vložit jakýkoli kód. To umožňuje spuštění libovolného kódu z textové šablony.

 Ujistěte se, že jste získali šablony z důvěryhodných zdrojů. Nezapomeňte upozornit koncové uživatele vaší aplikace, aby neprováděly šablony, které nepocházejí z důvěryhodných zdrojů.

## <a name="malicious-directive-processor"></a>Škodlivý procesor direktiv
 Modul textových šablon spolupracuje s hostitelem transformace a jedním nebo více procesory direktiv pro transformaci textu šablony do výstupního souboru. Další informace naleznete v tématu [proces transformace textové šablony](../modeling/the-text-template-transformation-process.md).

 Pokud mechanismus, který hostitel používá k vyhledání procesoru direktivy, není zabezpečený, spustí se riziko spuštění škodlivého procesoru direktiv. Procesor škodlivé direktivy by mohl poskytnout kód, který je spuštěn v režimu `FullTrust` při spuštění šablony. Vytvoříte-li vlastního hostitele transformace textové šablony, je nutné použít zabezpečený mechanismus, jako je například registr, aby modul mohl vyhledat procesory direktiv.