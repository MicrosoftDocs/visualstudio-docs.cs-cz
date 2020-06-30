---
title: Programové automatické ukončení & koncových znaků v rozsazích
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 485945f235a9161b6dc0584f7018c6f03c6024f5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537654"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Postupy: načítání počátečních a koncových znaků v oblastech prostřednictvím kódu programu
  Tento příklad ukazuje, jak lze načíst pozice znaků počáteční a koncové pozice rozsahu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Načtení počátečních a koncových znaků rozsahu v přizpůsobení na úrovni dokumentu

1. Získejte hodnoty <xref:Microsoft.Office.Interop.Word.Range.Start%2A> <xref:Microsoft.Office.Interop.Word.Range.End%2A> vlastností <xref:Microsoft.Office.Interop.Word.Range> objektu a. Následující příklad kódu získá počáteční a koncovou pozici druhé věty v dokumentu. Chcete-li použít tento příklad kódu, spusťte jej z `ThisDocument` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Načtení počátečních a koncových znaků rozsahu pomocí doplňku VSTO

1. Získejte hodnoty <xref:Microsoft.Office.Interop.Word.Range.Start%2A> <xref:Microsoft.Office.Interop.Word.Range.End%2A> vlastností <xref:Microsoft.Office.Interop.Word.Range> objektu a. Následující příklad kódu získá počáteční a koncovou pozici druhé věty v aktivním dokumentu. Chcete-li použít tento příklad kódu, spusťte jej z `ThisAddIn` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]

## <a name="see-also"></a>Viz také
- [Postupy: definování a výběr oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Postupy: resetování oblastí v dokumentech aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Postupy: sbalení oblastí nebo výběrů v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Postupy: vyloučení značek odstavců při vytváření rozsahů prostřednictvím kódu programu](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Postupy: počítání znaků v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-count-characters-in-documents.md)
