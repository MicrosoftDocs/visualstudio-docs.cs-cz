---
title: Vložení poznámek dokumentace XML
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e21d0617f954c0cc34975b7f8626b83966f6b5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77706388"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Postup: Vložení komentářů XML pro generování dokumentace

Visual Studio vám může pomoci dokumentovat prvky kódu, jako jsou třídy a metody, automatickým generováním standardní struktury komentářů dokumentace XML. V době kompilace můžete vygenerovat soubor XML, který obsahuje komentáře dokumentace.

> [!TIP]
> Informace o konfiguraci názvu a umístění generovaného souboru XML naleznete v [tématu Dokumentace kódu pomocí komentářů XML (C# Guide).](/dotnet/csharp/codedoc)

Soubor XML generovaný kompilátorem lze distribuovat společně s sestavením rozhraní .NET, aby visual studio a další idemohly pomocí technologie IntelliSense zobrazit rychlé informace o typech a členech. Soubor XML lze navíc spustit prostřednictvím nástrojů, jako jsou [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle,](https://www.microsoft.com/download/details.aspx?id=10526) které generují referenční webové stránky rozhraní API.

> [!NOTE]
> Příkaz **Vložit komentář,** který automaticky vloží komentáře dokumentace XML, je k dispozici v [jazyce C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) a [jazyce Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation). Můžete však ručně vložit komentáře dokumentace XML do souborů [jazyka C++](/cpp/build/reference/xml-documentation-visual-cpp) a stále generovat soubory dokumentace XML v době kompilace.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Vložení poznámek XML pro element kódu

1. Umístěte textový kurzor nad prvek, který chcete dokumentovat, například metodu.

2. Proveďte jednu z těchto akcí:

   - Typ `///` v jazyce `'''` C# nebo V jazyce Visual Basic

   - Z nabídky **Úpravy** zvolte **IntelliSense** > **Insert Comment** .

   - Z nabídky pravým tlačítkem nebo v místní nabídce na elementu kódu nebo těsně nad ním zvolte **Výstřižk** > **vložit komentář.**

   Šablona XML je okamžitě vygenerována nad elementem kódu. Například při komentování metody generuje ** \<souhrnný\> ** ** \<\> ** prvek, prvek param pro každý parametr a ** \<prvek\> vrátí** k dokumentu vrácené hodnoty.

   ![Šablona komentáře XML - C #](media/doc-preview-cs.png)

   ![Šablona komentáře XML – Visual Basic](media/doc-preview-vb.png)

3. Zadejte popisy pro každý element XML, aby byl prvek kódu plně dokumentován.

   ![Dokončený komentář](media/doc-result-cs.png)

Styly můžete použít v komentářích XML, které se vykreslí v rychlých informacích při najetí na prvek. Mezi tyto styly patří: kurzíva, tučné písmo, odrážky a odkaz, na který lze kliknout.

   ![Dokončený komentář](media/doc-style-cs.png) 

> [!NOTE]
> Po zadání [option](../../ide/reference/options-text-editor-csharp-advanced.md) `///` do jazyka C# nebo `'''` Visual Basic je možné přepnout komentáře dokumentace XML. Na řádku nabídek zvolte**Možnosti** **nástrojů,** > abyste otevřeli dialogové okno **Volby.** Potom přejděte do **textového editoru** > **C#** nebo **základní** > **rozšířené**. V části **Nápověda editoru** vyhledejte možnost **Generovat komentáře dokumentace XML.**

## <a name="see-also"></a>Viz také

- [Komentáře k dokumentaci XML (Průvodce programováním jazyka C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentace kódu pomocí komentářů XML (Průvodce C# )](/dotnet/csharp/codedoc)
- [Postup: Vytvoření dokumentace XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [C++ Komentáře](/cpp/cpp/comments-cpp)
- [Dokumentace XML (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Generování kódu](../code-generation-in-visual-studio.md)
