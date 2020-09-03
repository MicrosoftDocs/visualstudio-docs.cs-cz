---
title: Zabezpečení textových šablon | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e24a90d4e7af351fc4ba5807d2af7830edede9cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671218"
---
# <a name="security-of-text-templates"></a>Zabezpečení textových šablon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Šablony textu mají následující aspekty zabezpečení:

- Textové šablony jsou zranitelné pro libovolná vložení kódu.

- Pokud mechanismus, který hostitel používá k vyhledání procesoru direktivy, není zabezpečený, může být spuštěný procesor se škodlivými direktivami.

## <a name="arbitrary-code"></a>Libovolný kód
 Při psaní šablony můžete do značek vložit libovolný kód \<# #> . To umožňuje spuštění libovolného kódu z textové šablony.

 Ujistěte se, že jste získali šablony z důvěryhodných zdrojů. Nezapomeňte upozornit koncové uživatele vaší aplikace, aby neprováděly šablony, které nepocházejí z důvěryhodných zdrojů.

## <a name="malicious-directive-processor"></a>Škodlivý procesor direktiv
 Modul textových šablon spolupracuje s hostitelem transformace a jedním nebo více procesory direktiv pro transformaci textu šablony do výstupního souboru. Další informace naleznete v tématu [proces transformace textové šablony](../modeling/the-text-template-transformation-process.md).

 Pokud mechanismus, který hostitel používá k vyhledání procesoru direktivy, není zabezpečený, spustí se riziko spuštění škodlivého procesoru direktiv. Procesor škodlivé direktivy by mohl poskytnout kód, který je spuštěn v `FullTrust` režimu při spuštění šablony. Vytvoříte-li vlastního hostitele transformace textové šablony, je nutné použít zabezpečený mechanismus, jako je například registr, aby modul mohl vyhledat procesory direktiv.
