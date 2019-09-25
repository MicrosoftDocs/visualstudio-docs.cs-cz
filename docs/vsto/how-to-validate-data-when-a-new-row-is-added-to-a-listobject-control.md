---
title: Ověřit data při přidání nového řádku do ovládacího prvku ListObject
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f65bbc374c1d0ec2a940ff98fcc6f04e5391b2db
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255683"
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Postupy: Ověřit data při přidání nového řádku do ovládacího prvku ListObject
  Uživatelé mohou přidat nové řádky do <xref:Microsoft.Office.Tools.Excel.ListObject> ovládacího prvku vázaného na data. Před potvrzením změn ve zdroji dat můžete ověřit data uživatele.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="data-validation"></a>Ověření dat
 <xref:Microsoft.Office.Tools.Excel.ListObject> Pokaždé<xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> , když je přidán řádek do, který je vázán na data, je vyvolána událost. Tuto událost můžete zpracovat a provést tak ověření dat. Například pokud vaše aplikace vyžaduje, aby se do zdroje dat přidaly pouze zaměstnanci mezi počtem 18 a 65, ověřte, že zadaný věk spadá do tohoto rozsahu před přidáním řádku.

> [!NOTE]
> Kromě klienta byste měli vždycky kontrolovat vstup uživatele na serveru. Další informace najdete v tématu [zabezpečené klientské aplikace](/dotnet/framework/data/adonet/secure-client-applications).

### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Ověření dat při přidání nového řádku do ListObject vázaného na data

1. Vytvořte proměnné pro ID a <xref:System.Data.DataTable> na úrovni třídy.

     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]

2. Vytvořte nové <xref:System.Data.DataTable> a přidejte vzorové sloupce a data `Startup` v obslužné rutině `Sheet1` události třídy (v projektu na úrovni dokumentu) nebo `ThisAddIn` třídě (v projektu doplňku VSTO).

     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]

3. Přidejte kód do `list1_BeforeAddDataBoundRow` obslužné rutiny události a ověřte, zda zadaný věk spadá do přijatelného rozsahu.

     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]

## <a name="compile-the-code"></a>Kompilace kódu
 Tento příklad kódu předpokládá, že máte existující <xref:Microsoft.Office.Tools.Excel.ListObject> pojmenovanou `list1` na listu, ve kterém se zobrazuje tento kód.

## <a name="see-also"></a>Viz také:
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Ovládací prvek ListObject](../vsto/listobject-control.md)
- [Automatizace aplikace Excel s použitím rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Postupy: Mapování sloupců ListObject na data](../vsto/how-to-map-listobject-columns-to-data.md)
