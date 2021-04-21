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
ms.openlocfilehash: c0929ccf3bb2567099dc7f3b795ad2257da0edb3
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825794"
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Postupy: vyloučení značek odstavců při vytváření rozsahů prostřednictvím kódu programu
  Pokaždé, když vytvoříte <xref:Microsoft.Office.Interop.Word.Range> objekt na základě odstavce, budou do rozsahu zahrnuty všechny netisknutelné znaky, například značky odstavce. Je možné, že budete chtít vložit text ze zdrojového odstavce do cílového odstavce. Pokud nechcete rozdělit cílový odstavec na samostatné odstavce, musíte nejdřív ze zdrojového odstavce odebrat značku konce odstavce. Kromě toho, vzhledem k tomu, že informace o formátování odstavců jsou uloženy v rámci značky odstavce, nebudete chtít tyto údaje zahrnout, pokud rozsah vložíte do existujícího odstavce.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Následující ukázkový postup deklaruje dvě řetězcové proměnné, načte obsah prvního a druhého odstavce v aktivním dokumentu a pak vymění jeho obsah. Příklad následně ukazuje odebrání značky odstavce z rozsahu pomocí <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody a vložení textu do odstavce.

## <a name="to-control-paragraph-structure-when-inserting-text"></a>Řízení struktury odstavců při vkládání textu

1. Vytvořte dvě proměnné rozsahu pro první a druhý odstavec a načtěte jejich obsah pomocí <xref:Microsoft.Office.Interop.Word.Range.Text%2A> Vlastnosti.

     Následující příklad kódu lze použít v přizpůsobení na úrovni dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet27":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet27":::

     Následující příklad kódu lze použít v doplňku VSTO na úrovni aplikace. Tento kód používá aktivní dokument.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet27":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet27":::

2. Přiřaďte <xref:Microsoft.Office.Interop.Word.Range.Text%2A> vlastnost k záměně textu mezi dvěma odstavci.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet28":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet28":::

3. Výběrem jednotlivých rozsahů v příkazu zapnout a pozastavit zobrazíte výsledky v okně se zprávou.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet29":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet29":::

4. Upravte `firstRange` pomocí <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody tak, aby označení odstavce již nebylo součástí `firstRange` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet30":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet30":::

5. Nahraďte zbytek textu v prvním odstavci přiřazením nového řetězce k <xref:Microsoft.Office.Interop.Word.Range.Text%2A> Vlastnosti rozsahu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet31":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet31":::

6. Nahraďte text v `secondRange` , včetně označení odstavce.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet32":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet32":::

7. Vyberte `firstRange` a pozastavte, pokud chcete zobrazit výsledky v okně se zprávou, a pak Totéž udělejte s `secondRange` .

     Vzhledem `firstRange` k tomu, že byla předefinována tak, aby nedošlo k označení odstavce, původní formátování odstavce je zachováno. Do konce odstavce se však vložila věta `secondRange` , která odebere samostatný odstavec.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet33":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet33":::

     Původní obsah obou rozsahů byl uložen jako řetězec, takže můžete obnovit původní stav dokumentu.

8. Upravte `firstRange` tak, aby obsahovala značku odstavce pomocí <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody pro pozici s jedním znakem.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet34":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet34":::

9. Odstraňte `secondRange`. Tím se obnoví původní pozice odstavce tři.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet35":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet35":::

10. Obnovte původní text odstavce v `firstRange` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet36":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet36":::

11. Použijte <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> metodu <xref:Microsoft.Office.Interop.Word.Range> objektu pro vložení původního odstavce – dva obsah po `firstRange` a pak vyberte `firstRange` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet37":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet37":::

## <a name="document-level-customization-example"></a>Příklad přizpůsobení na úrovni dokumentu

### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>Řízení struktury odstavců při vkládání textu v přizpůsobeních na úrovni dokumentu

1. Následující příklad ukazuje metodu Complete pro přizpůsobení na úrovni dokumentu. Chcete-li použít tento kód, spusťte jej z `ThisDocument` třídy v projektu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet26":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet26":::

## <a name="vsto-add-in-example"></a>Příklad doplňku VSTO

### <a name="to-control-paragraph-structure-when-inserting-text-in-a-vsto-add-in"></a>Řízení struktury odstavců při vkládání textu do doplňku VSTO

1. Následující příklad ukazuje metodu Complete pro doplněk VSTO. Chcete-li použít tento kód, spusťte jej z `ThisAddIn` třídy v projektu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet26":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet26":::

## <a name="see-also"></a>Viz také
- [Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Postupy: sbalení oblastí nebo výběrů v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Postupy: vkládání textu do dokumentů aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Postupy: resetování oblastí v dokumentech aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Postupy: definování a výběr oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
