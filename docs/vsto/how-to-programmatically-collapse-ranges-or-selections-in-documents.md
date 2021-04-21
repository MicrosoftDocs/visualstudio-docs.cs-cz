---
title: Programové sbalení oblastí nebo výběrů v dokumentech
description: Přečtěte si, že pokud pracujete s objektem rozsahu nebo výběru, můžete před vložením textu změnit výběr na místo vložení.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5d1fb41943690da5144fb06245ed7f4aa70250aa
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828641"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Postupy: sbalení oblastí nebo výběrů v dokumentech prostřednictvím kódu programu
  Pokud pracujete s <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Interop.Word.Selection> objektem nebo, možná budete chtít před vložením textu změnit výběr na místo, aby se zabránilo přepsání stávajícího textu. <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Interop.Word.Selection> Objekty i mají metodu sbalení, která využívá <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> hodnoty výčtu:

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> sbalí výběr na začátek výběru. Toto je výchozí nastavení, pokud nezadáte hodnotu výčtu.

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> sbalí výběr na konec výběru.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-collapse-a-range-and-insert-new-text"></a>Sbalení rozsahu a vložení nového textu

1. Vytvořte <xref:Microsoft.Office.Interop.Word.Range> objekt, který se skládá z prvního odstavce v dokumentu.

    Následující příklad kódu lze použít v přizpůsobení na úrovni dokumentu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet46":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet46":::

    V doplňku VSTO se dá použít následující příklad kódu. Tento kód používá aktivní dokument.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet46":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet46":::

2. Rozsah můžete <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> sbalit pomocí hodnoty výčtu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet47":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet47":::

3. Vložte nový text.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet48":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet48":::

4. Vyberte <xref:Microsoft.Office.Interop.Word.Range>.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet49":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet49":::

   Použijete-li <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> hodnotu výčtu, text bude vložen na začátku následujícího odstavce.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet50":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet50":::

   Můžete očekávat, že vložením nové věty by se vložila před značku odstavce, ale ne v případě, že původní rozsah obsahuje značku odstavce. Další informace naleznete v tématu [How to: reexclude znak konce odstavců při vytváření rozsahů](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).

## <a name="document-level-customization-example"></a>Příklad přizpůsobení na úrovni dokumentu

### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Sbalení rozsahu v přizpůsobení na úrovni dokumentu

1. Následující příklad ukazuje metodu Complete pro přizpůsobení na úrovni dokumentu. Chcete-li použít tento kód, spusťte jej z `ThisDocument` třídy v projektu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet45":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet45":::

## <a name="vsto-add-in-example"></a>Příklad doplňku VSTO

### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>Sbalení rozsahu v doplňku VSTO

1. Následující příklad ukazuje metodu Complete pro doplněk VSTO. Chcete-li použít tento kód, spusťte jej z `ThisAddIn` třídy v projektu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet45":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet45":::

## <a name="see-also"></a>Viz také
- [Postupy: vkládání textu do dokumentů aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Postupy: definování a výběr oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Postupy: načítání počátečních a koncových znaků v oblastech prostřednictvím kódu programu](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Postupy: vyloučení značek odstavců při vytváření rozsahů prostřednictvím kódu programu](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Postupy: resetování oblastí v dokumentech aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
