---
title: 'Postupy: Přidání ovládacích prvků XmlMappedRange – do listů'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1d69e705e8f537ba3636422ad6883a7633e03322
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544882"
---
# <a name="how-to-add-xmlmappedrange-controls-to-worksheets"></a>Postupy: Přidání ovládacích prvků XmlMappedRange – do listů
  Při mapování elementu XML na buňku v aplikaci systém Microsoft Office Excel, Visual Studio automaticky přidá <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> ovládací prvek do listu.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Ovládací prvek není k dispozici v okně **Sada nástrojů** nebo **zdroje dat** . Navíc nemůžete vytvářet <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> ovládací prvky programově.

## <a name="to-add-an-xmlmappedrange-control-to-a-worksheet"></a>Přidání ovládacího prvku XmlMappedRange – do listu

1. Otevřete excelový sešit v návrháři sady Visual Studio.

2. Otevřete list, do kterého chcete ovládací prvek přidat.

3. Na kartě **vývojář** klikněte na **zdroj**.

    > [!NOTE]
    > Pokud karta **vývojář** na pásu karet není zobrazená, musíte ji povolit. Další informace najdete v tématu [Postup: zobrazení karty Vývojář na pásu karet](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

     Zobrazí se podokno **zdrojová úloha XML** .

4. V podokně úloh **zdroj XML** klikněte na **mapování XML**.

5. V dialogovém okně **mapy XML** klikněte na tlačítko **Přidat**.

     Zobrazí se dialogové okno **zdroj XML** .

6. V dialogovém okně **zdroj XML** vyberte schéma XML a klikněte na **otevřít**.

     Schéma je přidáno do dialogového okna **mapy XML** .

7. V dialogovém okně **mapy XML** klikněte na tlačítko **OK**.

8. Přetáhněte prvek z podokna úloh **zdroj XML** do buňky na listu.

     <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>Je vytvořen a přidán do projektu.

    > [!NOTE]
    > Pokud přetáhnete nadřazený element z podokna úloh **zdroj XML** , <xref:Microsoft.Office.Tools.Excel.ListObject> bude vytvořen ovládací prvek.

## <a name="see-also"></a>Viz také:
- [Ovládací prvek XmlMappedRange –](../vsto/xmlmappedrange-control.md)
- [Automatizace Excelu pomocí rozšířených objektů](../vsto/automating-excel-by-using-extended-objects.md)
- [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md)
- [Programové omezení hostitelských položek a hostitelských ovládacích prvků](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Postupy: mapování schémat na listy v rámci sady Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
