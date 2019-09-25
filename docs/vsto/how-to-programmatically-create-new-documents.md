---
title: 'Postupy: Vytváření nových dokumentů prostřednictvím kódu programu'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 71610d0bd2e957d932e31d83d06aca914bf8b585
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251955"
---
# <a name="how-to-programmatically-create-new-documents"></a>Postupy: Vytváření nových dokumentů prostřednictvím kódu programu
  Při vytváření dokumentu programově je nový dokument nativním <xref:Microsoft.Office.Interop.Word.Document> objektem. Tento objekt nemá další události a možnosti vazby dat pro <xref:Microsoft.Office.Tools.Word.Document> hostitelskou položku. Další informace najdete v tématu [programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Když vyvíjíte projekt na úrovni dokumentu, nemůžete programově přidat <xref:Microsoft.Office.Tools.Word.Document> hostitelské položky do projektu. V projektu doplňku VSTO můžete převést libovolný <xref:Microsoft.Office.Interop.Word.Document> objekt <xref:Microsoft.Office.Tools.Word.Document> na položku hostitele v době běhu. Další informace najdete v tématu [rozšiřování dokumentů aplikace Word a sešitů aplikace Excel v doplňkech VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="to-create-a-new-document-based-on-the-normal-template"></a>Vytvoření nového dokumentu na základě šablony Normal

- <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> Pomocí metody <xref:Microsoft.Office.Interop.Word.Documents> kolekce vytvořte nový dokument založený na šabloně Normal. Chcete-li použít tento příklad kódu, spusťte jej `ThisDocument` z `ThisAddIn` třídy nebo v projektu.

     [!code-vb[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#1)]
     [!code-csharp[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#1)]

## <a name="use-custom-templates"></a>Použití vlastních šablon
 Metoda má volitelný argument šablony pro vytvoření nového dokumentu na základě jiné šablony než šablony Normal. <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> Je nutné, abyste zadali název souboru a plně kvalifikovanou cestu k šabloně.

### <a name="to-create-a-new-document-based-on-a-custom-template"></a>Vytvoření nového dokumentu založeného na vlastní šabloně

- <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> Zavolejte metodu <xref:Microsoft.Office.Interop.Word.Documents> kolekce a zadejte cestu k šabloně. Chcete-li použít tento příklad kódu, spusťte jej `ThisDocument` z `ThisAddIn` třídy nebo v projektu.

     [!code-vb[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#2)]
     [!code-csharp[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#2)]

## <a name="see-also"></a>Viz také:
- [Postupy: Programové otevření existujících dokumentů](../vsto/how-to-programmatically-open-existing-documents.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
