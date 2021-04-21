---
title: Naplnění tabulek aplikace Word vlastnostmi dokumentu prostřednictvím kódu programu
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově naplnit tabulku pomocí vlastností dokumentu v dokumentu Microsoft Wordu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document properties, inserting in Word tables
- documents [Office development in Visual Studio], document properties
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a5cb9303e7891ec6657d0fa599921d37a184073f
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827247"
---
# <a name="how-to-programmatically-populate-word-tables-with-document-properties"></a>Postupy: naplnění tabulek Wordu pomocí vlastností dokumentu prostřednictvím kódu programu
  Následující příklad vytvoří tabulku systém Microsoft Office Word v horní části dokumentu a naplní ji vlastnostmi hostitelského dokumentu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="populate-tables-in-a-document-level-customization"></a>Naplnění tabulek v přizpůsobení na úrovni dokumentu

### <a name="to-create-a-table-and-populate-it-with-document-properties"></a>Vytvoření tabulky a její vyplnění vlastnostmi dokumentu

1. Nastaví rozsah na začátek dokumentu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet90":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet90":::

2. Vložte nadpis tabulky a přidejte znaky konce odstavce.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet91":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet91":::

3. Přidejte tabulku do dokumentu v rozsahu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet92":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet92":::

4. Naformátuje tabulku a použije styl.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet93":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet93":::

5. Vložte vlastnosti dokumentu do buněk.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet94":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet94":::

   Následující příklad ukazuje kompletní postup. Chcete-li použít tento kód, spusťte jej z `ThisDocument` třídy v projektu.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet89":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet89":::

## <a name="populate-tables-in-a-vsto-add-in"></a>Naplnění tabulek v doplňku VSTO

### <a name="to-create-a-table-and-populate-it-with-document-properties"></a>Vytvoření tabulky a její vyplnění vlastnostmi dokumentu

1. Nastaví rozsah na začátek dokumentu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet90":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet90":::

2. Vložte nadpis tabulky a přidejte znaky konce odstavce.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet91":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet91":::

3. Přidejte tabulku do dokumentu v rozsahu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet92":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet92":::

4. Naformátuje tabulku a použije styl.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet93":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet93":::

5. Vložte vlastnosti dokumentu do buněk.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet94":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet94":::

   Následující příklad ukazuje kompletní postup. Chcete-li použít tento kód, spusťte jej z `ThisAddIn` třídy v projektu.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet89":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet89":::

## <a name="see-also"></a>Viz také
- [Postupy: vytváření tabulek aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-create-word-tables.md)
- [Postupy: přidávání textu a formátování do buněk v tabulkách aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)
- [Postupy: přidávání řádků a sloupců do tabulek aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
