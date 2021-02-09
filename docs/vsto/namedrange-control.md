---
title: NamedRange – ovládací prvek
description: Přečtěte si, jak je ovládací prvek NamedRange rozsah, který má jedinečný název, zpřístupňuje události a může být svázán s daty.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Range
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, named
- NamedRange control, events
- NamedRange control, data binding
- NamedRange control
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 74eb3467c4cfbba5a2cb411a1f0ad439b1a7620b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926622"
---
# <a name="namedrange-control"></a>NamedRange – ovládací prvek
  <xref:Microsoft.Office.Tools.Excel.NamedRange>Ovládací prvek je rozsah, který má jedinečný název, zpřístupňuje události a může být svázán s daty. Další informace najdete v tématu [Přehled modelu objektů aplikace Excel](../vsto/excel-object-model-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Vytvoření ovládacího prvku
 <xref:Microsoft.Office.Tools.Excel.NamedRange>Ovládací prvky můžete přidat do listu aplikace systém Microsoft Office Excel v době návrhu nebo v době běhu v projektech na úrovni dokumentu.

 <xref:Microsoft.Office.Tools.Excel.NamedRange>V doplňku VSTO můžete do listu přidat ovládací prvky v době běhu. Další informace najdete v tématu [Postup: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

> [!NOTE]
> Ve výchozím nastavení se dynamicky vytvořené pojmenované rozsahy neukládají v listu jako hostitelské ovládací prvky při zavření listu. Další informace najdete v tématu [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md).

 <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvky mohou obsahovat pouze rozsahy na konkrétních listech. <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvky nemohou mít relativní názvy, které se vztahují na všechny listy a nesmí se skládat z rozsahů, které jsou v sešitu rozloženy na dva nebo více listů (3D oblasti).

## <a name="bind-data-to-the-control"></a>Vázání dat k ovládacímu prvku
 Pojmenovaný rozsah by byl dobrým kandidátem na složitou datovou vazbu, protože může mít mnoho buněk. Rozsah je však pouze kolekcí buněk, které nelze snadno namapovat na konkrétní sloupec z datové sady. Proto <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvky podporují pouze jednoduché datové vazby. <xref:Microsoft.Office.Tools.Excel.ListObject>Ovládací prvek lze použít pro složitou datovou vazbu. Další informace naleznete v tématu [ListObject Control](../vsto/listobject-control.md).

 <xref:Microsoft.Office.Tools.Excel.NamedRange>Ovládací prvek může být svázán se zdrojem dat pomocí <xref:System.Windows.Forms.Control.DataBindings%2A> vlastností. Výchozí vlastnost datové vazby <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládacího prvku je <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> .

 Pokud jsou data v vázané datové sadě aktualizována prostřednictvím libovolného mechanismu, <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek tyto změny odráží.

## <a name="formatting"></a>Formátování
 Formátování, které lze použít na objekt, <xref:Microsoft.Office.Interop.Excel.Range> lze použít pro <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek. To zahrnuje ohraničení, písma, formáty čísel a styly.

## <a name="rename-the-control"></a>Přejmenování ovládacího prvku
 Když přidáte <xref:Microsoft.Office.Tools.Excel.NamedRange> ovládací prvek do listu ze **sady nástrojů, sada** Visual Studio automaticky vygeneruje název ovládacího prvku. Název můžete změnit v okně **vlastnosti** .

## <a name="events"></a>Události
 Pro ovládací prvek jsou k dispozici následující události <xref:Microsoft.Office.Tools.Excel.NamedRange> :

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>

## <a name="see-also"></a>Viz také
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Ukázky a návody pro vývoj pro Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Rozšiřování dokumentů aplikace Word a excelových sešitů v doplňcích VSTO za běhu](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Ovládací prvky v dokumentech Office](../vsto/controls-on-office-documents.md)
- [Přidání ovládacích prvků do dokumentů Office v době běhu](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Postupy: Přidání ovládacích prvků NamedRange do listů](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Postupy: Změna velikosti ovládacích prvků NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Návod: program na události ovládacího prvku NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
