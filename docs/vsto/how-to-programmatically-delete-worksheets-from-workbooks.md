---
title: 'Postupy: Odstraňování listů ze sešitů prostřednictvím kódu programu'
description: Přečtěte si, jak můžete programově odstranit libovolný list v sešitu Microsoft Excelu pomocí položky hostitele na listu, například.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e9d1330c454e0b9b9f5ad4624c18e4ed1055343d
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527782"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Postupy: Odstraňování listů ze sešitů prostřednictvím kódu programu
  Můžete odstranit kterýkoli list v sešitu. Chcete-li odstranit list, použijte položku hostitele listu nebo přejděte k listu pomocí kolekce listů sešitu.

 [!INCLUDE[appliesto_xlalldocapp](includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Použít položku hostitele listu
 Pokud byl sešit přidán v době návrhu v přizpůsobení na úrovni dokumentu, použijte <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> metodu k odstranění zadaného listu. Následující kód odstraní list ze sešitu odkazem přímo na položku hostitele na listu.

> [!IMPORTANT]
> Tento kód se spouští pouze v projektech, které vytvoříte pomocí kterékoli z následujících šablon projektu:
>
> - Sešit aplikace Excel 2013
> - Šablona Excelu 2013
> - Sešit aplikace Excel 2010
> - Šablona aplikace Excel 2010
>
>   Chcete-li tuto úlohu provést v jakémkoli jiném typu projektu, je nutné přidat odkaz na sestavení **Microsoft. Office. Interop. Excel** a poté je nutné použít třídy z tohoto sestavení k otevření sešitu a odstranění listu. Další informace najdete v tématu [Postupy: cílení aplikací Office prostřednictvím primárních sestavení spolupráce](how-to-target-office-applications-through-primary-interop-assemblies.md) a [odkaz na primární definiční sestavení v Excelu 2010](office-primary-interop-assemblies.md).

### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Odstranění listu pomocí položky hostitele na listu

1. Zavolejte <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> metodu `Sheet1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#17](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Použití kolekce listů excelového sešitu
 Přístup k listům prostřednictvím kolekce aplikace systém Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Sheets> v následujících případech:

- Chcete odstranit list v doplňku VSTO.

- List, který chcete odstranit, byl vytvořen v době běhu v přizpůsobení na úrovni dokumentu.

  Následující kód odstraní list ze sešitu odkazem na list s číslem indexu kolekce **listů** . Tento kód předpokládá, že byl vytvořen nový list programově.

> [!IMPORTANT]
> Chcete-li tuto úlohu provést v jakémkoli jiném typu projektu, je nutné přidat odkaz na sestavení **Microsoft. Office. Interop. Excel** a poté je nutné použít třídy z tohoto sestavení k otevření sešitu a odstranění listu. Další informace najdete v tématu [Postupy: cílení aplikací Office prostřednictvím primárních sestavení spolupráce](how-to-target-office-applications-through-primary-interop-assemblies.md) a [odkaz na primární definiční sestavení v Excelu 2010](office-primary-interop-assemblies.md).

### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Odstranění listu pomocí kolekce listů sešitu aplikace Excel

1. Zavolejte <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> metodu <xref:Microsoft.Office.Interop.Excel.Sheets> kolekce.

     [!code-csharp[Trin_VstcoreExcelAutomation#18](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]

## <a name="see-also"></a>Viz také
- [Práce s listy](working-with-worksheets.md)
- [Postupy: skrývání listů prostřednictvím kódu programu](how-to-programmatically-hide-worksheets.md)
- [Postupy: přesouvání listů v sešitech prostřednictvím kódu programu](how-to-programmatically-move-worksheets-within-workbooks.md)
- [Postupy: Výběr listů prostřednictvím kódu programu](how-to-programmatically-select-worksheets.md)
- [Postupy: přidávání nových listů do sešitů prostřednictvím kódu programu](how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Položka hostitele listu](worksheet-host-item.md)
- [Globální přístup k objektům v projektech pro systém Office](global-access-to-objects-in-office-projects.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](programmatic-limitations-of-host-items-and-host-controls.md)
