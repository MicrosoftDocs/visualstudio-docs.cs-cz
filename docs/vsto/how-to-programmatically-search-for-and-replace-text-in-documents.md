---
title: Hledání a nahrazování textu v dokumentech prostřednictvím kódu programu
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově vyhledat a nahradit text v dokumentu Microsoft Wordu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], searching
- text searches, replacing text
- text searches, documents
- text [Office development in Visual Studio], searching in documents
- text [Office development in Visual Studio], text searches
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0f2fc5bbfabbe2672ae59c55734a5cf57fc84318
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825157"
---
# <a name="how-to-programmatically-search-for-and-replace-text-in-documents"></a>Postupy: hledání a nahrazování textu v dokumentech prostřednictvím kódu programu
  <xref:Microsoft.Office.Interop.Word.Find>Objekt je členem <xref:Microsoft.Office.Interop.Word.Selection> objektů i a <xref:Microsoft.Office.Interop.Word.Range> a můžete použít jeden z nich k hledání textu v systém Microsoft Office dokumentů aplikace Word. Příkaz replace je rozšíření příkazu find.

 Pomocí <xref:Microsoft.Office.Interop.Word.Find> objektu Projděte systém Microsoft Office dokumentu aplikace Word a vyhledejte konkrétní text, formátování nebo styl a pomocí <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> Vlastnosti nahraďte libovolnou nalezenou položku.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-a-selection-object"></a>Použití objektu výběru
 Když pomocí <xref:Microsoft.Office.Interop.Word.Selection> objektu vyhledáte text, všechna zadaná kritéria hledání se použijí jenom proti aktuálně vybranému textu. Pokud <xref:Microsoft.Office.Interop.Word.Selection> je místo vložení, je prohledáván dokument. Když se najde položka, která odpovídá kritériím hledání, je automaticky vybraná.

 Je důležité si uvědomit, že <xref:Microsoft.Office.Interop.Word.Find> kritéria jsou kumulativní, což znamená, že jsou do předchozích kritérií hledání přidána kritéria. Vymažte formátování z předchozích hledání pomocí <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> metody před hledáním.

### <a name="to-find-text-using-a-selection-object"></a>Vyhledání textu pomocí objektu výběru

1. Přiřaďte k proměnné hledaný řetězec.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet68":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet68":::

2. Vymažte formátování z předchozích hledání.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet69":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet69":::

3. Spusťte hledání a zobrazí se okno se zprávou s výsledky.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet70":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet70":::

   Následující příklad ukazuje metodu Complete.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet67":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet67":::

## <a name="use-a-range-object"></a>Použití objektu Range
 Pomocí <xref:Microsoft.Office.Interop.Word.Range> objektu můžete hledat text bez zobrazení cokoli v uživatelském rozhraní. <xref:Microsoft.Office.Interop.Word.Find>Objekt vrátí **hodnotu true** , pokud je nalezen text, který odpovídá kritériím hledání, a **hodnotu false** , pokud tomu tak není. Předefinuje také <xref:Microsoft.Office.Interop.Word.Range> objekt tak, aby odpovídal kritériím hledání, pokud je nalezen text.

### <a name="to-find-text-using-a-range-object"></a>Vyhledání textu pomocí objektu Range

1. Definujte <xref:Microsoft.Office.Interop.Word.Range> objekt, který se skládá z druhého odstavce v dokumentu.

    Následující příklad kódu lze použít v přizpůsobení na úrovni dokumentu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet72":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet72":::

    V doplňku VSTO se dá použít následující příklad kódu. Tento příklad používá aktivní dokument.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet72":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet72":::

2. Pomocí <xref:Microsoft.Office.Interop.Word.Range.Find%2A> vlastnosti <xref:Microsoft.Office.Interop.Word.Range> objektu nejprve vymažte všechny existující možnosti formátování a vyhledejte řetězec **Najít**.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet73":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet73":::

3. Zobrazit výsledky hledání v okně se zprávou a vybrat <xref:Microsoft.Office.Interop.Word.Range> ho, aby byl viditelný.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet74":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet74":::

    Pokud vyhledávání neproběhne úspěšně, je vybrán druhý odstavec; v případě úspěchu se zobrazí kritéria hledání.

   Následující příklad ukazuje kompletní kód pro přizpůsobení na úrovni dokumentu. Chcete-li použít tento příklad, spusťte kód z `ThisDocument` třídy v projektu.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet71":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet71":::

   Následující příklad ukazuje úplný kód doplňku VSTO. Chcete-li použít tento příklad, spusťte kód z `ThisAddIn` třídy v projektu.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet71":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet71":::

## <a name="search-for-and-replace-text-in-documents"></a>Hledání a nahrazování textu v dokumentech
 Následující kód vyhledá aktuální výběr a nahradí všechny výskyty řetězce **nalezené** **řetězcem** .

### <a name="to-search-for-and-replace-text-in-documents"></a>Hledání a nahrazování textu v dokumentech

1. Do `ThisDocument` třídy nebo v projektu přidejte následující vzorový kód `ThisAddIn` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet75":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet75":::

     <xref:Microsoft.Office.Interop.Word.Find>Třída má <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> metodu a <xref:Microsoft.Office.Interop.Word.Replacement> Třída má také svou vlastní <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A> metodu. Při provádění operací Find-and-nahrazování je nutné použít metodu ClearFormatting obou objektů. Použijete-li jej pouze na <xref:Microsoft.Office.Interop.Word.Find> objekt, může se stát, že se nepředpokládá výsledek nahrazujícího textu.

2. Použijte <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodu <xref:Microsoft.Office.Interop.Word.Find> objektu k nahrazení každé nalezené položky. Chcete-li určit, které položky mají být nahrazeny, použijte parametr *Replace* . Tento parametr může být jedna z následujících <xref:Microsoft.Office.Interop.Word.WdReplace> hodnot:

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> nahradí všechny nalezené položky.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> nahradí žádné nalezené položky.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> nahradí první nalezenou položku.

## <a name="see-also"></a>Viz také
- [Postupy: nastavování možností hledání v aplikaci Word prostřednictvím kódu programu](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Postupy: procházení nalezených položek v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Postupy: definování a výběr oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Postupy: obnovení výběru po hledání prostřednictvím kódu programu](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
