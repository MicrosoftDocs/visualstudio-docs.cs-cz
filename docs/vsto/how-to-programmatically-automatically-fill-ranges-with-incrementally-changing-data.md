---
title: Automatické vyplňování přírůstkových změn oblastí dat prostřednictvím kódu programu
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 076381c93d11c2d13bdd89ea5c36c0039e15ef71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547469"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Postupy: Automatické vyplňování oblastí pomocí přírůstkových změn dat prostřednictvím kódu programu
  <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>Metoda <xref:Microsoft.Office.Interop.Excel.Range> objektu umožňuje vyplnit rozsah na listu hodnotami automaticky. Nejčastěji se <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> Metoda používá k ukládání přírůstkových nebo klesajících hodnot v rozsahu. Chování můžete určit tak, že zadáte volitelnou konstantu z <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> výčtu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Při použití je nutné zadat dva rozsahy <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> :

- Rozsah, který volá <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodu, která určuje počáteční bod výplně a obsahuje počáteční hodnotu.

- Rozsah, který chcete vyplnit, byl předán jako parametr <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodě. Tento cílový rozsah musí zahrnovat rozsah obsahující počáteční hodnotu.

    > [!NOTE]
    > Nemůžete předat <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek místo <xref:Microsoft.Office.Interop.Excel.Range> . Další informace najdete v tématu [programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="example"></a>Příklad
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]

## <a name="compile-the-code"></a>Kompilovat kód
 První buňka rozsahu, který chcete vyplnit, musí obsahovat počáteční hodnotu.

 Příklad vyžaduje, abyste vyplnili tři oblasti:

- Sloupec B zahrnuje pět dnů v týdnu. Pro počáteční hodnotu zadejte **pondělí** do buňky B1.

- Sloupec C zahrnuje pět měsíců. Jako počáteční hodnotu zadejte **leden** v buňce C1.

- Sloupec D má zahrnovat řadu čísel, přičemž každý řádek se zvýší o dva. U počátečních hodnot zadejte **4** do buňky D1 a **6** v buňce D2.

## <a name="see-also"></a>Viz také
- [Práce s rozsahy](../vsto/working-with-ranges.md)
- [Postupy: odkazování na oblasti listů v kódu prostřednictvím kódu programu](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Postupy: používání stylů pro oblasti v sešitech prostřednictvím kódu programu](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Postupy: spouštění výpočtů v aplikaci Excel prostřednictvím kódu programu](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
