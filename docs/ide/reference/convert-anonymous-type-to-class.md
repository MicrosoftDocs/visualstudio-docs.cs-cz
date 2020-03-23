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
ms.openlocfilehash: 2379ce588eeb4773e562f630ade37e28d7f17315
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094289"
---
# <a name="convert-anonymous-type-to-class"></a>Převedení anonymního typu na třídu

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Převeďte anonymní typ na třídu.

**Kdy:** Máte anonymní typ, který chcete pokračovat v jeho sestavení ve třídě.

**Proč:** Anonymní typy jsou užitečné, pokud je používáte pouze místně. Jak váš kód roste, je hezké mít snadný způsob, jak je propagovat do třídy.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor anonymním typem.
2. Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**

   ![Převést anonymní typ na třídu](media/convert-anon-to-class.png)

2. Stisknutím **klávesy Enter** přijměte refaktoring.

   ![Převést anonymní typ na třídu přijat](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
