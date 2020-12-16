---
title: 'Postupy: skrytí textu v dokumentech prostřednictvím kódu programu'
description: Zjistěte, jak lze skrýt text v dokumentu aplikace Microsoft Word nastavením skryté vlastnosti písma pro určitý rozsah textu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a375e8b844f82b5d310841d7b4cdc092b18ff6c3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525701"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Postupy: skrytí textu v dokumentech prostřednictvím kódu programu
  Text v dokumentu můžete skrýt nastavením <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> vlastnosti <xref:Microsoft.Office.Interop.Word.Range.Font%2A> pro určitý rozsah textu.

 Před odesláním dokumentu na tiskárnu můžete například dočasně skrýt text v rámci <xref:Microsoft.Office.Tools.Word.Bookmark> (v přizpůsobení na úrovni dokumentu) nebo <xref:Microsoft.Office.Interop.Word.Bookmark> (v doplňku VSTO).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Skrytí textu v ovládacím prvku záložka při tisku dokumentu

1. Vytvoří proceduru, která skryje veškerý text v zadaném rozsahu.

     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]

2. Vytvořte proceduru, která bude odkrýt veškerý text v zadaném rozsahu.

     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]

3. Předejte do metody rozsah záložky `HideText` , vytiskněte dokument a pak předejte stejný rozsah `UnhideText` metodě.

     Následující příklad kódu lze použít v přizpůsobení na úrovni dokumentu. Chcete-li použít tento příklad, spusťte jej z `ThisDocument` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]

     V doplňku VSTO se dá použít následující příklad kódu. Tento příklad používá aktivní dokument. Chcete-li použít příklad, spusťte jej z `ThisAddIn` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad kódu předpokládá, že dokument obsahuje <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek (v přizpůsobení na úrovni dokumentu) nebo <xref:Microsoft.Office.Interop.Word.Bookmark> ovládací prvek (v doplňku VSTO), který je pojmenován `bookmark1` .

## <a name="see-also"></a>Viz také
- [Postupy: tisk dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-print-documents.md)
- [Postupy: definování a výběr oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Postupy: resetování oblastí v dokumentech aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Postupy: aktualizace textu záložek prostřednictvím kódu programu](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
