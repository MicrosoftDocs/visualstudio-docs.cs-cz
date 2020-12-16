---
title: Ovládací prvek XmlMappedRange –
description: Přečtěte si, že ovládací prvek XmlMappedRange – je rozsah, který je vytvořen pouze v případě, že je prvek neopakujícího se schématu mapován na buňku v aplikaci Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f3b3fd140787d44cdd8364ce77d5292dfcd83f54
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525890"
---
# <a name="xmlmappedrange-control"></a>Ovládací prvek XmlMappedRange –
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Ovládací prvek je rozsah, který je vytvořen pouze v případě, že je prvek neopakujícího se schématu mapován na buňku v aplikaci systém Microsoft Office Excel. Například, pokud se `maxOccurs` atribut elementu schématu rovná 1. Poté, co aplikace Visual Studio vytvoří rozsah mapovaného kódu XML, lze naprogramovat přímo bez nutnosti procházení objektového modelu aplikace Excel. Ovládací prvek lze odstranit pouze <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> v aplikaci Excel, pokud je odebráno mapování elementu.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>Vázání dat k ovládacímu prvku
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Ovládací prvek podporuje vazbu s jedním datovým polem (jednoduchou datovou vazbu). <xref:Microsoft.Office.Tools.Excel.ListObject>Ovládací prvek může podporovat složitou datovou vazbu a je automaticky vytvořen při mapování opakujícího se elementu schématu na buňku. Další informace naleznete v tématu [ListObject Control](../vsto/listobject-control.md).

 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Ovládací prvek je svázán se zdrojem dat pomocí <xref:System.Windows.Forms.Control.DataBindings%2A> Vlastnosti. Když <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> se přidá do buňky listu, sada Visual Studio automaticky vygeneruje datovou sadu z dat v mapovaných buňkách a naváže ovládací prvek na tuto datovou sadu. Výchozí vlastnost datové vazby <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> je <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A> .

 Pokud jsou data v vázané datové sadě aktualizována prostřednictvím libovolného mechanismu, <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> ovládací prvek tyto změny odráží.

## <a name="formatting"></a>Formátování
 Můžete použít stejné formátování pro <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> ovládací prvek, který můžete použít na <xref:Microsoft.Office.Interop.Excel.Range> . To zahrnuje ohraničení, písma, formát čísel a styly.

## <a name="events"></a>Události
 K dispozici jsou události pro <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> ovládací prvek:

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>Viz také
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Postupy: Přidání ovládacích prvků XmlMappedRange – do listů](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Postupy: mapování schémat na listy v rámci sady Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
