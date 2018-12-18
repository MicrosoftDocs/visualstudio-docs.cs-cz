---
title: Refaktorovat kód převést dotaz LINQ foreach – příkaz
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
ms.openlocfilehash: e3e4e448931e028c53d62c534e2785e4f026a7ec
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34268916"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>Refaktoring převést LINQ foreach – příkaz

Pomocí této refaktoring můžete převést [syntaxe dotazů LINQ](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) k [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) příkaz.

Tato refaktoring platí pro:

- C#

## <a name="how-to-use-it"></a>Způsobu jeho použití

1. Vyberte celou LINQ dotazů počáteční s `from`.

   > [!NOTE]
   > Tento refaktoring pouze slouží k převedení dotazů LINQ vyjádřený syntaxe dotazů a není syntaxe využívající metody.

1. Stiskněte klávesu **Ctrl**+**.** nebo klikněte na tlačítko šroubovák ![šroubovák ikonu](../media/screwdriver-icon.png) ikonu na okraji souboru kódu.

   ![Převést LINQ do nabídky rychlé akce foreach](media/convert-linq-to-foreach.png)

1. Vyberte **převést na 'foreach'**. Nebo vyberte **zobrazení náhledu změn** otevřete [zobrazení náhledu změn](../../ide/preview-changes.md) dialogové okno a potom vyberte **použít**.

> [!NOTE]
> Pro jazyk C#, kód vygenerovaný tyto refaktoring používá typ explicitní nebo [var](/dotnet/csharp/language-reference/keywords/var) pro proměnné iterace z `foreach` smyčky. Typ generovaného kódu, explicitní nebo implicitní, závisí na nastavení kódu stylu, které jsou v oboru. Tato nastavení konkrétního kódu stylu jsou konfigurována na úrovni počítače v části **nástroje** > **možnosti** > **textového editoru**  >  **C#** > **kódu stylu** > **Obecné** > **\'var' Předvolby**, nebo na úrovni řešení [EditorConfig](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types) souboru. Pokud změníte nastavení kódu stylu **možnosti**, otevřete soubor kódu pro změny se projeví.

## <a name="see-also"></a>Viz také

- [LINQ](/dotnet/standard/using-linq)
- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)