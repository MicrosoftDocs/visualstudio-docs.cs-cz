---
title: Refaktorovat kód nahradit var explicitního typu
ms.date: 05/15/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 9d816921f3449edfcd28a2fa9f4e2af9b9d015f9
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268918"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>Refaktoring pro nahrazení var explicitního typu

Použít tento refaktoring k nahrazení [var](/dotnet/csharp/language-reference/keywords/var) v místní deklarace proměnné explicitního typu.

Tato refaktoring platí pro:

- C#

## <a name="why-to-use-an-explicit-type"></a>Proč používat explicitního typu

Toto jsou některé důvody deklarovat proměnnou explicitního typu:

- Pro zlepšení čitelnosti kódu.

- Pokud nechcete inicializace proměnné v deklaraci.

Ale [var](/dotnet/csharp/language-reference/keywords/var) při proměnné je inicializován s anonymní typ a vlastnosti objektu jsou k němu přistupovat a později se musí použít. Další informace najdete v tématu [implicitně typované lokální proměnné (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables).

## <a name="how-to-use-it"></a>Způsobu jeho použití

1. Umístit pomocí kurzoru na `var` – klíčové slovo.

1. Stiskněte klávesu **Ctrl**+**.** nebo klikněte na tlačítko šroubovák ![šroubovák ikonu](../media/screwdriver-icon.png) ikonu na okraji souboru kódu.

   ![Použití explicitního typu rychlé akce nabídky](media/use-explicit-type.png)

1. Vyberte **použití explicitního typu**. Nebo vyberte **zobrazení náhledu změn** otevřete [zobrazení náhledu změn](../../ide/preview-changes.md) dialogové okno a potom vyberte **použít**.

## <a name="see-also"></a>Viz také

- [Implicitně typovaná proměnné (C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)