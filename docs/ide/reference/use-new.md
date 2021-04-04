---
title: Použití výrazu new()
description: Naučte se používat `new()` , když nemůžete použít `var` .
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 889be18ab342f515bf5add266088a7ee69c087c1
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218071"
---
# <a name="use-new"></a>Použití `new()`

To platí pro:

- C#

**Co:** Použijte `new()` .

**Když:** Máte pole, které nemůžete použít, `var` nebo nechcete použít předvolby stylu kódu `var` .

**Proč:** Takže nemusíte psát opakující kód opakováním typu dvakrát.

## <a name="how-to"></a>Postupy

1. Umístěte blikající kurzor na deklaraci pole.

2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

3. Vyberte **použít New (...)**:

    ![Použít New (...)](media/use-new.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
