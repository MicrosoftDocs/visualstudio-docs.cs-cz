---
title: Vložit komentáře dokumentace XML
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e21d0617f954c0cc34975b7f8626b83966f6b5d
ms.sourcegitcommit: 9de7d25056da59df0941508c80c0b12766ba6580
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706388"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Postupy: vložení komentáře XML pro generování dokumentace

Visual Studio vám může pomoct dokumentovat prvků kódu, jako jsou třídy a metody, pomocí automatického generování standardní struktura komentáře dokumentace XML. V době kompilace můžete vygenerovat soubor XML, který obsahuje komentáře k dokumentaci.

> [!TIP]
> Informace o konfiguraci názvu a umístění vygenerovaného souboru XML naleznete v tématu [dokumentování kódu pomocí komentářů XMLC# (Průvodce)](/dotnet/csharp/codedoc).

XML souboru generovaného kompilátorem můžete distribuovat spolu s sestavení .NET, aby Visual Studio a jiná Integrovaná vývojová prostředí pomocí technologie IntelliSense můžete zobrazit rychlé informace o typech a členech. Navíc můžete soubor XML spustit prostřednictvím nástrojů, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) , pro generování odkazů na webové stránky rozhraní API.

> [!NOTE]
> Příkaz **Vložit komentář** , který automaticky vloží dokumentační komentáře XML, je k [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) dispozici v a [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation). Můžete však ručně vložit [dokumentační komentáře XML do C++ ](/cpp/build/reference/xml-documentation-visual-cpp) souborů a přesto vygenerovat soubory dokumentace XML v době kompilace.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Chcete-li vložit komentáře XML pro prvek kódu

1. Umístěte kurzor nad element, který má k dokumentu, například metoda text.

2. Proveďte jednu z těchto akcí:

   - Zadejte `///` v C#nebo `'''` v Visual Basic

   - V nabídce **Upravit** vyberte **IntelliSense** > **Vložit komentář** .

   - V místní nabídce nebo v kontextové nabídce klikněte na tlačítko nebo hned nad prvkem kódu, vyberte **fragment** > **Vložit komentář**

   XML šablony okamžitě generováno nad prvek kódu. Například při komentování metody generuje **\>prvek\<summary** , **\<param\>** element pro každý parametr a **\<vrátí\>** elementu pro dokumentaci návratové hodnoty.

   ![Šablona komentáře XML –C#](media/doc-preview-cs.png)

   ![Šablona komentáře XML – Visual Basic](media/doc-preview-vb.png)

3. Zadejte popis jednotlivých prvků XML do plně dokumentu na prvek kódu.

   ![Dokončené komentář](media/doc-result-cs.png)

Můžete použít styly v komentářích XML, které budou vykresleny rychle informace při přechodu na prvek. Mezi tyto styly patří kurzíva, tučné, odrážky a odkaz s odkazem.

   ![Dokončené komentář](media/doc-style-cs.png) 

> [!NOTE]
> Po zadání `///` [](../../ide/reference/options-text-editor-csharp-advanced.md) do C# nebo `'''` Visual Basic je k dispozici možnost přepínat dokumentační komentáře XML. V řádku nabídek vyberte **nástroje** > **Možnosti** . tím otevřete dialogové okno **Možnosti** . Pak přejděte do **textového editoru** > **C#** nebo **Basic** > **Advanced**. V části **help editoru** vyhledejte možnost **Generovat dokumentační komentáře XML** .

## <a name="see-also"></a>Viz také

- [Komentáře dokumentace XML (C# Průvodce programováním)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentace kódu s komentáři XML (C# průvodce)](/dotnet/csharp/codedoc)
- [Postupy: vytvoření dokumentace XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [C++Vyjádření](/cpp/cpp/comments-cpp)
- [Dokumentace XML (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Generování kódu](../code-generation-in-visual-studio.md)
