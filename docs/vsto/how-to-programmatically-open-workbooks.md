---
title: 'Postupy: otevírání sešitů prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově otevřít sešit Microsoft Excelu nebo pracovat s existujícím sešitem.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4dba79b1b0eea03ca3aae23e98fb93e6ef776d80
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824780"
---
# <a name="how-to-programmatically-open-workbooks"></a>Postupy: otevírání sešitů prostřednictvím kódu programu
  Tato <xref:Microsoft.Office.Interop.Excel.Workbooks> kolekce v aplikaci systém Microsoft Office Excel umožňuje pracovat se všemi otevřenými sešity a otevírat sešity.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Otevření existujícího sešitu

1. Použijte <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> metodu <xref:Microsoft.Office.Interop.Excel.Workbooks> kolekce a předejte cestu k sešitu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet2":::

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad kódu vyžaduje následující:

- Sešit s názvem `YourWorkbook.xls` musí existovat v adresáři s názvem `Test` na jednotce C.

## <a name="see-also"></a>Viz také
- [Práce se sešity](../vsto/working-with-workbooks.md)
- [Postupy: otevírání textových souborů jako sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Postupy: vytváření nových sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Postupy: ukládání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-save-workbooks.md)
- [Postupy: zavírání sešitů prostřednictvím kódu programu](../vsto/how-to-programmatically-close-workbooks.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
