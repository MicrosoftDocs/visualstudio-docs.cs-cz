---
title: 'Postupy: Programové přidávání a odstraňování komentářů v listech'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fe41fe7f6370697335fa76b468e79e61d6e1269a
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675648"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Postupy: Programové přidávání a odstraňování komentářů v listech
  Můžete programově přidávání a odstraňování komentářů v listech aplikace Microsoft Office Excel. Komentáře můžete přidávat pouze do jedné buňky, ne do více oblastí.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>Přidávání a odstraňování komentářů v projektu úrovni dokumentu  
 Následující příklady předpokládají, že se jednotlivé buňky <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek s názvem `dateComment` na listu s názvem `Sheet1`.  
  
### <a name="to-add-a-new-comment-to-a-named-range"></a>Chcete-li přidat nový komentář na pojmenované oblasti  
  
1.  Volání <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> metodu <xref:Microsoft.Office.Tools.Excel.NamedRange> řídit a zadejte komentář. Tento kód musí být umístěné ve `Sheet1` třídy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]  
  
#### <a name="to-delete-a-comment-from-a-named-range"></a>Chcete-li odstranit komentář z pojmenované oblasti  
  
1.  Ověřte, zda existuje komentář na rozsahu a odstraňte ho. Tento kód musí být umístěné ve `Sheet1` třídy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]  
  
## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>Přidávání a odstraňování komentářů v projektu doplňku VSTO  
 Následující příklady předpokládají, že se jednotlivé buňky <xref:Microsoft.Office.Interop.Excel.Range> s názvem `dateComment` na aktivním listu.  
  
### <a name="to-add-a-new-comment-to-an-excel-range"></a>Chcete-li přidat nový komentář k oblasti aplikace Excel  
  
1.  Volání <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> metodu <xref:Microsoft.Office.Interop.Excel.Range> a zadejte komentář.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]  
  
### <a name="to-delete-a-comment-from-an-excel-range"></a>Chcete-li odstranit komentář z oblasti aplikace Excel  
  
1.  Ověřte, zda existuje komentář na rozsahu a odstraňte ho.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]  
  
## <a name="see-also"></a>Viz také:  
 [Práce s listy](../vsto/working-with-worksheets.md)   
 [Postupy: zobrazování komentářů v listech prostřednictvím kódu programu](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [Namedrange – ovládací prvek](../vsto/namedrange-control.md)  
  
  