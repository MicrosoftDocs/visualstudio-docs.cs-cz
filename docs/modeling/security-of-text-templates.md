---
title: Zabezpečení textových šablon
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 71052a0d4120a74269f2aa05412230284271e574
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947518"
---
# <a name="security-of-text-templates"></a>Zabezpečení textových šablon
Textové šablony mají následující potížích se zabezpečením:

-   Textové šablony jsou citlivé na libovolný kód vložení.

-   Pokud mechanismus, který hostitel používá k nalezení procesoru direktiv není zabezpečený, může spustit škodlivý procesoru direktiv.

## <a name="arbitrary-code"></a>Libovolný kód
 Když píšete šablonu, můžete vložit žádný kód v rámci \<## > značky. To umožňuje v rámci textové šablony provést z libovolného kódu.

 Ujistěte se, že získat šablony z důvěryhodných zdrojů. Ujistěte se, že upozornit koncovým uživatelům vaší aplikace není k provedení šablony, které nepocházejí z důvěryhodných zdrojů.

## <a name="malicious-directive-processor"></a>Škodlivý procesoru direktiv
 Text šablony modul komunikuje se službou hostitel transformaci a jeden nebo více procesory direktiv k transformaci text šablony do výstupního souboru. Další informace najdete v tématu [proces transformace textových šablon](../modeling/the-text-template-transformation-process.md).

 Pokud mechanismus, který hostitel používá k nalezení procesoru direktiv nejsou zabezpečené, spustí se nebezpečí spuštění škodlivého procesoru direktiv. Škodlivý procesoru direktiv může poskytnout kód, který běží v `FullTrust` režimu při spuštění šablony. Pokud vytvoříte vlastního hostitele textových šablon transformace, je nutné použít zabezpečený mechanismus, například registr pro modul vyhledat procesory direktiv.