---
title: 'Postupy: skrývání textu v dokumentech prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 83b25c37ee2ce4dd9cb1ffeda21fbda1b5f3f139
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35676501"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Postupy: skrývání textu v dokumentech prostřednictvím kódu programu
  Text v dokumentu můžete skrýt nastavením <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> vlastnost <xref:Microsoft.Office.Interop.Word.Range.Font%2A> pro konkrétní rozsah textu.  
  
 Například můžete dočasně skrýt text v rámci <xref:Microsoft.Office.Tools.Word.Bookmark> (v přizpůsobení úrovni dokumentu) nebo <xref:Microsoft.Office.Interop.Word.Bookmark> (in VSTO Add-) před odesláním dokument na tiskárně.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Chcete-li skrýt text v ovládacím prvku záložek při tisku dokumentu  
  
1.  Vytvořte proceduru, která skrývá veškerý text, který je v zadaném rozsahu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]  
  
2.  Vytvořte proceduru, která slouží k zobrazení veškerý text, který je v zadaném rozsahu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]  
  
3.  Předat rozsah záložky `HideText` metoda, vytisknout dokument a pak předejte stejný rozsah na `UnhideText` metoda.  
  
     Následující příklad kódu je možné v přizpůsobení na úrovni dokumentu. Pokud chcete použít tento příklad, spusťte jej z `ThisDocument` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]  
  
     Následující příklad kódu je možné v doplňku VSTO. Tento příklad používá aktivní dokument. Pokud chcete použít v příkladu, spusťte jej z `ThisAddIn` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Tento příklad kódu předpokládá, že dokument obsahuje <xref:Microsoft.Office.Tools.Word.Bookmark> control (na úrovni dokumentu přizpůsobení) nebo <xref:Microsoft.Office.Interop.Word.Bookmark> ovládacího prvku (in VSTO Add-), který je pojmenován `bookmark1`.  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: tisk dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-print-documents.md)   
 [Postupy: Programová definování a výběr oblastí v dokumentech](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Postupy: Programová resetování oblastí v dokumentech aplikace Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Postupy: programově aktualizovat textu záložky](../vsto/how-to-programmatically-update-bookmark-text.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  