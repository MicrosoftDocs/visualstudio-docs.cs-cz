---
title: 'Postupy: hledání textu v oblastech listů prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově vyhledávat text v oblastech listů Microsoft Excelu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 762cb3fc35b43bfd3ad15aea669adff2d370b632
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827939"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Postupy: hledání textu v oblastech listů prostřednictvím kódu programu
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A>Metoda <xref:Microsoft.Office.Interop.Excel.Range> objektu umožňuje vyhledávat text v rámci rozsahu. Tento text může také obsahovat libovolný z chybových řetězců, které se mohou objevit v buňce listu, jako je například `#NULL!` nebo `#VALUE!` . Další informace o chybových řetězcích najdete v tématu [hodnoty chyb buněk](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Následující příklad vyhledá rozsah s názvem `Fruits` a upraví písmo pro buňky, které obsahují slovo "jablka". Tento postup také používá <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> metodu, která pomocí dříve nastaveného nastavení hledání opakuje hledání. Zadejte buňku, po které chcete hledat, a <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> metoda zpracuje zbytek.

> [!NOTE]
> <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>Vyhledávání metody zalomí zpět na začátek rozsahu hledání poté, co dosáhlo konce rozsahu. Váš kód musí zajistit, aby se hledání Nezalamovat v nekonečné smyčce. Vzorový postup ukazuje jeden ze způsobů, jak tuto funkci zpracovat pomocí <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> Vlastnosti.

## <a name="to-search-for-text-in-a-worksheet-range"></a>Hledání textu v rozsahu listu

1. Deklarujete proměnné pro sledování celého rozsahu, prvního nalezeného rozsahu a aktuálně nalezeného rozsahu.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet58":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet58":::

2. Vyhledejte první shodu a určete všechny parametry s výjimkou buňky, která se má hledat.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet59":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet59":::

3. Pokračuje v hledání, dokud se shodují.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet60":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet60":::

4. Porovnejte první nalezený rozsah ( `firstFind` ) s **žádným**. Pokud `firstFind` neobsahuje žádnou hodnotu, kód si uloží pryč nalezený rozsah ( `currentFind` ).

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet61":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet61":::

5. Ukončí smyčku, pokud adresa nalezeného rozsahu odpovídá adrese prvního nalezeného rozsahu.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet62":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet62":::

6. Nastavte vzhled nalezeného rozsahu.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet63":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet63":::

7. Proveďte další hledání.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet64":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet64":::

   Následující příklad ukazuje metodu Complete.

## <a name="example"></a>Příklad
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet57":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet57":::

## <a name="see-also"></a>Viz také
- [Práce s rozsahy](../vsto/working-with-ranges.md)
- [Postupy: používání stylů pro oblasti v sešitech prostřednictvím kódu programu](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Postupy: odkazování na oblasti listů v kódu prostřednictvím kódu programu](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
