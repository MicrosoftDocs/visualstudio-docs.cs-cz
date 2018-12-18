---
title: 'Postupy: kopírování listů prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: eddecb7bdb087797bc3f9f4abf4841ab4cdf97b5
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256536"
---
# <a name="how-to-programmatically-copy-worksheets"></a>Postupy: kopírování listů prostřednictvím kódu programu
  Můžete vytvořit kopii sešitu a vložit tento list před nebo po existujícího listu v sešitu. Pokud nezadáte, kam chcete vložit listu, bude vytvořen nový sešit tak, aby obsahovala nového listu.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Ať už zkopírujete listu prostřednictvím kódu programu, nebo koncový uživatel ručně zkopíruje listu, neexistuje žádný kód za nový list a ovládacích prvků na nový list nefungují. Důvodem je, že je na nově zkopírovaný listu <xref:Microsoft.Office.Interop.Excel.Worksheet> objekt a není <xref:Microsoft.Office.Tools.Excel.Worksheet> hostitelská položka. Ovládací prvky Windows Forms a hostitelských ovládacích prvků lze přidat pouze hostitele položek. Další informace najdete v tématu [programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Chcete-li přidat do listu zkopírovaný do sešitu aplikace přizpůsobení na úrovni dokumentu  
  
1.  Použití <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> metoda umístěte kopii po třetí list a zkopírujte první listu v aktuálním sešitu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]  
  
## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Chcete-li přidat do listu zkopírovaný do sešitu v doplňku VSTO  
  
1.  Použití <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> metoda umístěte kopii po třetí list a zkopírujte první listu v aktuálním sešitu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="see-also"></a>Viz také:  
 [Práce s listy](../vsto/working-with-worksheets.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Postupy: přidávání nových listů do sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Postupy: odstraňování listů ze sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Postupy: výběr listů prostřednictvím kódu programu](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)   
 [Globální přístup k objektům v projektech pro systém Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  