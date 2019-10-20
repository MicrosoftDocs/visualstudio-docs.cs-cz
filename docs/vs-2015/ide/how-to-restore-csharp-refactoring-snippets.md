---
title: 'Postupy: obnovení C# fragmentů refaktoringu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- unsafe expansion
- expansions, unsafe
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ae3f1d74a482192d3782aaa87baa816694abcf4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670789"
---
# <a name="how-to-restore-c-refactoring-snippets"></a>Postupy: Obnovení fragmentů kódu refaktoringu jazyka C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C#operace refaktoringu spoléhají na fragmenty kódu, které se nacházejí v následujícím adresáři:

 *Instalační adresář*\Microsoft Visual Studio 14,0 \VC#\Snippets \\*Language ID*\Refactoring

 Pokud se tento adresář refaktoringu nebo nějaké soubory v tomto adresáři odstraní nebo jsou poškozené, C# operace refaktoringu nemusí v integrovaném vývojovém prostředí fungovat. Následující postupy vám mohou pomáhat s obnovením C# fragmentů kódu refaktoringu.

### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>Pro ověření C# , že fragmenty refaktoringu jsou k dispozici prostřednictvím Správce fragmentů kódu

1. V nabídce **nástroje** vyberte **Správce fragmentů kódu**.

2. V dialogovém okně **Správce fragmentů kódů** vyberte v rozevíracím seznamu **jazyk** možnost **Visual C#**  .

     Složka **refaktoringu** by se měla zobrazit v seznamu složek stromového zobrazení.

### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>Postup obnovení refaktoringu viz komentář ve Správci fragmentů kódu

1. Pokud se složka **refaktoringu** nezobrazuje v seznamu složky stromového zobrazení Správce fragmentů kódu, pak pomocí tohoto postupu přidejte fragmenty refaktoringu zpátky do Správce fragmentů kódu.

2. V nabídce **nástroje** vyberte **Správce fragmentů kódu**.

3. V dialogovém okně **Správce fragmentů kódů** vyberte v rozevíracím seznamu **jazyk** možnost **Visual C#**  .

4. Klikněte na tlačítko **Přidat**. Zobrazí se dialogové okno **adresáře fragmentů kódu** , které vám pomůže najít a zadat adresář, který se má přidat zpátky do Správce fragmentů kódu.

5. Vyhledejte složku **refaktoringu** , jejíž cesta k adresáři je:

     *Instalační adresář*\Microsoft Visual Studio 14,0 \VC#\Snippets \\*Language ID*\Refactoring

     Skutečná cesta je pro výchozí instalaci podobná následující:

     C:\Program Files\Microsoft Visual Studio 14,0 \VC#\Snippets\1033\Refactoring.

6. V dialogovém okně **fragmenty** kódu klikněte na **otevřít** a potom ve Správci fragmentů kódů klikněte na **OK** .

## <a name="see-also"></a>Viz také
 [C# ](../ide/visual-csharp-code-snippets.md) [Fragmenty kódu](../ide/code-snippets.md) pro [C#refaktoring](../csharp-ide/refactoring-csharp.md) fragmentů kódu vizuálu ()
