---
title: 'Postupy: zavírání sešitů prostřednictvím kódu programu'
description: Přečtěte si, jak můžete zavřít aktivní sešit, nebo můžete určit sešit, který se má programově zavřít.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d09cbff06b1bb7048316629b7b958ee299029ec8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825261"
---
# <a name="how-to-programmatically-close-workbooks"></a>Postupy: zavírání sešitů prostřednictvím kódu programu
  Aktivní sešit můžete zavřít nebo můžete zadat sešit, který chcete zavřít.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="close-the-active-workbook"></a>Zavře aktivní sešit.
 Existují dva postupy pro zavření aktivního sešitu: jeden pro přizpůsobení na úrovni dokumentu a jeden pro doplňky VSTO.

### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>Zavření aktivního sešitu v přizpůsobení na úrovni dokumentu

1. Voláním <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> metody zavřete sešit přidružený k přizpůsobení. Chcete-li použít následující příklad kódu, spusťte jej ve `Sheet1` třídě v projektu na úrovni dokumentu pro aplikaci Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet3":::

### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>Zavření aktivního sešitu v doplňku VSTO

1. Voláním <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> metody zavřete aktivní sešit. Chcete-li použít následující příklad kódu, spusťte jej ve `ThisAddIn` třídě v projektu doplňku VSTO pro Excel.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet1":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="close-a-workbook-that-you-specify-by-name"></a>Zavřít sešit, který určíte podle názvu
 Způsob, jakým jste zavřeli sešit, který určíte podle názvu, je stejný pro doplňky VSTO a přizpůsobení na úrovni dokumentu.

### <a name="to-close-a-workbook-that-you-specify-by-name"></a>Zavření sešitu, který určíte podle názvu

1. Zadejte název sešitu jako argument pro <xref:Microsoft.Office.Interop.Excel.Workbooks> kolekci. Následující příklad kódu předpokládá, že sešit s názvem **NewWorkbook** je otevřen v aplikaci Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="see-also"></a>Viz také
- [Práce se sešity](../vsto/working-with-workbooks.md)
- [Postupy: ukládání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-save-workbooks.md)
- [Postupy: otevírání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-open-workbooks.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
