---
title: 'Postupy: zobrazování komentářů v listech prostřednictvím kódu programu'
description: Přečtěte si, jak můžete programově zobrazovat a skrývat komentáře v listu Microsoft Excelu na úrovni dokumentu nebo na úrovni aplikace.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: af327a6756189c73f80f624205451274abf19264
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828667"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Postupy: zobrazování komentářů v listech prostřednictvím kódu programu
  Komentáře můžete programově zobrazovat a skrývat v systém Microsoft Office listech aplikace Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Zobrazení všech komentářů na listu v přizpůsobení na úrovni dokumentu

1. Nastavte <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> vlastnost na **hodnotu true** , pokud chcete zobrazit komentáře. v opačném případě **false**. Tento kód musí být umístěn ve třídě listu, nikoli ve `ThisWorkbook` třídě.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet31":::

## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Zobrazení všech komentářů na listu v doplňku VSTO na úrovni aplikace

1. Nastavte <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> vlastnost na **hodnotu true** , pokud chcete zobrazit komentáře. v opačném případě **false**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet21":::

## <a name="see-also"></a>Viz také
- [Práce s listy](../vsto/working-with-worksheets.md)
- [Postupy: přidávání a odstraňování komentářů v listech prostřednictvím kódu programu](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
