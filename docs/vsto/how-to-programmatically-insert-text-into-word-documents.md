---
title: 'Postupy: vkládání textu do dokumentů aplikace Word prostřednictvím kódu programu'
description: Přečtěte si, jak můžete programově vkládat text do dokumentu Microsoft Wordu pomocí sady Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f17828b4617f84cb104761918787b4bbb79f7afc
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827354"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Postupy: vkládání textu do dokumentů aplikace Word prostřednictvím kódu programu
  Existují tři základní způsoby, jak vložit text do systém Microsoft Office dokumentů aplikace Word:

- Vloží text do rozsahu.

- Nahradí text v rozsahu novým textem.

- Použijte <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> metodu <xref:Microsoft.Office.Interop.Word.Selection> objektu pro vložení textu na kurzor nebo výběr.

> [!NOTE]
> Můžete také vložit text do ovládacích prvků obsahu a záložek. Další informace naleznete v tématu [ovládací prvky obsahu](../vsto/content-controls.md) a [ovládací prvek záložek](../vsto/bookmark-control.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="insert-text-in-a-range"></a>Vložení textu do rozsahu
 <xref:Microsoft.Office.Interop.Word.Range.Text%2A> <xref:Microsoft.Office.Interop.Word.Range> Pro vložení textu do dokumentu použijte vlastnost objektu.

### <a name="to-insert-text-in-a-range"></a>Vložení textu do rozsahu

1. Zadejte rozsah na začátku dokumentu a vložte text **Nový** text.

     Následující příklad kódu lze použít v přizpůsobení na úrovni dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet51":::

     V doplňku VSTO se dá použít následující příklad kódu. Tento kód používá aktivní dokument.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet51":::

2. Vyberte <xref:Microsoft.Office.Interop.Word.Range> objekt, který se rozšíří z jednoho znaku na délku vloženého textu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet52":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet52":::

## <a name="replace-text-in-a-range"></a>Nahrazení textu v rozsahu
 Pokud zadaný rozsah obsahuje text, bude veškerý text v rozsahu nahrazen vloženým textem.

### <a name="to-replace-text-in-a-range"></a>Nahrazení textu v rozsahu

1. Vytvoří <xref:Microsoft.Office.Interop.Word.Range> objekt, který se skládá z prvních 12 znaků v dokumentu.

     Následující příklad kódu lze použít v přizpůsobení na úrovni dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet53":::

     V doplňku VSTO se dá použít následující příklad kódu. Tento kód používá aktivní dokument.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet53":::

2. Nahraďte tyto znaky **novým textovým** řetězcem.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet54":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet54":::

3. Vyberte rozsah.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet55":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet55":::

## <a name="insert-text-using-typetext"></a>Vložení textu pomocí TypeText
 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>Metoda vloží text na výběr. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> se chová odlišně v závislosti na možnostech nastavených v počítači uživatele. Kód v následujícím postupu deklaruje <xref:Microsoft.Office.Interop.Word.Selection> proměnnou objektu a vypne možnost **přepisování** , pokud je zapnutá. Pokud je aktivována možnost **přepisování** , je text vedle kurzoru přepsán.

### <a name="to-insert-text-using-the-typetext-method"></a>Vložení textu pomocí metody TypeText

1. Deklarujte <xref:Microsoft.Office.Interop.Word.Selection> proměnnou objektu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet57":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet57":::

2. Vypněte možnost **přepisování** , pokud je zapnutá.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet58":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet58":::

3. Ověřte, zda je aktuální výběr místem vložení.

    Pokud je, kód vloží větu pomocí <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> a pak znak odstavce pomocí <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> metody.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet59":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet59":::

4. Kód **v blocích Block** Tests pro zjištění, zda je výběr normálního výběru. **Pokud je, pak další testovací** testy, abyste viděli, zda je zapnutá možnost **ReplaceSelection** . Pokud je, kód používá <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> metodu výběru pro sbalení výběru na místo vložení na začátku vybraného bloku textu. Vložte text a značku odstavce.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet60":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet60":::

5. Pokud výběr není bod vložení nebo blok vybraného textu, pak kód v bloku **Else** neprovede žádnou akci.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet61":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet61":::

   Můžete také použít <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> metodu <xref:Microsoft.Office.Interop.Word.Selection> objektu, která napodobuje funkčnost klávesy **BACKSPACE** na klávesnici. Nicméně když přichází k vložení a manipulaci s textem, <xref:Microsoft.Office.Interop.Word.Range> objekt nabízí větší kontrolu.

   Následující příklad ukazuje úplný kód. Chcete-li použít tento příklad, spusťte kód z `ThisDocument` `ThisAddIn` třídy nebo v projektu.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet56":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet56":::

## <a name="see-also"></a>Viz také
- [Postupy: formátování textu v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-format-text-in-documents.md)
- [Postupy: definování a výběr oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
