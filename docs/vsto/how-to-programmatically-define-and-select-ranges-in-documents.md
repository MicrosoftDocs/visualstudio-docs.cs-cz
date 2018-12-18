---
title: 'Postupy: Programová definování a výběr oblastí v dokumentech'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8770871bfdc361e29d7ac7c2fc984477b1ec0ea1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833132"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>Postupy: Programová definování a výběr oblastí v dokumentech
  Můžete definovat rozsah v dokumentu aplikace Microsoft Office Word s použitím <xref:Microsoft.Office.Interop.Word.Range> objektu. Můžete vybrat celý dokument v několika způsoby, například pomocí <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metodu <xref:Microsoft.Office.Interop.Word.Range> objektu, nebo pomocí vlastnosti obsahu <xref:Microsoft.Office.Tools.Word.Document> třídy (v přizpůsobení úrovni dokumentu) nebo <xref:Microsoft.Office.Interop.Word.Document> třídy (v Doplněk VSTO).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="define-a-range"></a>Definujte rozsah  
 Následující příklad ukazuje, jak vytvořit novou <xref:Microsoft.Office.Interop.Word.Range> objekt, který obsahuje první sedm znaky v aktivním dokumentu, včetně netisknutelné znaky. Potom vybere text v rámci rozsahu.  
  
### <a name="to-define-a-range-in-a-document-level-customization"></a>Chcete-li definovat rozsah v přizpůsobení na úrovni dokumentu  
  
1.  Přidat oblast v dokumentu předáním počáteční a koncový znak do <xref:Microsoft.Office.Tools.Word.Document.Range%2A> metodu <xref:Microsoft.Office.Tools.Word.Document> třídy. Pokud chcete použít tento příklad kódu, spusťte jej z `ThisDocument` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#18)]  
  
### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>Chcete-li definovat rozsah s použitím doplňku VSTO  
  
1.  Přidat oblast v dokumentu předáním počáteční a koncový znak do <xref:Microsoft.Office.Interop.Word._Document.Range%2A> metodu <xref:Microsoft.Office.Interop.Word.Document> třídy. Následující příklad kódu přidá rozsah v aktivním dokumentu. Pokud chcete použít tento příklad kódu, spusťte jej z `ThisAddIn` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#18)]  
  
## <a name="select-a-range-in-a-document-level-customization"></a>Vyberte oblast v přizpůsobení na úrovni dokumentu  
 Následující příklady ukazují, jak vybrat celý dokument pomocí <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metodu <xref:Microsoft.Office.Interop.Word.Range> objektu, nebo pomocí <xref:Microsoft.Office.Tools.Word.Document.Content%2A> vlastnost <xref:Microsoft.Office.Tools.Word.Document> třídy.  
  
### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Vybrat celý dokument jako rozsah pomocí metody Select  
  
1.  Použití <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metodu <xref:Microsoft.Office.Interop.Word.Range> , který obsahuje celý dokument. Pokud chcete použít následující příklad kódu, spusťte jej z `ThisDocument` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#19)]  
  
### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Vybrat celý dokument jako rozsah pomocí vlastnosti obsahu  
  
1. Použití <xref:Microsoft.Office.Tools.Word.Document.Content%2A> vlastnost pro účely definování rozsahu, který zahrnuje celý dokument.  
  
    [!code-vb[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#20)]  
  
   Chcete-li definovat rozsah můžete také použít metody a vlastnosti jiného objektu.  
  
### <a name="to-select-a-sentence-in-the-active-document"></a>Chcete-li vybrat větu v aktivním dokumentu.  
  
1. Nastavte rozsah s použitím <xref:Microsoft.Office.Interop.Word.Sentences> kolekce. Pomocí rejstříku věty, kterou chcete vybrat.  
  
    [!code-vb[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#21)]  
  
   Dalším způsobem, jak vybrat větu je ručně nastavit počáteční a koncové hodnoty rozsahu.  
  
### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Chcete-li vybrat větu ručně nastavte počáteční a koncové hodnoty  
  
1.  Vytvořte proměnnou rozsahu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#23)]  
  
2.  Zkontrolujte, zda existují alespoň dvě věty v dokumentu, nastavte *Start* a *End* argumenty rozsah a pak vyberte oblast.  
  
     [!code-vb[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#24)]  
  
## <a name="select-a-range-by-using-a-vsto-add-in"></a>Výběr rozsahu pomocí doplňku VSTO  
 Následující příklady ukazují, jak vybrat celý dokument pomocí <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metodu <xref:Microsoft.Office.Interop.Word.Range> objektu, nebo pomocí <xref:Microsoft.Office.Interop.Word._Document.Content%2A> vlastnost <xref:Microsoft.Office.Interop.Word.Document> třídy.  
  
### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Vybrat celý dokument jako rozsah pomocí metody Select  
  
1.  Použití <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metodu <xref:Microsoft.Office.Interop.Word.Range> , který obsahuje celý dokument. Následující příklad kódu vybere obsah aktivního dokumentu. Pokud chcete použít tento příklad kódu, spusťte jej z `ThisAddIn` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#19)]  
  
### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Vybrat celý dokument jako rozsah pomocí vlastnosti obsahu  
  
1. Použití <xref:Microsoft.Office.Interop.Word._Document.Content%2A> vlastnost pro účely definování rozsahu, který zahrnuje celý dokument.  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#20)]  
  
   Chcete-li definovat rozsah můžete také použít metody a vlastnosti jiného objektu.  
  
### <a name="to-select-a-sentence-in-the-active-document"></a>Chcete-li vybrat větu v aktivním dokumentu.  
  
1. Nastavte rozsah s použitím <xref:Microsoft.Office.Interop.Word.Sentences> kolekce. Pomocí rejstříku věty, kterou chcete vybrat.  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#21)]  
  
   Dalším způsobem, jak vybrat větu je ručně nastavit počáteční a koncové hodnoty rozsahu.  
  
### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Chcete-li vybrat větu ručně nastavte počáteční a koncové hodnoty  
  
1.  Vytvořte proměnnou rozsahu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#23)]  
  
2.  Zkontrolujte, zda existují alespoň dvě věty v dokumentu, nastavte *Start* a *End* argumenty rozsah a pak vyberte oblast.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#24)]  
  
## <a name="see-also"></a>Viz také:  
 [Přehled modelu objektů aplikace Word](../vsto/word-object-model-overview.md)   
 [Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Postupy: načítání počátečních a koncových znaků oblastí prostřednictvím kódu programu](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Postupy: Programová resetování oblastí v dokumentech aplikace Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Postupy: oblastí nebo výběrů v dokumentech prostřednictvím kódu programu sbalit](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Postupy: Programová vyloučení značek odstavů při vytváření oblastí](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  
  