---
title: Refaktorovat kód pro převod smyčky for na příkaz foreach
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
ms.openlocfilehash: af52761f5cb199c7f842d01589c35501898b09aa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094596"
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Refaktoring převést mezi for smyčky a foreach prohlášení

Tento článek popisuje rychlé akce refaktoringy, které převádějí mezi dvěma strukturami opakování. Obsahuje některé důvody, proč můžete chtít přepínat mezi [for](/dotnet/csharp/language-reference/keywords/for) smyčky a [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) prohlášení v kódu.

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Převést smyčku for na příkaz foreach

Pokud máte [for](/dotnet/csharp/language-reference/keywords/for) smyčky v kódu, můžete použít toto refaktoring převést na [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) prohlášení.

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

> [!NOTE]
> **Převést na foreach** rychlé akce refaktoring je k dispozici pouze [pro](/dotnet/csharp/language-reference/keywords/for) smyčky, které obsahují všechny tři části: inicializátor, podmínka a iterátor.

### <a name="why-convert"></a>Proč konvertovat

Mezi důvody, proč můžete chtít převést smyčku [for](/dotnet/csharp/language-reference/keywords/for) na [foreach,](/dotnet/csharp/language-reference/keywords/foreach-in) patří:

- Nepoužíváte proměnnou místní smyčky uvnitř smyčky s výjimkou jako index pro přístup k položkám.

- Chcete zjednodušit kód a snížit pravděpodobnost logických chyb v inicializačním systému, stavu a iterátoru.

### <a name="how-to-use-it"></a>Jak ji použít

1. Umístěte stříšku `for` do klíčového slova.

1. Stiskněte **klávesu Ctrl**+**.** nebo klikněte ![na ikonu](../media/screwdriver-icon.png) ikony šroubováku šroubováku v okraji souboru kódu.

   ![Převést na nabídku foreach](media/convert-to-foreach.png)

1. Vyberte **převést na 'foreach'**. Nebo vyberte **Náhled změn,** chcete-li otevřít dialogové okno [Změny náhledu,](../../ide/preview-changes.md) a pak vyberte **Použít**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Převést příkaz foreach na smyčku for

Pokud máte [foreach (C#)](/dotnet/csharp/language-reference/keywords/foreach-in) nebo [pro každý... Další (Visual Basic)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) příkaz ve vašem kódu, můžete použít toto refaktoring převést na [for](/dotnet/csharp/language-reference/keywords/for) smyčky.

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

### <a name="why-convert"></a>Proč konvertovat

Mezi důvody, proč chtít převést příkaz [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) na smyčku [for,](/dotnet/csharp/language-reference/keywords/for) patří:

- Chcete použít proměnnou místní hospo- uvnitř smyčky pro více než jen přístup k položce.

- [Iterace prostřednictvím vícerozměrné pole](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) a chcete větší kontrolu nad prvky pole.

### <a name="how-to-use-it"></a>Jak ji použít

1. Umístěte stříšku `foreach` `For Each` do klíčového slova nebo.

1. Stiskněte **klávesu Ctrl**+**.** nebo klikněte ![na ikonu](../media/screwdriver-icon.png) ikony šroubováku šroubováku v okraji souboru kódu.

   ![Převést na nabídku](media/convert-to-for.png)

1. Vyberte **Převést na 'pro'**. Nebo vyberte **Náhled změn,** chcete-li otevřít dialogové okno [Změny náhledu,](../../ide/preview-changes.md) a pak vyberte **Použít**.

1. Vzhledem k tomu, že refaktoring zavádí novou proměnnou počtu iterací, zobrazí se pole **Přejmenovat** v pravém horním rohu editoru. Pokud chcete pro proměnnou zvolit jiný název, zadejte ji a pak stiskněte **Enter** nebo vyberte **Použít** v poli **Přejmenovat.** Pokud nechcete vybrat nový název, stiskněte **Esc** nebo vyberte **Použít,** chcete-li zavřít pole **Přejmenovat.**

> [!NOTE]
> Pro C#kód generovaný těmito refaktoringy používá buď explicitní typ nebo [var](/dotnet/csharp/language-reference/keywords/var) pro typ položek v kolekci. Typ v generovaném kódu, explicitní nebo implicitní, závisí na nastavení stylu kódu, které jsou v oboru. Tato konkrétní nastavení stylu kódu jsou konfigurována na úrovni počítače v**\'předvolbách** >  **Tools** > **Nástroje:** > **Textový editor** > **C#** > **Styl kódu****Obecné** > var nebo na úrovni řešení v souboru [EditorConfig.](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types) Pokud změníte nastavení stylu kódu v **možnostech**, znovu otevřete soubor kódu, aby se změny projevily.

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
