---
title: Refaktorovat kód pro nahrazení var pomocí explicitního typu
ms.date: 05/15/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 566d064ac0ac1b9c48ee8e75697cef39b2ec4ee1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661690"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Refaktoring pro náhradu var pomocí explicitního typu

Pomocí tohoto refaktoringu nahraďte [var](/dotnet/csharp/language-reference/keywords/var) v deklaraci lokální proměnné explicitním typem.

Tento refaktoring platí pro:

- C#

## <a name="why-to-use-an-explicit-type"></a>Důvody použití explicitního typu

Níže jsou uvedeny některé důvody k deklaraci proměnné s explicitním typem:

- Pro zlepšení čitelnosti kódu.

- Pokud nechcete inicializovat proměnnou v deklaraci.

[Var](/dotnet/csharp/language-reference/keywords/var) však musí být použita, je-li proměnná inicializována anonymním typem a k vlastnostem objektu jsou přistupované později. Další informace naleznete v tématu [implicitně typované lokální proměnné (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Jak ji použít

1. Umístěte blikající kurzor na klíčové slovo `var`.

1. Stiskněte klávesu **Ctrl** + **.** nebo klikněte na ikonu ![screwdriver Screwdriver ](../media/screwdriver-icon.png) ikonu na okraji souboru s kódem.

   ![Použití nabídky explicitního typu pro rychlé akce](media/use-explicit-type.png)

1. Vyberte možnost **použít explicitní typ**. Případně můžete výběrem **Zobrazit náhled změn** otevřít dialogové okno [Náhled změn](../../ide/preview-changes.md) a pak vybrat **použít**.

## <a name="see-also"></a>Viz také:

- [Implicitně typované proměnné (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)