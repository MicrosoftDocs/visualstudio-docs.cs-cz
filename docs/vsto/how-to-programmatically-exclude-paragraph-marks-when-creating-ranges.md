---
title: Při programovém vytváření rozsahů vylučte znaky konce odstavců
description: Přečtěte si, jak můžete při vytváření rozsahů v dokumentu Microsoft Wordu programově vyloučit označení odstavců.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], excluding paragraphs
- ranges, excluding paragraph marks in Word
- documents [Office development in Visual Studio], paragraph marks
- paragraphs, controlling structure
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 898eae77928908dfc077ddf80d2659328ec6475d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885479"
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Postupy: vyloučení značek odstavců při vytváření rozsahů prostřednictvím kódu programu
  Pokaždé, když vytvoříte <xref:Microsoft.Office.Interop.Word.Range> objekt na základě odstavce, budou do rozsahu zahrnuty všechny netisknutelné znaky, například značky odstavce. Je možné, že budete chtít vložit text ze zdrojového odstavce do cílového odstavce. Pokud nechcete rozdělit cílový odstavec na samostatné odstavce, musíte nejdřív ze zdrojového odstavce odebrat značku konce odstavce. Kromě toho, vzhledem k tomu, že informace o formátování odstavců jsou uloženy v rámci značky odstavce, nebudete chtít tyto údaje zahrnout, pokud rozsah vložíte do existujícího odstavce.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Následující ukázkový postup deklaruje dvě řetězcové proměnné, načte obsah prvního a druhého odstavce v aktivním dokumentu a pak vymění jeho obsah. Příklad následně ukazuje odebrání značky odstavce z rozsahu pomocí <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody a vložení textu do odstavce.

## <a name="to-control-paragraph-structure-when-inserting-text"></a>Řízení struktury odstavců při vkládání textu

1. Vytvořte dvě proměnné rozsahu pro první a druhý odstavec a načtěte jejich obsah pomocí <xref:Microsoft.Office.Interop.Word.Range.Text%2A> Vlastnosti.

     Následující příklad kódu lze použít v přizpůsobení na úrovni dokumentu.

     [!code-vb[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#27)]

     Následující příklad kódu lze použít v doplňku VSTO na úrovni aplikace. Tento kód používá aktivní dokument.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#27)]

2. Přiřaďte <xref:Microsoft.Office.Interop.Word.Range.Text%2A> vlastnost k záměně textu mezi dvěma odstavci.

     [!code-vb[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#28)]
     [!code-csharp[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#28)]

3. Výběrem jednotlivých rozsahů v příkazu zapnout a pozastavit zobrazíte výsledky v okně se zprávou.

     [!code-vb[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#29)]
     [!code-csharp[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#29)]

4. Upravte `firstRange` pomocí <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody tak, aby označení odstavce již nebylo součástí `firstRange` .

     [!code-vb[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#30)]
     [!code-csharp[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#30)]

5. Nahraďte zbytek textu v prvním odstavci přiřazením nového řetězce k <xref:Microsoft.Office.Interop.Word.Range.Text%2A> Vlastnosti rozsahu.

     [!code-vb[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#31)]
     [!code-csharp[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#31)]

6. Nahraďte text v `secondRange` , včetně označení odstavce.

     [!code-vb[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#32)]
     [!code-csharp[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#32)]

7. Vyberte `firstRange` a pozastavte, pokud chcete zobrazit výsledky v okně se zprávou, a pak Totéž udělejte s `secondRange` .

     Vzhledem `firstRange` k tomu, že byla předefinována tak, aby nedošlo k označení odstavce, původní formátování odstavce je zachováno. Do konce odstavce se však vložila věta `secondRange` , která odebere samostatný odstavec.

     [!code-vb[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#33)]
     [!code-csharp[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#33)]

     Původní obsah obou rozsahů byl uložen jako řetězec, takže můžete obnovit původní stav dokumentu.

8. Upravte `firstRange` tak, aby obsahovala značku odstavce pomocí <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody pro pozici s jedním znakem.

     [!code-vb[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#34)]
     [!code-csharp[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#34)]

9. Odstraňte `secondRange`. Tím se obnoví původní pozice odstavce tři.

     [!code-vb[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#35)]
     [!code-csharp[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#35)]

10. Obnovte původní text odstavce v `firstRange` .

     [!code-vb[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#36)]
     [!code-csharp[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#36)]

11. Použijte <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> metodu <xref:Microsoft.Office.Interop.Word.Range> objektu pro vložení původního odstavce – dva obsah po `firstRange` a pak vyberte `firstRange` .

     [!code-vb[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#37)]
     [!code-csharp[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#37)]

## <a name="document-level-customization-example"></a>Příklad přizpůsobení na úrovni dokumentu

### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>Řízení struktury odstavců při vkládání textu v přizpůsobeních na úrovni dokumentu

1. Následující příklad ukazuje metodu Complete pro přizpůsobení na úrovni dokumentu. Chcete-li použít tento kód, spusťte jej z `ThisDocument` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#26)]

## <a name="vsto-add-in-example"></a>Příklad doplňku VSTO

### <a name="to-control-paragraph-structure-when-inserting-text-in-a-vsto-add-in"></a>Řízení struktury odstavců při vkládání textu do doplňku VSTO

1. Následující příklad ukazuje metodu Complete pro doplněk VSTO. Chcete-li použít tento kód, spusťte jej z `ThisAddIn` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#26)]

## <a name="see-also"></a>Viz také
- [Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Postupy: sbalení oblastí nebo výběrů v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Postupy: vkládání textu do dokumentů aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Postupy: resetování oblastí v dokumentech aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Postupy: definování a výběr oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
