---
title: 'Postupy: definování a výběr oblastí v dokumentech prostřednictvím kódu programu'
description: Naučte se programově definovat a vybírat rozsahy v dokumentech Microsoft Wordu pomocí objektu Range.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d1cc0475f7b25550b85018477d7c842f012445e2
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528321"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>Postupy: definování a výběr oblastí v dokumentech prostřednictvím kódu programu
  Rozsah můžete definovat v systém Microsoft Office wordovém dokumentu pomocí <xref:Microsoft.Office.Interop.Word.Range> objektu. Celý dokument můžete vybrat několika různými způsoby, například pomocí <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metody <xref:Microsoft.Office.Interop.Word.Range> objektu nebo pomocí vlastnosti Content <xref:Microsoft.Office.Tools.Word.Document> třídy (v přizpůsobení na úrovni dokumentu) nebo <xref:Microsoft.Office.Interop.Word.Document> třídy (v doplňku VSTO) (v doplňku VSTO).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="define-a-range"></a>Definovat rozsah
 Následující příklad ukazuje, jak vytvořit nový <xref:Microsoft.Office.Interop.Word.Range> objekt, který obsahuje prvních sedm znaků v aktivním dokumentu, včetně netisknutelných znaků. Pak vybere text v rámci rozsahu.

### <a name="to-define-a-range-in-a-document-level-customization"></a>Definování rozsahu v přizpůsobení na úrovni dokumentu

1. Přidejte rozsah do dokumentu předáním počátečního a koncového znaku do <xref:Microsoft.Office.Tools.Word.Document.Range%2A> metody <xref:Microsoft.Office.Tools.Word.Document> třídy. Chcete-li použít tento příklad kódu, spusťte jej z `ThisDocument` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#18)]

### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>Definování rozsahu pomocí doplňku VSTO

1. Přidejte rozsah do dokumentu předáním počátečního a koncového znaku do <xref:Microsoft.Office.Interop.Word._Document.Range%2A> metody <xref:Microsoft.Office.Interop.Word.Document> třídy. Následující příklad kódu přidá rozsah do aktivního dokumentu. Chcete-li použít tento příklad kódu, spusťte jej z `ThisAddIn` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#18)]

## <a name="select-a-range-in-a-document-level-customization"></a>Výběr rozsahu v přizpůsobení na úrovni dokumentu
 Následující příklady ukazují, jak vybrat celý dokument pomocí <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metody <xref:Microsoft.Office.Interop.Word.Range> objektu nebo pomocí <xref:Microsoft.Office.Tools.Word.Document.Content%2A> vlastnosti <xref:Microsoft.Office.Tools.Word.Document> třídy.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Výběr celého dokumentu jako rozsahu pomocí metody Select

1. Použijte <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metodu <xref:Microsoft.Office.Interop.Word.Range> , která obsahuje celý dokument. Chcete-li použít následující příklad kódu, spusťte jej z `ThisDocument` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#19)]

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Výběr celého dokumentu jako rozsahu pomocí vlastnosti obsahu

1. Vlastnost použijte <xref:Microsoft.Office.Tools.Word.Document.Content%2A> k definování rozsahu, který zahrnuje celý dokument.

    [!code-vb[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#20)]

   Můžete také použít metody a vlastnosti jiných objektů k definování rozsahu.

### <a name="to-select-a-sentence-in-the-active-document"></a>Výběr věty v aktivním dokumentu

1. Nastavte rozsah pomocí <xref:Microsoft.Office.Interop.Word.Sentences> kolekce. Použijte index věty, kterou chcete vybrat.

    [!code-vb[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#21)]

   Dalším způsobem, jak vybrat větu, je ruční nastavení počátečních a koncových hodnot rozsahu.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Výběr věty ručním nastavením počátečních a koncových hodnot

1. Vytvořte proměnnou rozsahu.

     [!code-vb[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#23)]

2. Zkontrolujte, zda v dokumentu existují alespoň dvě věty, nastavte *počáteční* a *koncové* argumenty rozsahu a pak vyberte rozsah.

     [!code-vb[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#24)]

## <a name="select-a-range-by-using-a-vsto-add-in"></a>Výběr rozsahu pomocí doplňku VSTO
 Následující příklady ukazují, jak vybrat celý dokument pomocí <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metody <xref:Microsoft.Office.Interop.Word.Range> objektu nebo pomocí <xref:Microsoft.Office.Interop.Word._Document.Content%2A> vlastnosti <xref:Microsoft.Office.Interop.Word.Document> třídy.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Výběr celého dokumentu jako rozsahu pomocí metody Select

1. Použijte <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metodu <xref:Microsoft.Office.Interop.Word.Range> , která obsahuje celý dokument. Následující příklad kódu vybere obsah aktivního dokumentu. Chcete-li použít tento příklad kódu, spusťte jej z `ThisAddIn` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#19)]

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Výběr celého dokumentu jako rozsahu pomocí vlastnosti obsahu

1. Vlastnost použijte <xref:Microsoft.Office.Interop.Word._Document.Content%2A> k definování rozsahu, který zahrnuje celý dokument.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#20)]

   Můžete také použít metody a vlastnosti jiných objektů k definování rozsahu.

### <a name="to-select-a-sentence-in-the-active-document"></a>Výběr věty v aktivním dokumentu

1. Nastavte rozsah pomocí <xref:Microsoft.Office.Interop.Word.Sentences> kolekce. Použijte index věty, kterou chcete vybrat.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#21)]

   Dalším způsobem, jak vybrat větu, je ruční nastavení počátečních a koncových hodnot rozsahu.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Výběr věty ručním nastavením počátečních a koncových hodnot

1. Vytvořte proměnnou rozsahu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#23)]

2. Zkontrolujte, zda v dokumentu existují alespoň dvě věty, nastavte *počáteční* a *koncové* argumenty rozsahu a pak vyberte rozsah.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#24)]

## <a name="see-also"></a>Viz také
- [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)
- [Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Postupy: načítání počátečních a koncových znaků v oblastech prostřednictvím kódu programu](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Postupy: resetování oblastí v dokumentech aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Postupy: sbalení oblastí nebo výběrů v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Postupy: vyloučení značek odstavců při vytváření rozsahů prostřednictvím kódu programu](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
