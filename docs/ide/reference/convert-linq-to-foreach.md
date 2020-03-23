---
title: Refaktorovat kód pro převod dotazu LINQ na příkaz foreach
description: Převeďte libovolný dotaz LINQ napsaný v syntaxi dotazu na příkaz foreach.
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
ms.openlocfilehash: 6e1b24cb8406ff29659eb79d1d9fa856db628b89
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094093"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refaktoring převést LINQ foreach příkaz

Pomocí tohoto refaktoringu převést [LINQ syntaxe dotazu](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) [foreach.](/dotnet/csharp/language-reference/keywords/foreach-in)

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

## <a name="how-to-use-it"></a>Jak ji použít

1. Vyberte celý dotaz LINQ začínající písmenem `from`.

   > [!NOTE]
   > Toto refaktoring lze použít pouze k převodu LINQ dotazy vyjádřené syntaxí dotazu a nikoli syntaxe metody.

1. Stiskněte **klávesu Ctrl**+**.** nebo klepněte ![na ikonu](../media/screwdriver-icon.png) ikony šroubováku šroubováku v okraji souboru kódu.

   ![Převést LINQ na nabídku foreach rychlé akce](media/convert-linq-to-foreach.png)

1. Vyberte **převést na 'foreach'**. Nebo vyberte **Náhled změn,** chcete-li otevřít dialogové okno [Změny náhledu,](../../ide/preview-changes.md) a pak vyberte **Použít**.

> [!NOTE]
> Pro C# kód generovaný těmito refaktoringy používá [var](/dotnet/csharp/language-reference/keywords/var) buď explicitní typ `foreach` nebo var pro itikovou proměnnou smyčky. Typ v generovaném kódu, explicitní nebo implicitní, závisí na nastavení stylu kódu, které jsou v oboru. Tato konkrétní nastavení stylu kódu jsou konfigurována na úrovni počítače v**\'předvolbách** >  **Tools** > **Nástroje:** > **Textový editor** > **C#** > **Styl kódu****Obecné** > var nebo na úrovni řešení v souboru [EditorConfig.](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types) Pokud změníte nastavení stylu kódu v **možnostech**, znovu otevřete soubor kódu, aby se změny projevily.

## <a name="see-also"></a>Viz také

- [LINQ](/dotnet/standard/using-linq)
- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
