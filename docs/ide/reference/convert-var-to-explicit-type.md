---
title: Refaktorovat kód pro nahrazení var pomocí explicitního typu
description: Naučte se používat rychlé akce k nahrazení var v lokální proměnné výrazu explicitního typu.
ms.custom: SEO-VS-2020
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: d45d4ffcbdedb456bde40b3fd1103fa8b21a8f9b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919596"
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

1. Umístěte blikající kurzor na `var` klíčové slovo.

1. Stiskněte klávesu **CTRL** + **.** nebo klikněte na ![ ikonu ikony Screwdriver Screwdriver na ](../media/screwdriver-icon.png) okraji souboru s kódem.

   ![Použití nabídky explicitního typu pro rychlé akce](media/use-explicit-type.png)

1. Vyberte možnost **použít explicitní typ**. Případně můžete výběrem **Zobrazit náhled změn** otevřít dialogové okno [Náhled změn](../../ide/preview-changes.md) a pak vybrat **použít**.

## <a name="see-also"></a>Viz také

- [Implicitně typované proměnné (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
