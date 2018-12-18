---
title: 'Postupy: Programová vyloučení značek odstavů při vytváření oblastí'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], excluding paragraphs
- ranges, excluding paragraph marks in Word
- documents [Office development in Visual Studio], paragraph marks
- paragraphs, controlling structure
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 11015f0afb59f0d1aa71bad4adbc48b6c99887a2
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675675"
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Postupy: Programová vyloučení značek odstavů při vytváření oblastí
  Vždy, když vytvoříte <xref:Microsoft.Office.Interop.Word.Range> objektu podle odstavce, všechny netisknutelné znaky, jako je například značek odstavů, jsou zahrnuté v rozsahu. Můžete vložit text odstavce zdroje do cílového odstavce. Pokud nechcete cílového odstavce rozdělit na samostatné odstavce, pak musíte nejdřív odebrat značku odstavce od zdroje odstavce. Navíc protože informace o formátování odstavce se uloží v rámci značku odstavce, pravděpodobně chcete zahrnout to při vložení do existujícího odstavce rozsahu.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Následující postup příklad deklaruje dvě proměnné řetězce, načte obsah prvního a druhého odstavců v aktivním dokumentu a potom vymění jejich obsah. V příkladu uvidíte, odebrání značku odstavce rozsahu pomocí <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody a vložit text odstavce.  
  
## <a name="to-control-paragraph-structure-when-inserting-text"></a>Řízení struktury odstavec při vkládání textu  
  
1.  Vytvořte dvě proměnné rozsahu pro první a druhý odstavec a načíst pomocí jejich obsah <xref:Microsoft.Office.Interop.Word.Range.Text%2A> vlastnost.  
  
     Následující příklad kódu je možné v přizpůsobení na úrovni dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#27)]  
  
     Následující příklad kódu je možné v doplňku VSTO úrovni aplikace. Tento kód používá aktivního dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#27)]  
  
2.  Přiřazení <xref:Microsoft.Office.Interop.Word.Range.Text%2A> vlastnost prohození text mezi dva odstavce.  
  
     [!code-vb[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#28)]
     [!code-csharp[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#28)]  
  
3.  Pak vyberte každého rozsahu a pozastavit a zobrazte výsledky v okně se zprávou.  
  
     [!code-vb[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#29)]
     [!code-csharp[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#29)]  
  
4.  Upravit `firstRange` pomocí <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metodu tak, aby značku odstavce už nejsou součástí `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#30)]
     [!code-csharp[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#30)]  
  
5.  Nahradit zbývající část textu v prvním odstavci nový řetězec k přiřazení <xref:Microsoft.Office.Interop.Word.Range.Text%2A> vlastnost rozsahu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#31)]
     [!code-csharp[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#31)]  
  
6.  Nahraďte text v `secondRange`, včetně značku odstavce.  
  
     [!code-vb[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#32)]
     [!code-csharp[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#32)]  
  
7.  Vyberte `firstRange` a pozastavit a zobrazte výsledky v okně se zprávou a potom postupujte stejným způsobem pracovat s `secondRange`.  
  
     Protože `firstRange` byl předefinovat vyloučit značku odstavce, je zachováno původní formátování odstavce. Ale věty byl vložen nad odstavce v `secondRange`, odebrání samostatných odstavce.  
  
     [!code-vb[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#33)]
     [!code-csharp[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#33)]  
  
     Původní obsah oba rozsahy byly uloženy jako řetězce, dokument mohli obnovit do původního stavu.  
  
8.  Přizpůsobit `firstRange` zahrnout konce odstavce pomocí <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metodu jedním znakem.  
  
     [!code-vb[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#34)]
     [!code-csharp[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#34)]  
  
9. Odstraňte `secondRange`. Tím se obnoví odstavec tři na původní pozici.  
  
     [!code-vb[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#35)]
     [!code-csharp[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#35)]  
  
10. Obnovit původní text odstavce v `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#36)]
     [!code-csharp[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#36)]  
  
11. Použití <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> metodu <xref:Microsoft.Office.Interop.Word.Range> objektu, který chcete vložit původní obsah dva odstavce po `firstRange`a pak vyberte `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#37)]
     [!code-csharp[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#37)]  
  
## <a name="document-level-customization-example"></a>Příklad přizpůsobení na úrovni dokumentu  
  
### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>Řízení struktury odstavec při vkládání textu v přizpůsobeních na úrovni dokumentu  
  
1.  Následující příklad ukazuje kompletní metodu pro přizpůsobení na úrovni dokumentu. Chcete-li tento kód použít, spusťte z `ThisDocument` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#26)]  
  
## <a name="vsto-add-in-example"></a>Příklad doplňku VSTO  
  
### <a name="to-control-paragraph-structure-when-inserting-text-in-a-vsto-add-in"></a>Řízení struktury odstavec při vkládání textu v doplňku VSTO  
  
1.  Následující příklad ukazuje kompletní metodu pro doplňku VSTO. Chcete-li tento kód použít, spusťte z `ThisAddIn` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#26)]  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Postupy: oblastí nebo výběrů v dokumentech prostřednictvím kódu programu sbalit](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Postupy: vkládání textu do dokumentů aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Postupy: Programová resetování oblastí v dokumentech aplikace Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Postupy: Programová definování a výběr oblastí v dokumentech](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  