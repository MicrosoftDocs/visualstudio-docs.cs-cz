---
title: Kopírování a vkládání obrazců v dokumentu Visia prostřednictvím kódu programu
description: Přečtěte si, jak můžete programově kopírovat obrazce na jedné stránce dokumentu a vložit je do nové stránky ve stejném dokumentu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 90a065ec98da440af6e52a191e11f4371575c2d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964222"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Postupy: kopírování a vkládání tvarů v dokumentu aplikace Visio prostřednictvím kódu programu
  Můžete programově zkopírovat obrazce na jednu stránku dokumentu a vložit je do nové stránky do stejného dokumentu. Můžete zvolit jejich vložení do výchozího umístění (uprostřed aktivního okna) nebo do stejného umístění souřadnic, jako kdyby byla na původní stránce.

## <a name="copy-and-paste-shapes"></a>Kopírování a vkládání obrazců
 Podrobnosti o objektovém modelu naleznete v referenční dokumentaci k jazyku VBA pro [Microsoft. Office. Interop. Visio. Shape. DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft. Office. Interop. Visio. Shape. DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft. Office. Interop. Visio. Shape. Copy](/office/vba/api/Visio.Shape.Copy)a [Microsoft. Office. Interop. Visio. Shape. past](/office/vba/api/Visio.Shape.Paste) a Microsoft. [Office. Interop. Visio. VisCutCopyPasteCodes. visCopyPasteNormal](/office/vba/api/Visio.viscutcopypastecodes) .

### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Kopírování tvarů do středu jiné stránky

- Následující příklad ukazuje, jak zkopírovat tvary z první stránky a vložit je do středu druhé stránky.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]

## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Kopírovat a vložit obrazce se stejnými umístěními
 Podrobnosti o objektovém modelu naleznete v referenční dokumentaci k jazyku VBA pro [Microsoft. Office. Interop. Visio. Shape. DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft. Office. Interop. Visio. Shape. DrawOval](/office/vba/api/Visio.Shape.DrawOval), [Microsoft. Office. Interop. Visio. Shape. Copy](/office/vba/api/Visio.Shape.Copy)a [Microsoft. Office. Interop. Visio. Shape. past](/office/vba/api/Visio.Shape.Paste) a Microsoft. [Office. Interop. Visio. VisCutCopyPasteCodes. visCopyPasteNoTranslate](/office/vba/api/Visio.viscutcopypastecodes) .

 Pokud potřebujete řídit formát vložených informací a (volitelně) vytvořit odkaz na zdrojový soubor (například systém Microsoft Office wordový dokument), použijte metodu PasteSpecial.

### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Kopírování obrazců a umístění obrazců na jinou stránku

- Následující příklad ukazuje, jak zkopírovat obrazce z první stránky a vložit je do druhé stránky s jejich původními umístěními souřadnic.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>Viz také
- [Řešení aplikace Visio](../vsto/visio-solutions.md)
- [Přehled modelu objektů aplikace Visio](../vsto/visio-object-model-overview.md)
- [Práce s obrazci aplikace Visio](../vsto/working-with-visio-shapes.md)
- [Postupy: přidávání obrazců do dokumentů aplikace Visio prostřednictvím kódu programu](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)
