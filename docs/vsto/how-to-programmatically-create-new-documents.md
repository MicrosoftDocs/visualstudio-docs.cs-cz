---
title: 'Postupy: vytváření nových dokumentů prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 964bcfe9d582d51794ec3f9469686df029c7cab1
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257430"
---
# <a name="how-to-programmatically-create-new-documents"></a>Postupy: vytváření nových dokumentů prostřednictvím kódu programu
  Když vytvoříte dokumentů prostřednictvím kódu programu, nový dokument je nativní <xref:Microsoft.Office.Interop.Word.Document> objektu. Tento objekt nemá další události a možnosti vazby dat <xref:Microsoft.Office.Tools.Word.Document> hostitelská položka. Další informace najdete v tématu [programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Pokud vyvíjíte projekt na úrovni dokumentu a, nemůžete přidat prostřednictvím kódu programu <xref:Microsoft.Office.Tools.Word.Document> hostitele položek do projektu. V projektu doplňku VSTO můžete převést některé <xref:Microsoft.Office.Interop.Word.Document> do objektu <xref:Microsoft.Office.Tools.Word.Document> hostitele položky v době běhu. Další informace najdete v tématu [dokumentů rozšířit aplikace Word a sešitů aplikace Excel v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="to-create-a-new-document-based-on-the-normal-template"></a>Chcete-li vytvořit nový dokument založený na šabloně Normální  
  
-   Použití <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> metodu <xref:Microsoft.Office.Interop.Word.Documents> kolekce k vytvoření nového dokumentu založený na šabloně Normální. Chcete-li použít tento příklad kódu, spusťte jej z `ThisDocument` nebo `ThisAddIn` třídy ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#1)]
     [!code-csharp[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#1)]  
  
## <a name="use-custom-templates"></a>Použití vlastní šablony  
 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> Metoda má volitelný *šablony* argument vytvořit nový dokument založená na šabloně šabloně Normální. Je třeba zadat název souboru a plně kvalifikovanou cestu šablony.  
  
### <a name="to-create-a-new-document-based-on-a-custom-template"></a>Chcete-li vytvořit nový dokument na základě vlastní šablony  
  
-   Volání <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> metodu <xref:Microsoft.Office.Interop.Word.Documents> kolekce a zadejte cestu k šabloně. Chcete-li použít tento příklad kódu, spusťte jej z `ThisDocument` nebo `ThisAddIn` třídy ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#2)]
     [!code-csharp[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#2)]  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: otevírání stávajících dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Přehled ovládacích prvků hostitele a hostitelské položky](../vsto/host-items-and-host-controls-overview.md)   
 [Programová omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  