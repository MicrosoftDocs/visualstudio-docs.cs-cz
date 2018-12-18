---
title: Refaktorovat kódu pro převod pro opakování ve smyčce bude foreach – příkaz
ms.date: 05/10/2018
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
ms.openlocfilehash: 6a200874cec92fada17c13eb45e226ce26119a60
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34267670"
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>Refaktoring pro převod mezi smyčky a ForEach – příkaz

Tento článek popisuje refaktoring rychlé akce, která převod mezi dvěma opakování struktury. Její součástí jsou některé důvody, proč můžete chtít přepínat mezi [pro](/dotnet/csharp/language-reference/keywords/for) smyčky a [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) příkaz v kódu.

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>Převést pro opakování ve smyčce bude foreach – příkaz

Pokud máte [pro](/dotnet/csharp/language-reference/keywords/for) smyčky v kódu, můžete tento refaktoring převeďte ho na [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) příkaz.

Tato refaktoring platí pro:

- C#

> [!NOTE]
> **Převést na foreach** refaktoring rychlé akce je dostupná jenom pro [pro](/dotnet/csharp/language-reference/keywords/for) cykly, které obsahují všech tří částí: inicializátoru, podmínku a iterator.

### <a name="why-convert"></a>Proč převést

Důvodů, proč můžete chtít převést [pro](/dotnet/csharp/language-reference/keywords/for) cykly k [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) příkaz patří:

- Proměnná místní smyčky uvnitř smyčky s výjimkou jako index nepoužívejte pro přístup k položkám.

- Chcete zjednoduší kódování a snížit pravděpodobnost chyb logiku v inicializátoru, podmínku a iterator oddíly.

### <a name="how-to-use-it"></a>Způsobu jeho použití

1. Umístěte vaší pomocí kurzoru v `for` – klíčové slovo.

1. Stiskněte klávesu **Ctrl**+**.** nebo klikněte na tlačítko šroubovák ![šroubovák ikonu](../media/screwdriver-icon.png) ikonu na okraji souboru kódu.

   ![Převést do nabídky foreach](media/convert-to-foreach.png)

1. Vyberte **převést na 'foreach'**. Nebo vyberte **zobrazení náhledu změn** otevřete [zobrazení náhledu změn](../../ide/preview-changes.md) dialogové okno a potom vyberte **použít**.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>Převést příkazu foreach k smyčky for

Pokud máte [příkazu foreach (C#)](/dotnet/csharp/language-reference/keywords/foreach-in) nebo [For Each... Další (Visual Basic)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) příkaz ve vašem kódu, můžete tento refaktoring převeďte ho na [pro](/dotnet/csharp/language-reference/keywords/for) smyčky.

Tato refaktoring platí pro:

- C#

- Visual Basic

### <a name="why-convert"></a>Proč převést

Důvodů, proč můžete chtít převést [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) příkaz, který má [pro](/dotnet/csharp/language-reference/keywords/for) smyčky patří:

- Chcete použít pro více než jen přístup k položce proměnnou místní smyčky uvnitř smyčky.

- Jste [iterace v rámci vícerozměrné](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays) a chcete mít větší kontrolu nad prvků pole.

### <a name="how-to-use-it"></a>Způsobu jeho použití

1. Umístěte vaší pomocí kurzoru v `foreach` nebo `For Each` – klíčové slovo.

1. Stiskněte klávesu **Ctrl**+**.** nebo klikněte na tlačítko šroubovák ![šroubovák ikonu](../media/screwdriver-icon.png) ikonu na okraji souboru kódu.

   ![Převést na nabídky](media/convert-to-for.png)

1. Vyberte **převést na 'pro'**. Nebo vyberte **zobrazení náhledu změn** otevřete [zobrazení náhledu změn](../../ide/preview-changes.md) dialogové okno a potom vyberte **použít**.

1. Protože refaktoring zavádí nové proměnné počet iterací **přejmenovat** pole se zobrazí v pravém horním rohu editoru. Pokud chcete zvolit jiný název pro proměnnou, zadejte ho a stiskněte klávesu **Enter** nebo vyberte **použít** v **přejmenovat** pole. Pokud nechcete, aby vybrat nový název, stiskněte klávesu **Esc** nebo vyberte **použít** pro zavření **přejmenovat** pole.

> [!NOTE]
> Pro jazyk C#, kód vygenerovaný tyto refaktoring používá typ explicitní nebo [var](/dotnet/csharp/language-reference/keywords/var) pro typ položky v kolekci. Typ generovaného kódu, explicitní nebo implicitní, závisí na nastavení kódu stylu, které jsou v oboru. Tato nastavení konkrétního kódu stylu jsou konfigurována na úrovni počítače v části **nástroje** > **možnosti** > **textového editoru**  >  **C#** > **kódu stylu** > **Obecné** > **\'var' Předvolby**, nebo na úrovni řešení [EditorConfig](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types) souboru. Pokud změníte nastavení kódu stylu **možnosti**, otevřete soubor kódu pro změny se projeví.

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)