---
title: 'Postupy: vytváření tabulek aplikace Word prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a65c42f19602929b546bf105f148bf80e2d9b2db
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914187"
---
# <a name="how-to-programmatically-create-word-tables"></a>Postupy: vytváření tabulek aplikace Word prostřednictvím kódu programu
  <xref:Microsoft.Office.Interop.Word.Tables> Kolekce je členem skupiny <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection>, a <xref:Microsoft.Office.Interop.Word.Range> třídy, což znamená, že můžete vytvořit tabulku v některém z těchto kontextech. Můžete použít <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> metodu <xref:Microsoft.Office.Interop.Word.Tables> kolekce přidat tabulku v zadaném rozsahu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="create-tables-in-document-level-customizations"></a>Vytvoření tabulek v přizpůsobeních na úrovni dokumentu  
  
### <a name="to-add-a-table-to-a-document"></a>Chcete-li přidat tabulku do dokumentu  
  
- Použití <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> způsob, jak přidat tabulku skládající se z tři řádky a čtyři sloupce na začátku dokumentu.  
  
   Pokud chcete použít následující příklad kódu, spusťte jej z `ThisDocument` třídu ve vašem projektu.  
  
   [!code-vb[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomation#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#86)]  
  
  Když vytvoříte tabulku, je automaticky přidán do <xref:Microsoft.Office.Interop.Word.Tables> kolekce <xref:Microsoft.Office.Tools.Word.Document> hostitelský objekt. Poté můžete odkázat na tabulku pomocí položky čísla pomocí <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> vlastnost, jak je znázorněno v následujícím kódu.  
  
### <a name="to-refer-to-a-table-by-item-number"></a>K odkazování na tabulku číslem položky  
  
1. Použití <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> vlastnost a zadejte počet položek v tabulce, který chcete odkazovat na.  
  
    Pokud chcete použít následující příklad kódu, spusťte jej z `ThisDocument` třídu ve vašem projektu.  
  
    [!code-vb[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomation#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#87)]  
  
   Každý <xref:Microsoft.Office.Interop.Word.Table> objekt má také <xref:Microsoft.Office.Interop.Word.Table.Range%2A> atributy vlastnosti, která vám umožní nastavit formátování.  
  
### <a name="to-apply-a-style-to-a-table"></a>Pokud chcete použít styl na tabulku  
  
1.  Použití <xref:Microsoft.Office.Interop.Word.Table.Style%2A> vlastnost použít jeden z předdefinovaných stylů Word do tabulky.  
  
     Pokud chcete použít následující příklad kódu, spusťte jej z `ThisDocument` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomation#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#88)]  
  
## <a name="create-tables-in-vsto-add-ins"></a>Vytvoření tabulek v doplňcích VSTO  
  
### <a name="to-add-a-table-to-a-document"></a>Chcete-li přidat tabulku do dokumentu  
  
- Použití <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> způsob, jak přidat tabulku skládající se z tři řádky a čtyři sloupce na začátku dokumentu.  
  
   Následující příklad kódu přidá do aktivního dokumentu tabulku. Pokud chcete použít tento příklad, spusťte jej z `ThisAddIn` třídu ve vašem projektu.  
  
   [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#86)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#86)]  
  
  Když vytvoříte tabulku, je automaticky přidán do <xref:Microsoft.Office.Interop.Word.Tables> kolekce <xref:Microsoft.Office.Interop.Word.Document>. Poté můžete odkázat na tabulku pomocí položky čísla pomocí <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> vlastnost, jak je znázorněno v následujícím kódu.  
  
### <a name="to-refer-to-a-table-by-item-number"></a>K odkazování na tabulku číslem položky  
  
1. Použití <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> vlastnost a zadejte počet položek v tabulce, který chcete odkazovat na.  
  
    Následující příklad kódu používá aktivního dokumentu. Pokud chcete použít tento příklad, spusťte jej z `ThisAddIn` třídu ve vašem projektu.  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#87)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#87)]  
  
   Každý <xref:Microsoft.Office.Interop.Word.Table> objekt má také <xref:Microsoft.Office.Interop.Word.Table.Range%2A> atributy vlastnosti, která vám umožní nastavit formátování.  
  
### <a name="to-apply-a-style-to-a-table"></a>Pokud chcete použít styl na tabulku  
  
1.  Použití <xref:Microsoft.Office.Interop.Word.Table.Style%2A> vlastnost použít jeden z předdefinovaných stylů Word do tabulky.  
  
     Následující příklad kódu používá aktivního dokumentu. Pokud chcete použít tento příklad, spusťte jej z `ThisAddIn` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#88)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#88)]  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: přidávání textu a formátování do buněk tabulek aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Postupy: Programové přidávání řádků a sloupců do tabulek aplikace Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Postupy: vkládání kódu programu s vlastností dokumentu do tabulek aplikace Word](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  