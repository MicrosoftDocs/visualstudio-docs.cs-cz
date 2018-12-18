---
title: 'Postupy: načítání počátečních a koncových znaků oblastí prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1244fb2ba0a9e902d4dd853e7bef25376a205a0e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675857"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Postupy: načítání počátečních a koncových znaků oblastí prostřednictvím kódu programu
  Tento příklad ukazuje, jak můžete načíst pozice znaku pozic začátek a konec rozsahu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>K načtení počátečních a koncových znaků rozsahu v přizpůsobení na úrovni dokumentu  
  
1.  Získat hodnoty <xref:Microsoft.Office.Interop.Word.Range.Start%2A> a <xref:Microsoft.Office.Interop.Word.Range.End%2A> vlastnosti <xref:Microsoft.Office.Interop.Word.Range> objektu. Následující příklad kódu získá počáteční a koncovou pozici druhého větu v dokumentu. Pokud chcete použít tento příklad kódu, spusťte jej z `ThisDocument` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>K načtení počátečních a koncových znaků rozsahu pomocí doplňku VSTO  
  
1.  Získat hodnoty <xref:Microsoft.Office.Interop.Word.Range.Start%2A> a <xref:Microsoft.Office.Interop.Word.Range.End%2A> vlastnosti <xref:Microsoft.Office.Interop.Word.Range> objektu. Následující příklad kódu získá počáteční a koncovou pozici druhého větu v aktivním dokumentu. Pokud chcete použít tento příklad kódu, spusťte jej z `ThisAddIn` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: Programová definování a výběr oblastí v dokumentech](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Postupy: Programová resetování oblastí v dokumentech aplikace Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Postupy: oblastí nebo výběrů v dokumentech prostřednictvím kódu programu sbalit](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Postupy: Programová vyloučení značek odstavů při vytváření oblastí](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Postupy: Programová počet znaků v dokumentech](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  