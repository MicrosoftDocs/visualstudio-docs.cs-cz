---
title: Ověřit data při přidání nového řádku do ovládacího prvku ListObject
description: Zjistěte, jak můžete pomocí sady Visual Studio ověřit data při přidání nového řádku do ovládacího prvku ListObject.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a7002cdc0787850fc7be5a782f3cf3a2101d7593
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825716"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Postupy: ověření dat při přidání nového řádku do ovládacího prvku ListObject
  Uživatelé mohou přidat nové řádky do <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku vázaného na data. Před potvrzením změn ve zdroji dat můžete ověřit data uživatele.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="data-validation"></a>Ověřování dat
 Pokaždé, když je přidán řádek do <xref:Microsoft.Office.Tools.Excel.ListObject> , který je vázán na data, <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> je vyvolána událost. Tuto událost můžete zpracovat a provést tak ověření dat. Například pokud vaše aplikace vyžaduje, aby se do zdroje dat přidaly pouze zaměstnanci mezi počtem 18 a 65, ověřte, že zadaný věk spadá do tohoto rozsahu před přidáním řádku.

> [!NOTE]
> Kromě klienta byste měli vždycky kontrolovat vstup uživatele na serveru. Další informace najdete v tématu [zabezpečené klientské aplikace](/dotnet/framework/data/adonet/secure-client-applications).

### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Ověření dat při přidání nového řádku do ListObject vázaného na data

1. Vytvořte proměnné pro ID a <xref:System.Data.DataTable> na úrovni třídy.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet8":::

2. Vytvořte nové <xref:System.Data.DataTable> a přidejte vzorové sloupce a data v `Startup` obslužné rutině události `Sheet1` třídy (v projektu na úrovni dokumentu) nebo `ThisAddIn` třídě (v projektu doplňku VSTO).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet9":::

3. Přidejte kód do `list1_BeforeAddDataBoundRow` obslužné rutiny události a ověřte, zda zadaný věk spadá do přijatelného rozsahu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet10":::

## <a name="compile-the-code"></a>Kompilovat kód
 Tento příklad kódu předpokládá, že máte existující <xref:Microsoft.Office.Tools.Excel.ListObject> pojmenovanou `list1` na listu, ve kterém se zobrazuje tento kód.

## <a name="see-also"></a>Viz také
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Ovládací prvek ListObject](../vsto/listobject-control.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Postupy: mapování sloupců ListObject na data](../vsto/how-to-map-listobject-columns-to-data.md)
