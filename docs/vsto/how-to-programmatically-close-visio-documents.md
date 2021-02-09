---
title: 'Postupy: zavírání dokumentů aplikace Visio prostřednictvím kódu programu'
description: Zjistěte, jak můžete zavřít aktivní systém Microsoft Office dokument Visia pomocí Microsoft.Office.Interop.Visio.Document. Close – metoda
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c1592bd500103a2db42934ab8f81392a5f1fa0d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903681"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Postupy: zavírání dokumentů aplikace Visio prostřednictvím kódu programu
  Aktivní systém Microsoft Office dokument Visia můžete zavřít pomocí `Microsoft.Office.Interop.Visio.Document.Close` metody.

 Podrobnosti o této metodě najdete v referenční dokumentaci k jazyku VBA pro [Microsoft.Office.Interop.Visio.Document. Close](/office/vba/api/Visio.Document.Close) – metoda

## <a name="close-the-active-document"></a>Zavřít aktivní dokument

### <a name="to-close-the-active-document"></a>Zavření aktivního dokumentu

- Voláním `Microsoft.Office.Interop.Visio.Document.Close` metody zavřete aktivní dokument.

     Chcete-li použít následující příklad kódu, spusťte jej ve `ThisAddIn` třídě v projektu doplňku VSTO pro Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>Viz také
- [Řešení aplikace Visio](../vsto/visio-solutions.md)
- [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)
- [Postupy: vytváření nových dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Postupy: otevírání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-open-visio-documents.md)
- [Postupy: ukládání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-save-visio-documents.md)
- [Postupy: tisk dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-print-visio-documents.md)
