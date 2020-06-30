---
title: Programové sbalení oblastí nebo výběrů v dokumentech
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1575a130a525c169553598fd15acfa8ba8fc397a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546117"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Postupy: sbalení oblastí nebo výběrů v dokumentech prostřednictvím kódu programu
  Pokud pracujete s <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Interop.Word.Selection> objektem nebo, možná budete chtít před vložením textu změnit výběr na místo, aby se zabránilo přepsání stávajícího textu. <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Interop.Word.Selection> Objekty i mají metodu sbalení, která využívá <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> hodnoty výčtu:

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart>sbalí výběr na začátek výběru. Toto je výchozí nastavení, pokud nezadáte hodnotu výčtu.

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd>sbalí výběr na konec výběru.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-collapse-a-range-and-insert-new-text"></a>Sbalení rozsahu a vložení nového textu

1. Vytvořte <xref:Microsoft.Office.Interop.Word.Range> objekt, který se skládá z prvního odstavce v dokumentu.

    Následující příklad kódu lze použít v přizpůsobení na úrovni dokumentu.

    [!code-vb[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#46)]

    V doplňku VSTO se dá použít následující příklad kódu. Tento kód používá aktivní dokument.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#46)]

2. Rozsah můžete <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> sbalit pomocí hodnoty výčtu.

    [!code-vb[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#47)]
    [!code-csharp[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#47)]

3. Vložte nový text.

    [!code-vb[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#48)]
    [!code-csharp[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#48)]

4. Vyberte <xref:Microsoft.Office.Interop.Word.Range> .

    [!code-vb[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#49)]
    [!code-csharp[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#49)]

   Použijete-li <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> hodnotu výčtu, text bude vložen na začátku následujícího odstavce.

   [!code-vb[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#50)]
   [!code-csharp[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#50)]

   Můžete očekávat, že vložením nové věty by se vložila před značku odstavce, ale ne v případě, že původní rozsah obsahuje značku odstavce. Další informace naleznete v tématu [How to: reexclude znak konce odstavců při vytváření rozsahů](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).

## <a name="document-level-customization-example"></a>Příklad přizpůsobení na úrovni dokumentu

### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Sbalení rozsahu v přizpůsobení na úrovni dokumentu

1. Následující příklad ukazuje metodu Complete pro přizpůsobení na úrovni dokumentu. Chcete-li použít tento kód, spusťte jej z `ThisDocument` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#45)]

## <a name="vsto-add-in-example"></a>Příklad doplňku VSTO

### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>Sbalení rozsahu v doplňku VSTO

1. Následující příklad ukazuje metodu Complete pro doplněk VSTO. Chcete-li použít tento kód, spusťte jej z `ThisAddIn` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#45)]

## <a name="see-also"></a>Viz také
- [Postupy: vkládání textu do dokumentů aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Postupy: definování a výběr oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Postupy: načítání počátečních a koncových znaků v oblastech prostřednictvím kódu programu](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Postupy: vyloučení značek odstavců při vytváření rozsahů prostřednictvím kódu programu](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Postupy: resetování oblastí v dokumentech aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
