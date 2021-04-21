---
title: Změna formátů v řádcích obsahujících vybrané buňky prostřednictvím kódu
description: Zjistěte, jak můžete změnit písmo pro celý řádek, který obsahuje vybranou buňku, aby byl text tučný.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- rows [Office development in Visual Studio]
- formatting [Office development in Visual Studio]
- worksheets, changing formatting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c35a176dd6780e08dafea3da7b051a9733a788e5
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827640"
---
# <a name="how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells"></a>Postupy: Změna formátování řádků listů obsahujících vybrané buňky prostřednictvím kódu programu
  Můžete změnit písmo pro celý řádek, který obsahuje vybranou buňku, aby text byl tučný.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-make-the-current-row-bold-and-the-previously-bolded-row-normal"></a>Nastavení aktuálního řádku jako tučného a dříve tučného normálního řádku

1. Deklarujete statickou proměnnou, která bude sledovat dříve vybraný řádek.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet37":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet37":::

2. Načte odkaz na aktuální buňku pomocí <xref:Microsoft.Office.Interop.Excel._Application.ActiveCell%2A> Vlastnosti.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet38":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet38":::

3. Naformátuje aktuální řádek tučně pomocí <xref:Microsoft.Office.Interop.Excel.Range.EntireRow%2A> vlastnosti aktivní buňky.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet39":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet39":::

4. Ujistěte se, že aktuální hodnota není `previousRow` 0. 0 (nula) znamená, že se jedná o první krok tohoto kódu.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet40":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet40":::

5. Zajistěte, aby byl aktuální řádek jiný než předchozí řádek.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet41":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet41":::

6. Načtěte odkaz na rozsah, který představuje dříve vybraný řádek, a nastavte tento řádek na netučné.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet42":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet42":::

7. Umožňuje uložit aktuální řádek, aby se mohl stát předchozí řádek při příštím průchodu.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet43":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet43":::

   Následující příklad ukazuje metodu Complete.

## <a name="example"></a>Příklad
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet36":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet36":::

## <a name="see-also"></a>Viz také
- [Práce s listy](../vsto/working-with-worksheets.md)
- [Postupy: používání stylů pro oblasti v sešitech prostřednictvím kódu programu](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Postupy: kopírování dat a formátování mezi listy prostřednictvím kódu programu](../vsto/how-to-programmatically-copy-data-and-formatting-across-worksheets.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
