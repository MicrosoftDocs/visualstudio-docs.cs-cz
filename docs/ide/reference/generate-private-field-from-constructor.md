---
title: Generovat soukromé pole z konstruktoru
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8ef4188216b669b30b7af9bd725ec432bcd0a774
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527659"
---
# <a name="generate-private-field-from-constructor"></a>Generovat soukromé pole z konstruktoru

Tento refaktoring platí pro: 

- C# 

**Co:** Vygeneruje soukromé pole z konstruktoru. 

**Když:** Chcete rychle přidat soukromé pole z konstruktoru.

**Proč:** Zápis privátních polí může být časově náročný a opakující se. Použití tohoto refaktoringu je rychlé a díky tomu je program robustnější.

## <a name="how-to"></a>Postupy 

1. Umístěte kurzor na název parametru v rámci konstruktoru.

2. Stiskněte klávesu **Ctrl**+ **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
   
3. Vyberte možnost pro **Vytvoření a inicializaci pole**.

   ![Generovat soukromé pole z konstruktoru](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Viz také 

- [Refaktoring](../refactoring-in-visual-studio.md)
