---
title: 'Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu'
description: Přečtěte si, jak programově rozšiřuje rozsahy počátečních a koncových bodů v dokumentu aplikace Microsoft Word na úrovni dokumentu nebo na úrovni aplikace.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b3236a6303f25d8d24fe77c434a60d31aa572aa7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885440"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>Postupy: rozšiřování oblastí v dokumentech prostřednictvím kódu programu
  Po definování <xref:Microsoft.Office.Interop.Word.Range> objektu v systém Microsoft Office dokumentu aplikace Word změníte jeho počáteční a koncové body pomocí <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metod a. <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A>Metody a <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> přijímají stejné dva argumenty, *jednotky* a *počet*. Argument *Count* je počet jednotek, které se mají přesunout, a argument *Unit* může být jedna z následujících <xref:Microsoft.Office.Interop.Word.WdUnits> hodnot:

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  Následující příklad definuje rozsah sedmi znaků. Pak přesune počáteční pozici rozsahu sedm znaků po původní počáteční pozici. Vzhledem k tomu, že koncová pozice rozsahu byla zároveň sedm znaků za počáteční pozicí, výsledkem je rozsah, který obsahuje nula znaků. Kód pak přesune koncovou pozici sedm znaků za aktuální koncovou pozicí.

## <a name="to-extend-a-range"></a>Postup rozšiřování rozsahu

1. Definujte rozsah znaků. Další informace najdete v tématu [Postup: definování a výběr oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).

     Následující příklad kódu lze použít v přizpůsobení na úrovni dokumentu.

     [!code-vb[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#39)]

     V doplňku VSTO se dá použít následující příklad kódu. Tento příklad používá aktivní dokument.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#39)]

2. Použijte <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> metodu <xref:Microsoft.Office.Interop.Word.Range> objektu pro přesunutí počáteční pozice rozsahu.

     [!code-vb[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#40)]
     [!code-csharp[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#40)]

3. Použijte <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metodu <xref:Microsoft.Office.Interop.Word.Range> objektu pro přesunutí koncové pozice rozsahu.

     [!code-vb[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#41)]
     [!code-csharp[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#41)]

## <a name="document-level-customization-code"></a>Kód přizpůsobení na úrovni dokumentu

### <a name="to-extend-a-range-in-a-document-level-customization"></a>Postup rozšiřování rozsahu v přizpůsobení na úrovni dokumentu

1. Následující příklad ukazuje kompletní kód pro přizpůsobení na úrovni dokumentu. Chcete-li použít tento kód, spusťte jej z `ThisDocument` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#38)]

## <a name="vsto-add-in-code"></a>Kód doplňku VSTO

### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>Postup rozšiřování rozsahu doplňku VSTO na úrovni aplikace

1. Následující příklad ukazuje úplný kód doplňku VSTO. Chcete-li použít tento kód, spusťte jej z `ThisAddIn` třídy v projektu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#38)]

## <a name="see-also"></a>Viz také
- [Postupy: resetování oblastí v dokumentech aplikace Word prostřednictvím kódu programu](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Postupy: sbalení oblastí nebo výběrů v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Postupy: definování a výběr oblastí v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Postupy: načítání počátečních a koncových znaků v oblastech prostřednictvím kódu programu](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Postupy: vyloučení značek odstavců při vytváření rozsahů prostřednictvím kódu programu](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
