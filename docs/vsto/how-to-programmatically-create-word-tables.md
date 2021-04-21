---
title: 'Postupy: vytváření tabulek aplikace Word prostřednictvím kódu programu'
description: Naučte se používat metodu Add kolekce Tables k přidání tabulky v zadaném rozsahu do dokumentu Microsoft Wordu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], adding tables
- tables [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5651487e280d7fb9912734b919b00fab28a702db
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827380"
---
# <a name="how-to-programmatically-create-word-tables"></a>Postupy: vytváření tabulek aplikace Word prostřednictvím kódu programu
  <xref:Microsoft.Office.Interop.Word.Tables>Kolekce je členem <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Tools.Word.Document> tříd,, a <xref:Microsoft.Office.Interop.Word.Selection> <xref:Microsoft.Office.Interop.Word.Range> , což znamená, že můžete vytvořit tabulku v některém z těchto kontextů. Pomocí <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> metody <xref:Microsoft.Office.Interop.Word.Tables> kolekce přidáte tabulku v zadaném rozsahu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="create-tables-in-document-level-customizations"></a>Vytváření tabulek v přizpůsobeních na úrovni dokumentu

### <a name="to-add-a-table-to-a-document"></a>Přidání tabulky do dokumentu

- Použijte <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> metodu k přidání tabulky sestávající ze tří řádků a čtyř sloupců na začátku dokumentu.

   Chcete-li použít následující příklad kódu, spusťte jej z `ThisDocument` třídy v projektu.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet86":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet86":::

  Když vytvoříte tabulku, automaticky se přidá do <xref:Microsoft.Office.Interop.Word.Tables> kolekce <xref:Microsoft.Office.Tools.Word.Document> položky hostitele. Pak můžete odkazovat na tabulku podle jejího čísla položky pomocí <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> vlastnosti, jak je znázorněno v následujícím kódu.

### <a name="to-refer-to-a-table-by-item-number"></a>Postup při odkazování na tabulku podle čísla položky

1. Použijte <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> vlastnost a zadejte číslo položky tabulky, na kterou chcete odkazovat.

    Chcete-li použít následující příklad kódu, spusťte jej z `ThisDocument` třídy v projektu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet87":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet87":::

   Každý <xref:Microsoft.Office.Interop.Word.Table> objekt má také <xref:Microsoft.Office.Interop.Word.Table.Range%2A> vlastnost, která umožňuje nastavit atributy formátování.

### <a name="to-apply-a-style-to-a-table"></a>Použití stylu pro tabulku

1. Vlastnost použijte <xref:Microsoft.Office.Interop.Word.Table.Style%2A> k použití jednoho z vestavěných stylů Wordu pro tabulku.

     Chcete-li použít následující příklad kódu, spusťte jej z `ThisDocument` třídy v projektu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet88":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet88":::

## <a name="create-tables-in-vsto-add-ins"></a>Vytváření tabulek v doplňcích VSTO

### <a name="to-add-a-table-to-a-document"></a>Přidání tabulky do dokumentu

- Použijte <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> metodu k přidání tabulky sestávající ze tří řádků a čtyř sloupců na začátku dokumentu.

   Následující příklad kódu přidá tabulku do aktivního dokumentu. Chcete-li použít tento příklad, spusťte jej z `ThisAddIn` třídy v projektu.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet86":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet86":::

  Když vytvoříte tabulku, je automaticky přidána do <xref:Microsoft.Office.Interop.Word.Tables> kolekce <xref:Microsoft.Office.Interop.Word.Document> . Pak můžete odkazovat na tabulku podle jejího čísla položky pomocí <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> vlastnosti, jak je znázorněno v následujícím kódu.

### <a name="to-refer-to-a-table-by-item-number"></a>Postup při odkazování na tabulku podle čísla položky

1. Použijte <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> vlastnost a zadejte číslo položky tabulky, na kterou chcete odkazovat.

    Následující příklad kódu používá aktivní dokument. Chcete-li použít tento příklad, spusťte jej z `ThisAddIn` třídy v projektu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet87":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet87":::

   Každý <xref:Microsoft.Office.Interop.Word.Table> objekt má také <xref:Microsoft.Office.Interop.Word.Table.Range%2A> vlastnost, která umožňuje nastavit atributy formátování.

### <a name="to-apply-a-style-to-a-table"></a>Použití stylu pro tabulku

1. Vlastnost použijte <xref:Microsoft.Office.Interop.Word.Table.Style%2A> k použití jednoho z vestavěných stylů Wordu pro tabulku.

     Následující příklad kódu používá aktivní dokument. Chcete-li použít tento příklad, spusťte jej z `ThisAddIn` třídy v projektu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet88":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet88":::

## <a name="see-also"></a>Viz také
- [Postupy: přidávání textu a formátování do buněk v tabulkách aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Postupy: přidávání řádků a sloupců do tabulek aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Postupy: naplnění tabulek Wordu pomocí vlastností dokumentu prostřednictvím kódu programu](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
