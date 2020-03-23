---
title: Refaktorovat kód, který nahradí var explicitním typem
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 4ec388564e1851402f085f6bbaefba08dbea212c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595771"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Refaktoring nahrazení var u explicitního typu

Tento refaktoring slouží k nahrazení [var](/dotnet/csharp/language-reference/keywords/var) v deklaraci místní proměnné explicitním typem.

Toto refaktoring se vztahuje na:

- C#

## <a name="why-to-use-an-explicit-type"></a>Proč používat explicitní typ

Níže jsou uvedeny některé důvody deklarovat proměnnou s explicitní typ:

- Chcete-li zlepšit čitelnost kódu.

- Pokud nechcete inicializovat proměnnou v deklaraci.

[Var](/dotnet/csharp/language-reference/keywords/var) však musí být použit při inicializování proměnné s anonymním typem a vlastnosti objektu jsou přístupné později. Další informace naleznete [v tématu Implicitně zadané místní proměnné (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Jak ji použít

1. Umístěte stříšku `var` na klíčové slovo.

1. Stiskněte **klávesu Ctrl**+**.** nebo klepněte ![na ikonu](../media/screwdriver-icon.png) ikony šroubováku šroubováku v okraji souboru kódu.

   ![Použití nabídky explicitních textových rychlých akcí](media/use-explicit-type.png)

1. Vyberte **použít explicitní typ**. Nebo vyberte **Náhled změn,** chcete-li otevřít dialogové okno [Změny náhledu,](../../ide/preview-changes.md) a pak vyberte **Použít**.

## <a name="see-also"></a>Viz také

- [Implicitně zadané proměnné (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
