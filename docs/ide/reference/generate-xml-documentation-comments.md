---
title: Vložit komentáře k dokumentaci XML
ms.date: 01/22/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0e21d0617f954c0cc34975b7f8626b83966f6b5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77706388"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Postupy: vložení komentářů XML pro generování dokumentace

Visual Studio vám může přispět k dokumentaci prvků kódu, jako jsou třídy a metody, automatickým generováním standardní struktury komentářů dokumentace XML. V době kompilace můžete vygenerovat soubor XML, který obsahuje dokumentační komentáře.

> [!TIP]
> Informace o konfiguraci názvu a umístění vygenerovaného souboru XML naleznete v tématu [dokumentování kódu pomocí komentářů XML (Průvodce C#)](/dotnet/csharp/codedoc).

Soubor XML generovaný kompilátorem lze distribuovat společně s sestavením .NET tak, aby Visual Studio a jiné prostředí pro vývoj mohli používat technologii IntelliSense k zobrazení rychlých informací o typech a členech. Navíc můžete soubor XML spustit prostřednictvím nástrojů, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) , pro generování odkazů na webové stránky rozhraní API.

> [!NOTE]
> Příkaz **Vložit komentář** , který automaticky vloží dokumentační komentáře XML, je k dispozici v [jazyce C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) a [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation). Můžete však ručně vložit [dokumentační komentáře XML do souborů C++](/cpp/build/reference/xml-documentation-visual-cpp) a přesto vygenerovat soubory dokumentace XML v době kompilace.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Vložení komentářů XML pro prvek kódu

1. Umístěte textový kurzor nad prvek, který chcete dokumentovat, například metodu.

2. Proveďte jednu z následujících akcí:

   - Typ `///` v jazyce C# nebo `'''` v Visual Basic

   - V nabídce **Upravit** vyberte **IntelliSense**  >  **Vložit komentář** .

   - V místní nabídce nebo v kontextové nabídce klikněte na tlačítko nebo těsně nad prvkem kódu, vyberte možnost **fragment**  >  **Vložit komentář**

   Šablona XML je ihned vygenerována nad prvkem kódu. Například při komentování metody vygeneruje **\<summary\>** element, **\<param\>** prvek pro každý parametr a **\<returns\>** prvek pro dokumentaci návratové hodnoty.

   ![Šablona komentářů XML – C #](media/doc-preview-cs.png)

   ![Šablona komentářů XML – Visual Basic](media/doc-preview-vb.png)

3. Zadejte popisy pro každý element XML pro úplné dokumentování elementu kódu.

   ![Dokončený komentář](media/doc-result-cs.png)

Můžete použít styly v komentářích XML, které budou vykresleny rychle informace při přechodu na prvek. Mezi tyto styly patří kurzíva, tučné, odrážky a odkaz s odkazem.

   ![Dokončený komentář](media/doc-style-cs.png) 

> [!NOTE]
> Po zadání [option](../../ide/reference/options-text-editor-csharp-advanced.md) `///` v jazyce C# nebo Visual Basic existuje možnost přepínat komentáře k dokumentaci XML `'''` . V řádku nabídek klikněte na možnost **Tools**  >  **Možnosti** nástrojů a otevřete dialogové okno **Možnosti** . Pak přejděte do **textového editoru**  >  **C#** nebo **Basic**  >  **Advanced**. V části **help editoru** vyhledejte možnost **Generovat dokumentační komentáře XML** .

## <a name="see-also"></a>Viz také

- [Komentáře dokumentace XML (Průvodce programováním v C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentace kódu s komentáři XML (Průvodce C#)](/dotnet/csharp/codedoc)
- [Postupy: vytvoření dokumentace XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [C++ – komentáře](/cpp/cpp/comments-cpp)
- [Dokumentace XML (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Generování kódu](../code-generation-in-visual-studio.md)
