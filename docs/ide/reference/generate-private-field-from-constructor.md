---
title: Generovat soukromé pole a vlastnost z konstruktoru
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
ms.openlocfilehash: 56bd361d2bffb4ff17b03ac6743837032d1934e1
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283720"
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
