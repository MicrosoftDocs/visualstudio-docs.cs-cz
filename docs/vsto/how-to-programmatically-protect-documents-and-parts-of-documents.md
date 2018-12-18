---
title: 'Postupy: zamykání dokumentů a částí dokumentů'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document protection
- documents [Office development in Visual Studio], document protection
- Word documents, protection
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9acef141944b106a9bace38fef8ede7041bfecc5
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675656"
---
# <a name="how-to-programmatically-protect-documents-and-parts-of-documents"></a>Postupy: zamykání dokumentů a částí dokumentů
  Přidat ochranu do dokumentů aplikace Microsoft Office Word zabráníte uživatelům provádět veškeré úpravy dokumentu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Můžete také označit určité oblasti dokumentu jako výjimky tak, aby zadaný uživatelé mohou upravovat pouze ty oblasti dokumentu. Můžete například chtít chránit celý dokument s výjimkou určitou záložku. Heslo můžete volitelně přidat tak, aby uživatelé nelze odebrat ochranu dokumentu, není-li heslo, které znají.  
  
> [!NOTE]  
>  V následujícím příkladu nepoužívá ochrana heslem; Můžete však chtít vezměte v úvahu při přidání ochrany dokumentů pomocí hesla. Další informace najdete v ukázce ochrany dokumentů pomocí na [Office Ukázky a návody vývoje](../vsto/office-development-samples-and-walkthroughs.md).  
  
 Ovládací prvky obsahu můžete použít také k ochraně částí dokumentů. Další informace najdete v tématu [postupy: ochrana částí dokumentů pomocí ovládacích prvků obsahu](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
## <a name="protect-a-document-that-is-part-of-a-document-level-customization"></a>Ochrana dokumentu, který je součástí přizpůsobení na úrovni dokumentu  
  
### <a name="to-protect-a-document-that-is-part-of-a-document-level-customization"></a>K ochraně dokumentu, který je součástí přizpůsobení na úrovni dokumentu  
  
1.  Volání <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> metodu `ThisDocument` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
### <a name="to-exclude-a-bookmark-control-from-document-protection"></a>Ovládací prvek bookmark vyloučit z ochrany dokumentu  
  
1.  Chránit pomocí celý dokument <xref:Microsoft.Office.Tools.Word.Document.Protect%2A> metody.  
  
     [!code-vb[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomation#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#111)]  
  
2.  Vyloučit `Bookmark1` z ochrany dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#112)]
     [!code-csharp[Trin_VstcoreWordAutomation#112](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#112)]  
  
### <a name="compile-the-code"></a>Kompilace kódu  
 Pokud chcete použít tyto příklady kódu, spusťte z `ThisDocument` třídu ve vašem projektu. Tyto příklady kódu předpokládá, že jste existující <xref:Microsoft.Office.Tools.Word.Bookmark> ovládací prvek s názvem `Bookmark1` pro dokument, ve kterém se zobrazí tento kód.  
  
## <a name="protect-a-document-by-using-a-vsto-add-in"></a>Ochrana dokumentu pomocí doplňku VSTO  
  
### <a name="to-protect-a-document-by-using-an-application-level-vsto-add-in"></a>K ochraně dokumentu pomocí úrovni aplikace doplňku VSTO  
  
1.  Volání <xref:Microsoft.Office.Interop.Word._Document.Protect%2A> metodu <xref:Microsoft.Office.Interop.Word.Document> , který chcete chránit.  
  
     Následující příklad kódu chrání aktivní dokument. Pokud chcete použít tento příklad kódu, spusťte jej z `ThisAddIn` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#111)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#111](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#111)]  
  
## <a name="see-also"></a>Viz také:  
 [Ochrana dokumentů v řešeních na úrovni dokumentu](../vsto/document-protection-in-document-level-solutions.md)   
 [Ochrana dokumentů Office heslem](../vsto/password-protection-on-office-documents.md)   
 [Postupy: povolení kódu ke spuštění pozadí dokumentů s omezenými oprávněními](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Postupy: Přidání ovládacích prvků záložek do dokumentů aplikace Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)  
  
  