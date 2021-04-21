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
ms.openlocfilehash: 8802cc34555fcb695c5554209255cb8fd9f154c2
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825300"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Postupy: zavírání dokumentů aplikace Visio prostřednictvím kódu programu
  Aktivní systém Microsoft Office dokument Visia můžete zavřít pomocí `Microsoft.Office.Interop.Visio.Document.Close` metody.

 Podrobnosti o této metodě najdete v referenční dokumentaci k jazyku VBA pro [Microsoft.Office.Interop.Visio.Document. Close](/office/vba/api/Visio.Document.Close) – metoda

## <a name="close-the-active-document"></a>Zavřít aktivní dokument

### <a name="to-close-the-active-document"></a>Zavření aktivního dokumentu

- Voláním `Microsoft.Office.Interop.Visio.Document.Close` metody zavřete aktivní dokument.

     Chcete-li použít následující příklad kódu, spusťte jej ve `ThisAddIn` třídě v projektu doplňku VSTO pro Visio.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet7":::

## <a name="see-also"></a>Viz také
- [Řešení aplikace Visio](../vsto/visio-solutions.md)
- [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)
- [Postupy: vytváření nových dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Postupy: otevírání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-open-visio-documents.md)
- [Postupy: ukládání dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-save-visio-documents.md)
- [Postupy: tisk dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-print-visio-documents.md)
