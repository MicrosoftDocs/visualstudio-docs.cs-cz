---
title: Převést anonymní typ na třídu
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
monikerRange: '>= vs-2019'
ms.openlocfilehash: 251a011695f6f5056e1fdf8e1a6be36b898b66f5
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809208"
---
# <a name="convert-anonymous-type-to-class"></a>Převedení anonymního typu na třídu

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Převést anonymní typ na třídu.

**Když:** Máte anonymní typ, na který chcete pokračovat ve vytváření ve třídě.

**Proč:** Anonymní typy jsou užitečné, pokud je používáte pouze místně. Jak váš kód roste, je vhodné mít snadný způsob, jak je propagovat na třídu.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor do anonymního typu.
2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

   ![Převést anonymní typ na třídu](media/convert-anon-to-class.png)

2. Stisknutím klávesy **ENTER** přijměte refaktoring.

   ![Převést anonymní typ na povolenou třídu](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
