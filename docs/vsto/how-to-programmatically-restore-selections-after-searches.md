---
title: 'Postupy: obnovení výběru po hledání prostřednictvím kódu programu'
description: Přečtěte si, jak můžete pomocí sady Visual Studio programově obnovit výběry po hledání v dokumentu Microsoft Wordu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 493f736ce899a0d90332418ca37a5b2825dd2d7b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897504"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Postupy: obnovení výběru po hledání prostřednictvím kódu programu
  Pokud vyhledáte a nahradíte text v dokumentu, možná budete chtít obnovit původní výběr uživatele po dokončení hledání.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Kód v ukázkové proceduře využívá dva <xref:Microsoft.Office.Interop.Word.Range> objekty. Jeden ukládá aktuální <xref:Microsoft.Office.Interop.Word.Selection> a jeden nastaví celý dokument, který se má použít jako rozsah hledání.

## <a name="to-restore-the-users-original-selection-after-a-search"></a>Obnovení původního výběru uživatele po hledání

1. Vytvořte <xref:Microsoft.Office.Interop.Word.Range> objekty pro dokument a aktuální výběr.

    [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
    [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]

2. Proveďte operaci hledání a nahrazení.

    [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
    [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]

3. Vyberte počáteční rozsah pro obnovení původního výběru uživatele.

    [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
    [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]

   Následující příklad ukazuje metodu Complete.

## <a name="example"></a>Příklad
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]

## <a name="see-also"></a>Viz také
- [Postupy: hledání a nahrazování textu v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Postupy: nastavování možností hledání v aplikaci Word prostřednictvím kódu programu](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Postupy: procházení nalezených položek v dokumentech prostřednictvím kódu programu](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
