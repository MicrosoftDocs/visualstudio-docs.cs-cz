---
title: 'Postupy: formátování textu v dokumentech prostřednictvím kódu programu'
description: Naučte se, jak můžete pomocí objektu Range programově formátovat text v dokumentu Microsoft Wordu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 931991529b160fedfe65a92e8243183792abf518
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525720"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Postupy: formátování textu v dokumentech prostřednictvím kódu programu
  Objekt lze použít <xref:Microsoft.Office.Interop.Word.Range> k formátování textu v dokumentu aplikace systém Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Následující příklad vybere první odstavec v dokumentu a změní velikost písma, název písma a zarovnání. Pak vybere rozsah a před provedením další části kódu zobrazí okno se zprávou pro pozastavení. V další části je volána metoda Undo <xref:Microsoft.Office.Tools.Word.Document> položky hostitele (pro přizpůsobení na úrovni dokumentu) nebo <xref:Microsoft.Office.Interop.Word.Document> třídy (pro doplněk VSTO) třikrát. Použije normální styl odsazení a zobrazí okno se zprávou pro pozastavení kódu. Potom kód volá <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> metodu jednou a zobrazí okno se zprávou.

## <a name="document-level-customization-example"></a>Příklad přizpůsobení na úrovni dokumentu

### <a name="to-format-text-using-a-document-level-customization"></a>Formátování textu pomocí přizpůsobení na úrovni dokumentu

1. Následující příklad lze použít v přizpůsobení na úrovni dokumentu. Chcete-li použít tento kód, spusťte jej z `ThisDocument` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]

## <a name="vsto-add-in-example"></a>Příklad doplňku VSTO

### <a name="to-format-text-using-a-vsto-add-in"></a>Formátování textu pomocí doplňku VSTO

1. V doplňku VSTO se dá použít následující příklad. Tento příklad používá aktivní dokument. Chcete-li použít tento kód, spusťte jej z `ThisAddIn` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]

## <a name="see-also"></a>Viz také
- [Postupy: definování a výběr oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Postupy: vkládání textu do dokumentů aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Postupy: hledání a nahrazování textu v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
