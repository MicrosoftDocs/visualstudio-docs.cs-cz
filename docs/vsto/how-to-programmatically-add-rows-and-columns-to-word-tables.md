---
title: 'Postupy: přidávání řádků a sloupců do tabulek aplikace Word prostřednictvím kódu programu'
description: Naučte se, jak můžete použít metodu Add objektu Rows k přidání řádků do tabulky. Můžete také použít metodu Add objektu Columns, chcete-li přidat sloupce.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a4077e78da512ef7b49546ae9b5271b5dfd8ff15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910164"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Postupy: přidávání řádků a sloupců do tabulek aplikace Word prostřednictvím kódu programu
  V tabulce systém Microsoft Office Word jsou buňky uspořádány do řádků a sloupců. Můžete použít <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metodu <xref:Microsoft.Office.Interop.Word.Rows> objektu pro přidání řádků do tabulky a <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metodu <xref:Microsoft.Office.Interop.Word.Columns> objektu pro přidání sloupců.

 [!INCLUDE[appliesto_wdalldocapp](includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customization-examples"></a>Příklady přizpůsobení na úrovni dokumentu
 Následující příklady kódu lze použít v přizpůsobení na úrovni dokumentu. Chcete-li použít tyto příklady, spusťte je z `ThisDocument` třídy v projektu. V těchto příkladech se předpokládá, že dokument přidružený k vašemu přizpůsobení má již alespoň jednu tabulku.

> [!IMPORTANT]
> Tento kód se spouští pouze v projektech, které vytvoříte pomocí kterékoli z následujících šablon projektu:
>
> - Dokument aplikace Word 2013
> - Šablona pro Word 2013
> - Dokument aplikace Word 2010
> - Šablona aplikace Word 2010
>
>   Chcete-li provést tuto úlohu v jakémkoli jiném typu projektu, je nutné přidat odkaz na sestavení **Microsoft. Office. Interop. Word** , a poté je nutné použít třídy z tohoto sestavení pro přidání řádků a sloupců do tabulek. Další informace najdete v tématu [Postupy: cílení aplikací Office prostřednictvím primárních sestavení spolupráce](how-to-target-office-applications-through-primary-interop-assemblies.md) a [odkaz na primární definiční sestavení pro Word 2010](office-primary-interop-assemblies.md).

### <a name="to-add-a-row-to-a-table"></a>Přidání řádku do tabulky

1. Použijte <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metodu pro přidání řádku do tabulky.

     [!code-vb[Trin_VstcoreWordAutomation#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>Přidání sloupce do tabulky

1. Použijte <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metodu a potom pomocí <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> metody nastavte stejnou šířku všech sloupců.

     [!code-vb[Trin_VstcoreWordAutomation#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]

## <a name="vsto-add-in-examples"></a>Příklady doplňku VSTO
 V doplňku VSTO lze použít následující příklady kódu. Chcete-li použít příklady, spusťte je z `ThisAddIn` třídy v projektu. V těchto příkladech se předpokládá, že aktivní dokument již obsahuje alespoň jednu tabulku.

> [!IMPORTANT]
> Tento kód se spouští pouze v projektech, které vytvoříte pomocí šablon doplňku aplikace Word VSTO.
>
> Chcete-li provést tuto úlohu v jakémkoli jiném typu projektu, je nutné přidat odkaz na sestavení **Microsoft. Office. Interop. Word** , a poté je nutné použít třídy z tohoto sestavení pro přidání řádků a sloupců do tabulek. Další informace najdete v tématu [Postupy: cílení aplikací Office prostřednictvím primárních sestavení spolupráce](how-to-target-office-applications-through-primary-interop-assemblies.md) a [odkaz na primární definiční sestavení pro Word 2010](office-primary-interop-assemblies.md).

### <a name="to-add-a-row-to-a-table"></a>Přidání řádku do tabulky

1. Použijte <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metodu pro přidání řádku do tabulky.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>Přidání sloupce do tabulky

1. Použijte <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metodu a potom pomocí <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> metody nastavte stejnou šířku všech sloupců.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]

## <a name="see-also"></a>Viz také
- [Postupy: vytváření tabulek aplikace Word prostřednictvím kódu programu](how-to-programmatically-create-word-tables.md)
- [Postupy: přidávání textu a formátování do buněk v tabulkách aplikace Word prostřednictvím kódu programu](how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Postupy: naplnění tabulek Wordu pomocí vlastností dokumentu prostřednictvím kódu programu](how-to-programmatically-populate-word-tables-with-document-properties.md)
