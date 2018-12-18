---
title: 'Postupy: tisk dokumentů aplikace Visio prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6beed729ed670d5f34c645575795b625e03e9583
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671219"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Postupy: tisk dokumentů aplikace Visio prostřednictvím kódu programu
  Můžete vytisknout úplné dokumentu aplikace Microsoft Office Visio nebo pouze konkrétní stránku.  
  
 Podrobné informace o tiskových metodách, naleznete v referenční dokumentaci VBA pro [Microsoft.Office.Interop.Visio.Document.Print](/office/vba/api/Visio.Document.Print) metoda a [Microsoft.Office.Interop.Visio.Page.Print](/office/vba/api/Visio.Page.Print) – metoda .  
  
## <a name="print-a-visio-document"></a>Tisk dokumentů aplikace Visio  
  
### <a name="to-print-a-complete-document"></a>K vytištění celého dokumentu  
  
-   Volání `Microsoft.Office.Interop.Visio.Document.Print` metodu `Microsoft.Office.Interop.Visio.Document` objekt, který chcete vytisknout.  
  
     Následující příklad kódu zobrazí aktivní dokument. Pokud chcete použít tento příklad, spusťte kód z `ThisAddIn` třídu ve vašem projektu.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]  
  
## <a name="print-a-page-of-a-visio-document"></a>Vytisknout stránku dokumentů aplikace Visio  
  
### <a name="to-print-a-page-of-a-document"></a>K tisku stránky z dokumentu  
  
-   Volání `Microsoft.Office.Interop.Visio.Pages.Print` metodu `Microsoft.Office.Interop.Visio.Pages` objekt, který chcete vytisknout.  
  
     Následující příklad kódu zobrazí první stránka aktivní dokument. Pokud chcete použít tento příklad, spusťte kód z `ThisAddIn` třídu ve vašem projektu.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Viz také:  
 [Řešení pro aplikaci Visio](../vsto/visio-solutions.md)   
 [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)   
 [Postupy: vytváření nových dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Postupy: otevírání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Postupy: zavírání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Postupy: ukládání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  