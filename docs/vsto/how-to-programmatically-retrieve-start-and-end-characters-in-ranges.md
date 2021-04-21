---
title: Programové automatické ukončení & koncových znaků v rozsazích
description: Tento příklad ukazuje, jak lze načíst pozice znaků počáteční a koncové pozice rozsahu.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4739043362a0f183574959f32a6e324d03522f65
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824026"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Postupy: načítání počátečních a koncových znaků v oblastech prostřednictvím kódu programu
  Tento příklad ukazuje, jak lze načíst pozice znaků počáteční a koncové pozice rozsahu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Načtení počátečních a koncových znaků rozsahu v přizpůsobení na úrovni dokumentu

1. Získejte hodnoty <xref:Microsoft.Office.Interop.Word.Range.Start%2A> <xref:Microsoft.Office.Interop.Word.Range.End%2A> vlastností <xref:Microsoft.Office.Interop.Word.Range> objektu a. Následující příklad kódu získá počáteční a koncovou pozici druhé věty v dokumentu. Chcete-li použít tento příklad kódu, spusťte jej z `ThisDocument` třídy v projektu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet25":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet25":::

## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Načtení počátečních a koncových znaků rozsahu pomocí doplňku VSTO

1. Získejte hodnoty <xref:Microsoft.Office.Interop.Word.Range.Start%2A> <xref:Microsoft.Office.Interop.Word.Range.End%2A> vlastností <xref:Microsoft.Office.Interop.Word.Range> objektu a. Následující příklad kódu získá počáteční a koncovou pozici druhé věty v aktivním dokumentu. Chcete-li použít tento příklad kódu, spusťte jej z `ThisAddIn` třídy v projektu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet25":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet25":::

## <a name="see-also"></a>Viz také
- [Postupy: definování a výběr oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Postupy: resetování oblastí v dokumentech aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Postupy: sbalení oblastí nebo výběrů v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Postupy: vyloučení značek odstavců při vytváření rozsahů prostřednictvím kódu programu](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Postupy: počítání znaků v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-count-characters-in-documents.md)
