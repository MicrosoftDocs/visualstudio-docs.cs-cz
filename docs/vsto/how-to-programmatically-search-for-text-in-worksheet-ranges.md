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
ms.openlocfilehash: 3cf3894a2fb6d34678786686fe3c229d2e16a9a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877886"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Postupy: hledání textu v oblastech listů prostřednictvím kódu programu
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A>Metoda <xref:Microsoft.Office.Interop.Excel.Range> objektu umožňuje vyhledávat text v rámci rozsahu. Tento text může také obsahovat libovolný z chybových řetězců, které se mohou objevit v buňce listu, jako je například `#NULL!` nebo `#VALUE!` . Další informace o chybových řetězcích najdete v tématu [hodnoty chyb buněk](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Následující příklad vyhledá rozsah s názvem `Fruits` a upraví písmo pro buňky, které obsahují slovo "jablka". Tento postup také používá <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> metodu, která pomocí dříve nastaveného nastavení hledání opakuje hledání. Zadejte buňku, po které chcete hledat, a <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> metoda zpracuje zbytek.

> [!NOTE]
> <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>Vyhledávání metody zalomí zpět na začátek rozsahu hledání poté, co dosáhlo konce rozsahu. Váš kód musí zajistit, aby se hledání Nezalamovat v nekonečné smyčce. Vzorový postup ukazuje jeden ze způsobů, jak tuto funkci zpracovat pomocí <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> Vlastnosti.

## <a name="to-search-for-text-in-a-worksheet-range"></a>Hledání textu v rozsahu listu

1. Deklarujete proměnné pro sledování celého rozsahu, prvního nalezeného rozsahu a aktuálně nalezeného rozsahu.

    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]

2. Vyhledejte první shodu a určete všechny parametry s výjimkou buňky, která se má hledat.

    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]

3. Pokračuje v hledání, dokud se shodují.

    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]

4. Porovnejte první nalezený rozsah ( `firstFind` ) s **žádným**. Pokud `firstFind` neobsahuje žádnou hodnotu, kód si uloží pryč nalezený rozsah ( `currentFind` ).

    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]

5. Ukončí smyčku, pokud adresa nalezeného rozsahu odpovídá adrese prvního nalezeného rozsahu.

    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]

6. Nastavte vzhled nalezeného rozsahu.

    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]

7. Proveďte další hledání.

    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]

   Následující příklad ukazuje metodu Complete.

## <a name="example"></a>Příklad
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]

## <a name="see-also"></a>Viz také
- [Práce s rozsahy](../vsto/working-with-ranges.md)
- [Postupy: používání stylů pro oblasti v sešitech prostřednictvím kódu programu](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Postupy: odkazování na oblasti listů v kódu prostřednictvím kódu programu](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
