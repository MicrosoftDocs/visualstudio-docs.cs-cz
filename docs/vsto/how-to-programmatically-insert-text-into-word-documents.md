---
title: 'Postupy: vkládání textu do dokumentů aplikace Word prostřednictvím kódu programu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a602f50e9d3c439fc450c286923341dafff1e116
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881661"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Postupy: vkládání textu do dokumentů aplikace Word prostřednictvím kódu programu
  Existují tři základní způsoby vkládání textu do dokumentů aplikace Microsoft Office Word:  
  
-   Vložte text v rozsahu.  
  
-   Nahraďte text v rozsahu novým textem.  
  
-   Použití <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> metodu <xref:Microsoft.Office.Interop.Word.Selection> objektu pro vložení textu na výběr nebo kurzor.  
  
> [!NOTE]  
>  Můžete také vložit text do ovládacích prvků obsahu a záložky. Další informace najdete v tématu [ovládací prvky obsahu](../vsto/content-controls.md) a [Bookmark – ovládací prvek](../vsto/bookmark-control.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="insert-text-in-a-range"></a>Vložit text v rozsahu  
 Použití <xref:Microsoft.Office.Interop.Word.Range.Text%2A> vlastnost <xref:Microsoft.Office.Interop.Word.Range> objekt vložení textu do dokumentu.  
  
### <a name="to-insert-text-in-a-range"></a>Chcete-li vložit text v rozsahu  
  
1.  Zadejte rozsah na začátku dokumentu a vložit text **nový Text**.  
  
     Následující příklad kódu je možné v přizpůsobení na úrovni dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#51)]  
  
     Následující příklad kódu je možné v doplňku VSTO. Tento kód používá aktivního dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#51)]  
  
2.  Vyberte <xref:Microsoft.Office.Interop.Word.Range> objektu, který se rozšířila z jeden znak a délka byl vložen text.  
  
     [!code-vb[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#52)]
     [!code-csharp[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#52)]  
  
## <a name="replace-text-in-a-range"></a>Nahradit text v rozsahu  
 Pokud zadaný rozsah obsahuje text, veškerý text v rozsahu, nahradí se vložený text.  
  
### <a name="to-replace-text-in-a-range"></a>Nahradí text v rozsahu  
  
1.  Vytvoření <xref:Microsoft.Office.Interop.Word.Range> objekt, který se skládá z prvních 12 znaků v dokumentu.  
  
     Následující příklad kódu je možné v přizpůsobení na úrovni dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#53)]  
  
     Následující příklad kódu je možné v doplňku VSTO. Tento kód používá aktivního dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#53)]  
  
2.  Nahraďte řetězcem, tyto znaky **nový Text**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#54)]
     [!code-csharp[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#54)]  
  
3.  Vyberte oblast.  
  
     [!code-vb[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#55)]
     [!code-csharp[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#55)]  
  
## <a name="insert-text-using-typetext"></a>Vložit text pomocí TypeText  
 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> Metoda vloží text ve výběru. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> jak se bude chovat odlišně v závislosti na možnostech nastavení v počítači uživatele. Kód v následujícím postupu deklaruje <xref:Microsoft.Office.Interop.Word.Selection> objektové proměnné a vypne **přepisování** možnost, pokud je zapnutý. Pokud **přepisování** volba aktivován a pak se přepíše veškerý text vedle kurzor.  
  
### <a name="to-insert-text-using-the-typetext-method"></a>Chcete-li vložit text pomocí TypeText – metoda  
  
1. Deklarace <xref:Microsoft.Office.Interop.Word.Selection> proměnné objektu.  
  
    [!code-vb[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#57)]
    [!code-csharp[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#57)]  
  
2. Vypnout **přepisování** možnost, pokud je zapnutý.  
  
    [!code-vb[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#58)]
    [!code-csharp[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#58)]  
  
3. Test ke zjištění, zda je aktuální výběr bod vložení.  
  
    Pokud se jedná, vloží kód větu pomocí <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>a potom odstavec označit pomocí <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> metody.  
  
    [!code-vb[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#59)]
    [!code-csharp[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#59)]  
  
4. Kód v **ElseIf** blokovat otestuje, jestli jedná o normální výběr. Pokud se jedná, pak další **Pokud** blokovat otestuje, jestli **ReplaceSelection** je možnost nastavená na on. Pokud se jedná, tento kód použije <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> metoda výběru Sbalit výběr kurzor na začátek vybraného bloku textu. Vložte text a značku odstavce.  
  
    [!code-vb[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#60)]
    [!code-csharp[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#60)]  
  
5. Pokud výběr není bod vložení nebo blok vybraný text a potom v kódu **Else** blok nemá žádný účinek.  
  
    [!code-vb[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#61)]
    [!code-csharp[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#61)]  
  
   Můžete také použít <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> metodu <xref:Microsoft.Office.Interop.Word.Selection> objektu, která napodobuje funkce **Backspace** kláves na klávesnici. Ale pokud jde o vkládání a manipulace s nimi text, <xref:Microsoft.Office.Interop.Word.Range> objekt nabízí větší kontrolu.  
  
   Následující příklad ukazuje kompletní kód. Pokud chcete použít tento příklad, spusťte kód z `ThisDocument` nebo `ThisAddIn` třídu ve vašem projektu.  
  
   [!code-vb[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#56)]
   [!code-csharp[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#56)]  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: formátování textu v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-format-text-in-documents.md)   
 [Postupy: Programová definování a výběr oblastí v dokumentech](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-extend-ranges-in-documents.md)  
  
  