---
title: 'Postupy: Programová hledání a nahrazování textu v dokumentech'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], searching
- text searches, replacing text
- text searches, documents
- text [Office development in Visual Studio], searching in documents
- text [Office development in Visual Studio], text searches
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6de96133a810898fe847cce71bb2711dd7c31dd9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822394"
---
# <a name="how-to-programmatically-search-for-and-replace-text-in-documents"></a>Postupy: Programová hledání a nahrazování textu v dokumentech
  <xref:Microsoft.Office.Interop.Word.Find> Objektu je členem obou <xref:Microsoft.Office.Interop.Word.Selection> a <xref:Microsoft.Office.Interop.Word.Range> objektů a vy můžete použít buď pro hledání textu v dokumentech aplikace Microsoft Office Word. Příkaz replace je rozšířením najít příkaz.  
  
 Použít <xref:Microsoft.Office.Interop.Word.Find> objektu pro cyklický průchod dokument aplikace Microsoft Office Word a vyhledat konkrétní text, formátování a styl a použít <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> vlastnost pro nahrazení kterékoli z položek nalezen.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="use-a-selection-object"></a>Použití výběr objektu  
 Při použití <xref:Microsoft.Office.Interop.Word.Selection> objektu Hledat text, jakékoli hledání zadáte kritéria se použijí jenom pro aktuálně vybraný text. Pokud <xref:Microsoft.Office.Interop.Word.Selection> je kurzor, je prohledána dokumentu. Pokud položka není nalezen, které by odpovídalo kritériím hledání, je automaticky vybrán.  
  
 Je důležité si uvědomit, že <xref:Microsoft.Office.Interop.Word.Find> kritéria jsou kumulativní, což znamená, že kritéria jsou přidány do předchozího kritériím hledání. Vymazat formátování z předchozích hledání s použitím <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> metoda před hledání.  
  
### <a name="to-find-text-using-a-selection-object"></a>Hledat pomocí výběru objektu text  
  
1. Přiřaďte proměnné hledaný řetězec.  
  
    [!code-vb[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#68)]
    [!code-csharp[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#68)]  
  
2. Vymažte formátování z předchozích hledání.  
  
    [!code-vb[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#69)]
    [!code-csharp[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#69)]  
  
3. Spustit hledání a zobrazte okno se zprávou s výsledky.  
  
    [!code-vb[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#70)]
    [!code-csharp[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#70)]  
  
   Následující příklad ukazuje kompletní metodu.  
  
   [!code-vb[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#67)]
   [!code-csharp[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#67)]  
  
## <a name="use-a-range-object"></a>Použití objektu rozsahu  
 Použití <xref:Microsoft.Office.Interop.Word.Range> objektu umožňuje hledat text bez zobrazení něco v uživatelském rozhraní. <xref:Microsoft.Office.Interop.Word.Find> Objektu vrátí **True** li nalezen text, který by odpovídal kritériím hledání a **False** Pokud tomu tak není. Také předefinuje <xref:Microsoft.Office.Interop.Word.Range> objektu tak, aby odpovídala kritériím hledání, pokud je nalezen text.  
  
### <a name="to-find-text-using-a-range-object"></a>K vyhledání textu s použitím objektu rozsahu  
  
1. Definování <xref:Microsoft.Office.Interop.Word.Range> objekt, který se skládá z odstavec v dokumentu.  
  
    Následující příklad kódu je možné v přizpůsobení na úrovni dokumentu.  
  
    [!code-vb[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#72)]  
  
    Následující příklad kódu je možné v doplňku VSTO. Tento příklad používá aktivní dokument.  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#72)]  
  
2. Použití <xref:Microsoft.Office.Interop.Word.Range.Find%2A> vlastnost <xref:Microsoft.Office.Interop.Word.Range> objektu, nejprve zrušte všechny existující možnosti formátování a vyhledejte řetězec **nepracuju,**.  
  
    [!code-vb[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#73)]
    [!code-csharp[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#73)]  
  
3. Zobrazení výsledků hledání v okně se zprávou a vyberte <xref:Microsoft.Office.Interop.Word.Range> aby byla viditelná.  
  
    [!code-vb[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#74)]
    [!code-csharp[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#74)]  
  
    Pokud se hledání nezdaří, je vybraný odstavec; Pokud je úspěšná, zobrazí se kritériím hledání.  
  
   Následující příklad ukazuje kompletní kód pro přizpůsobení na úrovni dokumentu. Pokud chcete použít tento příklad, spusťte kód z `ThisDocument` třídu ve vašem projektu.  
  
   [!code-vb[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#71)]  
  
   Následující příklad ukazuje kompletní kód doplňku VSTO. Pokud chcete použít tento příklad, spusťte kód z `ThisAddIn` třídu ve vašem projektu.  
  
   [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#71)]  
  
## <a name="search-for-and-replace-text-in-documents"></a>Hledání a nahrazování textu v dokumentech  
 Následující kód vyhledá aktuálního výběru a nahradí všechny výskyty řetězce **nepracuju,** řetězcem **nalezeno**.  
  
### <a name="to-search-for-and-replace-text-in-documents"></a>K hledání a nahrazování textu v dokumentech  
  
1.  Následující příklad kódu pro přidání `ThisDocument` nebo `ThisAddIn` třídu ve vašem projektu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#75)]
     [!code-csharp[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#75)]  
  
     <xref:Microsoft.Office.Interop.Word.Find> Třída má <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> metoda a <xref:Microsoft.Office.Interop.Word.Replacement> třídy také mají svůj vlastní <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A> metoda. Při provádění operace hledání a nahrazování, musíte použít metodu ClearFormatting oba objekty. Když ho používáte jenom na <xref:Microsoft.Office.Interop.Word.Find> objektu, může se zobrazit neočekávané výsledky v Nahrazovací text.  
  
2.  Použití <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodu <xref:Microsoft.Office.Interop.Word.Find> a nahraďte každé nalezené položky. K určení položek k nahrazení, použijte *nahradit* parametru. Tento parametr může být jeden z následujících <xref:Microsoft.Office.Interop.Word.WdReplace> hodnoty:  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> nahradí všechny nalezené položky.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> nahradí žádná z nalezených položek.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> nahradí první nalezené položky.  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: nastavování možností hledání v aplikaci Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Postupy: procházení nalezených položek v dokumentech prostřednictvím kódu programu smyčky](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Postupy: Programová definování a výběr oblastí v dokumentech](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Postupy: obnovení výběru po hledání prostřednictvím kódu programu](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)  
  