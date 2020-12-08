---
title: 'Postupy: zavírání dokumentů prostřednictvím kódu programu'
description: Přečtěte si, jak můžete zavřít aktivní dokument, nebo můžete zadat systém Microsoft Office dokument aplikace Word, který chcete zavřít.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing
- Word [Office development in Visual Studio], closing documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52914e60d0519eb923e5c4f327d58afdfa858c1c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848258"
---
# <a name="how-to-programmatically-close-documents"></a>Postupy: zavírání dokumentů prostřednictvím kódu programu
  Můžete zavřít aktivní dokument nebo můžete zadat dokument, který chcete zavřít.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="close-the-active-document"></a>Zavřít aktivní dokument
 Existují dva postupy pro zavření aktivního dokumentu: jeden pro přizpůsobení na úrovni dokumentu a jeden pro doplňky VSTO.

### <a name="to-close-the-active-document-in-a-document-level-customization"></a>Zavření aktivního dokumentu v přizpůsobení na úrovni dokumentu

1. <xref:Microsoft.Office.Tools.Word.Document.Close%2A> `ThisDocument` Chcete-li zavřít dokument přidružený k přizpůsobení, zavolejte metodu třídy v projektu. Chcete-li použít následující příklad kódu, spusťte jej z `ThisDocument` třídy.

    > [!NOTE]
    > Tento příklad předá <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> hodnotu parametru *SaveChanges* pro zavření bez uložení změn nebo zobrazení výzvy uživateli.

     [!code-vb[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#3)]

### <a name="to-close-the-active-document-in-a-vsto-add-in"></a>Zavření aktivního dokumentu v doplňku VSTO

1. Voláním <xref:Microsoft.Office.Interop.Word._Document.Close%2A> metody <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> vlastnosti zavřete aktivní dokument. Chcete-li použít následující příklad kódu, spusťte jej z `ThisAddIn` třídy v projektu.

    > [!NOTE]
    > Tento příklad předá <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> hodnotu parametru *SaveChanges* pro zavření bez uložení změn nebo zobrazení výzvy uživateli.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#3)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#3)]

## <a name="close-a-document-that-you-specify-by-name"></a>Zavřít dokument, který určíte podle názvu
 Způsob, jakým můžete zavřít dokument, který určíte podle názvu, je stejný pro doplňky VSTO a přizpůsobení na úrovni dokumentu.

### <a name="to-close-a-document-that-you-specify-by-name"></a>Zavření dokumentu, který určíte podle názvu

1. Zadejte název dokumentu jako argument <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> kolekce a pak zavolejte <xref:Microsoft.Office.Interop.Word._Document.Close%2A> metodu. Následující příklad kódu předpokládá, že dokument s názvem **NewDocument** je otevřen v aplikaci Word.

    > [!NOTE]
    > Tento příklad předá <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> hodnotu parametru *SaveChanges* pro zavření bez uložení změn nebo zobrazení výzvy uživateli.

     [!code-vb[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreWordAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#4)]

## <a name="see-also"></a>Viz také
- [Postupy: otevírání existujících dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-open-existing-documents.md)
- [Postupy: ukládání dokumentů prostřednictvím kódu programu](../vsto/how-to-programmatically-save-documents.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Volitelné parametry v řešeních pro systém Office](../vsto/optional-parameters-in-office-solutions.md)
