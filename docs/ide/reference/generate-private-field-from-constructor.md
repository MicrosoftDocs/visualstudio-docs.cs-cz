---
title: Generovat soukromé pole a vlastnost z konstruktoru
description: Naučte se, jak pomocí nabídky rychlé akce a refaktoring vytvořit soukromé pole nebo vlastnost z konstruktoru.
ms.custom: SEO-VS-2020
ms.date: 06/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: e989efed8b58746312ed5f5a510efa049393f3db
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617458"
---
# <a name="generate-private-field-and-property-from-constructor"></a>Generovat soukromé pole a vlastnost z konstruktoru

Tento refaktoring platí pro: 

- C# 

**Co:** Vygeneruje soukromé pole nebo vlastnost z konstruktoru. 

**Když:** Chcete rychle přidat a inicializovat soukromé pole nebo vlastnost z konstruktoru.

**Proč:** Zápis privátních polí a vlastností může být časově náročný a opakující se. Použití tohoto refaktoringu je rychlé a díky tomu je program robustnější.

## <a name="how-to"></a>Postupy 

1. Umístěte kurzor na název parametru v rámci konstruktoru.

2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
   
3. Dále vyberte jednu z následujících možností:

- **Vytvořit a inicializovat pole** nebo **vytvořit a inicializovat vlastnost**.

   ![Generování soukromého pole z konstruktoru](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Viz také 

- [Refactoring](../refactoring-in-visual-studio.md)
