---
title: Použití ovládacích prvků model Windows Forms v listech aplikace Excel
description: Naučte se, jak můžete přidat ovládací prvky model Windows Forms do sešitů aplikace Microsoft Excel stejným způsobem jako ovládací prvky pro model Windows Forms.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f8c79e487e116741c393cef5a6f65b30cc4a8cfb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838214"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Použití ovládacích prvků model Windows Forms v listech aplikace Excel
  Do systém Microsoft Office excelových sešitů můžete přidat ovládací prvky model Windows Forms stejným způsobem, jako přidáte ovládací prvky do model Windows Forms. Obecné informace o práci s ovládacími prvky v dokumentech naleznete v tématu [model Windows Forms Controls on Office documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="control-considerations-for-excel"></a>Řízení požadavků pro aplikaci Excel
 K dispozici je několik důležitých informací, které jsou specifické pro aplikaci Excel.

### <a name="match-control-size-to-cell-size"></a>Přizpůsobit velikost ovládacího prvku na velikost buňky
 Můžete nastavit, aby se při změně velikosti nadřazené buňky automaticky změnila velikost ovládacího prvku. Další informace najdete v tématu [Postup: Změna velikosti ovládacích prvků v buňkách listu](../vsto/how-to-resize-controls-within-worksheet-cells.md).

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Přidat komponenty, které jsou sdíleny všemi listy
 Můžete přidat součásti, které chcete sdílet mezi všemi listy, například a <xref:System.Data.DataSet> , do návrháře sešitu místo do listů. Komponenta se zobrazí v zásobníku součásti.

### <a name="formula-for-embedding-controls"></a>Vzorec pro vkládání ovládacích prvků
 Když vyberete ovládací prvek v aplikaci Excel, zobrazí se na **řádku vzorců** **= vložení ("WinForms. Control. host", ")** . Tento text je nezbytný a neměl by být odstraněn.

## <a name="see-also"></a>Viz také
- [Postupy: Změna velikosti ovládacích prvků v buňkách listu](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Postupy: skrytí ovládacích prvků na listech při tisku](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Návod: Změna formátování listů pomocí ovládacích prvků CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Návod: zobrazení textu v textovém poli na listu s použitím tlačítka](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Návod: aktualizace grafu na listu pomocí přepínačů](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
