---
title: Refaktoring kódu pro převod dotazu LINQ na příkaz foreach
description: Převeďte jakýkoli dotaz LINQ napsaný v syntaxi dotazu na příkaz foreach.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094093"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refaktoring pro převod LINQ na příkaz foreach

Tento refaktoring slouží k převodu [syntaxe dotazu LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) na příkaz [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) .

Tento refaktoring platí pro:

- C#

- Visual Basic

## <a name="how-to-use-it"></a>Jak ji použít

1. Vyberte celý dotaz LINQ od `from` .

   > [!NOTE]
   > Tento refaktoring lze použít pouze pro převod LINQ dotazů vyjádřených syntaxí dotazu a nikoli syntaxí metody.

1. Stiskněte klávesu **CTRL** + **.** nebo klikněte na ![ ikonu ikony Screwdriver Screwdriver na ](../media/screwdriver-icon.png) okraji souboru s kódem.

   ![Nabídka rychlé akce převedení LINQ na foreach](media/convert-linq-to-foreach.png)

1. Vyberte **převést na foreach**. Případně můžete výběrem **Zobrazit náhled změn** otevřít dialogové okno [Náhled změn](../../ide/preview-changes.md) a pak vybrat **použít**.

> [!NOTE]
> V jazyce C# kód vygenerovaný těmito refaktoringy používá explicitní typ nebo [var](/dotnet/csharp/language-reference/keywords/var) pro proměnnou iterace `foreach` smyčky. Typ v generovaném kódu, explicitní nebo implicitní, závisí na nastavení stylu kódu, které jsou v rozsahu. Tato konkrétní nastavení stylu kódu jsou konfigurována na úrovni počítače v nabídce **nástroje**  >  **Možnosti**  >  **textový editor**  >  **C#**  >  **Code Style**  >  **General**  >  ** \' Předvolby obecné var**nebo na úrovni řešení v souboru [EditorConfig](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types) . Pokud změníte nastavení stylu kódu v **možnostech**, znovu otevřete soubor kódu, aby se změny projevily.

## <a name="see-also"></a>Viz také

- [LINQ](/dotnet/standard/using-linq)
- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
