---
title: 'Postupy: zavírání dokumentů prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing
- Word [Office development in Visual Studio], closing documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9a846aded5d24f84fdaeac79a1bad6c61a3f5570
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257771"
---
# <a name="how-to-programmatically-close-documents"></a>Postupy: zavírání dokumentů prostřednictvím kódu programu
  Můžete zavře aktivní dokument nebo můžete zadat dokument zavřít.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="close-the-active-document"></a>Zavře aktivní dokument.  
 Existují dva postupy pro aktivní dokument zavřít: jeden pro přizpůsobení na úrovni dokumentu a jeden pro doplňky VSTO.  
  
### <a name="to-close-the-active-document-in-a-document-level-customization"></a>Chcete-li zavře aktivní dokument v přizpůsobení na úrovni dokumentu  
  
1.  Volání <xref:Microsoft.Office.Tools.Word.Document.Close%2A> metodu `ThisDocument` třídy ve vašem projektu a zavřete dokument přidružené k přizpůsobení. Chcete-li použít následující příklad kódu, spusťte jej z `ThisDocument` třídy.  
  
    > [!NOTE]  
    >  Tento příklad předá <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> hodnotu *SaveChanges* parametr okno zavřít bez uložení změn nebo výzvy pro uživatele.  
  
     [!code-vb[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#3)]  
  
### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>Chcete-li zavře aktivní dokument v doplňku VSTO  
  
1.  Volání <xref:Microsoft.Office.Interop.Word._Document.Close%2A> metodu <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> vlastnost zavře aktivní dokument. Chcete-li použít následující příklad kódu, spusťte jej z `ThisAddIn` třídy ve vašem projektu.  
  
    > [!NOTE]  
    >  Tento příklad předá <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> hodnotu *SaveChanges* parametr okno zavřít bez uložení změn nebo výzvy pro uživatele.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#3)]  
  
## <a name="close-a-document-that-you-specify-by-name"></a>Zavřete dokument, který určíte podle názvu  
 Způsob, jakým zavřete dokument, který zadáte název je stejný pro doplňky VSTO a úpravy na úrovni dokumentů.  
  
### <a name="to-close-a-document-that-you-specify-by-name"></a>Zavřete dokument, který určíte podle názvu  
  
1.  Zadejte název dokumentu jako argument pro <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> kolekce a potom volání <xref:Microsoft.Office.Interop.Word._Document.Close%2A> metoda. Následující příklad kódu předpokládá, že dokument s názvem **NewDocument** je otevřený v aplikaci Word.  
  
    > [!NOTE]  
    >  Tento příklad předá <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> hodnotu *SaveChanges* parametr okno zavřít bez uložení změn nebo výzvy pro uživatele.  
  
     [!code-vb[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#4)]  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: otevírání stávajících dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Postupy: ukládání dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-save-documents.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)  
  