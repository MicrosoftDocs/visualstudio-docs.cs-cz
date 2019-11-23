---
title: Refaktoring kódu pro převod dotazu LINQ na příkaz foreach
description: Převeďte jakýkoli dotaz LINQ napsaný v syntaxi dotazu na příkaz foreach.
ms.date: 05/15/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: a618285e1981171eb8f5f2f435fb23d412296b5b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654537"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refaktoring pro převod LINQ na příkaz foreach

Tento refaktoring slouží k převodu [syntaxe dotazu LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) na příkaz [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) .

Tento refaktoring platí pro:

- C#

## <a name="how-to-use-it"></a>Jak ji použít

1. Vyberte celý dotaz LINQ od `from`.

   > [!NOTE]
   > Tento refaktoring lze použít pouze pro převod LINQ dotazů vyjádřených syntaxí dotazu a nikoli syntaxí metody.

1. Stisknutím klávesy **Ctrl**+ **.** nebo klikněte na ikonu Screwdriver ![Screwdriver ikony](../media/screwdriver-icon.png) na okraji souboru s kódem.

   ![Nabídka rychlé akce převedení LINQ na foreach](media/convert-linq-to-foreach.png)

1. Vyberte **převést na foreach**. Případně můžete výběrem **Zobrazit náhled změn** otevřít dialogové okno [Náhled změn](../../ide/preview-changes.md) a pak vybrat **použít**.

> [!NOTE]
> C#Kód generovaný těmito refaktoringy používá explicitní typ nebo [var](/dotnet/csharp/language-reference/keywords/var) pro proměnnou iterace `foreach` smyčky. Typ v generovaném kódu, explicitní nebo implicitní, závisí na nastavení stylu kódu, které jsou v rozsahu. Tato konkrétní nastavení stylu kódu jsou konfigurována na úrovni počítače v nabídce **nástroje** > **Možnosti** > **textový Editor** > **C#**  > **stylu kódu** > **Obecné** předvolby > \'**var**nebo na úrovni řešení v souboru [EditorConfig](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types) . Pokud změníte nastavení stylu kódu v **možnostech**, znovu otevřete soubor kódu, aby se změny projevily.

## <a name="see-also"></a>Viz také:

- [LINQ](/dotnet/standard/using-linq)
- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)