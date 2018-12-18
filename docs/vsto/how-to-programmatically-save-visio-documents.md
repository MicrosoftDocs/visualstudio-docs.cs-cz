---
title: 'Postupy: ukládání dokumentů aplikace Visio prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a9f065a32fc26d372b97a31eb70836451b31fa00
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670725"
---
# <a name="how-to-programmatically-save-visio-documents"></a>Postupy: ukládání dokumentů aplikace Visio prostřednictvím kódu programu
  Ukládání dokumentů aplikace Microsoft Office Visio několika způsoby:  
  
- Uložení změn v existující dokument.  
  
- Nový dokument uložit nebo uložit dokument s novým názvem.  
  
- Uložení dokumentu se zadanými argumenty.  
  
  Další informace najdete v tématu referenční dokumentaci jazyka VBA pro [Microsoft.Office.Interop.Visio.Document.Save](/office/vba/api/Visio.Document.Save) metody [Microsoft.Office.Interop.Visio.Document.SaveAs](/office/vba/api/Visio.Document.SaveAs) metoda a [ Microsoft.Office.Interop.Visio.Document.SaveAsEx](/office/vba/api/Visio.Document.SaveAsEx) metody.  
  
## <a name="save-an-existing-document"></a>Uložit stávající dokument  
  
### <a name="to-save-a-document"></a>Chcete-li uložit dokument  
  
-   Volání `Microsoft.Office.Interop.Visio.Document.Save` metodu `Microsoft.Office.Tools.Visio.Document` třídy dokumentu, který dřív uložená.  
  
     Pokud chcete použít tento příklad kódu, spusťte jej z `ThisAddIn` třídu ve vašem projektu.  
  
    > [!NOTE]  
    >  `Microsoft.Office.Interop.Visio.Document.Save` Metoda vyvolá výjimku, pokud ještě nebyla uložena nový dokument Visia.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]  
  
## <a name="save-a-document-with-a-new-name"></a>Uložit dokument s novým názvem.  
 Použití `Microsoft.Office.Interop.Visio.Document.SaveAs` metody uložte nový dokument nebo dokument, který se má nový název. Tato metoda vyžaduje, že zadáváte nový název souboru.  
  
### <a name="to-save-the-active-visio-document-with-a-new-name"></a>Uložit aktivní dokument Visia s novým názvem.  
  
-   Volání `Microsoft.Office.Interop.Visio.Document.SaveAs` metodu `Microsoft.Office.Tools.Visio.Document` , že chcete uložit pomocí plně kvalifikovanou cestu včetně názvu souboru. Pokud soubor s tímto názvem již existuje v této složce, je tiše přepsána.  
  
     Pokud chcete použít tento příklad kódu, spusťte jej z `ThisAddIn` třídu ve vašem projektu.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]  
  
## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>Uložit dokument s novým názvem a zadaných argumentů  
 Použití `Microsoft.Office.Interop.Visio.Document.SaveAsEx` má metoda uložit dokument s novým názvem a zadejte všechny příslušné argumenty použít k dokumentu.  
  
### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>Uložit dokument s novým názvem a zadaných argumentů  
  
-   Volání `Microsoft.Office.Interop.Visio.Document.SaveAsEx` metodu `Microsoft.Office.Tools.Visio.Document` , že chcete uložit pomocí plně kvalifikovanou cestu včetně názvu souboru. Pokud soubor s tímto názvem již existuje v této složce, je vyvolána výjimka.  
  
     Následující příklad kódu uloží aktivní dokument s novým názvem, označí jako jen pro čtení dokumentu a zobrazí dokument v seznamu naposledy použitých dokumentů. Pokud chcete použít tento příklad kódu, spusťte jej z `ThisAddIn` třídu ve vašem projektu.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="compile-the-code"></a>Kompilace kódu  
 Tento příklad kódu vyžaduje následující:  
  
-   Uložit dokument s novým názvem, adresář s názvem `Test` se musí nacházet v *dokumenty* složky (pro Windows XP a starší) nebo *dokumenty* složku (pro Windows Vista).  
  
## <a name="see-also"></a>Viz také:  
 [Řešení pro aplikaci Visio](../vsto/visio-solutions.md)   
 [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)   
 [Postupy: vytváření nových dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Postupy: otevírání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Postupy: zavírání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Postupy: tisk dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  