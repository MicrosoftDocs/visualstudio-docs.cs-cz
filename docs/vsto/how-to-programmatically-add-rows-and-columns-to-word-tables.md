---
title: 'Postupy: Programové přidávání řádků a sloupců do tabulek aplikace Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio], adding to Word tables
- tables [Office development in Visual Studio], adding rows and columns
- columns [Office development in Visual Studio], adding to Word tables
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fca44524c3a7c7f10e855eaf62e8b77dc225ae01
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818676"
---
# <a name="how-to-programmatically-add-rows-and-columns-to-word-tables"></a>Postupy: Programové přidávání řádků a sloupců do tabulek aplikace Word
  V tabulce aplikace Microsoft Office Word buňky jsou uspořádány do řádků a sloupců. Můžete použít <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metodu <xref:Microsoft.Office.Interop.Word.Rows> objektu pro přidání řádků do tabulky a <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metodu <xref:Microsoft.Office.Interop.Word.Columns> objektu, který chcete přidat sloupce.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customization-examples"></a>Příklady přizpůsobení na úrovni dokumentu  
 Následující příklady kódu je možné v přizpůsobení na úrovni dokumentu. Pokud chcete použít tyto příklady, spustit je z `ThisDocument` třídu ve vašem projektu. Tyto příklady předpokládají, že dokument související s přizpůsobením již má alespoň jednu tabulku.  
  
> [!IMPORTANT]
>  Tento kód se spustí jenom v projektech, které vytvoříte pomocí některého z následujících šablon projektu:  
> 
> - Dokument aplikace Word 2013  
> - Šablona pro Word 2013  
> - Dokument aplikace Word 2010  
> - Šablona aplikace Word 2010  
> 
>   Pokud chcete k provedení této úlohy v jakýkoli jiný typ projektu, je nutné přidat odkaz na **Microsoft.Office.Interop.Word** sestavení a pak pomocí třídy z tohoto sestavení k přidávání řádků a sloupců do tabulek. Další informace najdete v tématu [jak: aplikace Office cílové primárních sestaveních vzájemné spolupráce](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) a [odkaz na primární spolupracující sestavení aplikace Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
### <a name="to-add-a-row-to-a-table"></a>Chcete-li přidat řádek do tabulky  
  
1.  Použití <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metoda pro přidání řádku do tabulky.  
  
     [!code-vb[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomation#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#95)]  
  
### <a name="to-add-a-column-to-a-table"></a>Chcete-li přidat sloupec do tabulky  
  
1.  Použít <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metoda a pak <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> metoda chcete, aby všechny sloupce mají stejnou šířku.  
  
     [!code-vb[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomation#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#96)]  
  
## <a name="vsto-add-in-examples"></a>Příklady doplňku VSTO  
 Můžete použít následující příklady kódu v doplňku VSTO. Pokud chcete použít příklady, spusťte z `ThisAddIn` třídu ve vašem projektu. Tyto příklady předpokládají, že aktivní dokument už má alespoň jednu tabulku.  
  
> [!IMPORTANT]  
>  Tento kód se spustí jenom v projektech, které vytvoříte pomocí šablony doplňků VSTO pro Word.  
>   
>  Pokud chcete k provedení této úlohy v jakýkoli jiný typ projektu, je nutné přidat odkaz na **Microsoft.Office.Interop.Word** sestavení a pak pomocí třídy z tohoto sestavení k přidávání řádků a sloupců do tabulek. Další informace najdete v tématu [jak: aplikace Office cílové primárních sestaveních vzájemné spolupráce](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) a [odkaz na primární spolupracující sestavení aplikace Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
### <a name="to-add-a-row-to-a-table"></a>Chcete-li přidat řádek do tabulky  
  
1.  Použití <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> metoda pro přidání řádku do tabulky.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#95)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#95)]  
  
### <a name="to-add-a-column-to-a-table"></a>Chcete-li přidat sloupec do tabulky  
  
1.  Použít <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> metoda a pak <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> metoda chcete, aby všechny sloupce mají stejnou šířku.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#96)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#96)]  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: vytváření tabulek aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-create-word-tables.md)   
 [Postupy: přidávání textu a formátování do buněk tabulek aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Postupy: vkládání kódu programu s vlastností dokumentu do tabulek aplikace Word](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  