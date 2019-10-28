---
title: 'Postupy: přidávání řádků a sloupců do tabulek aplikace Word prostřednictvím kódu programu'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cc8fbc80a58afcb6f2256c56b1071276c50f319b
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985845"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Postupy: přidávání řádků a sloupců do tabulek aplikace Word prostřednictvím kódu programu
  V tabulce systém Microsoft Office Word jsou buňky uspořádány do řádků a sloupců. Metodu <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> objektu <xref:Microsoft.Office.Interop.Word.Rows> lze použít k přidání řádků do tabulky a metody <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> objektu <xref:Microsoft.Office.Interop.Word.Columns> pro přidání sloupců.

 [!INCLUDE[appliesto_wdalldocapp](includes/appliesto-wdalldocapp-md.md)]

## <a name="document-level-customization-examples"></a>Příklady přizpůsobení na úrovni dokumentu
 Následující příklady kódu lze použít v přizpůsobení na úrovni dokumentu. Chcete-li použít tyto příklady, spusťte je z třídy `ThisDocument` v projektu. V těchto příkladech se předpokládá, že dokument přidružený k vašemu přizpůsobení má již alespoň jednu tabulku.

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

1. K přidání řádku do tabulky použijte metodu <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>.

     [!code-vb[Trin_VstcoreWordAutomation#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>Přidání sloupce do tabulky

1. Použijte metodu <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> a potom pomocí metody <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> nastavte, aby všechny sloupce měly stejnou šířku.

     [!code-vb[Trin_VstcoreWordAutomation#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]

## <a name="vsto-add-in-examples"></a>Příklady doplňku VSTO
 V doplňku VSTO lze použít následující příklady kódu. Chcete-li použít příklady, spusťte je z třídy `ThisAddIn` v projektu. V těchto příkladech se předpokládá, že aktivní dokument již obsahuje alespoň jednu tabulku.

> [!IMPORTANT]
> Tento kód se spouští pouze v projektech, které vytvoříte pomocí šablon doplňku aplikace Word VSTO.
>
> Chcete-li provést tuto úlohu v jakémkoli jiném typu projektu, je nutné přidat odkaz na sestavení **Microsoft. Office. Interop. Word** , a poté je nutné použít třídy z tohoto sestavení pro přidání řádků a sloupců do tabulek. Další informace najdete v tématu [Postupy: cílení aplikací Office prostřednictvím primárních sestavení spolupráce](how-to-target-office-applications-through-primary-interop-assemblies.md) a [odkaz na primární definiční sestavení pro Word 2010](office-primary-interop-assemblies.md).

### <a name="to-add-a-row-to-a-table"></a>Přidání řádku do tabulky

1. K přidání řádku do tabulky použijte metodu <xref:Microsoft.Office.Interop.Word.Rows.Add%2A>.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]

### <a name="to-add-a-column-to-a-table"></a>Přidání sloupce do tabulky

1. Použijte metodu <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> a potom pomocí metody <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> nastavte, aby všechny sloupce měly stejnou šířku.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]

## <a name="see-also"></a>Viz také:
- [Postupy: vytváření tabulek aplikace Word prostřednictvím kódu programu](how-to-programmatically-create-word-tables.md)
- [Postupy: přidávání textu a formátování do buněk v tabulkách aplikace Word prostřednictvím kódu programu](how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Postupy: naplnění tabulek Wordu pomocí vlastností dokumentu prostřednictvím kódu programu](how-to-programmatically-populate-word-tables-with-document-properties.md)
