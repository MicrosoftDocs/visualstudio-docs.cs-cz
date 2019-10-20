---
title: Vložit komentáře k dokumentaci XML
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e9153677b833a89a236923a971b511548b064142
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668613"
---
# <a name="how-to-insert-xml-comments-for-documentation-generation"></a>Postupy: vložení komentářů XML pro generování dokumentace

Visual Studio vám může přispět k dokumentaci prvků kódu, jako jsou třídy a metody, automatickým generováním standardní struktury komentářů dokumentace XML. V době kompilace můžete vygenerovat soubor XML, který obsahuje dokumentační komentáře.

> [!TIP]
> Informace o konfiguraci názvu a umístění vygenerovaného souboru XML naleznete v tématu [dokumentování kódu pomocí komentářů XMLC# (Průvodce)](/dotnet/csharp/codedoc).

Soubor XML generovaný kompilátorem lze distribuovat společně s sestavením .NET tak, aby Visual Studio a jiné prostředí pro vývoj mohli používat technologii IntelliSense k zobrazení rychlých informací o typech a členech. Navíc můžete soubor XML spustit prostřednictvím nástrojů, jako je [DocFX](https://dotnet.github.io/docfx/) a [Sandcastle](https://www.microsoft.com/download/details.aspx?id=10526) , pro generování odkazů na webové stránky rozhraní API.

> [!NOTE]
> Příkaz **Vložit komentář** , který automaticky vloží dokumentační komentáře XML, je k [C#](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments) dispozici v a [Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation). Můžete však ručně vložit [dokumentační komentáře XML do C++ ](/cpp/build/reference/xml-documentation-visual-cpp) souborů a přesto vygenerovat soubory dokumentace XML v době kompilace.

## <a name="to-insert-xml-comments-for-a-code-element"></a>Vložení komentářů XML pro prvek kódu

1. Umístěte textový kurzor nad prvek, který chcete dokumentovat, například metodu.

1. Proveďte jednu z těchto akcí:

   - Zadejte `///` v C#nebo `'''` v Visual Basic

   - V nabídce **Upravit** vyberte **IntelliSense**  > **Vložit komentář** .

   - V místní nabídce nebo v kontextové nabídce klikněte na tlačítko nebo hned nad prvkem kódu, vyberte **fragment**  > **Vložit komentář**

   Šablona XML je ihned vygenerována nad prvkem kódu. Například při komentování metody generuje **\<summary \>** prvek, **\<param \>** element pro každý parametr a **\<returns \>** prvek pro dokumentování návratové hodnoty.

   ![Šablona komentářů XML –C#](media/doc-preview-cs.png)

   ![Šablona komentářů XML – Visual Basic](media/doc-preview-vb.png)

1. Zadejte popisy pro každý element XML pro úplné dokumentování elementu kódu.

   ![Dokončený komentář](media/doc-result-cs.png)

> [!NOTE]
> Po zadání `///` [](../../ide/reference/options-text-editor-csharp-advanced.md) do C# nebo `'''` Visual Basic je k dispozici možnost přepínat dokumentační komentáře XML. V řádku nabídek vyberte **nástroje**  > **Možnosti** . tím otevřete dialogové okno **Možnosti** . Pak přejděte do **textového editoru**  > **C#** nebo **Basic**  > **Advanced**. V části **help editoru** vyhledejte možnost **Generovat dokumentační komentáře XML** .

## <a name="see-also"></a>Viz také:

- [Komentáře dokumentace XML (C# Průvodce programováním)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
- [Dokumentace kódu s komentáři XML (C# průvodce)](/dotnet/csharp/codedoc)
- [Postupy: vytvoření dokumentace XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [C++Vyjádření](/cpp/cpp/comments-cpp)
- [Dokumentace XML (C++)](/cpp/build/reference/xml-documentation-visual-cpp)
- [Generování kódu](../code-generation-in-visual-studio.md)