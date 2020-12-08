---
title: 'Postupy: naplnění listů daty z databáze'
description: Naučte se, jak můžete použít data z objektu v řešení a jak můžete použít ovládací prvky model Windows Forms k zobrazení dat v listu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4252eac32540ac2d0b6e763b5b6e9cf0e2ac7055
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846438"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Postupy: naplnění listů daty z databáze

K datům v projektech Office na úrovni dokumentu můžete přistupovat stejným způsobem jako při přístupu k datům v model Windows Forms projektech. Můžete použít stejné nástroje a kód k přenesení dat do vašeho řešení a můžete dokonce použít ovládací prvky model Windows Forms k zobrazení dat. Kromě toho můžete využít ovládací prvky označované jako hostitelské ovládací prvky, které jsou nativní objekty v systém Microsoft Office Excel, které byly vylepšeny s událostmi a schopností vazby dat. Další informace naleznete v tématu [Přehled hostitelských položek a hostitelských ovládacích prvků](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

Následující příklad ukazuje, jak přidat ovládací prvky vázané na data v projektech na úrovni dokumentu pomocí návrháře. Příklad přidání ovládacích prvků vázaných na data v projektech na úrovni aplikace v době běhu naleznete v tématu [Návod: složitá datová vazba v projektu doplňku VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>Přidání ovládacího prvku vázaného na data do listu v době návrhu

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Naplnění listu daty z databáze

1. Otevřete projekt na úrovni dokumentu aplikace Excel v aplikaci Visual Studio s listem otevřeným v návrháři.

2. Otevřete okno **zdroje dat** a vytvořte zdroj dat pro projekt. Další informace najdete v tématu [Přidání nových připojení](../data-tools/add-new-connections.md).

3. Přetáhněte pole nebo tabulku z okna **zdroje dat** do listu.

Na listu se vytvoří jeden z následujících ovládacích prvků:

- Pokud přetáhnete pole, na <xref:Microsoft.Office.Tools.Excel.NamedRange> listu se vytvoří ovládací prvek. Další informace naleznete v tématu [NamedRange Control](../vsto/namedrange-control.md).

- Pokud tabulku přetáhnete, na <xref:Microsoft.Office.Tools.Excel.ListObject> listu se vytvoří ovládací prvek. Další informace naleznete v tématu [ListObject Control](../vsto/listobject-control.md).

Můžete přidat jiný ovládací prvek výběrem tabulky nebo pole v okně **zdroje dat** a následným výběrem jiného ovládacího prvku v rozevíracím seznamu.

## <a name="objects-in-the-project"></a>Objekty v projektu

Kromě ovládacího prvku jsou do projektu automaticky přidány následující objekty související s daty:

- Typová datová sada, která zapouzdřuje tabulky dat, ke kterým jste se připojili v databázi. Další informace najdete v tématu [nástroje datové sady v sadě Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).

- <xref:System.Windows.Forms.BindingSource>, Který spojuje ovládací prvek s typovou datovou sadou. Další informace najdete v tématu [Přehled komponent BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- TableAdapter, který připojuje typovou datovou sadu k databázi. Další informace najdete v tématu [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

- TableAdapterManager, který se používá ke koordinaci tabulkových adaptérů v datové sadě za účelem povolení hierarchických aktualizací. Další informace najdete v tématu [Hierarchická aktualizace](../data-tools/hierarchical-update.md) a [TableAdapterManager reference](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Při spuštění projektu ovládací prvek zobrazí první záznam ve zdroji dat. Pomocí nástroje můžete <xref:System.Windows.Forms.BindingSource> uživatelům umožnit procházení záznamů.

### <a name="to-scroll-through-the-records"></a>Procházení záznamů

- Použijte <xref:System.Windows.Forms.BindingSource> metody jako <xref:System.Windows.Forms.BindingSource.MoveNext%2A> a <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> .

Informace o tom, jak odeslat aktualizace typové datové sadě a databázi, naleznete v tématu [How to: Update a data source to data z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Viz také

- [Vázání dat k ovládacím prvkům v řešeních pro systém Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Přidání nových zdrojů dat](../data-tools/add-new-data-sources.md)
- [Vytvoření vazby ovládacích prvků modelu Windows Forms k datům v sadě Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Postupy: Naplnění dokumentů daty z objektů](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Postupy: Naplnění dokumentů daty z databáze](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Postupy: Naplnění dokumentů daty ze služeb](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Postupy: aktualizace zdroje dat s použitím dat z hostitelského ovládacího prvku](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)